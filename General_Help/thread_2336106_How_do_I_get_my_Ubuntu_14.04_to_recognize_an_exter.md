---
title: "How do I get my Ubuntu 14.04 to recognize an external drive"
date: 2016-09-04
forum: General Help
---

### Post by wjbradley on 2016-09-04
My Ubuntu is running on an HP mini. It has a camera card slot which U.14.04 does not recognize. I had an external drive which I plugged in with my camera card. When I try to find the drive to activate it I come up blank.
Any help would be appreciated.

---

### Post by autocrat on 2016-09-04
Can you see anything with
```
lsblk
```

---

### Post by wjbradley on 2016-09-05
> **autocrat said:**
> Can you see anything with

No, I tried it on another machine running Kubuntu and also a Windows machine. It lights up when I plug it into the USB port of all three machines. It actually worked once but that has turned out to be its swan song.

---

### Post by howefield on 2016-09-05
Try opening a terminal and typing..

```
tail -f /var/log/syslog
```

Then insert the card and watch for messages in the terminal, do you get a response ?

---

### Post by wjbradley on 2016-09-05
> **howefield said:**
> Try opening a terminal and typing..

```
tail -f /var/log/syslog
```

Then insert the card and watch for messages in the terminal, do you get a response ?

Yes I did as you suggested and got a page full of information that meant nothing to me.
However, I put another card in the same slot and it registered it and I could read the photos. But to change the card will it stays plugged in, does not work. I have to change the card, unplug it, replug it and the images come up. It just does not seem to like the card out of my camera. So i will test another card, to see if the plug-in drive likes it and then put it in my camera. Next time I am in Best Buy I will look for a cheap external drive. This one is pretty old, I bought it in 1997, it is a multi card size drive.

---

### Post by howefield on 2016-09-05
> **wjbradley said:**
> Yes I did as you suggested and got a page full of information that meant nothing to me...

Feel free to post it, it might mean something to someone else.

---

### Post by wjbradley on 2016-09-05
Thank you for all your help, it is appreciated.

---

