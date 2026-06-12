---
title: "help with wifi card"
date: 2005-10-20
forum: General Help
---

### Post by acejones on 2005-10-20
I have a Netgear MA521 wireless card that is not detected.  When I was running Warty and Hoary (at different times) I was able to install the card with ndiswrapper.  However, I'm unable to use ndiswrapper (gives errors when compiling).  Is there a way to install this card?

---

### Post by xristos on 2005-10-20
You don't have to compile it.
Just ```
apt-get install ndiswrapper
```
Does that give you any problems ?

---

### Post by acejones on 2005-10-20
[QUOTE=xristos]You don't have to compile it.
Just ```
apt-get install ndiswrapper
```
Does that give you any problems ?[/QUOTE]
yeah, i tried that too
```
sudo apt-get install ndiswrapper
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper
```

---

### Post by briguy on 2005-10-21
Try "apt-get install ndiswrapper-utils"  - ndiswrapper is already built into the kernel

---

### Post by acejones on 2005-10-21
that worked, but now i can't get the card to stay enabled in the network settings

---

### Post by knappen on 2005-10-21
Are you using WEP?

Try to manually add your network information to the /etc/network/interfaces file.

I had to add 

wireless-essid xxxxxx
wireless-key xxxxx (if you are using WEP)

to get it to work.

---

### Post by knappen on 2005-10-21
Oh did you add ndiswrapper to your modules file in /etc?

---

### Post by acejones on 2005-10-21
[QUOTE=knappen]Are you using WEP?

Try to manually add your network information to the /etc/network/interfaces file.

I had to add 

wireless-essid xxxxxx
wireless-key xxxxx (if you are using WEP)

to get it to work.[/QUOTE]ok, i got it to work.  i've disabled wep just to see if i could get it to work.  it didn't but when i looked in /etc/network/interfaces, i noticed that wlan0 was not listed anywhere.  so i changed the primary interface to wlan0 and added the essid to it and it started working.  now, i'll add the key and go back and enable wep on my router.

thanks for the help.

---

### Post by acejones on 2005-10-21
quick update...

is there a way to have both my nic and wifi card enabled at the same time with the nic as the default card?  i take my laptop back and forth to work with me and I can't use the wireless at work, but I would like to use the wireless at home without reconfiguring everything everytime.

---

### Post by knappen on 2005-10-22
Well there is a network manager for Gnome that does that automatically for you. Developed by Red Hat I think.

I have not found anything similar for KDE. If anyone else know, please post it here.

---

