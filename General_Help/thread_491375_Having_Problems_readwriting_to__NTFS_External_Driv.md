---
title: "Having Problems read/writing to  NTFS External Drive"
date: 2007-07-03
forum: General Help
---

### Post by GumbyX on 2007-07-03
I am having a slight problem getting my NTFS-formated Firewrie External Drive to mount with writing rights in Ubuntu. I used automatix to install ntfs-3g, but it will not allow writing to the external dirve. If anyone can point me the right direction of how to do this, I would appreciate it. Thanks ahead of time.

---

### Post by MCSE_Crossover on 2007-07-03
Step-by-step guide:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Also, I would avoid Automatix. It is known to cause system problems, even more so when trying to upgrade versions later on. Install everything manually.

Be sure to check out [www.ubuntuguide.org](www.ubuntuguide.org) as well for some great pointers on new installations. Shows you how to do mainly all of the stuff included in Automatix. You'll learn quite a bit.

---

### Post by GumbyX on 2007-07-03
> **MCSE_Crossover said:**
> Step-by-step guide:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Also, I would avoid Automatix. It is known to cause system problems, even more so when trying to upgrade versions later on. Install everything manually.

Be sure to check out [www.ubuntuguide.org](www.ubuntuguide.org) as well for some great pointers on new installations. Shows you how to do mainly all of the stuff included in Automatix. You'll learn quite a bit.

Hey, automatix has been good to me, so I will continue to use it. And are you sure this will work fine with an external drive?

Edit: Wow should read the article all the way before posing. I give this a try later tonight. Thanks

---

### Post by GumbyX on 2007-07-03
Hate to say it, but this won't mount my external mount. Anyone have any ideas why this might be happening?

---

### Post by NeoLithium on 2007-07-03
Does it just give you a write permission error?  Where does Ubuntu mount your external drive?  You may just need to:
```
sudo chown YOUR_USERNAME /mountpoint
```

Of course, that's assuming that you have it automounted.  You may need to check out fstab and set up a regular place that it will be mounted.

---

### Post by ajmorris on 2007-07-03
> **GumbyX said:**
> Hey, automatix has been good to me, so I will continue to use it. 


Automatix has been good to you so far, but maybe not for much longer. Automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu. I advise not to use Automatix.

---

### Post by GumbyX on 2007-07-03
> **NeoLithium said:**
> Does it just give you a write permission error?  Where does Ubuntu mount your external drive?  You may just need to:
```
sudo chown YOUR_USERNAME /mountpoint
```

Of course, that's assuming that you have it automounted.  You may need to check out fstab and set up a regular place that it will be mounted.

It does not give me a permission error at all. Sadly, it is auto-mounting, so I don't know if that is causing the problem. If it was in my fstab, shouldn't it still show up in ntfs-control?

---

### Post by NeoLithium on 2007-07-03
Does NTFS Config allow the computer to find the external device, and set up the write support that way?  It won't mount it persay; but it will set up a directory where ntfs3g should be able to pick that up and let you write to your hearts' content.

---

### Post by GumbyX on 2007-07-03
I thought it was supposed to, but maybe not. :( This sucks because I really need it. I don't want to make a backup of my 320GB drive, reformat it as FAT32, and and restore the backup. :(

Anyone else have any ideas of whatI can do?

---

### Post by GumbyX on 2007-07-04
Hate to double post, but this will be my final attempt. 

I still cannot get ntfs-control to reconize my Firewire external hard drive enclosure. I just wanted to know if there is something I should do to my Fstab that will allow ntfs-control to see it, or am I out of luck trying to write to an external NTFS drive?

Edit: Ut actually worked. Guess it didnt take at first. Cool Thanks guy.

---

