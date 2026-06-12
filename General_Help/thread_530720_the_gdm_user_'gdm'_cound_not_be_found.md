---
title: "the gdm user 'gdm' cound not be found"
date: 2007-08-20
forum: General Help
---

### Post by John Hoge on 2007-08-20
I had an install of 7.04 running great until I added a new user and restarted. Now it doesn't even get to the login screen. The progress bar makes it all the way to the end and then I get a bluescreen error.

 The error I got was

 "the GDM group 'gdm' does not exist. Please correct GDM configuration and restart GDM"

I'm brand new to linux, so I'm totally stuck here.

Thanks,
John

---

### Post by jamvegan on 2007-08-21
I am not familiar with this error, but I have a couple of questions based on the error message.

First, boot into Ubuntu in recovery mode (this should be the second item in the GRUB menu when you first start up the machine).  You will not see the Ubuntu logo and progress bar, just a bunch of white text on black background scrolling up the screen.  When the scrolling stops and you see something like:
```
root@john-desktop#
```
you are logged in as root.

Type the following commands (you will press the Enter/Return key after each line):
```
grep Group= /etc/gdm/gdm.conf
grep User= /etc/gdm/gdm.conf
grep gdm /etc/group
grep gdm /etc/passwd
```

Post the output of each of those commands here, and we'll go from there!

---

### Post by John Hoge on 2007-08-21
Hi Jamvegan,

Here's the result of those commands:

grep Group= /etc/gdm/gdm.conf
Group=gdm

grep User= /etc/gdm/gdm.conf
User=gdm

grep gdm /etc/group
[nothing]

grep gdm /etc/passwd
gdm:x:109:65534:Gnome Display Manager:/var/lib/gdm:/bin/false

Thanks,
John

---

### Post by jamvegan on 2007-08-21
Wow.  It looks like your error message told you the literal truth.  The group gdm doesn't exist.  So, at the same root prompt that you issued those commands at, type:
```
groupadd -K GID_MAX=999 gdm
```

There's one field in the /etc/passwd entry that might then need to be changed, but try rebooting normally and see if just creating the group fixed the problem.

---

### Post by talon 2 on 2007-09-30
I am running ubuntu 6.06 and just got them same error with a blue screen. I powered down and restarted. What it did was force check which failed them it had me forcechek manually.
Had to answer about 8 change to files but my system does work now.I am  just a little concerned about the security.  Rebooting help with the system. Hope this might give you some insight on your problem.

---

