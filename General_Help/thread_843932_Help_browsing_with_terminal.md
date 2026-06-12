---
title: "Help browsing with terminal"
date: 2008-06-28
forum: General Help
---

### Post by Gangularis on 2008-06-28
I just recently added a harddrive to my ubuntu machine. I almost never play with my ubuntu box, it's just a file server for the most part. The harddrive I put in already has files on it, and i can access them from the GUI, but I need to grant more than read only permissions to the files so i can delete some of them. All of that said, I can't do this using ubuntu's GUI, since the *owner *of the files/folders is set as *root*. In order to change these permissions i guess i have to use that sudo command stuff with terminal. Anyway, I don't even know how to find the new drive in terminal. When i open up a terminal, it just says that I'm at the desktop.. My computer's name is Gang so it says "gang@gang-desktop". Although I do know how to use commands like "dir" or "cd", I still have no idea how i begin to find the new hard drive through terminal. Any help would be appreciated. 

Thanks, from a newbie.

---

### Post by VMC on 2008-06-28
> **Gangularis said:**
> I just recently added a harddrive to my ubuntu machine. I almost never play with my ubuntu box, it's just a file server for the most part. The harddrive I put in already has files on it, and i can access them from the GUI, but I need to grant more than read only permissions to the files so i can delete some of them. All of that said, I can't do this using ubuntu's GUI, since the *owner *of the files/folders is set as *root*. In order to change these permissions i guess i have to use that sudo command stuff with terminal. Anyway, I don't even know how to find the new drive in terminal. When i open up a terminal, it just says that I'm at the desktop.. My computer's name is Gang so it says "gang@gang-desktop". Although I do know how to use commands like "dir" or "cd", I still have no idea how i begin to find the new hard drive through terminal. Any help would be appreciated. 

Thanks, from a newbie.

From your Terminal if you type the following, it will reveal what drives are online:

```
sudo fdisk -l
```

Come back and display show the output

---

### Post by Gangularis on 2008-06-28
um... doesn't fdisk typically stand for "format disk"??

---

### Post by the yawner on 2008-06-29
> fdisk - Partition table manipulator for Linux

Type *man fdisk* on the terminal to know more about the command. But anyway, *sudo fdisk -l*:
> List the partition tables for the specified devices and then exit. If no devices are given, those mentioned in /proc/partitions (if that exists) are used.

---

### Post by Gangularis on 2008-07-01
thanks for the help. ok so i did that, now i get 

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       19457   156280288+   7  HPFS/NTFS

```


the 160 gb ntfs drive is the one i want to navigate to, and give full permissions on everything, so i can take full ownership of files with my windows computer. could you help me with how to navigate to it and alter the permissions for the entire drive?

---

### Post by soccerboy on 2008-07-01
see if there is anything under ```
ls -l /media/sdb1
``` and also ```
ls -l /media
```

---

### Post by a fenderson on 2008-07-01
Type 'mount' to show which folder the drive was mounted to and then 'cd */whereever*' to go to that drive.  Once you're in the right directory type 'sudo chown -R *your username* *' to gain ownership of the files.

---

### Post by Hooya on 2008-07-01
Well, if the drive is mounted, it's probably located in /media/disk
```
cd /media
dir
(output of "dir" lists mounted drives by label)

sudo chown -hR <yourusername> /media/<drivelabel>
```
(I think that's the right command at the end there)

If it's not already mounted, do
```
sudo mkdir /media/drive
sudo mount -t ntfs /dev/sdb5 /media/drive
```
then do the above commands.

Hope that's right, I'm pretty new to this stuff myself.

---

### Post by soccerboy on 2008-07-01
actually cd to the /media/<insert disk name here> directory and then run ```
sudo chown -R gang:gang *
```

---

### Post by Gangularis on 2008-07-23
I tried doing chown with -hR and -R
I also tried using gang:gang, as well as gangularis to make them the owner.
then what happens is a listing of the files being changed goes through terminal, and at the end of each line it says read-only filesystem. basically the output i get looks like this:

```
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10/VirtualDub.exe': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10/VirtualDub.vdhelp': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10/VirtualDub.vdi': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10.zip': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff': Read-only file system
chown: changing ownership of `Big Rig': Read-only file system
gang@gang-desktop:/media$ 

```


then I go to look at a folder or file's permissions, and it still says "Owner: root"  "Group: root"
it's stuck as read only, and I can't change the access still.

---

### Post by spupy on 2008-07-23
> **Gangularis said:**
> I tried doing chown with -hR and -R
I also tried using gang:gang, as well as gangularis to make them the owner.
then what happens is a listing of the files being changed goes through terminal, and at the end of each line it says read-only filesystem. basically the output i get looks like this:

```
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10/VirtualDub.exe': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10/VirtualDub.vdhelp': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10/VirtualDub.vdi': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff/VirtualDub-1.5.10.zip': Read-only file system
chown: changing ownership of `Big Rig/Old Desktop Stuff': Read-only file system
chown: changing ownership of `Big Rig': Read-only file system
gang@gang-desktop:/media$ 

```


then I go to look at a folder or file's permissions, and it still says "Owner: root"  "Group: root"
it's stuck as read only, and I can't change the access still.

That is because chown is changing ext3 premissions. NTFS doesn't have such features, so chown wont work. You need to mount the NTFS drive for your user. But someone else can explain this, I'm not that knowledgeable.

---

### Post by Gangularis on 2008-07-23
Geez, I can't believe how complicated this is.. All I want to be able to do is take ownership of the files, so I can delete and edit them. 

:(

---

