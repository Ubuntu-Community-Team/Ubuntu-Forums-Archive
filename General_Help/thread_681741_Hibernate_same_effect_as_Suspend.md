---
title: "Hibernate same effect as Suspend"
date: 2008-01-29
forum: General Help
---

### Post by serhito on 2008-01-29
My Hibernate and Suspend function used to work perfectly, but now I have an issue.
Suspend still work as it is supposed to, but when I Hibernate, it basically does the same thing as Suspend. It does not shutdown. It goes to the login screen, I log back in and I am back where I was. 
The only thing I can think of from googling about the problem, I modified my swap partition a little while ago. I fixed the UUID in fstab.

Any idea ?

---

### Post by PmDematagoda on 2008-01-29
What modifications did you do to the Swap partition? And does the Swap partition still work properly?

---

### Post by serhito on 2008-01-29
Thank you for your answer.

I am fairly new to Linux, how do I check that the swap partition is ok ?

---

### Post by mali2297 on 2008-01-29
> **serhito said:**
> Thank you for your answer.

I am fairly new to Linux, how do I check that the swap partition is ok ?

There are probably several ways, but try this in the terminal:
```

free -m

```
What is your swap total?

---

### Post by serhito on 2008-01-29
free -m
             total       used       free     shared    buffers     cached
Mem:          2010       1905        105          0         42        623
-/+ buffers/cache:       1239        770
Swap:            0          0          0

Total is 2010

---

### Post by mali2297 on 2008-01-29
> **serhito said:**
> free -m
             total       used       free     shared    buffers     cached
Mem:          2010       1905        105          0         42        623
-/+ buffers/cache:       1239        770
Swap:            [COLOR="Red"]0[/COLOR]          0          0


The [COLOR="Red"]0[/color] above indicates that the swap partition is not seen by the system.

> **serhito said:**
> 
I fixed the UUID in fstab.


Apparently, you made some mistake here. I suggest that you replace the UUID with something like /dev/sda3 (check where you have the swap partition). This [link]("http://www.tuxfiles.org/linuxhelp/fstab.html") might give some guidance. Don't mess with the lines that concern the other partitions though.

I have my swap partition on /dev/hda7, and thus the line
```

/dev/hda7           none            swap    sw            0       0

```
in /etc/fstab.

---

### Post by serhito on 2008-01-29
Here's the output of my fstab file. The swap partition is the /dev/sda7
What do I have to fix ?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=8eab88b9-f344-492c-90a0-ecddce3b01af /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C2D8265ED8265149 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=AE54276254272C91 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=13D71D7F6E10A959 /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=D4D463ACD4638F92 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=EE046A95046A6097 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=330b2e6f-249f-4c55-8f1a-c0ee3b3e37d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

---

### Post by mali2297 on 2008-01-29
> **serhito said:**
> Here's the output of my fstab file. The swap partition is the /dev/sda7
What do I have to fix ?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=8eab88b9-f344-492c-90a0-ecddce3b01af /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C2D8265ED8265149 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=AE54276254272C91 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=13D71D7F6E10A959 /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=D4D463ACD4638F92 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=EE046A95046A6097 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=330b2e6f-249f-4c55-8f1a-c0ee3b3e37d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

First of all, make a backup.
```

sudo cp /etc/fstab /etc/fstab_backup

```

Check that swap is still located on /dev/sda7, type
```

sudo fdisk -l

```
in the terminal.

If that is OK, then just change
```

# /dev/sda7
UUID=330b2e6f-249f-4c55-8f1a-c0ee3b3e37d1 none            swap    sw              0       0

```
into
```

/dev/sda7   none            swap    sw              0       0

```
in /etc/fstab.

---

### Post by serhito on 2008-01-30
First of all thank you for taking the time to help me with this one. I really appreciate.
Is this the way it supposed to look ? If yes, then what do I do next to fix that hibernate problem ?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=8eab88b9-f344-492c-90a0-ecddce3b01af /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C2D8265ED8265149 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=AE54276254272C91 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=13D71D7F6E10A959 /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=D4D463ACD4638F92 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=EE046A95046A6097 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
/dev/sda7   none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

---

### Post by mali2297 on 2008-01-30
> **serhito said:**
> First of all thank you for taking the time to help me with this one. I really appreciate.
Is this the way it supposed to look ? If yes, then what do I do next to fix that hibernate problem ?


Reboot, and check **free -m** again. Hopefully, you will now see the available swap space.

---

### Post by serhito on 2008-01-30
free -m
             total       used       free     shared    buffers     cached
Mem:          2010        741       1269          0         26        302
-/+ buffers/cache:        412       1598
Swap:            0          0          0


I guess not much has changed.

---

