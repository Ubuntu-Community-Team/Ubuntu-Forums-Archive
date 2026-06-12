---
title: "root@(none) after editing /etc/init.d/rc"
date: 2007-07-26
forum: General Help
---

### Post by Joyride on 2007-07-26
Ok, it was my fault: I messed up my Kubuntu 7.04 installation cause i wrong edited the /etc/init.d/rc file to activate the Concurrent Booting.

Now the O.S. doesn't start and, if i choose the recovery option, after some lines of errors the system recognizes me as root@(none). I want to edit back the rc file with the vi command but i can't do this cause i'm not root.

If i try to switch user via the su root or the sudo command nothing happens and i remain as root@(none).

There is any workaround for this?

---

### Post by pointone on 2007-07-26
You should be able to edit the rc file using a live CD.

---

### Post by Joyride on 2007-07-26
SOLVED!!!

Sorry i'm very noob at Linux... I discovered that the error wasn't in the root account but in the mount device.

I used the command:

mount -o remount,rw /dev/sda1

So i got writing rights and i was able to modify the /etc/init.d/rc file...

I'm so happy! I think i'll spend the rest of the day with my girfriend and a lot of beer. :popcorn:

---

