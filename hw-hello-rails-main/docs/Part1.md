## Verify you have Ruby, Rails, and Heroku CLI installed


1. Run `ruby -v` to check your Ruby version
2. Run `rails -v` to check your Rails version 
3. Run `bundle -v` to check your Bundler version. If `bundle -v` fails, run `gem install bundler` to install it. (Normally, though, installing the `rails` gem will also install `bundler`.)
4. Run `heroku -v` to verify the `heroku` [command line tool](https://devcenter.heroku.com/articles/heroku-cli) has been installed in the development environment.  If not, the link has instructions for how to install it.

## Create a new Rails app

You  may find the Rails [online documentation](https://api.rubyonrails.org/) useful during this assignment.

Now that you have Ruby and Rails installed, create a new, empty Rails app with the command: 
```sh
rails new rottenpotatoes --skip-test-unit --skip-turbolinks --skip-spring
```

The options tell Rails to omit three aspects of the new app:

* Rather than Ruby's `Test::Unit` framework, in a future assignment we will instead create tests using the RSpec framework.

* Turbolinks is a piece of trickery that uses AJAX behind-the-scenes to speed up page loads in your app.  However, it causes so many problems with JavaScript event bindings and scoping that we strongly recommend against using it.  A well-tuned Rails app should not benefit much from the type of speedup Turbolinks provides.

* Spring is a gem that keeps your application "preloaded" making it faster to restart once stopped.  However, this sometimes causes unexpected effects when you make changes to your app, stop and restart, and the changes don't seem to take effect.  On modern hardware, the time saved by Spring is minimal, so we recommend against using it.

If you're interested, `rails new --help` shows more options available when creating a new app.


If all goes well, you'll see several messages about files being created, ending with `run bundle install`, which may take a couple of minutes to complete. You can now `cd` to the newly-created `rottenpotatoes` directory, called the **app root** directory for your new app.  From now on, unless we say otherwise, all file names will be relative to the app root.  Before going further, spend a few minutes examining the contents of the new app directory `rottenpotatoes` to remind yourself with some of the directories common to all Rails apps.

What about that message `run bundle install`?
Recall that Ruby libraries are packaged as "gems", and the tool `bundler` (itself a gem) tracks which versions of which libraries a particular app depends on. Open the file called `Gemfile` --it might surprise you that there are already gem names in this file even though you haven't written any app code, but that's because Rails itself is a gem and also depends on several other gems, so the Rails app creation process creates a default `Gemfile` for you.  For example, you can see that `sqlite3` is listed, because the default Rails development environment expects to use the SQLite3 database.

OK, now change into the directory of the app name you just created (`cd rottenpotatoes`) to continue...

## Specify Ruby version

It is a good practice to specify the Ruby version you are using in the `Gemfile`. Run `ruby -v` in the terminal to check the version you are using. In the `Gemfile`, add `ruby '<version>'` below `source 'https://rubygems.org'`.

<!--
## Work around the SQLite3 gem bug in v1.4

Rails uses the SQLite3 database as the default for development and testing. Unfortunately, versions of the SQLite3 gem starting with 1.4.0 introduced a bug that make it no longer work properly with Rails.  To work around this, we must force Rails to use an earlier version, namely any version beginning with 1.3.  Locate the line in the `Gemfile` that specifies the `sqlite3` gem and change it to read as follows:

`gem 'sqlite3', '~> 1.3.0'`

Then run `bundle update` and verify that its output contains "Fetching sqlite3 1.3.x" and "Installing sqlite3 1.3.x" where x is any minor version.
--->

## Check your work

To make sure everything works, run the app locally.  (It doesn't do anything yet, but we can verify that it is running and reachable!)

Follow the instructions below to run and preview a Rails app locally. When you visit the app's home page, you should see the generic Ruby on Rails landing page, which is actually being served by your app.  Later we will define our own routes so that the "top level" page does not default to this banner.


1. Start the app in a terminal: `rails server`  (omit `-b 0.0.0.0`)
2. Open a regular browser window to `localhost:3000/` to visit the app's home page (note the `:3000` rather than `-3000`)


## Commit your work
At this stage, everything is working. You should initialize a git repo in your app's folder and commit your changes. Note that when you created the app, Rails added a `.gitignore` file to prevent git from tracking unnecessary files.

```sh
cd rottenpotatoes
git init
git add -A
git commit -m "init commit"
```

## Next
[Part 2](Part2.md)
