Author:  Wayne E. Seguin <wayneeseguin@gmail.com>
License: See LICENSE file.

### Redis Installer NEWS

This has been superceeded by the BDSM redis extension which is far superior in
both scope and functionality.

Maintenance of this project has been discontinued in lieu of the BDSM
extension.

https://github.com/wayneeseguin/bdsm-extensions/
https://github.com/wayneeseguin/bdsm-extensions/tree/master/redis

I strongly advise that you switch to using the BDSM scripting framework for
managing your Redis installation http://bdsm.beginrescueend.com/.

### Installing BDSM

To Install BDSM, as root do:

  [[ ! -d /usr/local/src ]] && mkdir -p /usr/local/src
  cd /usr/local/src
  git clone git://github.com/wayneeseguin/bdsm
  cd bdsm
  ./install

At some point, hopefully soon, this will be a standard download tarball, extract
then install.

### Installing Redis BDSM extension

Note that a better BDSM workflow is forthcoming for extension management.
Until then,

    cd /usr/local/src
    git clone git://github.com/wayneeseguin/bdsm-extensions
    cd bdsm-extensions
    ./extend redis

At some point, hopefully very soon, this will become

    bdsm extend redis

If you do not have git you can install it quickly with another script as root do:

    bash < <( curl http://rvm.beginrescueend.com/install/git )

### Original README

This redis-installer project bootstraps Redis in two scenarios.

Scenario 1.

Installing as a single user

  ∴ ./bin/install-redis

  * As root on localhost (bin/install-redis) this will:

    - Install redis-server and redis-cli to /usr/local/bin/

    - Ensure that redis related directories exist,

      /etc/redis /var/log/redis /var/run/redis /data/redis


    After root installation you can control redis like so:

      ∴ /etc/init.d/redis start # /etc/rc.d on systems like ArchLinux

      ∴ /etc/init.d/redis stop  # /etc/rc.d on systems like ArchLinux

  * As a regular user (great for development) this will:

    - Install redis-server and redis-cli to $HOME/bin/

    - Ensure that redis related directories exist,

      $HOME/.redis/log $HOME/.redis/run $HOME/.redis/data $HOME/.redis/pids $HOME/bin


    After installing as a user, you can start redis like this:

      ∴ ~/bin/redis-server ~/.redis/config/redis.conf

    And then stop redis like this:

      ∴ ~/bin/redis-cli SHUTDOWN

    NOTE: This will improve 'soon' :)

Scenario 2.

Any number of remote hosts (bin/install-redis-on-hosts)

  ∴ ./bin/install-redis-on-hosts root@host1 root@host2

This will Install redis system wide on the remote hosts specified.


