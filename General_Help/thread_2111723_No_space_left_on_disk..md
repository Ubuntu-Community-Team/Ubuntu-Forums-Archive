---
title: "No space left on disk."
date: 2013-02-02
forum: General Help
---

### Post by UAdnan on 2013-02-02
*The title might not be accurate, it's a tough choice.*

Here's the deal,
Until recently, I'd been enjoying my Xubuntu 12.04 on my Hp Mini 311 Netbook, until when suddenly, it decided not to boot.
Once we're there, I get the following two messages:
*** Starting Network connection manager wicd** * which I think is not the real deal. *
*** Checking battery state...** * and like this, I continue. *

I hit CTRL ALT F6, and I login, great.
I have tried many multiple things to repair it, I even uninstalled the Nvidia driver because before I started getting these errors, I was getting something related to that driver, I suppose. Hopefully I haven't removed it uselessly.

The filesystem is mounted at /dev/sda3/ , which is 100GB big.
**ls -ld /dev/sda3/ ** Gives:
**brw-rw---- 1 root disk 8, Feb 2 22:13 /dev/sda3**
So ... It looks like that hard disk is writable, what else ?

I have tried and tried. There is one common problem between all the commands I try to input, which I assume is related to that the hard disk is actually read-only (while it says it isn't?) 
**cp: failed to extend *...* : No space left on device **

I've booted a Ubuntu security Remix liveUSB, trying to get things done from there. Even when I deleted files from that drive, it was always full. Yes I was Root, yes I emptied _its_ trash later on.
Not to count the countless mess-ups and all the everything I manipulated.
Oh, plus, I was adviced to run: **ls -ld X.authority** to check if it's owned by Root or not, it turned out that yes it was, I changed it to user, nothing changed.

I am pretty desperate, and I miss the graphical login screen (although if you're a dead-end geek, you might be preaching the death of graphical interfaces :p )

The last recent thing I remember doing before getting that to happen, is that I allocated 10GB for Windows XP in a virtual machine, so what.
I'm not sure what else to provide, I'll make sure that everything is available upon request.

Lastly, I beg you to make your replies clear, if it's a command, help me write it down, I know my way around but I need a clear map ! 

Thanks a lot,
UAdnan.

---

### Post by Bashing-om on 2013-02-02
UAdnan; Hi !

Best practice to see/find out what is going on is from the command line.
Command line interface -> key combo ctl+alt+t
Listing of free space on your disk:
```
df -h
```Disk usage -in this instance- for your home directory:
```
du -h /home | sort -nr | less
```The -h option makes the size output more readable as "human", then the output is fed into the "sort" utility that organizes the output numerically (n), and reverses (r) the order to display the largest files first, and finally the output is fed into the "less" utility which lets you scroll up and down through the listing. Enter "q" to quit less.

One changes the argument "/home" to drill around the file system as needed.


Remove undesired files:
```
sudo rm <filename>  
``` Be careful and sure what you remove.
In the case of /boot's kernels, I suggest using synaptic to remove old kernels and headers for thorough clean up reasons.
/var/log/<files> : any file ending in ".gz"(archived) may be safely deleted.
House cleaning:
```
sudo apt-get autoremove
sudo apt-get clean
```
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by UAdnan on 2013-02-02
Thanks mate, but I'm pretty sure I have already tried removing undesired files and running the commands you have just proposed.
I'd like to add something that seems uneven, I'm not sure what it is, but I'll just tell out:
While using Ubuntu LiveUSB (which I'm doing meanwhile), I went into Disks and found:
160 GB Hard Disk.
2.0 GB Drive 
8.3 Drive
[b]Other Devices
757 MB Loop Device
/cdrom/casper/filesystem.squashfs[/b] 
(The non-bold disks are known to me)

I just wonder what that could be ...

---

### Post by ibjsb4 on 2013-02-02
We could tell better if you  post the output of

```
df -TH
```

Just a bit easier to read than df -h

---

### Post by serpantman on 2013-02-03
```

du -h / | grep ^[0-9.]*G

```

Will help find the big files.

---

### Post by UAdnan on 2013-02-04
> **serpantman said:**
> ```

du -h / | grep ^[0-9.]*G

```Will help find the big files.

Uh-Oh, the big files were actually still hiding somewhere, thanks for helping me out.
It's just a bit annoying that once there's no enough unused space granted for it, ***** happens.

Thanks again.

---

