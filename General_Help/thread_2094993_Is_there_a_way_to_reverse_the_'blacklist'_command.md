---
title: "Is there a way to reverse the 'blacklist' command"
date: 2012-12-15
forum: General Help
---

### Post by parcdulas on 2012-12-15
While trying to get a mobile dongle to work I was advised to blacklist the internal wireless card. I have the dongle working well now since I updated the firmware but cannot connect to my home network using the internal wireless card. An external USB one works ok and the internal one works under Windows XP so I know my home wireless network is ok. Can someone tell me how to get my internal wireless card to be recognised by Ubuntu again? It's in an ASUS Laptop X50RL series.

---

### Post by steeldriver on 2012-12-15
AFAIK driver blacklisting is done simply by adding a line to one of the .conf files in the /etc/modprobe.d directory - or creating a custom .conf file and adding it there

If you know the exact name of the driver you blacklisted it should just be a matter of finding the line and commenting out or removing it

---

### Post by parcdulas on 2012-12-15
I found the file "blacklist.conf" in the etc/modprobe.d directory with the entry:

```
blacklist ath5k
```

so I tried to comment it out with a # at the start of the line. However as the file is read only I could not save it. Tried SaveAs with the same name and the system asked if I wanted to replace the file but at the last point it said I did not have permission to save. Any suggestions how to edit this file?

---

### Post by steeldriver on 2012-12-15
You will need root privileges to do that because it is a 'system' file - either

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```for a GUI editor, or

```
sudo nano /etc/modprobe.d/blacklist.conf
```if you are comfortable with the 'nano' text mode editor (or vi / vim / emacs etc.)

---

### Post by parcdulas on 2012-12-15
Thanks Steeldriver, I quite like learning how to use terminal commands. nano is much more friendly than the old line editor of MSDOS

I now have a fully working wireless connection!

---

### Post by steeldriver on 2012-12-15
Great - happy to help

You *may* find that ath5k hardware encryption misbehaves (at least it did last time I used it - I have a couple of old cardbus wifi adapters that used that driver) - if so post back and we can take a look at that

---

