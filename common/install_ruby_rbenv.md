---
title: Installing Ruby using rbenv
---

This topic describes how to install Ruby using rbenv.

<p class="note"><strong>Note</strong>: You can also build Ruby using the ruby-build plugin for rbenv. For more information, see <a href="https://github.com/sstephenson/ruby-build">https://github.com/sstephenson/ruby-build</a>.</p>

1. Use the following command to install Ruby dependencies:
  <pre class="terminal">
    $ sudo apt-get install git-core build-essential libsqlite3-dev curl libmysqlclient-dev \
libxml2-dev libxslt-dev libpq-dev zlib1g-dev openssl libssl-dev
  </pre>

1. Clone the rbenv repository from GitHub:
  <pre class="terminal">
    $ git clone git://github.com/sstephenson/rbenv.git .rbenv
  </pre>

1. Add `~/.rbenv/bin` to your `$PATH` to allow you to run the rbenv
command-line utility:
  <pre class="terminal">
    $ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
  </pre>

1. Add `rbenv init` to your shell to enable shims and autocompletion:
  <pre class="terminal">
    $ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
  </pre>

1. Download Ruby 1.9.3 or 2.1.2.
  * For Ruby 1.9.3, run the following command:
    <pre class="terminal">
      $ wget http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p550.tar.gz
    </pre>
  * For Ruby 2.1.2, run the following command:
    <pre class="terminal">
      $ wget http://ftp.ruby-lang.org/pub/ruby/2.1/ruby-2.1.2.tar.gz
    </pre>

1. Run the commands below to unpack and install Ruby.
  * For Ruby 1.9.3, run the following commands:
    <pre class="terminal">
      $ tar xvfz ruby-1.9.3-p550.tar.gz
      $ cd ruby-1.9.3-p550
      $ ./configure --prefix=$HOME/.rbenv/versions/1.9.3-p550
      $ make
      $ make install
      </pre>
  * For Ruby 2.1.2, run the following commands:
    <pre class="terminal">
      $ tar xvfz ruby-2.1.2.tar.gz
      $ cd ruby-2.1.2
      $ ./configure --prefix=$HOME/.rbenv/versions/2.1.2
      $ make
      $ make install
    </pre>

1. Restart your shell:
  <pre class="terminal">
    $ source ~/.bash_profile
  </pre>

1. Set your default Ruby version.
  * For Ruby 1.9.3, run the following command:
    <pre class="terminal">
      $ rbenv global 1.9.3-p550
    </pre>
  * For Ruby 2.1.2, run the following command:
    <pre class="terminal">
      $ rbenv global 2.1.2
    </pre>

1. You may need to reinstall a rake gem when using this method. If so, run the following command:
  <pre class="terminal">
    $ gem pristine rake
  </pre>

1. Use the following commands to update rubygems, install bundler, and add new
shims:
  <pre class="terminal">
    $ rbenv rehash
    $ gem update --system
    $ gem install bundler
    $ rbenv rehash
  </pre>