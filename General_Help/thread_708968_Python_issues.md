---
title: "Python issues"
date: 2008-02-27
forum: General Help
---

### Post by biggeek on 2008-02-27
Using Gutsy, installed [Zenoss,]("http://www.zenoss.com/community/docs/install-guides/install-on-ubuntu-7.04/") and any applets based on python scripts won't work any longer.

If I go to Add/Remove programs, I get [I]"Failed to execute child process "/usr/bin/gnome-app-install" (No such file or directory)"
[/I]
-or-

[I] apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/I]

-or-

An update for gimp came out (gimp-python) which now shows a broken dependency. If I try to upgrade it, Synaptic says:

*E: /var/cache/apt/archives/gimp-python_2.4.2-0ubuntu0.7.10.1_i386.deb: subprocess new pre-removal script returned error exit status 127*

with the details of:

[I]Preparing to replace gimp-python 2.4.0~rc3-1ubuntu7 (using .../gimp-python_2.4.2-0ubuntu0.7.10.1_i386.deb) ...
/var/lib/dpkg/info/gimp-python.prerm: 6: update-python-modules: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: not found
dpkg: error processing /var/cache/apt/archives/gimp-python_2.4.2-0ubuntu0.7.10.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/gimp-python_2.4.2-0ubuntu0.7.10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-app-install (0.4.13-0ubuntu1) ...
/var/lib/dpkg/info/gnome-app-install.postinst: 8: pycentral: not found
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 127
Setting up deskbar-applet (2.20.1-0ubuntu1) ...
/var/lib/dpkg/info/deskbar-applet.postinst: 11: gconf-schemas: not found
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tomboy (0.8.0-1ubuntu0.1) ...
[/I]

All these are separate issues, but they are all pointing back (as far as I can tell) to Python. 

I compared what is running in the LiveCD version of Gutsy to what's running on my laptop, and the significance seems to be that 2.4 Minimal is installed on the laptop, but if I try to uninstall it, I get this:

[I]E: python2.4-minimal: subprocess pre-removal script returned error exit status 1
[/I]
with details:

[I]Can't exec "lsb_release": No such file or directory at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 78, <> line 1.
(Reading database ... 130259 files and directories currently installed.)
Removing python2.4 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 129753 files and directories currently installed.)
Removing python2.4-minimal ...
Unlinking and removing bytecode for runtime python2.4
dpkg: error processing python2.4-minimal (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 python2.4-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-app-install (0.4.13-0ubuntu1) ...
/var/lib/dpkg/info/gnome-app-install.postinst: 8: pycentral: not found
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 127
Setting up deskbar-applet (2.20.1-0ubuntu1) ...
/var/lib/dpkg/info/deskbar-applet.postinst: 11: gconf-schemas: not found
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tomboy (0.8.0-1ubuntu0.1) ...
/var/lib/dpkg/info/tomboy.postinst: 26: gconf-schemas: not found
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 gnome-app-install
 deskbar-applet
 tomboy



[/I]
I'm officially stumped.

---

