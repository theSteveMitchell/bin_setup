Bin Setup
=========

Based on idea By [Brightbit](http://brightbit.com).

This is a fork of Brightbit's setup script.  The script is written in ruby instead of bash for cleanliness.  We also dropped Brightbit's assumption about Heroku and Dorenv, because I never use those.  

Make new developers like you.

**Bin Setup** aims to easily setup your Rails 4.2 app on a new machine. It also helps reset your app back to a clean state. It will reset redis, memcache and your postgres database.

## Installation

Create a bin/setup (or script/setup) file in your Rails project. From the root of your project run:

```bash
echo 'bash -c "$(curl -sL https://raw.github.com/thestevemitchell/bin_setup/master/bin/setup)"' > bin/setup
chmod +x bin/setup
```

## Usage

#### Running bin/setup:

```bash
bin/setup
```


Which should look something like this:

```bash
$ bin/setup
Installing libraries...
Flushing Memcache...
Flushing Redis...
Reloading the database...
All done!
10.477s total, 5.11s user, 1.28s system, 61% cpu
$
```

This will run `bundle install` (and install bundler if it doesn't exist) and many other commands to bootstrap your app. Documentation is currently lacking so please [browse the source](https://github.com/brightbit/bin_setup/blob/master/bin/setup) to get an idea of what's going on.

**Note:** If you have any problems tail the log: `tail -f log/setup.log`

**Note:** Since Rails 3 uses a `script` directory instead of `bin`, you will need to run `script/setup` instead of `bin/setup`. You could create a `bin` directory and pretend you're using Rails 4 if you'd like.

#### Installing dependencies:

it just does them by default...

## Your Project's README

You'll probably want to make note of how to get started on your project. Here's a simple README to get started:

```markdown

Welcome to the team
===================

To get started run:
    cd ~/Code
    git clone https://github.com/brightbit/project_abc.git # First time you'll need user/pass (then add it to keychain)
    cd project_abc
    bin/setup
    heroku config -s # Set the variables in .env from here
    rails s # And open http://localhost:3000
```

We are entertaining the idea of using something like `heroku config -s > .env`. If you do [let us know](mailto:hello@brightbit.com) how it works out.

## Information
### Conventions

Bin setup assumes you are using:
* Mac OS X (Probably Mountain Lion+) (Debian/Ubuntu pull requests are welcomed)
* [Homebrew](http://mxcl.github.io/homebrew/) for installing packages (e.g. postgres, redis, memcache)
* [Bundler](http://gembundler.com/) with binstubs at vendor/bundle/bin. It installs and runs bundle install (setting your binstubs up for you).
* [Brewdler](https://github.com/andrew/brewdler) - It installs and runs brewdle.
* `.git/safe/../../bin` in your `$PATH`; [See](https://github.com/ericboehs/dotfiles/blob/dd4554382f0344c9a5da9ae77e9f2ac445c25df1/shell/zsh/zshrc#L47-49)


It also assumes you:
* Have more than 512MB of RAM (alluding to the next point)
* Don't mind auto running homebrew's lightweight configs of postgres, memcache and redis
* Have a Gemfile, and Brewfile checked into your repo
* You like snickers.

### Todo

* Add databases.rake override files (4.x) for resetting the DB while rails is running
* Make it happy with pow (it already is but I think you have to symlink .powenv to .env)


### Bug reports

If you discover any bugs, feel free to create an issue on GitHub. Please add as much information as
possible to help us fixing the possible bug. We also encourage you to help even more by forking and
sending us a pull request.

https://github.com/brightbit/bin_setup/issues

## Maintainers

* Eric Boehs (https://github.com/ericboehs)

## License

MIT License. Copyright 2013 Brightbit. http://brightbit.com

You are not granted rights or licenses to the trademarks of Brightbit.
