---
title: "Help! CANT BOOT XUBUNTU! (got lots of errors)"
date: 2008-01-20
forum: General Help
---

### Post by aflog on 2008-01-20
Ok  when i boot up my computer i select Xubuntu from the GRUB loader menu... It shows the Xubuntu loading bar, and that loads ok. Then on that command line type looking screen u get before the login screen is displayed, the following came up:

> * Checking root file system...
fsck 1.40.2 (12-Jul-2007)
/dev/hda2 contains a file system with errors, check forced.
/dev/hda2: {Loading bar went here}
Duplicate or bad block in use!
/dev/hda2: Multiply-claimed block(s) in inode 18211259: 3658479
/dev/hda2: Multiply-claimed block(s) in inode 18211259: 3658479
/dev/hda2: (There are 2 inodes containing multiply-claimed blocks)

/dev/hda2: File /usr/lib/gconv/ISO-2022-JP-3.so (inode #1821260, mod time Mon Oct 1 14:02:07 2007)
has 1 multiply-claimed block(s) shared with 1 file(s):
/dev/hda2: File /usr/lib/gconv/ISO-2022-JP-3.so (inode #1821260, mod time Mon Oct 1 14:02:07 2007)
/dev/hda2:

/dev/hda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(ie without -a or -p options)
fsck died with status 4

* An automatic file system check (fsck) of the root file system failed.
{...
whole heap of other stuff
...}

After performing system maintenance, press Control-D to terminate maintenance shell and restart the system.

Give root password for maintenance
(or type Control-D to continue): _

And thats where it asks for an input from me... and at this stage im sitting here staring at the screen with wide open eyes thinking "wtf...".

So from the sounds of it there is multiply-claimed inodes (:S)... any ideas as how to fix it? i wouldnt have a clue what im doing here...

Thanks

Jayden
(Please dont offer any solutions resulting in me wiping my HDD, i WONT be happy)

---

### Post by aflog on 2008-01-20
Ok so at that command, i tried putting in my ROOT password, and the errors came far to quick to write down xD... then i tried using Control-D the next time and it rebooted my computer...

Jayden

---

### Post by banewman on 2008-01-20
You can run fsck on that partition from the live cd  - that might help.
:)

---

### Post by aflog on 2008-01-20
Xubuntu doesnt come with a Live CD... i have an Ubuntu live CD, will that work just the same?
I saw [THIS]("http://ubuntuforums.org/showthread.php?t=177377") post too and wondered how to run fsck when i cant get into Xubuntu's terminal xD

Thanks for the swift reply!

Jayden

---

### Post by aflog on 2008-01-20
Hehehe found my Kubuntu live CD too :D... so can i use them to run fsck? Or is there another method?

Jayden

---

### Post by aflog on 2008-01-20
Its VERY VERY INCREDIBLY important i can get onto Xubuntu again... it has ALL my important Documents on that partition! SO IF ANYONE can correctly answer my questions then please do... i dont want to do something that will harm my system! :S :(

Jayden

---

### Post by aflog on 2008-01-20
ok so ive loaded up my Ubuntu Live CD right now, and im using the other comp to type this. I have the terminal open, now what do i type to fix that error?

Jayden

---

### Post by aflog on 2008-01-20
Nvm i got it :D
> sudo fsck.ext3 /dev/hda2

Thx anyway

Jden

---

### Post by Clancy_s on 2008-01-20
fwiw you could also have used the live CD to back up your data onto another partition or an external drive.

---

### Post by rosegarden78 on 2008-01-20
If you can still boot to a terminal but not X server you can mount a USB stick or external hard drive by hand using the mount command.  The Johnny-Come-Latelys pop up in /etc/fstab and /etc/mtab.  A simple command like 

cp /home/* -t /mount/yourMountedFolder

will backup most if not all your home folder contents to the device you mounted on the folder.  Could also be a damaged installation CD.  I know you don't want to lose your data so I would try backup from terminal.  Then you can do a clean install to be sure it's not a virus or bad sectors.

Re: X server lockout

[http://ubuntuforums.org/showthread.php?t=673614](http://ubuntuforums.org/showthread.php?t=673614)
I guess Ubuntu does make a backup of xorg after all.

---

### Post by rosegarden78 on 2008-01-23
If you fix it try this article on MacDock and Vista eye candy
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
Works for me with an Intel 915 graphics card.

---

### Post by aflog on 2008-01-23
I dont mean to sound rude, but that post was completely off-topic....

---

### Post by rosegarden78 on 2008-01-26
EDIT: Sorry I meant this [article]("http://ubuntuforums.org/showthread.php?t=677959") about my Xfce with Compiz.  I'm assuming if you may want to get Xubuntu working with Compiz and Avant some day.  I'm sorry I cannot offer you the techical assistance you require at this time good luck!

---

### Post by aflog on 2008-01-26
Thx but i got it sorted ;)

---

