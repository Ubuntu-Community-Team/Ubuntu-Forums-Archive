---
title: "boot doesn't work the first time"
date: 2015-03-02
forum: General Help
---

### Post by george106 on 2015-03-02
Hello all,

I am new here.  I don't know if it is the right place to ask, but i didn't find any other group where i could post this query.

I have a peculiar problem.  I have installed ubuntu 14 lts on my portable external hard drive. It installed well, works fine, i have installed additional virtual box machines and they are also working fine.
The only irritating problem i face is that when cold boot the system it hangs on start up with only a cursor displayed 2 lines below from top. when i shut it down and then restart it works like a normal boot.

Any suggestions reasons why this might be happening. 

my sys specs are as under
amd xii Athlon 4 core 3ghz
6gb ram
asrock 960gc-gs fx motherboard

thank u

George

---

### Post by kc1di on 2015-03-02
You may want to give boot-repair a try you'll find it[ here.]("https://help.ubuntu.com/community/Boot-Repair")
if it does not work it will save a log file on line make sure you write down the address and post the output here.

---

### Post by grahammechanical on 2015-03-02
> [COLOR=#000000]it hangs on start up with only a cursor displayed 2 lines below from top[/COLOR]

I see something like that every time. How long do you wait? On my machine after a few seconds the Ubuntu boot loader (Grub) will present a boot menu. Is the BIOS/UEFI set to boot from the external drive? Did the Ubuntu installer install Grub to the boot loader of the internal drive? What OS is on that drive?

If the machine is looking first to the internal drive to find a boot loader and then the boot loader is directed to the external drive to find its configuration files - well it all takes time. So, please confirm that the loading process does indeed hang at that point and goes no further.

Regards.

---

### Post by dino99 on 2015-03-02
looks like a gdm/lightdm issue (does not know which one is used on LTS)

---

### Post by george106 on 2015-03-02
Hello kc1di,

i have done boot repair. the problem still persisits.  Pastebin link as provided is pasted below:
[http://paste.ubuntu.com/10505867/](http://paste.ubuntu.com/10505867/)

---

### Post by george106 on 2015-03-02
Hello grahammechanical,

Earlier when i installed the system about a month ago, i could easily do a c-a-d and reboot at this freeze and the reboot would work fine. But after some days the c-a-d option was not working and i had to mannualy shutdown the computer after starting it and then again restart it.

I am booting only from the external drive and there are no internal drives. i have set the boot to usb in bios.  and i have waited for more than a minute for it to boot from cold start.
during this period i see no grub menu.

---

