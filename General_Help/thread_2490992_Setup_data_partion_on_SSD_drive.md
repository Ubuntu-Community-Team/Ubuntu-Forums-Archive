---
title: "Setup data partion on SSD drive"
date: 2023-09-22
forum: General Help
---

### Post by bengtfalke on 2023-09-22
I have installed ubuntu server 22.04 and ubuntu desktop on a Mac mini from 2012.
I did accept the default partition suggestions and ended up with a 100 GB root partition. However the SSD drive is 1000 GB and I would like to use the rest of the
drive to store my data EG. Nextclode shared files.

Below is my current partitions. 

```
bengt@falkenc:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for bengt: 
NAME                      FSTYPE     SIZE MOUNTPOINT                   LABEL
loop0                     squashfs  63.4M /snap/core20/1974            
loop1                     squashfs  55.7M /snap/core18/2790            
loop2                     squashfs     4K /snap/bare/5                 
loop3                     squashfs  63.5M /snap/core20/2015            
loop4                     squashfs  73.9M /snap/core22/864             
loop5                     squashfs 236.9M /snap/firefox/3131           
loop6                     squashfs 485.5M /snap/gnome-42-2204/126      
loop7                     squashfs  91.7M /snap/gtk-common-themes/1535 
loop8                     squashfs 111.9M /snap/lxd/24322              
loop9                     squashfs 284.7M /snap/nextcloud/37045        
loop10                    squashfs  53.3M /snap/snapd/19457            
loop11                    squashfs  40.8M /snap/snapd/20092            
sda                                931.5G                              
&#9500;&#9472;sda1                    vfat         1G /boot/efi                    
&#9500;&#9472;sda2                    ext4         2G /boot                        
&#9492;&#9472;sda3                             928.5G                              
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4       100G / 
```

I have Ubuntu desktop installed so I can either use the terminal or the drive tool in the desktop utilities. 
I do hope for some tips or maybe even guidelines how to proceed.

---

### Post by oldfred on 2023-09-22
Please use Code Tags when posting text or terminal output.
Easy to add with Forum's Go Advanced forum editor & # icon.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

I do not use LVM.
But believe the default install uses smaller /, so you can later add or resize volumes (not partitions).
ThFu is one of several who post regularly on LVM.
[https://ubuntuforums.org/showthread.php?t=2487570](https://ubuntuforums.org/showthread.php?t=2487570)
[https://ubuntuforums.org/showthread.php?t=2476876](https://ubuntuforums.org/showthread.php?t=2476876)
[https://ubuntuforums.org/showthread.php?t=2372351&page=2](https://ubuntuforums.org/showthread.php?t=2372351&page=2)

---

### Post by TheFu on 2023-09-22
```
sda                                931.5G                              
&#9500;&#9472;sda1                    vfat         1G /boot/efi                    
&#9500;&#9472;sda2                    ext4         2G /boot                        
&#9492;&#9472;sda3                             928.5G                              
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4       100G /
```
tells me that you are using LVM. This is a very good thing from a flexibility standpoint, but not exactly noob-friendly.

Some thoughts.  I'm going to guess the commands and I'll be close, but may not be exact. Read the man pages if it doesn't work.

a. 100G for / is huge.  Much better to reduce that to 35G as step 1.

b. Created a swap logical volume. If this is a desktop, make it 4.1GB in size.  
```
sudo lvcreate -L 4.1G  -n swap vg-ubuntu
sudo mkswap /dev/vg-ubuntu/swap
sudoedit /etc/fstab    #   add the new swap LV there  (/dev/vg-ubuntu/swap) and remove the swapfile that exists, if it does exist.

```
c. Create a logical volume for the /home area and move all the files from the current /home into it.
```
sudo lvcreate -L 20G  -n home vg-ubuntu   # Check the size currently used, but 20G should be enough for 1 user.
sudo mkfs -t ext4 /dev/vg-ubuntu/home   # format the LV with ext4
sudoedit /etc/fstab    #   add the new home LV there  (/dev/vg-ubuntu/home)  

```
d. Create a temporary mount point, mount the new storage and copy over everything in the old /home/ to the new home
```
sudo mkdir /mnt/home-new
sudo mount  /dev/vg-ubuntu/home /mnt/home-new
sudo rsync -avz /home/  /mnt/home-new/   # if there are errors, 

```That should be enough for files in /home, provided you don't put media files there or other wasted crap there.  At reboot, this mount will move the /home, assuming you've correctly setup the fstab.

e. You might want to create an LV for /var/.  That's your decision. If you use lots of snap packages, this will need to be larger than expected.  If you place virtual machines here, it might need to be 200GB+.

f. You might want to create an LV for /media/data/.  That's your decision.  This would be where media files should go and perhaps lots of other junk.

g. After you copy over ll the files to the new /home/  that will leave the old files buried, hidden, underneath, inaccessible.  To remove them, you'll need to boot from a USB Flash drive, manually mount the old root, find the old home directory, and delete everything that isn't needed any more.  Be careful.

h. Also, if it were me, I'd reduce the current "root" logical volume from 100G to 35G, just to clean up the junk.  **lvreduce** is the command. It will need to be run from a USB flash drive boot, since reducing an actively used file system is a bit dangerous.  Be certain to use the option that includes resizing the file system in the lvreduce and lvextend commands is used.  Otherwise, you'll need to remember to run that file system reduce/extend commands separately.

I've posted my LVM layouts in these forums a few times over the last decade.

Expanding a logical volume that uses ext4 is 5 seconds. During the operation, the file system can be busy, active, mounted. It is 1 command.  If you work through an LVM2 tutorial, the good news is that LVM is LVM is LVM, regardless of Linux distro. Find a tutorial that makes sense to you - Ubuntu, RHEL, SuSE, Debian, whatever. The commands are the same. The ideas are the same.  Don't expect to use a GUI, ever. Most GUI tools for LVM are dead projects.

---

