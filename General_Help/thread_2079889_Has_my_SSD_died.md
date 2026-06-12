---
title: "Has my SSD died?"
date: 2012-11-02
forum: General Help
---

### Post by jwarder on 2012-11-02
Hi Guys,

This is my first post so treat me nicely :-)

I'm using Ubuntu 11.04 with XBMC as a media centre, and I just tried to run a few commands on it and I'm getting errors such as:

ls: reading directory .: Input/output error

-bash: /usr/bin/uptime: Input/output error

I've done some googling and I ran dmesg, I have loads of the following output:

[447753.428388] glxinfo[31681]: segfault at fffffff8 ip b6aac6e5 sp bf9d9300 error 4 in libnvidia-glcore.so.280.13[b5ae1000+18a0000]

I could paste in the output from mount but basically is says /etc/mtab is not writable

Any ideas? Could it really be my SSD? 

Thanks in advance,

Jack

---

### Post by jwarder on 2012-11-02
Bump, anyone?

---

### Post by sammiev on 2012-11-02
> **jwarder said:**
> Bump, anyone?

Usually just one bump per day. A few people may get a little angry with you.

---

### Post by cbraxton on 2012-11-02
It could well be your SSD. Although in theory you'd think they are more reliable due to the lack of moving parts in practice I have seen quite a few of them fail spectacularly.  You might want to boot up on a Linux live distribution and run some tests on it.

---

### Post by jwarder on 2012-11-03
Thanks for your reply, the only bit confusing is the output of dmesg as it seems to refer to libnvidia-, and I have an nvidia graphics card, but I can't see that causing I/O errors. What tests do you think I should run?

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-11-03
try to run a read only benchmark from a live cd on it (bad connection is possible)
make sure you have ahci enabled in your bios

---

### Post by jwarder on 2012-11-03
OK thanks it is AHCI in the BIOS, and also it's been running for about 4 months with no issues, I never actually turn it off, I've got an XBMCBuntu live disk so I'm not  sure if there are any diagnostic tests on there so I'll download Ubuntu 11.04 disk.

Cheers

---

### Post by pqwoerituytrueiwoq on 2012-11-03
disk utility (now named Disks) is present on a ubuntu iso (at least it was back in gnome2)
```
sudo apt-get install gnome-disk-utility gsmartcontrol
```
that will give you 2 thing for checking the ssd smart data
what brand is the ssd (and model)

---

### Post by jwarder on 2012-11-03
Slight problem with running that. I get this..

sudo: Can't open /var/lib/sudo/htmc/0: Read-only file system
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

My SSD is an OCZ Agility 3 60GB, googling it looks like one with a high failure rate, trust me to buy that one.

Jack

---

### Post by pqwoerituytrueiwoq on 2012-11-03
i know your pain (and then some), i had a 16gb Kingston die 3 times in a single year in a low write environment, yours is acting jut like that one did
run the command on a live cd/usb
if you can run a read benchmark successfully the drive is probably good and it is something else, if you can't it is most likely time to RMA

---

### Post by jwarder on 2012-11-03
Ok thanks, Im pretty sure it is the drive but will run the tests on it tomorrow, I'm not too worried as I have a FOG image of the drive, it's just annoying that I've shelled out for an SSD only to find I'd of been better off putting a standard drive in at half the cost.

---

### Post by jwarder on 2012-11-03
What the hell did that guy say?

---

### Post by techvish81 on 2012-11-04
can you tell me, when you bought it?  i too have the same make and model:(

---

### Post by jwarder on 2012-11-04
Around 6 months ago.

---

### Post by jwarder on 2012-11-04
I can confirm that it was a faulty SSD drive causing the problem.

---

### Post by mvidberg on 2012-11-14
I bought a 64Gig OCZ SSD and it lasted me a little less than a year.  It was fast while it lasted.  I went back to regular HD, won't return to SSD until the technology matures some more because I'm not made of money.

---

