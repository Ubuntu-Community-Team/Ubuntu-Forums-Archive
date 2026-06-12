---
title: "How to make grub automatically boot to windows if I dont hit a secret keystroke"
date: 2014-04-04
forum: General Help
---

### Post by Getindor_Fiftousu on 2014-04-04
so I want to boot to ubuntu if i hit ctrl-u and if I dont hit it for it to boot to windows. Is this possible?

---

### Post by oldfred on 2014-04-04
You need to change /etc/default/grub.
It has a line which defaults to boot first (counting from zero) entry in menu
 GRUB_DEFAULT=0

You can manually count entries and change number.
But I prefer to use description which also can be used instead of the number.

      
 find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by Getindor_Fiftousu on 2014-07-07
> **oldfred said:**
> You need to change /etc/default/grub.
It has a line which defaults to boot first (counting from zero) entry in menu
 GRUB_DEFAULT=0

You can manually count entries and change number.
But I prefer to use description which also can be used instead of the number.

      
 find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

:D Thanks

---

