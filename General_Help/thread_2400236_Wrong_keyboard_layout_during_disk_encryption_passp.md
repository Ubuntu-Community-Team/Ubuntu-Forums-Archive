---
title: "Wrong keyboard layout during disk encryption passphrase entry"
date: 2018-09-04
forum: General Help
---

### Post by zeroshi on 2018-09-04
Hi all,

I have been using Ubuntu since 2012 and have never encountered anything like this before. Right now I have 18.04.01 as a daily driver.
During GUI installation I've set LUKS passphrase (over 20 chars including symbols and numbers) in **ENGLISH LAYOUT. **I remember the password, have been entering it since the release of 18.04.
Since I can't see what I type (because of ***), it took me a while to realize that there is something wrong with a keyboard layout or something (I have English as system language and a second Russian keyboard layout.
I have tried all possible shortcuts to switch layout without any luck to get into the system.

**THE ONLY WAY FOR ME TO UNLOCK PC **was using [B]Alt Codes (eg. Alt+65 will give you "A" char).
[/B]
When I passed through LUKS encryption passphrase I was greeted by GNOME login page where layout is set to English by default (how it is supposed to be).
Then, I used Disks utility to change my LUKS encryption passphrase to Russian. After reboot, it accepts Russian passphrase from single try.

Now, how do I change my language layout to English during LUKS? initramfs?

Thanks

---

### Post by zeroshi on 2018-09-04
> echo "KEYMAP=Y" | sudo tee -a /etc/initramfs-tools/initramfs.conf
update-initramfs -u

Solved my problem!

---

