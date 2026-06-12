---
title: "Read Only File System! (/home D:)"
date: 2013-03-15
forum: General Help
---

### Post by BlastDV on 2013-03-15
Hi there, can anyone help me with this please?, I use Ubuntu 12.10 with Windows 7 on the same Hard Disk but on different partitions. I also have another PC with almost the same config. And both computers are connected to my home network using a Router (the classic ISP connected to a Modem wich is connected to a Router, providing WiFi to the whole house). The problem is that I use to requiere files from one computer to another, my PC is always running W7 and my laptop is running Ubuntu (this is the most common situation) so when I need to transfer stuff I just go to the Network "folder" provided in nautilus to access my PC file system. I named all this because I think the problem has something to do with it.


You see, I've been getting Hard Disk's errors everytime I boot with Ubuntu on my laptop. It says something like: "Se encontraron errores al comprobar el controlador del disco /" , which may be translated as "There were mistakes checking the Hard Disk Driver /", and giving me the options: "Press F to try fixing the mistakes, I to ignore, S to skip the mounting or M to manual recovery". If I press F the system reboots after a few seconds, and no warning is reported again for the next booting. But I still having the same problem as I press 'I' to ignore this: My whole file system has a stunning Read Only mark everywhere! I can't even use Gimp cause when it tries to use the Exchange Partition, Ubuntu does not let it to. So I can't take a .jpg from my Windows partition and paste it to my Ubuntu Desk cause it gives me the error of "Read Only File System". I "can use" sudo nautilus to get higher permissions, but after lots of mistakes nautilus opens in a new window and I still having the same problem. 


Does anyone have an idea? I don't want to format and install everything from zero! Thanks!

---

### Post by papibe on 2013-03-15
Hi BlastDV.

I would recommend using a LIVE CD, and check and reparing the disk using fsck. For instance:

First, list your disks:
```
sudo fdisk -l
```
When you recognize your hard disks partitions (for example /dev/sda1), repair it like this:
```
sudo fsck -r /dev/sda1
```
Once you have repair them all, boot normally.

If you still having problems, look for errors, on dmesg or syslog for more clues:
```
grep -i err | /var/log/dmesg

grep -i ata | /var/log/dmesg

grep -i /dev/sda | /var/log/dmesg
```
try also on /var/log/syslog.

Espero que te sirva. Avísanos como te va con eso.
Saludos.

---

### Post by BlastDV on 2013-03-15
Thank you so much! I fixed this and now I can finally do whatever I want with my files!


I didn't even had to search for errors as you suggested, the fsck did all the job :)


By the way, any idea of why does this happen? The first time, my system was unable to boot! so I had to reinstall everything! Does it have anything to do with exchanging content from one system to another by my network without defining Shared Folders?

---

