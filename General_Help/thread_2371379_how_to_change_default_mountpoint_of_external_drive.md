---
title: "how to change default mountpoint of external drives /media to any other location in u"
date: 2017-09-14
forum: General Help
---

### Post by rahul146146 on 2017-09-14
I tried all the way of udev rules and scripts but its only mount VFAT  format. If I attach an NTFS type pd all hd its shows end point not  connected.
  Here is the script I used:
  ```
KERNEL!="sd[a-z][0-9]", GOTO="media_by_label_auto_mount_end"  
# Import FS infos  
IMPORT{program}="/sbin/blkid -o udev -p %N"  
# Get a label if present, otherwise specify one  
ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"  
ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"  
# Global mount options  
ACTION=="add", ENV{mount_options}="relatime"  
# Filesystem-specific mount options  
ACTION=="add", ENV{ID_FS_TYPE}=="vfat|ntfs", ENV{mount_options}="$env{mount_options},utf8,gid=100,umask=002"  
# Mount the device  
ACTION=="add", RUN+="/bin/mkdir -p /media/%E{dir_name}", RUN+="/bin/mount -o $env{mount_options} /dev/%k /media/%E{dir_name}"  
# Clean up after removal  
ACTION=="remove", ENV{dir_name}!="", RUN+="/bin/umount -l /media/%E{dir_name}", RUN+="/bin/rmdir /media/%E{dir_name}"  
# Exit  
LABEL="media_by_label_auto_mount_end"
```  But it only mounts VFAT filesysytems. I also tried github script but it's not working, same result as the script above.
  I just want to change the default mountpoint of usb and external hdd of all format with full permission just like the /media mountpoint.

plz help me out of this...........

is there anyone knows where is the default file of location of automount usb....  there i can put my location replaced to /media to /home/usrname/

is there anyone knows where is the default file of location of automount usb....  there i can put my location replaced to /media to /home/usrname/

---

### Post by HermanAB on 2017-09-14
Ensure that the external disk has a unique Volume name, then put the mount details in /etc/fstab and then the system will mount the drive where you specified.

---

### Post by rahul146146 on 2017-09-14
@Herman - thanks for reply, but i need all external drives mounted on my desired path nt on default path, its a gud idea but u are not make a entry all the time in fstab for all different devices

---

### Post by Morbius1 on 2017-09-14
I do not know the answer to your question so you might want to consider using something like this until someone comes by that does:

Create a directory in your home folder:
```
mkdir /home/username/MyMedia
```
Install bindfs:
```
sudo apt install bindfs
```
To test how this would work do a temporary mount:
```
sudo bindfs -o perms=0777 /media/username /home/username/MyMedia
```

When you plug in an external device it will mount to two places simultaneous: **/media/username/$LABEL** and **/home/username/MyMedia/$LABEL**.

If it does what you want you can add the line to /etc/rc.local above the "exit 0" line ( without the sudo ) or set this up in fstab:

```
/media/username /home/username/MyMedia fuse.bindfs perms=0777 0 0
```

---

### Post by Cavsfan on 2017-09-14
This is how I mount a USB NTFS drive,
Use the label of the drives and see [this post]("https://ubuntuforums.org/showthread.php?t=2295804&page=4&p=13549647#post13549647").

---

### Post by rahul146146 on 2017-09-15
thanks for reply , @morbius- its a gud one bro but if i want /media/drive_name to /home/username/data   so is it possible directly mount with data folder with bind....

---

### Post by Cavsfan on 2017-09-15
> **rahul146146 said:**
> @cavsfan - but all time i have to add new entry for new external drives..... actually my aim is change default location from system and put my location in that..

You can name that script what ever you want (I just named it fantom for my purposes) and mount as many external drives as you have.
This mounts 6 but, you can add as many as you want. Just change what is needed to match your system and drives.

Just create mount points for each and modify this:

```
#!/bin/bash
# Mount all external drives
sudo mount /dev/sdb1 /media/<your username>/drive-name-1/
sudo mount /dev/sdc1 /media/<your username>/drive-name-2/
sudo mount /dev/sdd1 /media/<your username>/drive-name-3/
sudo mount /dev/sde1 /media/<your username>/drive-name-4/
sudo mount /dev/sdf1 /media/<your username>/drive-name-5/
sudo mount /dev/sdg1 /media/<your username>/drive-name-6/
 
exit 0
```

---

