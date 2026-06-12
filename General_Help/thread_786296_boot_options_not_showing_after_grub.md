---
title: "boot options not showing after grub"
date: 2008-05-08
forum: General Help
---

### Post by hprashi on 2008-05-08
Hi,
    I installed Ubuntu 8.04 last week and was working perfectly fine till yesterday... 

    After computer boots... the grub starts and freezes.... It says

> Loading Grub stage 1.5

Loading grub please.. will take time....

and it freezes there.... I left the comp for nearly an hour and nothing happened... and after rebooting for 5-6 times.. it works fine... 

Little more data....
    I started using torrents 2 days back and the comp will be know like 8-10 hrs at a stretch.... is this anything to do with this booting problem?

---

### Post by didac on 2008-05-08
I don't want to be scary but maybe your hard disk has started developing problems. Do you hear any scratching sound, or a tick-tick-tick? If you have smartmon installed and running, it may tell you something. Or try

```
sudo badblocks /dev/sda1
```

/dev/sda1 is your booting partition, where /boot is. Badblocks looks for bad blocks (How original)

Or maybe is your RAM which is giving problems.

---

### Post by hprashi on 2008-05-08
i was getting the tic tic sound..... now the computer is showing the boot screen .. even after a 100 reboots....

i tried inserting the ubuntu live cd and the screen comes where i need to choose to continue and after i choose an option computer reboots!!!

whats wrong? my hard-disk or ram... or both... [:(]

does formatting the whole hard disk solve the bad block problem?

---

### Post by didac on 2008-05-12
hprashi,

Sorry about the delay. I wasn't around.

If your HD makes a tick-tick sound, it has started failing. Don't use it anymore until you buy a new hard disk or you plug it in another computer. The more you continue using it, the more data you are going to lose.

No, formatting will not solve any problem, it will only accelerate disk degradation.

Sorry about the bad news...:(

---

### Post by hprashi on 2008-05-12
thanks a lot... damn unfortunate... will get a new hard disk soon... thanks a lot for the help...

---

