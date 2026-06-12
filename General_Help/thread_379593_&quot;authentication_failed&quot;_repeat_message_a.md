---
title: "&quot;authentication failed&quot; repeat message at login screen"
date: 2007-03-08
forum: General Help
---

### Post by bishman on 2007-03-08
Hi

I'm using Ubuntu Edgy and recently installed xubuntu-desktop and its dependancies (with synaptic), just to see what Xfce was like. After checking out the Xfce desktop, I rebooted. But when my login screen appears I can't type anything in as all I get is a recurring message saying "authentication failed". So I Ctrl-Alt-F1 to shell and try and login as root but it returns 'login incorrect' without prompting for my password. Same for my username.

At this stage, I manage to login to shell by pressing the power button on my compaq and it prompts for root password for mantainence (or ctrl-D to continue). So I enter root password and thats fine from there.

I have tried dpkg-reconfigure xserver-xorg - thought maybe it was thinking the 'enter key' was being pressed on the login screen when it actually wasn't, but no luck.

Could it be that xubuntu-desktop or one of it's dependencies locked me out of X like this? or something else perhaps?

Will I have to re-install? If so, could I re-install as little as possible so I don't have to start from scratch?

Please shed some light (I dis-like windows!). Cheers!

Edit: I have since remove Xubuntu-desktop and I also apt-get autoremove 'd also, with no luck.

---

### Post by bishman on 2007-03-09
Nevermind,

A day was too long to go without my Ubuntu so I have reinstalled. If wanyone could explain how it may have happened, it would be interesting to know.

Thanks

---

### Post by garbergs on 2007-03-13
Hi!

I have the same problem, but it appeared in a different situation. On boot, the fsck found problems on my hard drive, something like this:

UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
THEN REBOOT BY PRESSING CTRL-D

So I started fsck, and it went through some errors where I answered yes to all questions:

Unattached inode 912684
Connect to /lost+found<y>?

Inode 912684 ref count is 2, should be 1. Fix<y>?

And then something about "bitmap differences", with question to fix? (yes).

Somewhere in the errors the file /etc/pam.d/security was mentioned, and fixed.

After this was finished, it said: FILE SYSTEM WAS MODIFIED, REBOOT

So i pressed Ctrl-D, the reboot went fine, but in the login splash screen, I get the "Authentication failed" message window. The box where I'm supposed to enter my user name is faded and contains three dots. I can't enter anything. When I press OK on the message window, I get about 2 seconds where I can click on the Language and Session options, but I can't modify the login box.

-------

I'm unfortunately a Linux noob, but I've looked through the forum and managed a little progress: 

I can get into recovery mode from the Grub menu by pressing ESC on boot. 
"df -h" shows that the main (and only) partition /dev/hda1 use 46% (Some people had login problems due to full hard drives). 
"startx" works, but gives an error message window: "Internal error: failed to initialize HAL!". That doesn't matter, it seems.

So what do I do now?
Is it possible that some important system file was changed by fsck, for example in the /etc/pam.d directory?
Is there a way to get the latest fsck log?

sincerely
Henrik

---

### Post by bishman on 2007-03-13
Hi there!



Glad i'm not alone in this.


Come to think of it, my system did the same thing with fsck just before it happened. I didn't noticed if it changed anything because there was soooo much to fix during it, but after a quick google of pam.d, you might be onto something. Look here: [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/old/pam-4.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/old/pam-4.html)

Please be weary as i'm a noob too but check out the files within /etc/pam.d and see if anything is unusual.

For example:
use
```
 nano -w /etc/pam.d/login 
``` (remember if you want to edit anything in the file use 'sudo nano...')
and see how it compares to mine:

#
# The PAM configuration file for the Shadow `login' service
#

# Outputs an issue file prior to each login prompt (Replaces the
# ISSUE_FILE option from login.defs). Uncomment for use
# auth       required   pam_issue.so issue=/etc/issue

# Disallows root logins except on tty's listed in /etc/securetty
# (Replaces the `CONSOLE' setting from login.defs)
auth       requisite  pam_securetty.so

# Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
auth       requisite  pam_nologin.so

