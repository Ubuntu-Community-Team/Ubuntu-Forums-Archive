---
title: "GRUB help NEED it"
date: 2007-07-16
forum: General Help
---

### Post by retroP on 2007-07-16
well I need to access the recovery mode but can't while booting for some reason. Is there a way from the terminal or anyother way?

---

### Post by yabbadabbadont on 2007-07-16
When the machine gets to the point that it is starting grub, hit the escape key to see the menu.  Then you should be able to select the recovery mode option.

---

### Post by retroP on 2007-07-16
> **yabbadabbadont said:**
> When the machine gets to the point that it is starting grub, hit the escape key to see the menu.  Then you should be able to select the recovery mode option.

I try that but it gives me 3 seconds and I press esc over and over but it won't work for some reason. Which is why I want to know if I can from a different session or terminal or something, or even the disk...

---

### Post by confused57 on 2007-07-16
> **retroP said:**
> I try that but it gives me 3 seconds and I press esc over and over but it won't work for some reason. Which is why I want to know if I can from a different session or terminal or something, or even the disk...
Try mounting your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Then place a # in front of hiddenmenu and change the timeout to something like 10 seconds:
```
#hiddenmenu
```
to
```
hiddenmenu
```

and

```
timeout  10
```

---

### Post by retroP on 2007-07-16
> **confused57 said:**
> Try mounting your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Then place a # in front of hiddenmenu and change the timeout to something like 10 seconds:
```
#hiddenmenu
```
to
```
hiddenmenu
```

and

```
timeout  10
```

I have no idea how to do any of that hidden menu stuff, could you clarify please?

---

### Post by confused57 on 2007-07-16
Read through the link that I gave you, it explains it pretty well...I'll try to summarize, but the instructions in the link do a much better job.
Boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a small "L"
This will show your partitions, determine which is your root partition, then enter:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
substitute your root partition from the results of "fdisk -l" in place of /dev/hda1

Then to make the changes that I suggested:
```
cd /media/ubuntu
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```
find the lines with hiddenmenu and timeout, make the changes, quit&save

I would be best to copy&paste the commands above...be sure to change your root partition, though....reboot, remove the live cd...you should automatically get the grub boot menu displayed.

---

### Post by retroP on 2007-07-16
> **confused57 said:**
> Read through the link that I gave you, it explains it pretty well...I'll try to summarize, but the instructions in the link do a much better job.
Boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a small "L"
This will show your partitions, determine which is your root partition, then enter:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
substitute your root partition from the results of "fdisk -l" in place of /dev/hda1

Then to make the changes that I suggested:
```
cd /media/ubuntu
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```
find the lines with hiddenmenu and timeout, make the changes, quit&save

I would be best to copy&paste the commands above...be sure to change your root partition, though....reboot, remove the live cd...you should automatically get the grub boot menu displayed.

thats my problem though, I accidentally removed my sudo status, so I can't use sudo. I want to access the recovery mode, but can't cuz it won't let me on boot. Is there a way to start it via disk, because I got the boot disk soooo.... idk...

---

### Post by confused57 on 2007-07-16
All of the instructions I've given you are using the desktop live cd...you can use sudo in the live cd.

---

