---
title: "wp install crash: /bin/sh: bad interpreter"
date: 2005-05-17
forum: General Help
---

### Post by ct_srvnt on 2005-05-17
I've installed 2004 version of wordperfect 8 from CD without incident on SuSE 9.1, Xandros 2, Fedora Core 3, Mandrake 10, and Mepis, but Ubuntu Hoary won't cooperate.  From root terminal, install terminates with error message "/bin/sh: bad interpreter: permission denied."  /bin/sh links to /bin/bash.  Is it possible that the link is broken?  Or that bash needs to be reinstalled?  Could anyone suggest a way to begin troubleshooting this problem without the risk of screwing up my installation?  I really like Ubuntu Hoary, but I can't make any distro my primary os if I can't use wordperfect.  Thanks for any help you can offer.

---

### Post by cudaman73 on 2005-05-29
/bump

and.. I'm having similar problems. 'Cept mine extend to any script of any kind. let me give you two examples.

```
m3r1k@m3r1kb0x:~$ ./amsn
bash: ./amsn: /bin/bash: bad interpreter: Permission denied
```

and

```
m3r1k@m3r1kb0x:~/vmware-distrib$ sudo ./vmware-install.pl 
Password:
sudo: unable to execute ./vmware-install.pl: Permission denied
```

I have absolutely no idea when the problem started, or what I could've done to cause it. I had the same problem in gentoo, so I assume it's something I did.. but I still have no idea what. I've tried recreating the symbolic link from /bin/bash and such, but nothing seems to work. Please tell me someone else here has heard of/had this problem before. It's very frustrating.

---

### Post by JonahRowley on 2005-05-29
[QUOTE=cudaman73]```
m3r1k@m3r1kb0x:~/vmware-distrib$ sudo ./vmware-install.pl 
Password:
sudo: unable to execute ./vmware-install.pl: Permission denied
```[/QUOTE]
That one looks like there is no execute permission on vmware-install.pl, which is not related to the bash problem.  Try **chmod +x vmware-install.pl** or **sudo perl vmware-install.pl**.

---

### Post by freelsjd on 2005-05-29
where does one obtain a 2004 Wordperfect 8 for linux.  I have the old ones, including the v8.1 that came with the book, but not a 2004 version.  I would love to get wp8 running again on my ubuntu !

---

### Post by cudaman73 on 2005-05-29
[QUOTE=JonahRowley]That one looks like there is no execute permission on vmware-install.pl, which is not related to the bash problem.  Try **chmod +x vmware-install.pl** or **sudo perl vmware-install.pl**.[/QUOTE]


That's not the problem.
```
lrwxrwxrwx   1 m3r1k m3r1k     23 2005-05-11 14:54 vmware-install.pl -> bin/vmware-uninstall.pl
```

Also, in case you're curious...
```
-rwxr-xr-x   1 m3r1k m3r1k        50 2005-05-29 09:49 amsn
```
So it's not an executable problem. My problem is with using ./ to execute scripts. 

I've further isolated the problem. Since my /home dir is on a separate partition, I unmounted it and logged in again as my user, thus creating a whole new set of configs for my user. and I could execute /home/m3r1k/amsn. I made a backup of the 'new' config files (the ones not on my /home partition), and am currently in the process of going through both sets of files to look for differences. I haven't found much, though. Nothing appears to be any different.

EDIT: running sudo perl vmware-install.pl worked for it, and that's all fine and dandy, but it doesn't help how I can't execute scripts using ./filename. I'd much rather figure out this problem than have a whole bunch of workarounds.

Along the same lines, '/bin/bash /home/m3r1k/amsn' also allows the script to be executed, but I still want to know why i can't simply use ./
/EDIT

---

### Post by cudaman73 on 2005-05-29
/bump in hopes that someone can explain bad interpreter. I've looked all over and found nothing.

---

