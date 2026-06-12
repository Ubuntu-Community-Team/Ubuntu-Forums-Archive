---
title: "ubuntu vs win8 boot"
date: 2014-01-23
forum: General Help
---

### Post by keith14 on 2014-01-23
[COLOR=#000000]Hi, on pc boot the top left of screen allows 4 choices to boot from. ubuntu is first and win8 last, if 10 seconds elapse ubuntu will boot. I would like to have win8 be the top choise, such that after 10 seconds elapse w/o a user selection then win8 will boot. How can I do this?[/COLOR]
[COLOR=#000000]Thanks,[/COLOR]
[COLOR=#000000]Keith[/COLOR]

---

### Post by deadflowr on 2014-01-23
You can either edit the GRUB_DEFAULT=number in the file /etc/default/grub.
and make the entry the number that win8 is listed.
Or,
try [grub-customizer]("https://launchpad.net/grub-customizer")

Of the two, grub-customizer is probably the better choice for you, now...(as a opposed to later)

---

### Post by coldcritter64 on 2014-01-23
> **deadflowr said:**
> You can either edit the GRUB_DEFAULT=number in the file /etc/default/grub....
Or the same file and Use the Windows entry title in the GRUB_DEFAULT= line
I forget the actual name of a Windows entry but a default for any specific boot entry can be booted this way.

If the windows entry from os-prober was "Windows 7 Loader" or like that the entry would look like

GRUB_DEFAULT="Windows 7 Loader"

Saved and with grub updated, this will set the default, if numbering is used and Windows is at the bottom a new linux kernel addition can throw out the default boot, going by title nothing will change even with a kernel addition in Linux.

---