# This module parses environment configuration file(s)
# and also allows you to use an extended config
# file /etc/security/pam_env.conf.
# 
# parsing /etc/environment needs "readenv=1"
session       required   pam_env.so readenv=1
# locale variables are also kept into /etc/default/locale in etch
# reading this file *in addition to /etc/environment* does not hurt
session       required   pam_env.so readenv=1 envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# This allows certain extra groups to be granted to a user
# based on things like time of day, tty, service, and user.
# Please edit /etc/security/group.conf to fit your needs
# (Replaces the `CONSOLE_GROUPS' option in login.defs)
auth       optional   pam_group.so

# Uncomment and edit /etc/security/time.conf if you need to set
# time restrainst on logins.
# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs
# as well as /etc/porttime)
# account    requisite  pam_time.so

# Uncomment and edit /etc/security/access.conf if you need to
# set access limits.
# (Replaces /etc/login.access file)
# account  required       pam_access.so

# Sets up user limits according to /etc/security/limits.conf
# (Replaces the use of /etc/limits in old login)
session    required   pam_limits.so

# Prints the last login info upon succesful login
# (Replaces the `LASTLOG_ENAB' option from login.defs)
session    optional   pam_lastlog.so

# Prints the motd upon succesful login
# (Replaces the `MOTD_FILE' option in login.defs)
session    optional   pam_motd.so

# Prints the status of the user's mailbox upon succesful login
# (Replaces the `MAIL_CHECK_ENAB' option from login.defs). 
#
# This also defines the MAIL environment variable
# However, userdel also needs MAIL_DIR and MAIL_FILE variables
# in /etc/login.defs to make sure that removing a user 
# also removes the user's mail spool file.
# See comments in /etc/login.defs
session    optional   pam_mail.so standard

# Standard Un*x account and session
@include common-account
@include common-session
@include common-password

**************************************************

Hopefully someone more experienced will know more about the pam.d services and what you could do to fix it.

---

### Post by bishman on 2007-03-14
try reinstalling the pam library packages:
```
sudo apt-get udpate
sudo aptitude reinstall libpam0g libpam-modules libpam-runtime 
```

you could also try 'aptitude purge' the above packages then 'aptitude install' them again.

---

### Post by garbergs on 2007-03-15
My system works again! Full story here:

First I compared my /etc/pam.d/login file with yours, and it looked similar but with different order of some lines. And my file seemed longer, more lines. Could be because I'm using Breezy 5.10 and you have Edgy I believe?

So then I did this:
```

aptitude reinstall libpam0g libpam-modules libpam-runtime

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages will be REINSTALLED:
  libpam-modules libpam-runtime libpam0g
0 packages upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 281kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 http://se.archive.ubuntu.com breezy/main libpam-modules 0.7 6-22ubuntu3 [148kB]
Get:2 http://se.archive.ubuntu.com breezy/main libpam-runtime 0.7 6-22ubuntu3 [59.8kB]
Get:3 http://se.archive.ubuntu.com breezy/main libpam0g 0.76-22ub untu3 [73.8kB]
Fetched 281kB in 10s (27.0kB/s)
E: Internal Error, Could not perform immediate configuration (2) on libpam0g
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
```

So then I tried without libpam0g:
```

aptitude reinstall libpam-modules libpam-runtime

```
That went fine. 
Then this:
```

aptitude purge libpam0g

```
A lot of modules and apps were listed as "will also be removed", including openoffice, my postgres installation and some more things that really is the reason why I don't want to make a fresh install of Ubuntu. I wasn't that desperate, so I aborted the operation.

I hoped the reinstall of the other modules would be sufficent. I rebooted - and can you believe it? Login worked!!!

I kept a record of /etc/pam.d and the files seemed identical before and after the update. My noob guess would be that the fsck messed up the libpam-modules or the libpam-runtime, which caused the login-problem. The modules was restored with the reinstall. I've got plenty of stuff in my /lost+found/ directory, including a few links like this one:
```

lrwxrwxrwx   1 root root    11 2006-07-30 20:19 #3162343 -> pam_unix.so

```
I'm not sure what that means. 
Anyway, thanks a lot for your help bishman! I really appreciate it!

---

### Post by bishman on 2007-03-15
Thats great news! Too little too late for me unfortunately but well done for making the pam.d connection in the first place.

I am using Edgy so that probably made the difference in files.

The stuff in the lost+found was probably put there by fsck.
pam_unix.so comes from /lib/security/ directory in edgy. But since you reinstalled all pam files should be replaced.

Anyway, better not try and fix something that isn't broken anymore! 

Glad to be of help - it's good that two unexperienced users like ourselves can fix some obscure error that apparently no one else has come across, Cheers!

---

