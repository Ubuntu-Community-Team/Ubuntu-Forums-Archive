---
title: "Trying to access external hard drive. Getting Error"
date: 2017-06-10
forum: General Help
---

### Post by johns-roth on 2017-06-10
I have an external hard drive that I'm trying to access from Ubuntu.  I wasn't able to mount it, and so I tried this code, and got the output shown

```
 sudo ntfsfix /dev/sdg
```
[HTML]   Mounting volume... Windows is hibernated, refused to mount. FAILED   Attempting to correct errors...  Processing $MFT and $MFTMirr...   Reading $MFT... OK Reading $MFTMirr... OK Comparing $MFTMirr to   $MFT... OK Processing of $MFT and $MFTMirr completed successfully.   Setting required flags on partition... OK Going to empty the journal   ($LogFile)... OK Windows is hibernated, refused to mount. Remount   failed: Operation not permitted
 [/HTML]
After some googling I tried to remove the hibernation in that external drive so I typed
```
   sudo mount -t ntfs-3g -o remove_hiberfile /dev/sdg3 /media/FE46D60C46D5C615
```[HTML]   ntfs-3g-mount: failed to access mountpoint /media/FE46D60C46D5C615: No such file or directory [/HTML]

That didn't work, so I absent-mindedly tried 
```
   sudo mount -t ntfs-3g -o remove_hiberfile /dev/sdg3 /media/
```
  Now when I try to access the drive I get the error
  [IMG]https://i.stack.imgur.com/RVb04.png[/IMG]

---

### Post by Bucky Ball on 2017-06-10
Welcome. Why don't you try booting that drive directly (set the BIOS to boot from it), boot into Windows (as it looks like it is a Win OS disk and trying to boot Win), switch off hibernation and SHUTDOWN Windows completely? Might work.

As you have probably figured out, there will be no accessing that drive the way you are trying to access it while hibernation is on. The other alternative is to completely wipe the drive. If you want to do that, use Gparted.

Install Gparted from your package manager (or boot the install media and 'Try Ubuntu' if not installed then launch Gparted). Navigate to the drive in question from the drop-down menu in the top right corner of the Gparted window.

Right click and unmount partitions there then 'Devices> Create new partition table'. Be warned: THIS WILL OBLITERATE ALL DATA AND PARTITIONS ON THAT DRIVE. 

In other words, make sure you are looking at the correct drive prior to hitting 'Go'.

That *should* work. Others may/will have further suggestions.

---

### Post by howefield on 2017-06-10
Moved to the "*General Help*" forum.

---

### Post by johns-roth on 2017-06-10
Weird!  I tried to boot into the device and windows gave me a huge ":(" and said that it couldn't boot into it.  Upon logging back into Ubuntu I am able to access the drive.  Thanks anyway for the help!

---

### Post by Bucky Ball on 2017-06-10
In that case, great! If you're happy, use Thread Tools at the top right to mark the thread as solved and help others. Good luck. ;)

---

