---
title: "Readding drive to raid 5 array (mdadm)"
date: 2008-05-28
forum: General Help
---

### Post by dinomight on 2008-05-28
Ok so i have something wierd going on with my raid 5 array. It might be due to my crappy raid controller.(fake raid). Anywho every so often i one of my drives fails (completely randomly might be sda1 or sdb1 or sdc1.) The drive is properly failed and dissapears from /dev until i restart at which point it is back. If I run: 

mdadm --detail /dev/sda1
(replace /dev/sda1 with whatever drive was failed from the array) 

the failed drive the drive thinks is fine however the array no longer shows it attached. Now every time this has happened i have been able to 

mdadm --manage /dev/md0 --add /dev/sda1 
(replace /dev/sda1 with whatever drive was failed from the array) 

Now the raid will spend the next 3 1/2 hours rebuilding the failed drive without any issue. The array will be fine for a while and then the same thing happens. I have a script that monitors /proc/mdstat and emails me within 5 minutes if anything happens to the array (and emails me a nightly status). So i know very quickly when something fails. I also am very certain that nothing has been written to the array since the failure (since it is a file server that only i use and i don't write to it all that often) so i am fairly certain that the drive is probably fine and could be added back to the array without needing it to be rebuilt from parity data. The problem is i'm not exactly sure how to do that. What command should i use to add a drive that the array thinks failed back to the array without needing to rebuild. I'm always afraid to use --create and --build because i'm not certian if it will just readd the drive or if it will wipe the array and all of the data and create a new array. 

I really just want to add the drive back and assume that the data is good ( a parity check would be sufficient but i don't want to have to rebuild the drive every time this happens).
Anyone with enough experience with mdtools that could help me out i would appreciate it. 

Oh one other weird thing after the drive fails but before i reset the box (only to have the drive reappear) I noticed that a new drive appears in /dev (/dev/sdd1) I'm fairly certain that this newly detected drive is actually the failed drive. Not sure if that info helps anyone but i think it might.

---

### Post by fjgaude on 2008-05-28
The only thing I can think of is you do have a flakey drive that has random failures.

Ater a failure and a reboot, have you tried simply trying to reassemble:

```
sudo mdadm --assemble --scan
```

You might even delete or rename the /etc/mdadm/mdadm.conf file before you try the above command.

---

