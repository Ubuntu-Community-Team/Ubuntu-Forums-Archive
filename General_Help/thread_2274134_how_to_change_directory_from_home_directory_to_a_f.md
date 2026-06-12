---
title: "how to change directory from home directory to a flash drive I have just plugged in?"
date: 2015-04-18
forum: General Help
---

### Post by newbie14 on 2015-04-18
What to type in the terminal to change the working directory from home directory to a flash drive I have just plugged in?
cd flash_drive? cd d:/ ? cd d:\ ? cd dev/d/?

**SOLUTION**
type in the terminal:

```
cd "/media/username/diskname"
```

---

### Post by plucky on 2015-04-18
What does ```
mount
``` show you?

---

### Post by Holger_Gehrke on 2015-04-18
Depending on whether you have an older or newer version of Ubuntu, plugged in drives get mounted in a directory in /media or /media/"your_user_name". This directory has either the name / volume label of the filesystem(s) on the drive as it's name or - if the drive has no label - it's guuid(s) (a long-ish number in hexadecimal notation with a few dashes thrown in).
To give a name to a filesystem, you can either use gparted (the option only becomes available after unmounting the file system) or unmount from the command line and use one of "e2label","dosfslabel" or "ntfslabel" depending on the filesystem. Since these write directly to the device, you will need to use 'sudo' with these commands.
The "mount" command without any parameters - which plucky asked you to try - shows a list of all mounted devices, the directories they are mounted on, the file system types and the option used for mounting them.

---

### Post by newbie14 on 2015-04-18
I have typed ```
mount
``` in the terminal, and the terminal replied with this:

```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/fulani/.Private on /home/fulani type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=fa1faa6ff42e0c32,ecryptfs_fnek_sig=9d6515492b1f3f3a)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=fulani)
/dev/sdc1 on /media/fulani/UBUNTU 14_0 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

```

which line should I pay attention to?
what should I type next?

---

### Post by newbie14 on 2015-04-18
And oh, I use ubuntu 14.04 LTS

---

### Post by GrouchyGaijin on 2015-04-18
See Holger_Gehrke's reply (#3)
In the terminal use:
```
 ls /media/<your_user_name>
```
Replace <your_user_name> with your actual user name
This will show you the path to your Flash Drive.
In my case, I have an external drive called "Elements" connected to my machine.

So the command:
```
ls /media/john
```  gives me:
```
$ ls /media/john
Elements

```

I can change the working directory to the Elements drive by typing:
```
cd /media/john/Elements 
```

---

### Post by ajgreeny on 2015-04-18
cd "/media/fulani/UBUNTU 14_0"

You need to use the "" as you have a space in the pathway of the folder that is the mountpoint.
For future use of file and folder names it is always better to not have spaces in their names but to use an underscore or dash.

Also, to make life easier, you can use **cd /me** *(hit tab for autocomplete)* **fu**  *(hit tab again for autocomplete)* **UB**  *(hit tab yet again for autocomplete)*; each time you hit tab you will see the terminal autofill if there are no other folders or files starting with the same characters.

---

### Post by newbie14 on 2015-04-18
> **ajgreeny said:**
> cd "/media/fulani/UBUNTU 14_0"

Hey, that works, thanks ajgreeny

---

### Post by newbie14 on 2015-04-18
Now, I am at the /media/fulani directory, how to change the "UBUNTU 14_0" name to other name.. let's say flshdrve01 ?

---

### Post by ajgreeny on 2015-04-18
The flash drive partition is probably labelled as UBUNTU 14_0, so the easiest way to change that is using gparted, either from a live system (it's on all the *ubuntu live DVDs) or even by installing gparted in your installed OS.

Plug in the drive, open gparted, and in top right use the dropdown box to get to /dev/sdc.
/dev/sdc might have changed, depending on what other disks are attached so make sure you get the correct disk.
In the gparted window you will need to right-click on the partition and choose **unmount**, then go to **Partition ->Label** in menus and change the label from UBUNTU 14_0 to whatever you want (no spaces) and click on the green tick in the toolbar to carry out the action.

Done!  The flash drive will now automatically mount to /media/fulani/*newlabel*

---

### Post by newbie14 on 2015-04-18
Thanks, I will try it later.

---

