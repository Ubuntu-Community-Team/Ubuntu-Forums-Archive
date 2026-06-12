---
title: "installing lirc"
date: 2008-05-24
forum: General Help
---

### Post by stefansjs on 2008-05-24
I am running a server install of Ubuntu (for the purpose of running mythtv) and I am unable to get lirc installed.  Lirc was working on Fiesty, but when I upgraded to Hardy it stopped working.  I tried installing from these instructions: [https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy).  I have also tried installing from source following instructions from here: [https://wiki.ubuntu.com/LircHowto](https://wiki.ubuntu.com/LircHowto) (of course modifying it for the current lirc release and the current version of the kernel).  Both sets of instructions fail when it comes to the lircd.conf file because both sets of instructions rely on the repositories doing something for me that it refuses to.  I have no idea how to modify the lircd.conf file myself, because I don't know what module I should be using.  If anybody can give me instructions that actually work, I will be so so happy.  Please, this has been bothering me for a while.
thanks

---

### Post by stefansjs on 2008-06-01
Alright, well I found my problem.  I read (I don't remember where) that the newest kernel (2.6.24) does not support the lirc_gpio module.  I found a workaround online, but I have not yet tried it.  I'll post later if it works

---

### Post by kenmiles on 2008-06-04
> **stefansjs said:**
> Alright, well I found my problem.  I read (I don't remember where) that the newest kernel (2.6.24) does not support the lirc_gpio module.  I found a workaround online, but I have not yet tried it.  I'll post later if it works

Can you please let me know the workaround as this has bigged me for awhile now.
Regards, Kenneth.

---

### Post by stefansjs on 2008-06-04
This is the guide I've found.  I still haven't tried it yet, so I have no idea if it works, but this is going to be my first step.

[https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative](https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative)

---

### Post by kenmiles on 2008-06-04
> **stefansjs said:**
> This is the guide I've found.  I still haven't tried it yet, so I have no idea if it works, but this is going to be my first step.

[https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative](https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative)

Thanks for that. I have gone through all the stages and still get

/home/kenneth-->sudo /etc/init.d/lirc restart verbose
 * Stopping remote control daemon(s): LIRC                                                                                                                               [fail]
 * Loading LIRC modules                                                                                                                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

Regards, Kenneth.

---

