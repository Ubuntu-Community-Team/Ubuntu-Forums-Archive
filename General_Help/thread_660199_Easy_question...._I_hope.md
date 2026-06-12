---
title: "Easy question.... I hope"
date: 2008-01-06
forum: General Help
---

### Post by gdxchris on 2008-01-06
I am trying to make my Windows XP Partition available for use.  I was reading a tut on how to do that by going to System > Administration > Disks.  I can't find 'Disks' under administration.  Is there some other way to access this?

Best Regards,
Chris

---

### Post by taurus on 2008-01-06
You just have to mount it first before you can access it.  You can add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.  Open a terminal and post the output of this command to see which partition your windows is resided.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L, not number 1.

---

### Post by ModelM on 2008-01-06
If you install the gparted package, I think you'll find what you are looking for under:

System > Administration > Partition Editor

---

### Post by gdxchris on 2008-01-06
Can you give me a link to a tut that will go step by step on how to mount it please?  By the way, im running on Gutsy 7.1

EDIT:  I executed the command and WIndows XP was not on the list. :(

---

### Post by ModelM on 2008-01-06
Sorry, I misunderstood. When you said you wanted to make the Windows partition "available for use", I thought you meant you wanted to wipe the partition & format it.

Just ignore my advice (I'm used to it, my ex-wife always did.) :)

---

### Post by taurus on 2008-01-06
It would be nice if you show the command that you ran and the complete output.  Then,  I can walk you through it but here is the link.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by gdxchris on 2008-01-06
Are you saying you would like me to take a screenshot of me executing the command in the terminal?

---

### Post by Dodelijk on 2008-01-06
Hey i'm trying to the same. 

Read step 2 of this : [http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

It worked for me on another machine but unfortunatly i can't get it t work with extended partitions. It also tells you how to 'see' linux partitions from windows

---

### Post by taurus on 2008-01-06
Run the command, then post the output here.

---

### Post by gdxchris on 2008-01-06
Here you are

---

### Post by ajgreeny on 2008-01-06
You don't appear to have a windows partition;  I hope you didn't inadvertently wipe it when you installed Ubuntu.
sda1 is your ubuntu partition, sda2 is the extended partition in which ubuntu automatically put the swap partition sda5  If you still had windows there would be another partition, probably sda1, with ubuntu moved up to sda2, and it would be ntfs.  There is no such partition showing so I fear it does not exist and your windows has disappeared at some point.

---

### Post by stzasnail on 2008-01-06
Be more specific on "Making it available for use". Do you want access to the files on there? Do you want to be able to acess Windows XP? Or do you want to reformat the partition and use the space created? 

If you want to do any besides the third, you may not be able to. By the looks of your screenshot, you have no NTFS partitions.

---

### Post by gdxchris on 2008-01-06
When I say "Making It Available for use" I just want to be able to log on via Windows XP.  I don't care about accessing the files.  I just want it for the compatibility.

---

### Post by ajgreeny on 2008-01-07
> When I say "Making It Available for use" I just want to be able to log on via Windows XP. I don't care about accessing the files. I just want it for the compatibility.Sorry, this still doesn't make sense.  The only way you can log on via windows is if you have a virtual install of ubuntu in vmware or virtualbox on your windows install, but you don't seem to have windows at all.  If you have both OSs on the system grub will let you chose which to use a boot up, but you cant switch from one to the other without rebooting, unless you have a virtual disk install.

---

