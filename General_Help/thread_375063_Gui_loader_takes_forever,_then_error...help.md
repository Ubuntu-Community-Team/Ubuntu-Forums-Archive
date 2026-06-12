---
title: "Gui loader takes forever, then error...help"
date: 2007-03-03
forum: General Help
---

### Post by dustin0 on 2007-03-03
When i turn on my computer I get to the Ubuntu loading screen it the bar doesnt move at all. And after about 5minuets I get this error

Big Picture:[http://www.dustin0.net/ubuntu/firsterror.jpg]("http://www.dustin0.net/ubuntu/firsterror.jpg")
[IMG]http://img59.imageshack.us/img59/2976/firsterrortj6.jpg[/IMG]

Ive restarted and taken out all of my PCI cards so its not a driver error (i dont think)

So help please and thanks !

 - Dustin

---

### Post by taurus on 2007-03-03
Can you boot into the recovery mode from GRUB menu at all?

---

### Post by dustin0 on 2007-03-03
> **taurus said:**
> Can you boot into the recovery mode from GRUB menu at all?

When i click  to  enter recovery  mode and  a lot of stuff loads. But it just stales at 

Removable Scsi Drive.....     sooo     anyhelp   please and thank you

---

### Post by taurus on 2007-03-03
Do you have a LiveCD handy somewhere?  Boot from it and post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by dustin0 on 2007-03-03
I have     Ubuntu 6.10 on the  65gb parition  and
Ubuntu server on the 75gb   parition....

Disk /dev/hda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       10199    81923436   83  Linux
/dev/hda2           10200       19133    71762355   83  Linux
/dev/hda3           19134       19452     2562367+  82  Linux swap

Disk /dev/sda: 1021 MB, 1021836800 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         125      997856    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(123, 254, 63) logical=(124, 58, 61)

Disk /dev/sdb: 131 MB, 131072000 bytes
5 heads, 50 sectors/track, 1024 cylinders
Units = cylinders of 250 * 512 = 128000 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     7679804     9857553   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(7679803, 4, 9)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(9857552, 1, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?     5320737     7476642   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(5320736, 4, 3)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(7476641, 4, 40)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     2155958     7749410   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(2155957, 2, 42)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(7749409, 1, 3)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *     5578511     5578596       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(5578510, 3, 14)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(5578595, 4, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by taurus on 2007-03-03
Which one do you have problem booting (partition)?  And look at all the warnings for /dev/sdb!

---

### Post by dustin0 on 2007-03-03
> **taurus said:**
> Which one do you have problem booting (partition)?  And look at all the warnings for /dev/sdb!

The 6.10

the server one is fine but i dont have any  graphical  display. Do u know how to fix those errors? and the boot  loader.....?

 - Dustin

---

### Post by taurus on 2007-03-03
Which partition is your desktop 6.10 located?

If you want to install Gnome on your server version, just run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by dustin0 on 2007-03-03
I belive its on /dev/hda1
is there a code to check on what drive its on?
Thanks for the server graphical display  but its the  feisty fawn so i dont wana use that on my main OS    
plus i have other stuff  on the 6.10  so i wana fix it

---

### Post by taurus on 2007-03-03
The easiest way is to boot into your server and see what partition it is using as /.

```
df -h
```

---

### Post by dustin0 on 2007-03-03
Im installing the gnome display its gona take about an hour, so in an hour ill post an update on what drive it is.

---

### Post by taurus on 2007-03-03
Press <Alt>F3 to get to another virtual console.  Log in and run that command to see which partition (or disk) your server is on.

```
df -h
```
You don't have to sit there and wait for aptitude to finish before you can use your machine again.

---

### Post by dustin0 on 2007-03-03
Sorry it took so long

dustin@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              77G  2.6G   71G   4% /
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  104K  252M   1% /proc/bus/usb
udev                  252M  104K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/sda2              68G  6.6G   58G  11% /media/sda2
/dev/sdc              125M   69M   57M  55% /media/disk
/dev/sdb1             973M   88K  973M   1% /media/disk-1
/dev/scd0             479M  479M     0 100% /media/cdrom0


SO im guessing its on /dev/sda1

so can u help?

---

### Post by taurus on 2007-03-03
Did you install 6.10 first or did you install the server (the one you are using right now) first?  If you installed the server version first and 6.10 last, then 6.10 will install GRUB to your MBR and I need to look at the entries from 6.10.

---

### Post by dustin0 on 2007-03-03
> **taurus said:**
> Did you install 6.10 first or did you install the server (the one you are using right now) first?  If you installed the server version first and 6.10 last, then 6.10 will install GRUB to your MBR and I need to look at the entries from 6.10.

I installed 6.10 first and then the server but the server didnt mess it up. I unplugged my computer and moved around some hardrives and when i turned it back on i got that stupid error. I dont see my other parition ~The one that has all the stuff on it(6.10)~ if i could get a backup i wouldnt mind dumping the whole system and start fresh
So if telling me how to backup my data on the other parition would be easier we can take that route

---

### Post by taurus on 2007-03-03
Try something like

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sdb1 /mnt/ubuntu
df -h
```
Post the output of the last command.

---

### Post by dustin0 on 2007-03-03
Okay i can see my drive, is there an easy way to back up the home folder (on the broken OS) and the Desktop? Or should i just copy and paste it onto my network drive.

---

### Post by taurus on 2007-03-03
You can tar the whole $HOME on /dev/sdb1 into a single file and save it to your server partition or you can just burn the whole thing onto a DVD, if it's not more than 4.4GB.

```
sudo du -h /mnt/ubuntu/home
```

---

### Post by dustin0 on 2007-03-03
Thank you for ur help :) :) :) :) :) :)

---

