---
title: "New problem that causing my pakage failure"
date: 2006-10-30
forum: General Help
---

### Post by Tobster on 2006-10-30
It because of a Sun Java install failure :)  in the terminal this what i get after the apt-get command:

toby@toby-desktop:~$ apl-get
bash: apl-get: command not found
toby@toby-desktop:~$ apt-get
apt 0.6.45ubuntu14 for linux i386 compiled on Sep 27 2006 23:43:26
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
toby@toby-desktop:~$

---

### Post by ~LoKe on 2006-10-30
I don't see a problem.

---

### Post by Tobster on 2006-10-30
I got this message too...

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

---

### Post by Tobster on 2006-10-30
Here a screen shot

---

### Post by blind0wl on 2006-10-30
Have a look here:

[http://www.ubuntuforums.org/showthread.php?t=247800&highlight=apt-get+broken+filter]("http://www.ubuntuforums.org/showthread.php?t=247800&highlight=apt-get+broken+filter")

Try using the search function next time.

Cheers

Blindy

---

### Post by Tobster on 2006-10-30
Thanks

---

