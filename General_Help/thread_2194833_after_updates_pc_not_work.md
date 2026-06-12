---
title: "after updates pc not work"
date: 2013-12-20
forum: General Help
---

### Post by sount on 2013-12-20
Hello

I was so happy that i changed to from windows to linux everything was alright untill the updates idk which updates but probably nvidia


 I have installed the 12.04 ubuntu into usb with universal usb installer

Replaced with windows 7 

and then everything was good untill the updates i don't know sure which updates but ubuntu told me to install them

and then after restarting i get this 

[IMG]http://i.imgur.com/AhG2jWC.jpg[/IMG]


I tried everything and i asked also my brother a programmer he says i am a moron...

idk if someone gonna help if not i wont get a new pc so fast 

as always i will keep using ubuntu because it rocks..

---

### Post by TheFu on 2013-12-20
My brother thinks that I'm a moron too. ;)

Can you switch to a different console and read the log files?  What do those say?
Did the update work? Any errors?
Last, did you install nvidia drivers directly from nvidia (mistake) or use the version from the repos. If from the repos, try
[B]sudo apt-get update
sudo apt-get --reinstall install nvidia-current[/B]
to force the nvidia drivers to relink with the new kernel that was installed recently.
My blog (see signature) has more info on logs and nvidia driver stuff.

---

### Post by sount on 2013-12-20
I opened Console after recovery boot etc 

this is error sudo:unable to open /var/lib/sudo/hl/console read only file system

---

### Post by TheFu on 2013-12-20
You booted from a CDROM or DVD?  That would be a "read-only" file system and explains this error.

If not, then it sounds like the root partition is mounted read-only to protect itself from further corruption.  An **fsck** of that partition (while unmounted) is a good idea. [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting) should help. Run the fsck from a live-cd, not the local disk.

If the fsck doesn't help, I'd really try to boot off a DVD and run some hardware tests to validate that the disks are accessible, working and there aren't any cable, sata or controller issues.

---

### Post by sount on 2013-12-20
I did boot from usb not cd and its says : filesystem state ; read only how i make that not read only? sorry u need know i go special school :)

---

