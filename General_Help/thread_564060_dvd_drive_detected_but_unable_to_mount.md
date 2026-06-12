---
title: "dvd drive detected but unable to mount"
date: 2007-09-30
forum: General Help
---

### Post by DarkDancer on 2007-09-30
Ok, here is what is going on, it's my friends computer, he has an emachine. It came with a DVD reader. Later we added  a dvd writer to his computer. Standard disclaimer, since he has actual boot system, it works fine in windows.  The problem is that in feisty, (and it has always been this way in fiesty, which he has used since it was beta) it won't mount. Konquerer (he uses KDE) doesn't see it at all. If he puts in media, Kubuntu asks him what he wants to do with it, but won't do anything if he chooses an option.

K3b will see that the drive is there, but if he tries to burn anything, it tells him that the drive cannot be mounted. It can see it under /dev, but there  (I'm doing this from memory so forgive me) is no device link there, as if it can see it, but has no clue what to do with it.

---

### Post by tbroderick on 2007-09-30
Is there an entry for it in /etc/fstab?

---

### Post by Aikanar on 2007-10-01
> **tbroderick said:**
> Is there an entry for it in /etc/fstab?

Hi, I am the friend DarkDancer mentions.

Yes, there is an fstab entry.  Here is the relevant portion:

> UUID=4fbf817c-26c0-45fd-9e37-91ac2471725c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

As you can see, both entries appear quite similar.

/dev/scd0 is mountable, /dev/scd1 is not.  At all.

---

### Post by DarkDancer on 2007-10-01
Bump

---

### Post by DarkDancer on 2007-10-03
Come on guys, someone must know something, a suggestion? A question for calrification? Anything?

---

### Post by DarkDancer on 2007-10-04
Bump

---

### Post by DarkDancer on 2007-10-04
bumpity bump bump bump.

---

### Post by tj111 on 2007-10-04
I think this is very similar to [my problem](http://ubuntuforums.org/showthread.php?t=567612).  Except in my case it's a cdr/w drive, but thats irrelevent I think.  The only think I can think of is that the cdr/w is (P)ATA, while the dvdr/w is sata.  What are the results of dmesg | tail -n 20 when you put something in the drive?

---

### Post by tj111 on 2007-10-04
I found a fix to the problem.  See the bug report fix [here](https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25).

---

### Post by Aikanar on 2007-10-05
> **tj111 said:**
> I think this is very similar to [my problem](http://ubuntuforums.org/showthread.php?t=567612).  Except in my case it's a cdr/w drive, but thats irrelevent I think.  The only think I can think of is that the cdr/w is (P)ATA, while the dvdr/w is sata.  What are the results of dmesg | tail -n 20 when you put something in the drive?

First, **_thanks_** for answering.  I had basically given up on the Ubuntu Forums because no one seems to pay attention if your problems are anything but easily fixable newbie problems.

Here are the results from the dmesg command:

> aikanar@arantinnu:~$ dmesg | tail -n 20
[   86.707952] lo: Disabled Privacy Extensions
[   96.908102] ath0: no IPv6 routers present
[  119.485743] ath0: no IPv6 routers present
[153853.241565] ADDRCONF(NETDEV_UP): ath0: link is not ready
[153861.065526] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[153871.616177] ath0: no IPv6 routers present
[153892.580808] ADDRCONF(NETDEV_UP): ath0: link is not ready
[153895.788468] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[153897.228123] ADDRCONF(NETDEV_UP): ath0: link is not ready
[153911.762021] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[153928.389632] ath0: no IPv6 routers present
[224999.679285] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[224999.679298] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0xac data 8 in
[224999.679300]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
[225006.670162] ata2: port is slow to respond, please be patient (Status 0xd0)
[225029.643037] ata2: port failed to respond (30 secs, Status 0xd0)
[225029.643048] ata2: soft resetting port
[225030.477673] ata2.00: configured for UDMA/33
[225030.657386] ata2.01: configured for UDMA/33
[225030.657428] ata2: EH complete
aikanar@arantinnu:~$

I am not very famlilar with hardware.  Does this tell you anything useful (I hope)?

///Dave

---

### Post by Aikanar on 2007-10-05
> **tj111 said:**
> I found a fix to the problem.  See the bug report fix [here](https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25).

Thanks again :)

How would I translate these commands to my DVD drive at /dev/scd1?

///Dave

---

### Post by tj111 on 2007-10-05
It's the same error messages I was recieving.  

Edit: sorry, didn't see your post.  I just copied it word for word and it worked for me (excluded the optional stuff).  Let me know how it goes

---

### Post by Aikanar on 2007-10-08
This worked, well, thanks. :)

I would say, "like a charm", but it changed all of my drive designations from sd{a *or* b}*n* to hd{a *or* b}*n*.  Which since I have multiple partitions and have them sharing data between OSes (Opera prefs and bookmarks, torrents) was a bit of a chore reconfiguring everything, but after that it worked fine.

///Dave

---

### Post by JockVSJock on 2007-10-20
Hey, I'm having the same problem, my Ubuntu 7.04 Feisty is unable to auto detect DVDs 
when I insert them into the DVD burner. 

1.  I am trying to mount them with a simple command, found from:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)
 
```


sudo mount /media/cdrom0/ -o unhide

mount: No medium found


```

I would prefer to mount from the command line, if it won't automount.  Do I want to automount from /media or /dev?  

Also, I see in this thread that a modification of initramfs will fix the issue, is it that easy? 

thanks

---

### Post by tj111 on 2007-10-20
The initramfs fixed it for me right away,and was really easy.  I just copied and pasted it.  Alternatively, you could try something like:
```

sudo mount /dev/cdrom0 /media/cdrom0
```
Dunno if that will fix anything or not though.

---

