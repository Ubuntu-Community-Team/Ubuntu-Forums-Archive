---
title: "Can't mount NVME drive"
date: 2021-04-10
forum: General Help
---

### Post by wcnackers on 2021-04-10
All,

I had retired for a year, then got bored and am now back to work part time.  So I haven't used Ubuntu or any form of Linux for over a year.  Please be patient.

I have a system that has 24 NVME drives attached to a host system via 2 PCIe HBA adapters.  If I run lsblk I can see all 24 drives and it shows that all 24 drives are formatted with ext4.  However, I can't mount the drives.   I have tried via the terminal using the mount command and with the "disks" GUI.  I have tried fdisk'ing the drives and reformatting them.  Nothing.   

Ubuntu is 18.04.   The host system uses dual 6226 Cascade Lake CPUs and has 96GB of memory.   

Please, if anyone has any idea what the issue may be, let me know.  It is a work system so I won't have access to it until 4/12/21 but I can attach screen outputs of commands or anything else you would want to see at that time.

Thanks in advance for any help,

wcn

---

### Post by grahammechanical on 2021-04-10
I am out of my depth. Please confirm that the host OS has a mount point that the drives can be mounted at. It would be a folder or directory such as /media. Have you considered editing /etc/fstab?

This is what I did when I wanted to automount a Data partition on a second hard drive at boot time. You will need the Universally Unique Identifier (UUID) of each drive. this is what I put in my Fstab

> # to automount Data partition
UUID=311676c4-ca3e-46d7-8b81-a1a577f601d7 /media/Data ext4 auto,users,rw,relatime 0 2

I used the information from here

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Regards

---

### Post by TheFu on 2021-04-10
Please post commands and output. Simplify and test.
```
fdisk -l
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Assuming it isn't a driver, firmware or hardware issue.  Doubt we can help with those besides to say, check that each is current.

---

### Post by wcnackers on 2021-04-12
I found out I could mount the drives to /media....just not /mnt for some reason.   Not sure what changed...I had done it before.   Anyway...don't have time to investigate further and I don't want to waste any else's time.   Thanks for the replys.

---

