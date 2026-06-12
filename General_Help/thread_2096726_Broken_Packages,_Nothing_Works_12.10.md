---
title: "Broken Packages, Nothing Works 12.10"
date: 2012-12-20
forum: General Help
---

### Post by Goast on 2012-12-20
I'm running Xubuntu 12.10, while trying to download Java 6 (Oracles) I got this little problem.

dpkg: warning: files list file for package 'libgtk2.0-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcanberra-gtk3-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcanberra-gtk3-module:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk2-trayicon-perl' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libcanberra0:i386' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

I can't fix this
apt-get -f install returns the same error
apt-get clean doesn't work
dpkg --configure -a yields no results.

How do I simply removed these packages?
apt-get remove returns same error.

Also why does this happen so often?  Why does the updater have such trouble with dependency?  Any help?  I'm quiet tired of re-installing this operating system.  And now I can't install anything else, which makes even less sense to how this was designed.  So IS there a way to fix it?

---