### Post by ct_srvnt on 2005-06-02
[QUOTE=cudaman73]/bump in hopes that someone can explain bad interpreter. I've looked all over and found nothing.[/QUOTE]
 I can't tell you what's going on with ./command giving this error message, but I can say that it is not just present on Ubuntu.  The same bug appears in SimplyMEPIS 3.3.1 (2.6.10) using Bash 3.0.14.  ./command works fine in MEPIS 2.6.7 (2004) and in Fedora 3 (bash 3.0).  Using the /bin/bash /media/cdrom0/install workaround got my wordperfect install script to start in Hoary, but it crashed out later -- maybe it tried more ./ calls in the script :( .  As this strangeness appears to be a Linux or bash version-wide problem, could anyone suggest a wider forum to bring it up?  Thanks.

---

### Post by ct_srvnt on 2005-06-05
I've gotten past the ./command problem and succeeded in installing wordperfect 2003 :-)   It appears to have been a permissions problem after all.  Here's what worked:  I unmounted the CD (that was automounted when I put it in) AS ROOT:  sudo umount /media/cdrom.  AS ROOT, I remounted it with executable permissions:  sudo mount -t iso9660 -o /dev/cdrom /media/cdrom.  Then:  cd /media/cdrom.  Finally, ran the install script as root  with sudo ./install.  And it worked.
I think that the earlier problem had to do with how the automounting operated.  I had checked the properties and they had shown that the CD was mounted as executable on automount, but evidently it wasn't.  Or else only the owner (local user) could execute, but only root could install, so once again a conflict.  But I'm sure I had tried unmounting it as a normal user and remounting it as root before, and the install didn't work.  So for some reason, I had to both unmount and remount as root in order to have the permissions lined up properly.  I'm glad I could finally get the program installed, but the scientist in me is unsatisfied -- I'd like to understand why this particular sequence and only this particular sequence of actions worked.

---

### Post by ct_srvnt on 2005-06-05
[QUOTE=freelsjd]where does one obtain a 2004 Wordperfect 8 for linux.  I have the old ones, including the v8.1 that came with the book, but not a 2004 version.  I would love to get wp8 running again on my ubuntu ![/QUOTE]
 I checked the Corel website.  The 2003 version (adapted to the more recent glibc versions) that I bought as a "test" version is not being sold any more while they evaluate things.  By the time Corel decides that it may be worthwhile to again offer wordperfect to the Linux community everyone will probably have given up on them and migrated to OpenOffice, especially if the wordperfect filters  in OO 2.0 are any good.
I'd suggest you check out [www.linux-sys.org](www.linux-sys.org).  Check on Utilities, then on wordperfect.  You will find a document on how to get wordperfect 8 (old version) working on newer systems.  Read the one for Debian, since Ubuntu is a Debian based system.  It seems if you install the old libc5 libraries, you can successfully install and run your old wordperfect.  Good luck!  [But if you do this, also read my post about getting around the CD automount/permissions weirdness to allow the install script to work].

---

### Post by mencial on 2005-11-02
One of the reasons that this might be happening:

Check /etc/fstab for the partition. If the partition is marked "noexec", then "./script" won't work. Now, "man mount" states that "user" implies "noexec"; and my /home partition in Ubuntu is marked "defaults,user". That means that I cannot run scripts in my home partition!

The solution would be to change

/dev/hda2/ home ext3 defaults,user 0 2

to

/dev/hda2/ home ext3 defaults,user,exec 0 2

or even

/dev/hda2/ home ext3 defaults 0 2

and restart (I guess that there is a way to remount /home, but I just won't mess with that)

---

### Post by RikBlankestijn on 2005-11-10
Thanks mencial, that was exactly my problem. I changed my /etc/fstab, rebooted and am now able to execute everything again from my home partition.;)

---

### Post by ProfBib on 2006-03-16
Thanks to everyone who contributed to this thread.  I was having the exact same problems with wordperfect and I am now confident that I will get it to work with these strategies!

Cheers!

---

