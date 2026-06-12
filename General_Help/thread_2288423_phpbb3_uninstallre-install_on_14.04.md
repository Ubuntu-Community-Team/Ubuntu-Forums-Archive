---
title: "phpbb3 uninstall/re-install on 14.04"
date: 2015-07-27
forum: General Help
---

### Post by thetrickster2 on 2015-07-27
Hi,

Installed phpbb3 via apt, went to make a few changes and borked the install somewhere.

Decided to do an apt-get remove phpbb3 which deleted it, but now upon re-install it throws this:

Preconfiguring packages ...
Selecting previously unselected package phpbb3.
(Reading database ... 84739 files and directories currently installed.)
Preparing to unpack .../phpbb3_3.0.12-1_all.deb ...
Unpacking phpbb3 (3.0.12-1) ...
Setting up phpbb3 (3.0.12-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpbb3.conf

Creating config file /etc/dbconfig-common/phpbb3.conf with new version

Creating config file /etc/phpbb3/database.inc.php with new version
granting access to database phpbb3 for phpbb3@localhost: already exists.
creating database phpbb3: success.
verifying database phpbb3 exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password
Setting admin password
Not replacing deleted config file /etc/phpbb3/apache2.conf
dpkg: error processing package phpbb3 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 phpbb3
E: Sub-process /usr/bin/dpkg returned an error code (1)

Have tried an rm -f of /etc/phpbb3/apache2.conf, even checking after doing another apt-get remove (which works) the dir /etc/phpbb3 doesn't even exist. What is refering to this config file?

Any help much appreciated!

---

