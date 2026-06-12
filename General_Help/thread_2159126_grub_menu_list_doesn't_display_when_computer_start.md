---
title: "grub menu list doesn't display when computer startup"
date: 2013-07-01
forum: General Help
---

### Post by jtrol on 2013-07-01
There is only ubuntu 13.04 on my hard disc, no other os.

Uefi motherboard with mbr partition hd. Is it mater?

How should i do?

---

### Post by DeathByDenim on 2013-07-01
Do you mean you have Ubuntu 13.04 installed and working on your computer, but you would like to see the grub menu while booting for some reason?
If so, then open the file /etc/default/grub as root and change this line:
```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```
to 
```
GRUB_HIDDEN_TIMEOUT_QUIET=false
```
After you've done that, run
```
sudo update-grub
```

The next time you boot, the grub menu should be visible for 10 seconds (or whatever you change GRUB_TIMEOUT to in /etc/default/grub ).

---

### Post by oldfred on 2013-07-01
Does holding shift key work.
Some with UEFI have said they have to use escape key, but not sure about UEFI in BIOS/CSM mode.

---

### Post by jtrol on 2013-07-02
> **DeathByDenim said:**
> Do you mean you have Ubuntu 13.04 installed and working on your computer, but you would like to see the grub menu while booting for some reason?
If so, then open the file /etc/default/grub as root and change this line:
```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```
to 
```
GRUB_HIDDEN_TIMEOUT_QUIET=false
```
After you've done that, run
```
sudo update-grub
```

The next time you boot, the grub menu should be visible for 10 seconds (or whatever you change GRUB_TIMEOUT to in /etc/default/grub ).

it doesn't work.

I changed time to 3 seconds and update-grub and /boot/grub/grub.cfg does show 3 seconds, but menu list still does not display.

---

### Post by DeathByDenim on 2013-07-02
Does oldfred's suggestion work?
If not, you can try the stuff from this thread: [http://ubuntuforums.org/showthread.php?p=12249466](http://ubuntuforums.org/showthread.php?p=12249466)
It sound like the same problems as yours.

---

### Post by jtrol on 2013-07-02
resolved, thx a lot.

with this /etc/default/grub, no need to press shift


GRUB_DEFAULT=0
 **[COLOR=Red]GRUB_HIDDEN_TIMEOUT=[/COLOR]** 
GRUB_HIDDEN_TIMEOUT_QUIET=true
 GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 GRUB_CMDLINE_LINUX=""

---

