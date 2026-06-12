---
title: "Connecting a Nokia 6070 through USB"
date: 2007-02-04
forum: General Help
---

### Post by finferflu on 2007-02-04
Hi all,
I'm trying to connect my Nokia 6070 to my machine through a USB cable, but nothing seems to happen, even though I get this with lsusb:
```

Bus 001 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
```

Does anyone know anything about connecting a mobile phone to a computer through a USB cable?

Thanks!

---

### Post by reclusivemonkey on 2007-02-05
Don't know whether this will work with your mobile, but have a look here;

[http://www.gnokii.org/](http://www.gnokii.org/)

---

### Post by finferflu on 2007-02-05
Thanks for the useful link, even though my model doesn't seem to be supported... the site can still be useful for somebody else, though. It's going into my bookmarks.
I hope to find something for myself as well, though...

---

### Post by reclusivemonkey on 2007-02-05
Do you have bluetooth? Can you connect to the internet? I use a service called zyb, but I have a N80 and so I can connect free over my wireless router. I can also plug my N80 via USB and it will work just like a USB flash drive but I doubt your phone can do that.

[https://zyb.com/](https://zyb.com/)

---

### Post by finferflu on 2007-02-05
No I haven't, it's a shame that such a nice mobile phone misses a key feature like bluetooth...

---

### Post by pvdg on 2007-02-28
finferflu, I have exactlly the same problem as you do. If you find a solution, please post it here. I'll do the same. Have you tried gnokii, providing another model number (of a similar phone)? That's my best bet so far and I'll try it when I have the time. Good luck!

---

### Post by finferflu on 2007-02-28
Ah! That's a good one, I didn't know of the existence of this gnokii... let's see how it goes. Thanks!

---

### Post by pvdg on 2007-07-05
I have finally got to try gnokii and here are my findings so far, in case they are useful to others.

After upgrading to Feisty, I installed the gnokii package from the universe repository :

```
sudo apt-get install gnokii
```

Actually, I used synaptic and installed all the recommended and suggested packages as well.

I then followed the instructions from the gnokii site [http://www.gnokii.org/docs.shtml](http://www.gnokii.org/docs.shtml) and the gnokii wiki [http://wiki.gnokii.org/index.php/Config](http://wiki.gnokii.org/index.php/Config) to create and edit the .gnokiirc file in my home directory (in Ubuntu, a default  configuration file is created as /etc/gnokiirc; just copy it to your home directory as .gnokiirc and edit it: it will override the /etc/gnokiirc configuration, so there is no need to delete the default configuration file). Attached is a copy of my configuration file (don't forget to rename it .gnokiirc if you use it), which is working for a Nokia 6070 wiyh a CA-42 usb cable.

Note: the 6070 is not listed as supported in the gnokii documentation, so I used the (default)  "model=6510" as suggested in [http://wiki.gnokii.org/index.php/Config](http://wiki.gnokii.org/index.php/Config).

I have not tried all the gnokii options yet, but I have successfully applied both tests suggested in the documentation:

```
gnokii-identify
```
```
gnokii-monitor
```

and have been able to dial a number using

```
gnokii -- dialvoice XXXXXXXXX
```

Which proves communication between phone and computer is working!

---

### Post by Elmeromero on 2007-12-18
Thanks for the information.

I was having the same trouble, trying to connect my Nokia 6070 phone to my computer.  It works fine with PC suite and Windows but Ubuntu didn't work at all.

I followed your instructions and I'm able to run gnokii --identify and gnokii --monitor along with some other commands.

However when I try to transfer Java applications to the phone they are corrupted once the transfer is done.  I'm currently trying to transfer demo Java applications from Sun's Wireless Toolkit which involves a .jar file along with a .jad application descriptor. But for some reason they always end up being corrupt. I will try to transfer some other files, e.g. a ringtone or a bitmap and see how they turn out.

Another thing that bothers me is that gnokii is sometimes unable to connect to the phone. I prints "Switching to FBUS mode" and then stops. I have not figured out why this happens but if anyone out there finds out, please post a reply.

---

### Post by Arwen on 2007-12-18
I own a nokia N70 and I use obexFTP frontend for moving files,everything works fine except deletion.I think the thread that program was mentioned was named "nokia pcSuite alternative'.Also I think there is an application named "KMobile" but it didn't work for me.

---

### Post by linuxsucksalot on 2008-04-08
**Well, has *anyone* succeeded in using the Nokia 6070 as a mode**m?

It gets connected as ttyUSB0 and regularly recognized (gnokii --identify), I can transfer files through the cable *but* when I try to establish an Internet connection I got a "modem not responding" error. 

This happens also after launching *gnokiid*, which should provide support for those phones that do not accept AT Hayes commands.

The strange thing is that I got the same behavior under Windows using the official Nokia Suite, so I'm starting to think that something is wrong in my *phone* configuration or even in the phone model itself. 

Browsing through the Nokia forum I have found lots of reports of bad experiences with this phone, which is sometimes described as the black sheep in the Nokia family because of its alleged bugs.

Any contribution and config file from anyone who has got the Internet connection is welcome!

---

### Post by linuxsucksalot on 2008-04-11
After lots of trouble I found the solution: the problem was in the cable. 

If you experience problems such as those described in my previous post (phone is recognized, modem is not), try and check you connection cable first. It seems that some unoriginal ones (especially those sold from eBay) *do not* manage the 6070 as a modem, even if you can browse files and establish a connection. Please note that this seems to be true also for cable sold al CA-42 replacement. I have bought two from different vendors and now I know this.

Today I have bought the expansive 50 € official Nokia CA-42 and everything worked fine since the very first moment.

---

