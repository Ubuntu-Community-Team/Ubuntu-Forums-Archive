---
title: "Grub Rescue: just going crazy"
date: 2017-08-17
forum: General Help
---

### Post by borge.15 on 2017-08-17
Hi everybody,
 
so as you can imagine, I was updating windows 10 and the Grub system stop working as usual.  Now I get the >Grub rescue message and in my case I have no access to a live CD or a bootable USB so I found how to do it using the Grub command line...there are so many threads on the web about that...

So I typed ls to list all partitions and that's what I get (see the image). Then I type ls before each partition and I can't find where the root filesystem is. 

So I decide to just type set and what I found is that there's   another partition (msdos6)  that I can't find using the ls command. 

What's wrong with my Grub?  Why I can't repair it from the rescue mode? 

I really need to get access to my windows.

Thank you so much. 

Carlos

---

### Post by oldfred on 2017-08-17
Major update to Windows often "forgets" to include Linux partitions if BIOS/MBR and Linux partitions are logical. 

You need a live installer to repair using testdisk or parted rescue. And usually have to reinstall grub to MBR.

       Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 


 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)

---

