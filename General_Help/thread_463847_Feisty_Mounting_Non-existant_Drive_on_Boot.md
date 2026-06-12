---
title: "Feisty Mounting Non-existant Drive on Boot"
date: 2007-06-04
forum: General Help
---

### Post by flowingfire on 2007-06-04
Hello everybody!

Feisty is attempting to mount a non-existant drive every time I boot up.  It stops in boot time and expects me to press "ctrl-d" to exit the mounting process of the non-existant drive.  It then finishes booting and enters KDE.  

How do I get Feisty to stop trying to mount this thing?  

Here's how it happened to begin with: I had a second installation of Feisty on another Hard Drive.  On the new one's installation, apparantly it initiated some kind of swap-sharing with the other hard drive.  (I don't think it ever gave me a choice about it one way or another, either...)

Anyway, now that the former swap partition is no longer present, it's not smart enough to simply skip over its attempt to mount and swap-share with a drive that's not there.

Hmmm... I'm sure there's a really easy fix for this, but I'm not expert enough to figure it out. 

Thanks in advance,
-David :)

---

### Post by coffeecat on 2007-06-04
It's not quite clear what you've done, but assuming you've removed a partition(s) that is listed in fstab, you'll need to comment out the appropriate line in fstab or remove it altogether.

If you need help, open a terminal and post the output of:

```
cat /etc/fstab
```

---

### Post by flowingfire on 2007-06-04
Thank you. :)  Is this simply a matter of deleting a line in this file?  Here are my fstab contents:  

[FONT="Courier New"]david@porch-computer-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4ab6a66b-f468-4937-882e-f174d8d873dc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=DCBC8574BC8549CA /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=423b2275-5632-47ca-b7ac-74d3515d7b0d /media/sda2     ext3    defaults        0       2
# /dev/hda1
UUID=d40c0347-16ca-4c74-899f-ba843002d524 none            swap    sw              0       0
# /dev/sda3
UUID=2f6937f9-82e7-4b58-acac-9414028ca215 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0[/FONT]

---

### Post by flowingfire on 2007-06-04
Just an update-- problem solved.

I just deleted what looked like the two offending lines in FSTAB and it no longer attempts to mount non-existant stuff and happily boots into KDE without interruption.

Thanks.

---

### Post by coffeecat on 2007-06-04
I'm glad you've fixed it. For future reference, if you want to disable a line in a configuration file, but not commit yourself to deleting it, you can 'comment it out'. This means putting a # mark at the beginning of the line, i.e. going from:

```
superfluous line
```to

```
#superfluous line
```You may know this already but in case you don't it's a little safer than deleting the line. You can more easily revert if you find your edit doesn't work or does something you don't want - and you've forgotten to make a note of what you've taken out. :wink: (Been there, done that. :lol: )

---

