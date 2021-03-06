Hike
====

Hike is a Ruby library for finding files in a set of paths. Use it to
implement search paths, load paths, and the like.

# Examples

Find Ruby files in this project:

    trail = Hike::Trail.new "/Users/sam/Projects/hike"
    trail.extensions.push ".rb"
    trail.paths.push "lib", "test"

    trail.find "hike/trail"
    # => "/Users/sam/Projects/hike/lib/hike/trail.rb"

    trail.find "test_trail"
    # => "/Users/sam/Projects/hike/test/test_trail.rb"

Explore your Ruby load path:

    trail = Hike::Trail.new "/"
    trail.extensions.push ".rb", ".bundle"
    trail.paths.replace $:

    trail.find "net/http"
    # => "/Users/sam/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/1.8/net/http.rb"

    trail.find "strscan"
    # => "/Users/sam/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/1.8/i686-darwin10.4.0/strscan.bundle"

Explore your shell path:

    trail = Hike::Trail.new "/"
    trail.paths.replace ENV["PATH"].split(":")

    trail.find "ls"
    # => "/bin/ls"

    trail.find "gem"
    # => "/Users/sam/.rvm/rubies/ree-1.8.7-2010.02/bin/gem"

# Installation

    $ gem install hike

# License

Copyright (c) 2010 Sam Stephenson.

Released under the MIT license. See `LICENSE` for details.
