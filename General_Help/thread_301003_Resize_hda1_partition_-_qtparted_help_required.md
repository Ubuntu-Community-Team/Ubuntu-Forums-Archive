---
title: "Resize /hda1 partition - qtparted help required"
date: 2006-11-16
forum: General Help
---

### Post by tedrogers on 2006-11-16
Hi,

I'm trying to resize my /hda1 partition, essentially so that I can split it into two, so that I have a spare partition in order to perform a system backup onto using partimage.

My system is configured quite simply. I have a 20GB disk and 3 partitions.

Here's my df -l output:

```
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hda1             18492940   2491856  15061688  15% /
varrun                  127992       132    127860   1% /var/run
varlock                 127992         0    127992   0% /var/lock
procbususb               10240       104     10136   2% /proc/bus/usb
udev                     10240       104     10136   2% /dev
devshm                  127992         0    127992   0% /dev/shm
```

What's missing from here is my /hda2 (extended partition) and my /hda5 (swap).

When booting from the linux rescue CD, I can run qtparted and partimage - a perfect system for creating a full system back. But I'm stuck because I have to resize my /hda1 partition and it's not letting me.

The problem is that although there is an option to resize in qtparted, it is always ghosted out and I can never select it.

Today I thought that it might be because my /hda1 was active....so I unchecked the 'Active' option in qtparted and then 'Commited' the changed.

This didn't make a difference, even if I quit and reloaded qtparted, the resize option was still ghosted out.

Can anyone advise here on what I should be doing?

I don't think the partition is mounted...or at least it shouldn't be as I am running from a live CD. Correct??

I know this can be a dangerous business, so I want to be extra cautious.

Thanks all.

---

### Post by koenn on 2006-11-16
> Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hda1             18492940   2491856  15061688  15% /
looks to me that /dev/hda1 *is* mounted on /
and that would explain that you can't resize it.

try
```
mount
```
while running from the Live CD. This should show you all of what is mounted where ;
also list your disks and partitions and how they'd be mounted when running normally (not from CD), so we can compare.
I think its possible you're trying to resize the wrong partition, because the system from the live CD creates its own filesystem, or mounts your hd partitions. But I could be wrong. 

The unchecking 'active' has nothing to do with it, it's probably ment to set those bits that mark a partition 'active', something DOS (and Windows ?) need in order to consider a partition 'bootable'. Linux ignores it.

---

### Post by tedrogers on 2006-11-16
The above df -l output is how things are mounted normally under Edgy.

But here is my results for 'mount' under Edgy.

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

I will now boot into the rescue CD and do the same....and will update in a bit.

---

### Post by koenn on 2006-11-16
going to bed, work tomorrow. 
If noone else can help you sort it out in the meantime, I'll check in tomorrow

---

### Post by tedrogers on 2006-11-16
Hi Koenn,

Right then....just to reiterate...here's my 'mount' from edgy:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

...and here's my 'mount' from the rescue CD (took ages to write down and may have typo's, but is hopefully very accurate!)

```
tmpfs on / type tmpfs (rw)
/dev/nor on /initrd type ext2 (rw,nogrpid)
/sys on /initrd/sys type sysfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw)
udev on /initrd/dev type tmpfs (rw)
/newroot/dev/cdroms/cdrom0 on /mnt/cdrom type iso9660 (ro)
/dev/cloop on /mnt/cloop type ext2 (ro)
tmpfs on /mnt/cloop/lib/firmware type tmpfs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
udev on /dev type tmpfs (rw,nosuid)
devpts on /dev/pts type devpts (rw)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw,devmode=0664,devgid=85)
```

Phew! That was a lot of concentrating and typing. Hopefully I got it all down right.

Does this help things? 

Thanks.

---

### Post by wieman01 on 2006-11-16
Hi Ted, 

First of all, boot from the Ubuntu Live CD, not the Rescue CD for this operation. It much more convenient & has a GUI including GParted. Second, when booting "/dev/hda1" from Ubuntu Live CD all volumes/partitions should be unmounted by default as far as I remember. So that won't be a problem. Just in case... To unmount, do this from command line:
> sudo umount /media/[COLOR="Red"]**hda1**[/COLOR]
You can replace [COLOR="Red"]**hda1**[/COLOR] with whatever the device number of your partition is. 

Then fire up GParted & resize "hda1"... That won't be a problem for sure, I have done it many times myself. Can you try? It would equally help if you attached a screenshot of GParted so that we understand what's going on...

---

### Post by tedrogers on 2006-11-17
My first problem here is that I have never been able to run the live CD on this laptop...in Dapper 6.06 I had to use the text-install and with Edgy 6.10 I had to use the alternate CD.

For some reason, probably my rubbish Savage GFX on this IBM T22, I have never been able to boot graphically into X windows.

This occurs on many linux distros as well...although fedora core 5/6 and knoppix works better than the others.

Could I use one of these live CD's perhaps? Or is there a way I could continue to do this with the rescue CD?

Finally, for now, how might I create a screenshot without being logged into X windows?

Thanks.

---

