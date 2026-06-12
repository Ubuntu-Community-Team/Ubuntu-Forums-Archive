---
title: "[SOLVED] mount windows partitions"
date: 2008-06-05
forum: General Help
---

### Post by eskay_karthik on 2008-06-05
Hi.
I am using a dual boot ubuntu and windows.
I would like to mount my windows partition into my home folder (example  /home/eskay/windows)... because there are other users for whom I do not want to give access.
I think I must edit the /etc/fstab file. But I dont know how to edit. The partitions must automatically mount when I log in. 
For further information, if needed, I am using KDE.

This is the output of fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe00d5075

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9429    75736032+   7  HPFS/NTFS
/dev/sda2            9429       15166    46080000    7  HPFS/NTFS
/dev/sda3           18386       19457     8603648    7  HPFS/NTFS
/dev/sda4           15167       18380    25816455    5  Extended
/dev/sda5           15167       17883    21824271   83  Linux
/dev/sda6           17884       18380     3992121   82  Linux swap / Solaris

And I need to mount sda1 and sda2 ... 

Please help..

And also explain how to mount these partitions from terminal .. i would like to learn.. Thanks

eskay

---

### Post by rraj.be on 2008-06-05
Use NTFS configuration tool's to set that.

To mount from terminal just type.


sudo mount /dev/sda1 /media/<NAME of your mount point>

I think that you cant specify your mount point in NTFS CONFIG TOOL to /home.

---

### Post by Green_Star on 2008-06-05
if you are trying to mount try like this.

sudo mount /dev/sda1 /your_folder_path

right now I am not at ubuntu machine so i can not confirm.

---

### Post by eskay_karthik on 2008-06-05
what is the ntfs configuration tool ??? never heard of it ..

---

### Post by eriqjaffe on 2008-06-05
If you want to ensure that it gets mounted automatically at startup, you'd be best off mounting by the UUID of the partition.

There are a bunch of threads on the forums about how to do that, but the basics commands you'll need are:

```
sudo cp /etc/fstab /etc/fstab_backup
sudo fdisk -l
sudo blkid
sudo gedit /etc/fstab
```

Explained...

1) Makes a backup of your fstab, just in case you mess it up.
2) Gets a list of your disks & partitions so you know which one is which
3) Gets the UUIDs of the partitions, just match them up with the list from fdisk.
4) Edit the fstab file as root (regular users can't save changes to it).

---

### Post by eskay_karthik on 2008-06-05
/dev/sda1: UUID="7C80C73980C6F922" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="38BC5BC7BC5B7DF6" LABEL="ESKAY" TYPE="ntfs" 
/dev/sda3: UUID="9242CA5442CA3CAB" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="fe451631-0de9-4b16-826d-f3e30a0711ec" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="346698e9-97ab-444a-992f-1a2902305af4" 
/dev/sdb1: LABEL="ESKAY-1" UUID="A480-DCA4" TYPE="vfat" 


this is the output of sudo blkid   .... mow how am i supposed to edit the fstab ???

---

### Post by rraj.be on 2008-06-05
You can find NTFS configuration tools under the menu  of SYSTEM TOOLS.

right now i am inside GNOME.

I will conform after a few min plz.

---

### Post by rraj.be on 2008-06-05
Editing fstab may be somewhat tricky.

It can be modified automaticaly if you enable


```
Enable Write Acces To Internal Devices 
```

in NTFS CONFIG TOOL

---

### Post by eskay_karthik on 2008-06-05
I just did sudo mount /dev/sda1 /home/eskay/windows
It works fine. But there was no change in /etc/fstab   . Why ?? 
Instead, the change was in /etc/mtab ... 

Will I have to do this process every time I boot ??

---

### Post by rraj.be on 2008-06-05
Justdo this to make all your NTFS drives auto mount.


first un mount all drives,.

 Go to
```

system --> NTFS configuration tools.

select all partitions to be mounted and select suitable mount points.

click apply

A new window will pop up and in that check 

Enable write access to internal devices.
click ok


```

Now each time when you boot all your drives will be mounted automatically.

---

### Post by eskay_karthik on 2008-06-05
there is no such option for NTFS config tools under system .probably i have to install it .. will check now ..

---

### Post by rraj.be on 2008-06-05
To install just type

```
sudo apt-get install ntfs-config
```

---

### Post by eskay_karthik on 2008-06-05
installed the configuration tool. thank you very much..

---

### Post by eskay_karthik on 2008-06-05
and r u sure i need not do this every time i boot ??

---

### Post by eskay_karthik on 2008-06-05
when i try to give /home/eskay/windows/eskay , it says

/home/eskay/windows/drive contains an invalid caracter.
you must choose a name, not a directory.

what should i do ??

---

### Post by rraj.be on 2008-06-05
No dear,You dont need to do every time.

just do it this time alone.

next time when you boot all your NTFS drives will be on your desktop waiting for you :)

