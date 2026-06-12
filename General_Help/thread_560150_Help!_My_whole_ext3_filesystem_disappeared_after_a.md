---
title: "Help! My whole ext3 filesystem disappeared after a fsck!"
date: 2007-09-26
forum: General Help
---

### Post by schweini on 2007-09-26
Hello,
yesterday, i switched on my (K|X)Ubuntu (i was running the three of them) machine, and fsck wanted to check the root filesystem, because it had been mounted 30 times. No problem i thought. but it complained about "multiply claimed block" (or inodes - cant remember) so i told it to fix all that. It duefully did, and after that horrendous "FILESYSTEM WAS MODIFIED" message, it rebooted, and fsck came up AGAIN, checking everyhting. Again, i told it to just do whatever it wanted to do (really cant remember what it was this time). 
Anyhow: after the next reboot, GRUB complained that it couldn't boot. This kind of happened to me before: once, fsck, on a whim, moved my WHOLE FILESYSTEM into /lost+found/ (easily fixed by moving it back), so i wasnt stressed out just yet, and popped in my trusty Knoppix CD. But then it got nasty: the whole /dev/hda1 partition is empty, except for:

```
root@ubuntu:~# ls -la /mnt/
total 8
drwxr-xr-x  3 root root 4096 2007-05-29 04:36 .
drwxrwxrwt 32 root root  280 2007-09-25 00:38 ..
lrwxrwxrwx  2 root root   11 2007-05-01 15:55 cdrom -> media/cdrom
lrwxrwxrwx  2 root root   41 2007-05-02 05:43 .hidden -> /etc/kubuntu-default-settings/hidden-root
lrwxrwxrwx  2 root root   33 2007-05-29 04:36 initrd.img -> boot/initrd.img-2.6.20-16-generic
lrwxrwxrwx  2 root root   33 2007-05-05 05:36 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwx------  2 root root 4096 2007-09-25 03:18 lost+found
lrwxrwxrwx  2 root root   30 2007-05-29 04:36 vmlinuz -> boot/vmlinuz-2.6.20-16-generic
lrwxrwxrwx  2 root root   30 2007-05-05 05:36 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic

```

(the 'lost+found' directory is completely empty.).

i ran fsck again - but i even had to force it (-f) to take a closer look, but even that way it couldnt find anything wrong. So i told fsck to use the first backuped superblock (dont know if that's supposed to help, but it sounded worth a try), but it only complained about a couple wrongly marked free inodes or something like that, fixed them, and everything is still messed up.

now the weirdest part:
```

root@ubuntu:~# du -hs /mnt/
df -h
8.0K    /mnt/

```

but:

```

root@ubuntu:~# df -h /mnt/
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.1G  8.0G  617M  93% /mnt

```

which sounds exactly how that partition was used before this crash, so this still gives me some hope. Also, fsck (last time i ran it) mentioned something about a couple of thousand of files somewhere. 

Sooooo, can anybody help me with this? how can i get my files back - im actually only desperately looking for about 10 or 20 .odt and .doc files that where in a known directory there (my girlfriends application-papers for her postgrad). 

i ran [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") on the harddrive (it claims to recognize .odt, .doc and .pdf files), but it found thousands and thousands (various GB) of files, but AFAIK, none open in e.g. abiword.

Any help greatly appreciated,

schweini.

---

### Post by hexstar on 2007-09-26
Hello, shutdown your computer immediately and stop doing any activity on the computer. Any further activity could result in what files are left on the hard drive being overwritten. You should purchase some data recovery software such as this: [http://www.datarecoverylinux.com/](http://www.datarecoverylinux.com/) and hopefully you'll be able to recover your files. Sounds like the hard drive failed... Best of luck! :)

---

### Post by bodhi.zazen on 2007-09-26
+1 on shutting down and working from a live CD.

I would advise any number of open source solutions, like testdisk or photodisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

	[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by schweini on 2007-09-27
solved it!

it seems that fsck somehow managed to lose the inode of the root / directory. so, i managed to get the whole system back as follows:

1. plugged the hardrive into my USB2IDE adaptor, and connected it to a windows machine
2. downloaded and ran [r-linux]("http://www.data-recovery-software.net/Linux_Recovery.shtml"), which is a free (as in beer) ext2/3 file recovery program (that paradoxically only runs under windows - if anyone knows of a good program like this under linux, please do tell where to find it)
3. i got the important files of the hardrive with r-linux, but since lazyness is a virtue (i'm a perl programmer), and i didn't want to re-install everything, and since the filesystem looked completely intact, i wrote down the inode number that r-linux reported as lost, damaged or deleted, and to which all other files and directories where connected to.(in my case, 13282)
4. plugged the hardrive back into the linux machine, and booted with a live cd (Xubuntu install CD - should work with almost any other one, too)
5. ran "debugfs /dev/sda1", then typed "link <13282> /lost+found/" then "quit". (the angled brackets around the inode number are required - that took me a while to figure out. grrr.)
6. moves all directories and files from /lost+found/<13282>/ back to /
7. rebooted, and fsck popped up again, and wanted to screw up my filesystem AGAIN, so i told it to leave me alone.
8. rm -rf /lost+found/<13282> (this, now empty, directory is what confused the hell out of fsck)
9. reboot, let fsck try to fix anything it complains about, and everything is fine again.

what a PITA this episode was. i am really, really mad at fsck for screwing up a perfectly functioning filesystem on a routine check.

---

### Post by hexstar on 2007-09-28
You should report this bug to the fsck team

---

