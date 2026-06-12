---
title: "[SOLVED] Keyboard not detected"
date: 2008-05-05
forum: General Help
---

### Post by Lau_of_DK on 2008-05-05
Gents,


I have a desktop setup with a Logitech DiNovo Edge wireless keyboard, that connects to a little USB BT device. 

When I boot my system, the keyboard is detected both at the BIOS and GRUB stages, but once it reached GDM its gone. If I enable automatic login in (and thus bypass GDM?) its still gone when I reach the desktop.

To use my keyboard I have to physically unplug the USB BT receiver, reinsert it and connect. This problem does not occur in Windows and has been present since my first install of Ubuntu 7.10.  (Have not ever tried different distros).

How do I cause auto-detection of my keyboard?


Looking forward to hearing your suggestions :)
/Lau

---

### Post by Lau_of_DK on 2008-05-05
Come on boys, is this a tough one?


/Lau

---

### Post by Wybiral on 2008-05-05
*bump*

---

### Post by Lau_of_DK on 2008-05-08
*boomp*

---

### Post by ubername on 2008-05-08
How odd, you have exactly opposite symptoms to me. I can't see my keyboard in grub but it works fine after Ubuntu boots.

(P.S. you may be alienating some forum members by referring to Gents and Boys. No problems here, but a thought)

---

### Post by Lau_of_DK on 2008-05-08
> **ubername said:**
> How odd, you have exactly opposite symptoms to me. I can't see my keyboard in grub but it works fine after Ubuntu boots.

(P.S. you may be alienating some forum members by referring to Gents and Boys. No problems here, but a thought)

Hey,

Yours might be a BIOS issue then? I seem to remember having the same, though only with USB (ie. not Ps/2) which ended up just being a setting.

Gents/boys - which title do the users of UF prefer?

---

### Post by 23meg on 2008-05-11
Press some keys at the GDM prompt and wait for about 15 seconds; does it work then?

---

### Post by Lau_of_DK on 2008-05-12
> **23meg said:**
> Press some keys at the GDM prompt and wait for about 15 seconds; does it work then?

Ahem... Yes it does! :) Why is that? Can I reduce it to 0.5s instead of 15s ?



/Lau

---

### Post by amn on 2008-05-23
> **Lau_of_DK said:**
> I have a desktop setup with a Logitech DiNovo Edge wireless keyboard, that connects to a little USB BT device. 

When I boot my system, the keyboard is detected both at the BIOS and GRUB stages, but once it reached GDM its gone.

To use my keyboard I have to physically unplug the USB BT receiver, reinsert it and connect.

How do I cause auto-detection of my keyboard?

The thread "[**Logitech DiNovo Edge freezes in logon**]("http://ubuntuforums.org/showthread.php?t=625203")" have a simple solution to this problem (quoted below). I've tried it and it works like a charm.

> **fraserj said:**
> *snip*

UPDATE: I FOUND A SOLUTION!!!!
per [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
The following command will sort this problem in no time:
Type this command in a terminal:
sudo gedit /etc/default/bluetooth

Then look for the line that says:
HID2HCI_ENABLED=1

and change it to this:
HID2HCI_ENABLED=0

Problem solved.

For future reference ([source]("http://ubuntuforums.org/index.php?page=policy")):
[QUOTE=Ubuntu Forums Code of Conduct]Searching the Ubuntu Forums is a quick way to see if someone has had your issue and if it has been answered. In a forum as large and active as this one, there's a good chance your question has been answered before, and you can get the information you want quickly.
[/QUOTE]

---

### Post by Lau_of_DK on 2008-05-23
> **amn said:**
> 

For future reference ([source]("http://ubuntuforums.org/index.php?page=policy")):


Thanks alot! :)

---