just do what i have mentioned in

Reply #10.

ok i copied it here just see here.



```


Justdo this to make all your NTFS drives auto mount.


first un mount all drives,.

Go to
Code:

system --> NTFS configuration tools.

select all partitions to be mounted and select suitable mount points.

click apply

A new window will pop up and in that check 

Enable write access to internal devices.
click ok

Now each time when you boot all your drives will be mounted automatically
```.
__________________

---

### Post by rraj.be on 2008-06-05
> **eskay_karthik said:**
> 
/home/eskay/windows/drive contains an invalid caracter.
you must choose a name, not a directory.



You cannot select a folder to mount.

you can just give a name to your mont point as backup or 1 or just empty space or any name

---

### Post by eskay_karthik on 2008-06-05
my basic need is to mount it in my home folder.Do you say that it is not possible using ntfs-config ?

---

### Post by Green_Star on 2008-06-05
First thing is make sure the folder is empty where you are trying to mount.

if you want to auto mount everytime you boot, try editing fstab. 

Syntax is
> # "device name"        "mount point"       "fs-type"             "options"   "dump-freq" "pass-num"  
an example 
> /dev/hda1       /mnt/WinXP      ntfs-3g     quiet,defaults,locale=en_US.utf8,umask=0   0 0

if you are not sure what you are doing with options then try to copy an existing fstab line with NTFS, paste it at end of file and just change the device and mount point. do not worry about UUID crap. I did this and worked.

---

### Post by rraj.be on 2008-06-05
i dont think there's no way to mount inside home folder .


i will search xomething whether its possible or not.

But i am 75% sure we cant.

But we can set user permissions to not to access other folder's.

---

### Post by rraj.be on 2008-06-05
You just want it for security reasons only no?

If so i can suggest some other ide.

I dont know way to mount iside /home.

---

### Post by eskay_karthik on 2008-06-05
I got the method ... I mounted it as u told, ... and then changed the entry in /etc/fstab ...

---

### Post by rraj.be on 2008-06-05
i got a way.

You can mount into home directory if and only if you have root privelages.

Just try this

```
sudo mount /dev/sda1 /home/<your_username>/<your_foler name>
```

---

### Post by eskay_karthik on 2008-06-05
now i am having a new problem ... my pen drive is not mounting automatically ... i am mounting it every time from terminal .. how to rectify this ?

---

### Post by rraj.be on 2008-06-05
Is it working safe right now.

---

### Post by eskay_karthik on 2008-06-05
ya .. the windows partitions are working ... no problem with that .. auto mount into home folder occurs properly .. :-) but now the prob is with pen drive .. i am mounting it manually ...

---

### Post by rraj.be on 2008-06-05
post the output of dmesg for your usb

---

### Post by eskay_karthik on 2008-06-05
btw, this is part of o/p of fdisk -l ... 


Disk /dev/sdb: 4089 MB, 4089446400 bytes
33 heads, 63 sectors/track, 3841 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3842     3993584    b  W95 FAT32


Do u want me to type in the o/p of dmesg | grep usb ???

---

### Post by rraj.be on 2008-06-05
Mark this as solved if its solved.

As you made a new post to pendrive better mark it solved.

---

### Post by eskay_karthik on 2008-06-05
Actually it is not yet solved ... I am still not getting the icon on the desktop. I need help as to how to do it ... 
Anyways, thank u very much for patiently helping me out ... 

eskay

---

### Post by rraj.be on 2008-06-05
Is the shortcuts of drives doesn'nt appear on your desktop or whether not even a single other icons are appearing on the desktop.

---

