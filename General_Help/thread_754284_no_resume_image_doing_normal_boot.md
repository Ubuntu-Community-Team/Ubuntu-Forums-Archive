---
title: "no resume image doing normal boot"
date: 2008-04-13
forum: General Help
---

### Post by d_deniz on 2008-04-13
I know there are many posts about this but I couldn't find any solution, I was using firefox and suddenly system locked I couldn't open a terminal window so I shut down it. then when I turn on my computer ubuntu loading screen appears and then a red "fail" word is written on the top right corner.and it says 
```
Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/c7c2ccbc-18c3-4137-9cb2-f5cc7220f73) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/c7c2ccbc-18c3-4137-9cb2-f5cc7220f73
kinit: no resume image, doing normal boot...
```
and it leaves me in this situation
I can reach my files, but can't open some programs, and I want to use my computer from desktop, help please

---

### Post by Patb on 2008-04-13
> **d_deniz said:**
> 
```
Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/c7c2ccbc-18c3-4137-9cb2-f5cc7220f73) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/c7c2ccbc-18c3-4137-9cb2-f5cc7220f73
kinit: no resume image, doing normal boot...
```
and it leaves me in this situation
I can reach my files, but can't open some programs, and I want to use my computer from desktop, help please
If it leaves you "in this situation" how can you reach your files or open any programs?  

Try restarting in recovery mode, and if that works, restart with Control-Alt-Delete.  

Cheers, Pat.

---

### Post by d_deniz on 2008-04-13
what is the command to restart the computer in recovery mode? I know it is "restart" to restart the computer but I don't know the command to restart in recovery mode
thanks for reply

---

### Post by d_deniz on 2008-04-13
there is a bigger problem here I can't shoutdown computer Ican just restart it with 
```
reboot
```
however when I typed
```
shutdown (1 minute after as time)
```
it says
```
stopping system deamon---------------------------------[[COLOR="Red"]fail[/COLOR]]
stopping periodic command schedular------------------[[COLOR="Red"]fail[/COLOR]]
```

---

### Post by Patb on 2008-04-15
Deniz, sorry for the late reply.> **d_deniz said:**
> what is the command to restart the computer in recovery mode?
Choose the relevant line from the grub menu which is shown before the computer boots.  You should a line have something like:
```
Ubuntu 7.10, kernel 2.6.22-14-generic (**[COLOR="Sienna"]recovery mode[/COLOR]**)
```
If you do not see the grub menu, try hitting Esc as the system boots.  Otherwise, you might need to back up and edit the grub menu file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk1
sudo nano /boot/grub/menu.lst
```
Find the line which says 
```
timeout    0
```
and change it to 
```
timeout    10
```
Then save and reboot.  This will make your "grub menu" available for 10 seconds.  

Cheers, Pat.

---

