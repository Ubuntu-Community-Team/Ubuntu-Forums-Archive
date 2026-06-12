---
title: "[SOLVED] System-Administration locked out"
date: 2008-02-05
forum: General Help
---

### Post by billmoss on 2008-02-05
I access Via the rat System--Administration--??? (e.g., network).
When asked for my password, I mistype it.
I am than locked out from the system admin for what appears to be a rather long time.

This is more than a little annoying. I have been trying not to use the root user account (which I activated) since the Ubuntu system is mostly run so I can gain experience with a system that Windows users can migrate to.

su - works fine as does Sudu (checked /etc/sudoers) so the timeout and lock out criteria must be in another 'conf' file.

How can I reset this and/or is there a Gnome equivalent to kcontrol.

Thanks!!

reply to me offline if you prefer at [email]billmoss@acm.org[/email]

---

### Post by Zwack on 2008-02-05
It might be a PAM issue.  pam_unix by default gives a 2 second delay when authentication fails.  You might want to look at the pam_unix man page and consider editing some of the files in /etc/pam.d.

Z.

---

### Post by billmoss on 2008-02-06
OK
For whatever reason, the problem disappeared after the last reboot.
Now, I have a problem that has occurred before, the infamous 'gksu ????' problem from the system menu where some dbus back end applications will deny you access.

I have tried all the suggestions going back to 2006, none worked.

I checked /etc/sudoers and it too is fine as is the PAM configuration.

Permissions on the files in question seem OK, though there is no setuid or setgid set and I cannot find documentation on the need for this.

I cannot find a great deal of information with regards to the configuration files for dbus (/etc/dbus-1/.... and especially the the back ends configuration file.

Note, when I run
gksu network-admin 
from the command line, I get a error message indicating a problem communicating with the back end and with the Perl extension module.

This is very annoying. The idea of Ubuntu was to see if there was a Linux system that I could recommend to others as a replacement for MS Windows. Modifying conf files is in the same league as modifying the registry for the average user and not a good idea.

Note:
I'm running Gnome on this machine since KDE has some issues with certain music CD's and the Gnome desktop seemed more aimed at the Windows user. I don't know if the problem is specific to Gnome.

---

### Post by billmoss on 2008-02-07
OK
I figured it out with some considerable hacking.
To whit:

At a command prompt, I set ''xhost +local:' so the root user could get at the display.

Running 'network-admin' at the command prompt gave more information. It indicated that the Perl back end was not working.

I looked at the Perl script and noticed that it was using env(1) to get to Perl. This is not always a good idea since the version of perl it gets may not be correct for the Perl modules (libraries) that are included.

I changed the first line to a hard coded perl location
#! /usr/bin/perl
and now everything works fine.:)

---

