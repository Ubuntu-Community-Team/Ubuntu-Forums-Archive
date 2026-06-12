---
title: "swap changed to a new partition, and so how to update that swap location?"
date: 2019-10-31
forum: General Help
---

### Post by james2b on 2019-10-31
Have Ubuntu Mate 18.04 and Mint 19.01 installed and I did some partitions changing which then changed the swap file from /dev/sdb5 to now /dev/sdb3 and so how do I make this correction so that swap is active again? If I can get the terminal commands to enter to fix this, thanks. I do know the file for this is in; /etc/fstab, but that is read only. With my 16 GB of memory in this computer, does Linux normally even use the swap file?

---

### Post by yancek on 2019-10-31
If you do have a swap partition and it changed due to your actions, you will need to change the entry on both Mint and Ubuntu in their respective /etc/fstab files.  You need to be root (use sudo) to make changes in that system file.  Turning swap on is done with the swapon comand again, using sudo.  You probably won't need it with that much RAM but that depends upon what you use the computer for.  See the link below for Ubuntu documentation on swap.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by hk42 on 2019-10-31
sudo nano /etc/fstab should work.
Beware that the partition where your swapfile is should be mounted somewhere
in your root file system before defining the swap.

---

### Post by TheFu on 2019-10-31
Make a backup copy of the fstab before starting.
```
sudo cp /etc/fstab  /etc/fstab.old
```
Then edit the fstab
```
sudoedit /etc/fstab
```
and change the line for the swap.  sudoedit is the safest command to edit system files. Any editor you like, that is installed, can be used, safely this way.  NEVER use a GUI file editor with plain sudo.

Then you can either tell the system to remount everything in the fstab
```
sudo mount -a
```
or 
```
sudo swapon -a
```

For a desktop, there should be swap so when memory begins to run out, the system becomes slower before crashing.  The end-user is expected to "feel" the system slow down and take action to prevent an out-of-memory condition.  Use **top** to see that happening, before it actually happens.

IMHO, there is 1 size for swap on all desktop systems - 4.1GB.  Modern browsers are hogs.  2GB isn't enough.  Much more than 4G is a waste.  There are a few exceptions if you are running a VPS hosting company or use hibernation, but everyone else running a modern Linux desktop needs 4.1GB.

---

### Post by HermanAB on 2019-11-01
Note that the best swap documentation is in the swapon man page - it is really well written:
$ man swapon

---

### Post by james2b on 2019-11-02
So I did finally find out the method and did the changes. Since I have Linux installed on both a external esata drive, and on a solid state drive internal, I entered both swap file locations. In the fstab file as read only it says to run the blkid command to retreave the UUID for the swap partitions. Okay so I did run this; sudo xed /etc/fstab, and the xed can be any text editor application. Then I ran this; sudo blkid /dev/sdb3 to get the UUID and copy it to paste into the fstab file in place of the wrong UUID. And be sure to remove the quotation marks first, ("). Then click save file and exit fstab, and then I ran the swapon command for each correct swap file. Then in system monitor it shows swap active but not currently used, rather than not available. So now do also need to make it permanent with the mkinitrd script command to keep my changes? My 16 GB memory must be plenty for everyday use, since it shows 0% used. And thanks for all your help. Also is there a handy book with most Linux commands listed and good help for learning basic Linux? I do know about the help information with the man (your command) entered in a terminal window which really helps.

---

### Post by james2b on 2019-11-02
With the newer Linux can I change the /etc/fstab as root from UUID to by device to identify the swap location, such as; /dev/sdb3, or will the system not allow that change? This PC is a 11-2012 Dell XPS set with legacy BIOS and not the UEFI type, and the drives are all the MBR type so not the newer GPT.

---

### Post by TheFu on 2019-11-02
While you can change the UUID into a direct device path, that's a terrible idea.  Device order, the name, change.  Every reboot and the device path can change.  UUIDs do not change.

UEFI/BIOS and MBR/GPT don't matter for any of this.

---

