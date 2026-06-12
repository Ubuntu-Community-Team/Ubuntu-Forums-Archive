---
title: "Computer will not boot up!! I'm freaking out"
date: 2007-03-17
forum: General Help
---

### Post by hooked on 2007-03-17
Hello All,
   Yesterday I upgraded from edgy to feisty using sudo apt-get dist-upgrade. At that point I left the computer because projected download time was over 4 hours. I came back when it was finished and restarted my computer and now it will not boot. The load bar at the first screen gets about 2/3 of the way across and then switches to text. Some of the output messages are:
init:/etc/event.d/tty3:13: Unknown stanza
udevd[2016]: add_to_rules:invalid BUS operation
udevd[2016]: add_to_rules:invalid rule '/etc/udev/rules.d/51-udev.rules:1

All action halts after:
* Checking file systems...
fsck 1.40-WIP (14-Nov-2006)

I've also tried booting in recovery mode with essentially the same results, except that it stops at mapping the keyboard.

Please help!! I love this OS.

---

### Post by Meck1982 on 2007-03-17
Well I cannot really help you, just tell you that you are not alone with this... I have been using Feisty for a while now and the last update broke my system. I hope you have your home folder in a separate partition. Then you can just reinstall Edgy and mount it without loosing personal data.
If not, then... humm I hope there are people out there having better advices for you than me.
Feisty is really awesome... but it's still alpha and using it is still not recommended.

---

### Post by peabody on 2007-03-17
Can you boot from a live CD?  Can you mount the partition your Ubuntu is on?  If you can do both, you may be able to use a thing called "change root" to get into your installed system.  You can then attempt to fix the problem.

Something like:
sudo chroot /mnt
apt-get dist-upgrade --fix-broken

Run that a few times and see if it helps.

Edit: I forgot to mention you may need to mount the proc and sys filesystems for networking to work from within the chroot.
mount /proc
mount -t sysfs sysfs /sys

---

### Post by kerry_s on 2007-03-17
A clean install of feisty is the best fix. Feisty is still in testing and the changes from edgy is enormous. How feisty handles things is way different from edgy.

---

### Post by flapane on 2007-03-21
> **hooked said:**
> Hello All,
   Yesterday I upgraded from edgy to feisty using sudo apt-get dist-upgrade. At that point I left the computer because projected download time was over 4 hours. I came back when it was finished and restarted my computer and now it will not boot. The load bar at the first screen gets about 2/3 of the way across and then switches to text. Some of the output messages are:
init:/etc/event.d/tty3:13: Unknown stanza
udevd[2016]: add_to_rules:invalid BUS operation
udevd[2016]: add_to_rules:invalid rule '/etc/udev/rules.d/51-udev.rules:1

All action halts after:
* Checking file systems...
fsck 1.40-WIP (14-Nov-2006)

I've also tried booting in recovery mode with essentially the same results, except that it stops at mapping the keyboard.

Please help!! I love this OS.

I have init:/etc/event.d/tty3:13: Unknown stanza 
in feisty, I can boot but I can't access to tty's (eg. ctrl alt f1) and I NEED tty... what to do?

---

### Post by airtonix on 2007-03-23
the thing to do is prevent this from becoming a problem : 

have at least two partitions....one 4-6gb for the system, and the rest for your home directory.

thus you come upon this situation, do what you might think you can, but know that you can always be 1/2hr away from a celan system with the live cd.

simple...even more so when your adsl supplier mirrors the ubuntu repos  on a regular basis.

---

### Post by flapane on 2007-03-23
ok but...I've just reinstalled 2weeks ago, damn it...I can't see any reason in this problem, it seems meaningless, and I haven't deleted packages in the last days

---

### Post by aldegaz on 2007-03-23
I have the exact same problem doing thorugh update-manager

any ideas how to recover my data?

---

### Post by flapane on 2007-03-24
no, please confirm on [https://launchpad.net/ubuntu/+bug/95210](https://launchpad.net/ubuntu/+bug/95210)

---

### Post by aldegaz on 2007-03-24
there is actually a way to recover data using the live cd, you can find info here: [http://jclark.org/weblog/Miscellany/Tech/ubrescue.html](http://jclark.org/weblog/Miscellany/Tech/ubrescue.html)

---

### Post by flapane on 2007-03-24
it is useful when your xp doesn't boot up...
let's wait for developers in launchpad ;)

---

