---
title: "Delete /root by accident, any harm? can recover?"
date: 2008-03-13
forum: General Help
---

### Post by ljfrankie on 2008-03-13
I delete /root by accident, does it do any harm to ubuntu? Is there any way to recover?
It seems that ubuntu works fine now, but firestarter can not start.
Thank you in advance.

---

### Post by Oldsoldier2003 on 2008-03-13
> **ljfrankie said:**
> I delete /root by accident, does it do any harm to ubuntu? Is there any way to recover?
It seems that ubuntu works fine now, but firestarter can not start.
Thank you in advance.

do you have a backup? and did you delete /root with the gui or by command line? if you did it by the gui you might still be able to recover sine it would be in the .Trash...

---

### Post by Paul Weaver on 2008-03-13
/root doesn't contain much essential stuff -- it's the equivelent of /home/username, and as you presumably rarely log into root there's no real need. It's handy to have it just in case though, to prevent issues if you ever do log in as, or su to, root.

To recreate it, this should work

sudo mkdir /root
sudo cp /etc/skel/.* /root
sudo chmod 755 /root
sudo chown -R root:root /root

I guess that firestarter is run as root, and trys to create "/root/.firestarter". You may have lost some configuration settings for the program (and any other programs you run as root), but it's fairly salvagable.

---

### Post by ljfrankie on 2008-03-13
Thank you.

---

