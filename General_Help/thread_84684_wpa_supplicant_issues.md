---
title: "wpa_supplicant issues"
date: 2005-10-31
forum: General Help
---

### Post by utsaLinux on 2005-10-31
Hey all.  I am having troubles utilizing wpa_supplicant on Ubuntu.  I'm running a Dimension 2400 with a 3Com wireless card with an Atheros based chip.  I have been able to wpa running on other distros, and have had WEP on my current Ubuntu system, but I really prefer wpa.  When I run: 
  wpa_supplicant -B -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w
Everything looks great except for:
  ioctl[SIOCSIWPMKSA]: Operation not supported
and I never get a dhcp offer.

Is anyone familiar with my situation?  I appreciate any advice.

---

### Post by finni on 2005-11-02
Same problem here. WPA and dhcp used to work on hoary, but after upgrading to breezy wlan went berzerk.

I read on wpa maillist that wpa supplicant version 0.4.6 might/should fix that problem with madwifi devices. Breezy now has only 0.4.5.
[http://sourceforge.net/mailarchive/forum.php?thread_id=7938437&forum_id=33966](http://sourceforge.net/mailarchive/forum.php?thread_id=7938437&forum_id=33966)

EDIT: I got HP nc6000 with a Atheros A5212 chipset wireless card.

---

### Post by finni on 2005-11-02
Ah, my wlan is up and running again!
See last post from this thread: [http://bugzilla.ubuntu.com/show_bug.cgi?id=16785](http://bugzilla.ubuntu.com/show_bug.cgi?id=16785) 
or just install this package:
[http://archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.4.6-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.4.6-0ubuntu1_i386.deb)
and it should be working again!

---

### Post by finni on 2005-11-03
It works somehow, but not too well. Connection manager shows that connection breaks from time to time (avg. 2-3 times minute) but it manages to work. (I'm writing this over wlan.)
Something's not right. If wlan will not work soon, I will go back to hoary, it worked there flawlessly.. :confused:

---

