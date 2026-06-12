---
title: "Windows 10 to 16.04?"
date: 2016-09-15
forum: General Help
---

### Post by Quarkrad on 2016-09-15
I dual boot Win10 and 16.04 purely because I use itunes/ipod.  I have a 2nd HD that I use as a Backup - primarily for some folders in /home and another partition (on HD1) I use for personal data.  My Backup HD is ntfs solely so that I can use a utility on my win side to write from win10 to my Backup disc - hence I have two copies of my itune data files and actual tunes/music.  For a number of reasons I am thinking of converting my ntfs partitions and Backup HD to Ext4 but I there is a problem, natively, because obviously win10 cannot see ext4.  I have read of some third party apps you can put on win so that it can read ext4 but they do not fill me with confidence.  Is there a robust way to (auto) copy from win10 to ext4?  (At the moment I use a third party app in win10 that copies my iTunes folder from win10 to my Backup HD each time I shut down windows).

---

### Post by Bucky Ball on 2016-09-15
Not sure why you want to change to EXT4, but I will say you have a bit of a convoluted setup and could sit down with a beverage and pen and paper and draw a mud map to clean things up. First, you would want to do some serious backing up, of course.

My question: you have a /home partition on sdb (hard drive 2), but you also have your personal data stored on a partition on sda. Why? You should have all that stuff on one, big data partition somewhere, and if you want to share it with Win, make it NTFS. 

The idea is this. You install Ubuntu on sda and let it put its /home *directory* inside /, don't create a /home *partition* anywhere. You create an NTFS /data partition on sdb. You then delete the default folders in the /home directory and replace them with symlinks linking to your personal data directories (like /Documents, /Music, etc.) on the NTFS /data partition (on sdb).

You will then end up with:
Windows and Ubuntu on sda;
/data partition on sdb.

Use your external for backups. If you are in Ubuntu, remember, you can move files from an NTFS to EXT partition and vice versa. In other words, if you plop stuff to your /data partition from Windows, you can then boot to Ubuntu and drop it to the EXT external backup.

If using SSD, the OSs on the SSD and data on a HDD is the way to go. Your other option to make things easier is Virtualbox. Run Windows as a virtual machine inside Ubuntu or vice versa. That way you won't need to boot in and out of OSs to get the job done.  

Anyway, thinking out loud ... :)

---

### Post by ajgreeny on 2016-09-15
I'm in total agreement with Bucky Ball in terms of the way to set up and manage your shared data files

However, from my own several years ago experience of the windows drivers for ext# filesystem support my recommendation is not to bother.  I admit it was about 9 years ago while I still had an XP partition which was hardly used but the support then was to read only, not write, and it was for ext2 and ext3, not ext4 at all.  Things may have moved somewhat in those 9 years, but I suspect the support will still be a bit flaky.

Try it by all means, but I suggest you do not depend on it; rather use an NTFS shared partition where Linux read/write support now appears to be excellent.

---

### Post by Bucky Ball on 2016-09-15
> **ajgreeny said:**
> However, from my own several years ago experience of the windows drivers for ext# filesystem support my recommendation is not to bother ... Try it by all means, but I suggest you do not depend on it; rather use an NTFS shared partition where Linux read/write support now appears to be excellent.

+1. Wouldn't bother with the Windows EXT kludge.

---

### Post by Quarkrad on 2016-09-16
I'm very sorry, I wasn't clear in my first post.  On HD1 I dual boot win10 and 16.04 - hence 2 main partitions (one for win10 - and a few other smaller part's it creates like efi, etc)  and one for / - a third (main) partition for /home and a fourth large partition for my personal data (plus a small swap part'ion).  So everything (win10 and 16.04) is contained on one HD(1).  Physically, in the same pc, is another sata connected HD(2) that I use purely for Backup - this 2nd HD is configured ntfs and appears in 16.04 as /media/Backup. From what you say it appears I might as well leave HD2 as ntfs.  Apologies for my mix up.

---

### Post by ajgreeny on 2016-09-16
No problem!

Please mark as SOLVED from the Thread Tools menu up-top if you are fully satisfied this is a solution. It is a great help to users searching the forum.

---

### Post by Rocky_Bennett on 2016-09-16
> **ajgreeny said:**
> No problem!

Please mark as SOLVED from the Thread Tools menu up-top if you are fully satisfied this is a solution. It is a great help to users searching the forum.



You can't do that from this forum because this is a chat forum and not a support forum.

---

### Post by howefield on 2016-09-16
Support thread so moved to the "*General Help*" forum.

---

