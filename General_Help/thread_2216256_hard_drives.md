---
title: "hard drives"
date: 2014-04-10
forum: General Help
---

### Post by ronb19495 on 2014-04-10
this is weird,on windows my 5 hard drives are in sequence c,=windows d=ubuntu e=data, f=data, g=data in ubuntu disk utility sda=data,sdb=data,sdc=data,sdd=windows,sde=ubuntu does any one know whats wrong here gparted gives me same output as disk utility

---

### Post by CharlesA on 2014-04-10
The drive names can change, which is why it is a good idea to use the UUID to reference partitions.

Have a read:
[http://liquidat.wordpress.com/2013/03/13/uuids-and-linux-everything-you-ever-need-to-know/](http://liquidat.wordpress.com/2013/03/13/uuids-and-linux-everything-you-ever-need-to-know/)

---

### Post by ronb19495 on 2014-04-11
thanks for moving this thread but it is on 14.04 this is happening it hasnt happened on any of the other ubuntu systems i have

---

### Post by bab1 on 2014-04-11
> **ronb19495 said:**
> thanks for moving this thread but it is on 14.04 this is happening it hasnt happened on any of the other ubuntu systems i have

The device name (sdx) is assigned when the devices are discovered at boot time.  This can change and there is no logical order to the discovery.  The UUID is unique to the partition.  This has been this way for many years now.  The following is  from the top of the fstab file```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).

```

Try this command to see the UUID ```
blkid='sudo blkid -c /dev/null -o list
```

[COLOR="#0000FF"]Edit:  Cold boot the system with a USB flash drive inserted and you will see the change.[/COLOR]

---

### Post by grahammechanical on 2014-04-11
I think that with drives (not talking about partitions) it makes a difference in Linux which Sata connectors the drive is connected to. On my motherboard the Sata connectors are numbered 1 to 6. Put the drives into different numbered Sata connectors and the sda, sdb, sdc, numbering system changes.

Regards.

---

### Post by CharlesA on 2014-04-11
> **grahammechanical said:**
> I think that with drives (not talking about partitions) it makes a difference in Linux which Sata connectors the drive is connected to. On my motherboard the Sata connectors are numbered 1 to 6. Put the drives into different numbered Sata connectors and the sda, sdb, sdc, numbering system changes.

Regards.

It's random. In my server, sdb is the OS drive and sda is the RAID array, and sdc is my external backup drive.

The array is on a separate controller.

---

### Post by oldfred on 2014-04-11
My system is like grahammechanical's except I skipped a port and now when I plug in a flash drive it is sde., but if I reboot it is sdb and all the other drives are one letter higher.
So I have to pay attention on which drive is where.

---

### Post by ronb19495 on 2014-04-11
maybe I didnt make myself clear,I have five seperate hard drives on this computer, I fried the mainboard so had to install new mainboard which I got a computer tech to do I told him to put hard drives in sequence as they were beforeso I didnt get any problems it appers they are in the right sequence as windows also detects they are in sequence as **grahammechanical said linux can be picky so will check sata ports again have just checked sata ports it looks like they are not right after all **they have a0,a1,then 0 then 1 then 2 then 3 connected 4 and 5 are not used so I guessto make ubuntu happy I have to rearange the sata connectors

---

### Post by ronb19495 on 2014-04-12
@grahammechanical thanks you made me think and check sata ports rearanged them all ok now
thank you

---

