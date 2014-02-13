# MaxCDN is Hiring!

Do you like building cool stuff?  Do APIs keep you up at night? We're looking for our next superstar hacker and you could be it. Interested? Check out our job posting on [stackoverflow](http://careers.stackoverflow.com/jobs/37078/senior-web-engineer-for-fun-growing-la-startup-maxcdn&a=JdFbT4OY).

# MaxCDN REST Web Services Ruby Client

[![Build Status](https://travis-ci.org/MaxCDN/ruby-maxcdn.png?branch=master)](https://travis-ci.org/MaxCDN/ruby-maxcdn) &nbsp; [![Gem Version](https://badge.fury.io/rb/maxcdn.png)](http://badge.fury.io/rb/maxcdn)

## Installation

``` bash
gem install maxcdn
```

#### With Bundler

```
bundle init
echo "gem 'maxcdn'" >> Gemfile
bundle install --path vendor/bundle
```

## Usage
```ruby
require 'maxcdn'

api = MaxCDN::Client.new("myalias", "consumer_key", "consumer_secret")

####
# Turn on debugging for underlying Curl::Easy and CurbFu modules
#
# api.debug = true

api.get("/account.json")
```

## Methods
It has support for `GET`, `POST`, `PUT` and `DELETE` OAuth 1.0a signed requests.

```ruby
# To create a new Pull Zone
api.post("/zones/pull.json", {'name' => 'test_zone', 'url' => 'http://my-test-site.com'})

# To update an existing zone
api.put("/zones/pull.json/1234", {'name' => 'i_didnt_like_test'})

# To delete a zone
api.delete("/zones/pull.json/1234")

# To purge a file (robots.txt) from cache
api.delete("/zones/pull.json/1234/cache", {"file" => "/robots.txt"})
```

### We now have a shortcut for Purge Calls!
```ruby
zone_id = 12345

# Purge Zone
api.purge(zone_id)

# Purge File
api.purge(zone_id, '/some_file')

# Purge Files
api.purge(zone_id, ['/some_file', '/another_file'])
```


## Development Quick Start

``` bash
# get it
git clone git@github.com:<fork repo>/ruby-maxcdn.git

# setup
cd ruby-maxcdn
bundle install --path vendor/bundle

# unit tests
bundle exec ruby ./test/test.rb

# integration tests
export ALIAS=<your alias>
export KEY=<your key>
export SECRET=<your secret>
bundle exec ruby ./test/integration.rb # requires host's IP be whitelisted
```

