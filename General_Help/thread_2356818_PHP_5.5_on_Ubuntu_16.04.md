---
title: "PHP 5.5 on Ubuntu 16.04"
date: 2017-03-27
forum: General Help
---

### Post by darek88 on 2017-03-27
I have a problem with installation PHP 5.5. I added PHP repo and when I try to install, I received message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'php5.5-libsodium' for regex 'php5.5'
Note, selecting 'php5.5-tideways' for regex 'php5.5'
Note, selecting 'php5.5-xhprof' for regex 'php5.5'
Note, selecting 'php5.5-gmagick' for regex 'php5.5'
Note, selecting 'php5.5-smbclient' for regex 'php5.5'
Note, selecting 'php5.5-mongo' for regex 'php5.5'
Note, selecting 'php5.5-geoip' for regex 'php5.5'
Note, selecting 'php5.5-uuid' for regex 'php5.5'
Note, selecting 'php5.5-oauth' for regex 'php5.5'
Note, selecting 'php5.5-radius' for regex 'php5.5'
Note, selecting 'php5.5-rrd' for regex 'php5.5'
Note, selecting 'php5.5-memcache' for regex 'php5.5'
Note, selecting 'php5.5-uploadprogress' for regex 'php5.5'
Note, selecting 'php5.5-xcache' for regex 'php5.5'
Note, selecting 'php5.5-yac' for regex 'php5.5'
Note, selecting 'php5.5-yaml' for regex 'php5.5'
Note, selecting 'php5.5-zmq' for regex 'php5.5'
Note, selecting 'php5.5-raphf' for regex 'php5.5'
Note, selecting 'php5.5-msgpack' for regex 'php5.5'
Note, selecting 'php5.5-gearman' for regex 'php5.5'
Note, selecting 'php5.5-ssh2' for regex 'php5.5'
Note, selecting 'php5.5-propro' for regex 'php5.5'
Note, selecting 'php5.5-amqp' for regex 'php5.5'
Note, selecting 'php-radius' instead of 'php5.5-radius'
Note, selecting 'php-uploadprogress' instead of 'php5.5-uploadprogress'
Note, selecting 'php-yaml' instead of 'php5.5-yaml'
Note, selecting 'php-ssh2' instead of 'php5.5-ssh2'
Note, selecting 'php-amqp' instead of 'php5.5-amqp'
Note, selecting 'php-rrd' instead of 'php5.5-rrd'
Note, selecting 'php-uuid' instead of 'php5.5-uuid'
Note, selecting 'php-memcache' instead of 'php5.5-memcache'
Note, selecting 'php-gmagick' instead of 'php5.5-gmagick'
Note, selecting 'php-smbclient' instead of 'php5.5-smbclient'
Note, selecting 'php-zmq' instead of 'php5.5-zmq'
Note, selecting 'php-msgpack' instead of 'php5.5-msgpack'
Note, selecting 'php-geoip' instead of 'php5.5-geoip'
Note, selecting 'php-tideways' instead of 'php5.5-tideways'
Note, selecting 'php-yac' instead of 'php5.5-yac'
Note, selecting 'php-libsodium' instead of 'php5.5-libsodium'
Note, selecting 'php-oauth' instead of 'php5.5-oauth'
Note, selecting 'php-propro' instead of 'php5.5-propro'
Note, selecting 'php-raphf' instead of 'php5.5-raphf'
Note, selecting 'php-gearman' instead of 'php5.5-gearman'
Note, selecting 'php-xcache' instead of 'php5.5-xcache'
Note, selecting 'php-mongo' instead of 'php5.5-mongo'
Note, selecting 'php-xhprof' instead of 'php5.5-xhprof'

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php-yac : Conflicts: php-xcache but 3.2.0-2+deb.sury.org~xenial+1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Unfortunately I need this version and I can't install this. Can anyone help me because I can't find sollution for "php-yac : Conflicts: php-xcache but 3.2.0-2+deb.sury.org~xenial+1 is to be installed"

---

### Post by howefield on 2017-03-27
Welcome to the forum, thread moved to the "*General Help*" forum and quote tags change to code tags.

---

