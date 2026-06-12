---
title: "Linux n00b crying for help :'("
date: 2006-08-03
forum: General Help
---

### Post by DrBobert on 2006-08-03
Hello, all.

As the title suggests, I'm a Linux n00b. After spending all of my computing experience on Windows and Macs, I was handed a copy of Ubuntu 5.10 for 64bit PCs by a friend and decided to install it on a spare 20GB HD after my original slave HD died (Grr).

Anyway, installation went fine and I was rather impressed until I attempted to connect to the 'net via Firefox.

So, my first quandry is this:

Ubuntu doesn't recognise my Belkin 802.11g wireless (Belkin Wireless G Desktop Network Card on the box). When I tried to set up a wireless network connection, it didn't appear at all, leaving me a choice of my defunct ethernet card or nothing at all. How can I create a wireless network connection with this card?

Secondly, I have a lot of media on my master HD which Windows is installed on. I can't get access to it, so how can I?

If you can help, it would be greatly appreciated, but please understand that I have no idea what the hell is going on. In other words, treat me like a 5 year old with dementia.

---

### Post by christhemonkey on 2006-08-03
To read/write(!) NTFS:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

There are various posts (that i cant seem to find....:s) about your wifi card.
It is based on the Atheros chipset though, which will help greatly.

---

### Post by DrBobert on 2006-08-03
Well, that link was very informative, but my Windows HD is FAT32. Sorry, should've mentioned that.

Thanks, for the help, though. :)

---

### Post by christhemonkey on 2006-08-04
No problem.
Im sure if you have any more queries that someone more knowledgable than me will be able to handle them.

---

### Post by KaeseEs on 2006-08-07
Try copying this line into your /etc/fstab file:

```
/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
```


First, backup your fstab with this command, entered into your terminal:

```
sudo cp /etc/fstab /etc/fstab_backup
```
Then,  edit your  fstab file, by going to the terminal of your choice, and type:
```
gksudo gedit /etc/fstab
```



Then, just copy & paste the line in and save.  Your windows FAT32 partition should be available on your next boot, accessible from /media/windows

---

### Post by RaoulDuke on 2006-08-17
I have a Belkin Wireless G Desktop card in my desktop as well. I was able to get it working with ndiswrapper. I have only been using linux for a few months now, and I was able to get it working with ndiswrapper within the first few days of installing Breezy with little experience.

Let me know if you are still having trouble with the wireless.

G/L!

---

