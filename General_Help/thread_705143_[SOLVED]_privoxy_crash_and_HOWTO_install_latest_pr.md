---
title: "[SOLVED] privoxy crash and HOWTO install latest privoxy with checkinstall"
date: 2008-02-23
forum: General Help
---

### Post by Cato2 on 2008-02-23
On Feisty 7.04, Privoxy 3.06-1 kept crashing at some point, probably when nobody was using it (single user desktop and only noticed failure when I returned to PC).  Restarting privoxy was the workaround but this kept happening.  There were no messages about a crash in the privoxy /var/log/privoxy/error or logfile files.

I downloaded source for latest stable version, 3.08-1, from [http://sourceforge.net/project/showfiles.php?group_id=11118](http://sourceforge.net/project/showfiles.php?group_id=11118) and built using default options, and this fixed this issue.

This may also be fixed in hardy's privoxy 3.07, but trying to install that on feisty didn't work.

So, here's how I fixed this by installing it under /usr/local -  checkinstall makes it quite easy to do this and builds a .deb file for easy installation and removal at a later date.

Some notes:

[LIST]
[*]I've used wajig  for convenience as the aptitude command didn't seem to work in some cases (probably my lack of familiarity).  wajig is a bit like apt-get, aptitude and dpkg combined, but easier to use in some cases.
[*]I've used dpkg-divert - this useful but slightly confusing command is used to ensure that next time someone tries to install privoxy from the repositories, they don't trample on the /etc/init.d/privoxy file used here, which has our own configuration.
[*]All commands assume you have done "sudo su -" to get into a root shell.
[*]Assumes you already have privoxy installed - if not, you will need to add a privoxy user (using adduser, set to no shell and locked password) for this to work.
[*]The result of this is that your existing privoxy setup will be completely REMOVED.  Be sure to back up any config files before you do this - primary files to backup are usually in /etc/privoxy, i.e. config and user.action.
[*]I did this on Ubuntu Feisty 7.04, but this should work on almost any Ubuntu version - privoxy is quite a simple package and this HOWTO uses fairly standard commands (apart from wajig, which is not essential)
[/LIST] 
This HOWTO is not 100% accurate as it's been partly reconstructed from my notes and shell history, but it should make it **much easier** for you to get privoxy installed in a safe way that doesn't break in future.

Since we are using checkinstall here, you can simply use 'apt-get remove privoxy' to cleanly remove the version you've installed here at some point in the future, and you could even install on other systems using the dpkg command on the .deb file - not as nice as a real Ubuntu package, but not bad.

```

# get into a root shell
sudo su -

# install make, GCC etc
aptitude install build-essential

# install some tools used in install
aptitude install wajig checkinstall

# Diversion - on next privoxy installation via apt or dpkg, move RH file to LH filename - inverse of mv, cp and ln!
dpkg-divert --rename --divert /etc/init.d/privoxy.ubuntu-diverted /etc/init.d/privoxy

# WARNING: back up config files in /etc/privoxy and /etc/init.d/privoxy, if changed...
# Must do purge to avoid wrong files being left
aptitude purge privoxy

# Create a .deb package for install under /usr/local, with privoxy already installed from Ubuntu repositories

# Unpack the source under /root/src/privoxy/privoxy-3.0.8-stable using tar xzvf

# Configure the package for compilation - lots of output, generates makefile
# in GNUmakefile, automatically changes /usr/local/var to be /var
./configure

# Build
make

# Instead of make install, use checkinstall - must specify package version without '-' 
# or the deb build part complains no digits in 'stable'...
sudo -u privoxy checkinstall --install=no  --pkgname=privoxy --pkgversion=3.0.8stable_local --pakdir=..

cd ..
dpkg --info privoxy_3.0.8stable_local-1_i386.deb

dpkg --contents privoxy_3.0.8stable_local-1_i386.deb | less

dpkg --dry-run -i  privoxy_3.0.8stable_local-1_i386.deb

# Finally do the install:
dpkg -i  privoxy_3.0.8stable_local-1_i386.deb

# Check files installed
wajig listfiles privoxy

# Ensure that  our daemon is started up
cp   /etc/init.d/privoxy.ubuntu-diverted  /etc/init.d/privoxy
# EDIT NEW COPY OF FILE to point paths at to the top to the privoxy binary in /usr/local/sbin and
# the privoxy config file in /usr/local/etc/privoxy - startup is identical to standard Ubuntu package apart from this.

# Prevent future upgrades over top of this package
wajig hold privoxy
wajig listhold

# Now configure privoxy - restore into /usr/local/etc/privoxy/ the *changes* you made to the original config and user.action files.

# start daemon
/etc/init.d/privoxy restart

# Check the /var/log/privoxy files for any errors and startup issues, and check privoxy is running
ps aux | grep privoxy | grep -v grep

```

---

