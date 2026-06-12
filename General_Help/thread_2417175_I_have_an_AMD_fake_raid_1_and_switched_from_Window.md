---
title: "I have an AMD fake raid 1 and switched from Windows to Ubuntu 18.04"
date: 2019-04-22
forum: General Help
---

### Post by dwk001 on 2019-04-22
My motherboard is an MSI 970 Gaming. This is an AMD board. I have my sata configuration in Raid UEFI mode. This mode worked well with windows for years, however with my new installation of Ubuntu, Linux can see my drives in the drive utility, but isn't seeing the raid. After some research it seems like this is called a fake raid, since it isn't handled through dedicated raid hardware. That being said, these 2 6TB drives are in a Raid 1 mirror configuration and have a lot of media files on them. Is there anyway for me to get Ubuntu to recognize my raid and mount it like windows did?

I have been playing around with a various number of commands with 'mdadm' and haven't had any luck so far. Again, Ubuntu can see my /dev/sda and /dev/sdb 6TB drives, but they aren't mounting and I would like to retain the data on these drives.

Is there anyway for me to keep the data on these drives and continue using the raid in linux? 

Some things I've tried are 

```
[COLOR=#DDDDDD][FONT=monospace]mdadm --add /dev/sda /dev/sdb[/FONT][/COLOR]
```

I get 

```
[COLOR=#DDDDDD][FONT=monospace]mdadm: /dev/sda does not appear to be an md device[/FONT][/COLOR]
```

Also

```
[COLOR=#DDDDDD][FONT=monospace]sudo mdadm --assemble /dev/sda /dev/sdb[/FONT][/COLOR]
```

results

```
[COLOR=#DDDDDD][FONT=monospace]mdadm: device /dev/sda exists but is not an md array.[/FONT][/COLOR]
```

Anything that you can do to help would be greatly appreciated. Thanks again.

---

### Post by rsteinmetz70112 on 2019-04-22
I'm not sure what windows does. What is the file system on the drives? I assume it's NTFS. 
Have you tried ```
sudo mdadm --assemble --scan
```

Also lvm2 has the ability do raid arrays.

Running
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```
Should give you information about the existing partitions as seen by Linux

[This article]("https://askubuntu.com/questions/567432/how-do-i-properly-access-windows-software-raid-0") provides information on using XP array's in Linux

---

### Post by rsteinmetz70112 on 2019-04-29
Try :

```
sudo mdadm --examine <device>

sudo mdadm --examine /dev/sda1
```

That should tell you a lot about the device and point you in a direction.

---