### Post by mali2297 on 2008-01-30
Post the output of
```

sudo fdisk -l

```

---

### Post by serhito on 2008-01-30
> **mali2297 said:**
> Post the output of
```

sudo fdisk -l

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101        5908     6490228+   7  HPFS/NTFS
/dev/sda7            5909        6164     2056288+  82  Linux swap / Solaris
/dev/sda8            7061        9

---

### Post by mali2297 on 2008-01-30
I can't see what's wrong. :-k

From the terminal, run the commands
```

sudo mkswap -f /dev/sda7
sudo swapon /dev/sda7

```
and check
```

free -m

```

---

### Post by serhito on 2008-01-30
~$ sudo mkswap -f /dev/sda7
Setting up swapspace version 1, size = 2105634 kB
no label, UUID=45d97651-21d0-4ebb-a8f3-494dec15cdb2

s@NB1:~$ sudo swapon /dev/sda7

s@NB1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2010       1061        948          0         67        405
-/+ buffers/cache:        588       1421
Swap:         2008          0       2008

---

### Post by mali2297 on 2008-01-31
> **serhito said:**
> 
s@NB1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2010       1061        948          0         67        405
-/+ buffers/cache:        588       1421
Swap:         [COLOR="Red"]2008[/color]          0       2008


OK, now swap is working. The question is why it is not enabled automatically at boot.
Perhaps you could try another reboot. Note that it is not enough to restart the GUI.
Use
```

sudo reboot

```
from the terminal, just to be sure.

---

### Post by serhito on 2008-01-31
> **mali2297 said:**
> OK, now swap is working. The question is why it is not enabled automatically at boot.
Perhaps you could try another reboot. Note that it is not enough to restart the GUI.
Use
```

sudo reboot

```
from the terminal, just to be sure.


I did a few tests here. I did the sudo reboot and did the free -m and it was still ok. 
When I do a normal reboot everything is ok.
When I do suspend everything ok.
NOW. Hibernate seems to work until it shuts off. Upon restart, it does a normal reboot, but at this point that's when it is not enabled, and note that it does not restore to the state it was before. It just does a normal boot. So that's the only case where it seems to mess up the swap partition.

---

### Post by mali2297 on 2008-01-31
Open the file **/etc/initramfs-tools/conf.d/resume** in an editor. It should contain the line
```

RESUME=/dev/sda7

```
If not, correct it.

Then run
```

sudo update-initramfs -u
sudo reboot

```

After reboot, test hibernate again.

---

### Post by serhito on 2008-01-31
> **mali2297 said:**
> Open the file **/etc/initramfs-tools/conf.d/resume** in an editor. It should contain the line
```

RESUME=/dev/sda7

```
If not, correct it.

Then run
```

sudo update-initramfs -u
sudo reboot

```

After reboot, test hibernate again.


WE ARE ALMOST THERE !!!

Hibernate works but it comes back on with the wrong screen resolution. Comes out as 1024x768 instead of 1280x800. Mission almost complete.  :)

---

### Post by mali2297 on 2008-01-31
> **serhito said:**
> WE ARE ALMOST THERE !!!

Hibernate works but it comes back on with the wrong screen resolution. Comes out as 1024x768 instead of 1280x800. Mission almost complete.  :)

If you have nvidia, [this]("http://paulsiu.wordpress.com/2007/11/21/video-screen-shrinks-if-you-logout-after-sleep-or-hibernate-in-linux/") might help.

Can you change back to the correct resolution without restarting?

---

### Post by serhito on 2008-01-31
> **mali2297 said:**
> If you have nvidia, [this]("http://paulsiu.wordpress.com/2007/11/21/video-screen-shrinks-if-you-logout-after-sleep-or-hibernate-in-linux/") might help.

Can you change back to the correct resolution without restarting?

I can change back to 1280x800 but it looks a little blury. So it is definitely not the same. I need to reboot to recover the one I normally have.

I do not have an Nvidia. It's a dell laptop with an Intel 855GM chip.

---

### Post by serhito on 2008-02-05
> **serhito said:**
> I can change back to 1280x800 but it looks a little blury. So it is definitely not the same. I need to reboot to recover the one I normally have.

I do not have an Nvidia. It's a dell laptop with an Intel 855GM chip.

Any idea ?

---

### Post by mali2297 on 2008-02-05
> **serhito said:**
> Any idea ?

I'm out of them, sorry.

I don't know why you get the wrong resolution when you didn't before, You could try reinstalling acpi-support and your graphics driver, but I doubt that it will help.

---

### Post by serhito on 2008-02-06
> **mali2297 said:**
> I'm out of them, sorry.


No problem. You've helped a lot already. That's why I love Linux, it's that sense of community !!!!

See ya.

---