### Post by hal10000 on 2006-11-17
Hi Ted,
you can choose a knoppix CD to resize your partitions, but before starting qtparted you have to look if there are any mounted filesystems from your harddisk. Just type the command mount on a xterm window. If you get something like
> /dev/hda1 on /media/hda1 type ext3 (rw)
or
> /dev/hda1 on /media/auto
then you have to unmount it before starting qtparted. I think that knoppix automounts the partitions on yout harddisk (but I'm not sure about that).
Also, you should unmount any other partitions that may be (auto)mounted.
> sudo umount /dev/hda1
sudo umount /dev/hda2
sudo umount /dev/hdaX
You should also swapoff your swap-partition (if it is used). You can safely do that if you have at least 256MB RAM.
> sudo swapoff /dev/hda5      (if this is your swap partition)
I'm not sure if it is really necessary to turn off swap, but if nothing else works, then you can try this.
After unmounting _all_ partitions from your harddisk (and probably swapoff) you can (hopefully) resize your harddrive

---

### Post by koenn on 2006-11-17
So far we've been trying to make sure nothing of the harddisks is mounted, so it could be resized. 

If this ( [http://qtparted.sourceforge.net/features.en.html](http://qtparted.sourceforge.net/features.en.html) ) is correct, resizing ect2/ext3 with qtparted is just not gonna happen.

the ubuntu live cd's have gparted (gnome partition editor), wich seems more performant : [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

Since you can't get X to work with the PC in question, you might want to try
the gparted live cd.

---

### Post by koenn on 2006-11-17
I just had a quick look at the gparted live CD. 
looks fine to me. 

If your laptop is acting up re. X config, try selecting
"use vesa" and/or "manual video config". The latter allows you to choose a low resolution and color depth that will propably work. 

I tried it on VMware - it wouldn't show anything untill I did the above and selected 800x600 and 16 colors.

---

### Post by tedrogers on 2006-11-17
That gparted live CD looks just the business...I will get it downloaded and give it a go.

I think I'll try the usb version first...as this doesn't involve wasting media.

Thanks for all your suggestions so far everyone...I'll keep you posted.

If anyone has any other ideas then keep 'em coming! ;)

---

### Post by tedrogers on 2006-11-17
Sorry for the double post...but anyway...

So much for the USB idea...what a load of hassle that was...and all for nothing in the end because my T22 won't boot from USB. I checked first, and mistook the 'removable media' boot option for meaning USB - it actually means  the floppy/cd/dvd I have since discovered!

Anyway...at least I know a bit more about formatting those things now and permissions etc. Sorry...going off the point a bit.

The main thing is that the gparted live cd worked a treat and booted into X windows really easily.

I resized my /hda1 partition to just under half the size of the new one...so my new partition is slightly bigger, called /hda3.

Now...I can see the new partition in gparted and it is formatted to ext3, but it is not showing within edgy.

I have tried this code:

```
mount /dev/hda3
```

...but I get an error saying this:

```
mount: can't find /dev/hda3 in /etc/fstab or /etc/mtab
```

I have looked into /etc/fstab with gedit...but I don't really understand what I'm looking at. Here's the output:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2328e06a-12ee-40c5-b7d1-0c3925e8f928 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=03492d66-0863-4f13-8788-6c2e26a17253 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

What do I need to do now??

Thanks.

---

### Post by wieman01 on 2006-11-17
Please show us the result of:
> df -H

---

### Post by hal10000 on 2006-11-18
First of all you can test if your new hda3 partition is correctly setup.
Assuming that your filesystem is ext3:
```
sudo mkdir /mnt/hda3
mount -t ext3 /dev/hda3 /mnt/hda3
df -h

```
After the last command you should see your partition.
If that works, next is to add a suitable entry to your /etc/fstab file.
If you like to have it mounted on boot-time:
Choose your preferred editor (nano, gedit or any other)
```
sudo gedit /etc/fstab

At the end of the file type:

/dev/hda3 /mnt/hda3     ext3    defaults        0       2
```
You have to take care about the syntax (spaces or tabs between the columns)
Save your file and be happy. After your next reboot the partition is mounted on /mnt/hda3. You can only mount and unmount it as root (sudo umount /mnt/hda3 or sudo mount /mnt/hda3.
If you prefer to mount/umount is as normal user, make the following entry to /etc/fstab instead of the above:
```
/dev/hda3       /mnt/hda3     ext3    user,rw   0       2
```
Again, take care of the syntax, specially the part [COLOR="Red"]user,rw[/COLOR] must be written without a space before or after the comma.
The second method mounts your partition during boot-time, but gives you the option to unmount/remount it as normal user with write permission. As you mentioned, you want to use it for backup tasks; if you plan to make backups as normal user, then you might prefer the second method, otherwise the first entry is the better.

A third method is not to mount it at boot-time and only mount it on users request:
```
/dev/hda3       /mnt/hda3     ext3    noauto,user,rw   0       2
```
Here you have the option to mount the partition only if you want to perform a backup.
There are much more options you can do mounting/unmounting, see the manual pages:
```
man fstab

and

man mount

```

---

### Post by tedrogers on 2006-11-18
Hi Wieman01 and Hal10000,

Thanks for your help here....I managed to set it up properly allowing normal user access to my /hda3 partition.

Took me while to find it, because I thought it might appear in 'Computer' in the 'Places' menu, but then I remembered it would be in the /mnt folder. Sure enough, there it was.

The next problem I had was I didn't have to right permissions, so I ran:

```
sudo chmod -R 777 /mnt/hda3
```

...and then in order to put my 'lost+found' folder back to read + execute only I ran...

```
sudo chmod -R 755 /mnt/hda3/lost+found
```

I had to do this second step (I think) because the first command set all the folders on /hda3 to read, write and execute.

I don't know if this was crucial....but I did it anyway.

Now onto get partimage working...fingers crossed this time!

Thanks for all your help.

---

### Post by koenn on 2006-11-18
fun, isn't it  :-)

---

### Post by tedrogers on 2006-11-18
It's the *MOST* fun I've ever had with a computer...better than Solitaire even! :p :rolleyes: 

Still, it's a good way to learn!

---

