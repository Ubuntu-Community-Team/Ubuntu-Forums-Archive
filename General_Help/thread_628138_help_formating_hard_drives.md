---
title: "help formating hard drives"
date: 2007-11-30
forum: General Help
---

### Post by syxbit on 2007-11-30
First of all, I've searched extensively, but those posts don't help.

I am quite disappointed with how terrible formatting and labeling drives is in ubuntu. Gparted absolutely SUCKS.

I have 2 SATA HDs in my desktop, and one external USB. The main drive has both Windows and Ubuntu, and the others are blank.

Formatting with Gparted not only makes the owner root, but keeps closing after each operation (loading it from the terminal shows errors)
Those drives then don't mount and boot.

using the command 
e2label /dev/sdb "WD2"
gives the error
e2label: Permission denied while trying to open /dev/sdb
Couldn't find valid filesystem superblock.

it gives this error whether the drive is mounted or not

why can't there just be an easy way to format a drive, give it a label, and have it automatically mount. yet another reason why linux is used by so few...

---

### Post by jcsteele on 2007-11-30
Because in order to access a hardware device such as a hard drive, you much have "root" or Administrator privileges.  This is a feature, not a bug, and the reason why unix/linux has such a better security model then other operating systems....you sound like your used to using Windows, which by default in most cases, runs under administrative privileges...this means if you, or a piece of software (i.e. virus, malware, etc.) is ran, it can access any part of the system it likes with impunity.  This simply does not occur in the unix/linux world.

Try using the "sudo" command to perform operations that require "root" privileges.  You will be asked for a password, which is the password of the user you are currently logged in as.  This will allow you to gain administrative access for a short time.

Also, with the e2label you must specify the partition you wish to label, not simply the entire device itself.

Try:

sudo e2label /dev/sdb1 "WD2"

assuming you only have one partition on this drive.  Then unmount/remount the drive.

//jcs

---

### Post by syxbit on 2007-12-01
actually, i've been using only linux for almost 2 years. Been on since Breezy
I only use Windows for gaming :)
I'm aware of the root stuff, but that doesn't stop it from being ridiculous, and i'll tell you why.
there is a distinct difference between running as ROOT, and doing a temp bypass.
in ubuntu you can just type 'sudo' because they've made the primary juser account a member of the wheels group.
so, unless i'm mistaken, you're not actually root, but you have root priveledges
the way i got it working was by just reinstalling and setting it up at the beginning.
that way it's in my fstab

---

### Post by jcsteele on 2007-12-01
No.  sudo is alot more complicated that just adding a user to the wheel group.

Basically, your UID and GID is changed to the target user (root user by default, but any user can be used with -u flag), so in fact you ARE the target user....however there are differences between logging in as a root user or using the su command, and running a command through the sudo interface (controlled through /etc/sudoers)

//jcs

---

