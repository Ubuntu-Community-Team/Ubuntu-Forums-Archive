---
title: "making ntfs partition visible"
date: 2008-01-06
forum: General Help
---

### Post by Dodelijk on 2008-01-06
Hello All, 


I'm trying to get access to my windows partition. I'm following an instruction on the net but this instruction doesn't work for me. 

My ntfs partition is an extended one. Here's what i've done so far: 

```

sudo apt-get install ntfs-config

```
Then 
```

gksu ntfs-config

```
and checked the two (write internal/external) options.

The instruction now says to edit the etc/fstab file by adding the following line:

/dev/  /media/  ntfs-3g defaults,locale=en_US.utf8 0 0

changing the /dev/ part for the position of my partition. 
When I look in gparted it says my partition is /dev/hda5. (it actually says i 
have an extended partition /dev/hda2/ of which there is the /dev/hda5/ ntfs
partition and an unallocated space)  so I added this line :

/dev/hda5/ /media/ ntfs-3g defaults,locale=en_US.utf8 0 0

but when I reboot i don't see the partition in /media/

I have also tried changing the /dev/hda5/ to /dev/hda2/ but this doesn't work. 
I'm not sure i'm getting it.

Can anyone help ? 

Thanks



p.s. if anyone wants the instructions its here [http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)
as it says its things to do after installing ubuntu. enjoy

---

### Post by taurus on 2008-01-06
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and modify the entry for your windows partition to look like this.

```
/dev/hda5   /media/hda5   ntfs-3g   defaults,locale=en_US.utf8   0   0
```
Save it and close gedit window.  Then, create that new mount point and mount it.

```
sudo mkdir /media/hda5
sudo mount -a
df -h
```
Meanwhile can you post the output of this command from a terminal to see exactly which partition is your windows.

```
sudo fdisk -l
```

---

### Post by Dodelijk on 2008-01-06
Thanks for the reply. 
I'll try your suggestion but meanwhile here's the output 

```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f719f71

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3502    28129783+  83  Linux
/dev/hda2            3764        4863     8835750    f  W95 Ext'd (LBA)
/dev/hda3            3503        3763     2096482+  82  Linux swap / Solaris
/dev/hda5            3764        4863     8835718+   7  HPFS/NTFS

Partition table entries are not in disk order


```

Is it a mess ?

---

### Post by taurus on 2008-01-06
I assume you want to mount /dev/hda5.  Just follow my previous post.

---

### Post by Dodelijk on 2008-01-06
Hello, 

The 
```

sudo mount -a 

```
 command fails: 
```

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda5 /media/hda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda5 /media/hda5 ntfs-3g defaults,force 0 0


```

What  should i do here ?

---

### Post by taurus on 2008-01-06
It means that you didn't shut down your windows cleanly.  So, you have two options:

1.  Boot into XP and shut it down cleanly.  This means _no_ hibernation or sleep mode.

2.  Or you can mount it with the force option.

```
sudo mount -t ntfs-3g /dev/hda5 /media/hda5 -o force
ls -la /media/hda5
```

---

### Post by Dodelijk on 2008-01-06
Ah, 

Thanks for the reply. I've just returned from a re-boot! 
I changed the ect/stab file to include this line 

```

/dev/hda5 /media/hda5 ntfs-3g defaults,force 0 0

```

 and i can see the partition now. Has this done the same as you were suggesting ? 

Thanks

---

