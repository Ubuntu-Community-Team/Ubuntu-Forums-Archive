---
title: "Need an app that can rip an ISO from a CD-ROM"
date: 2006-08-23
forum: General Help
---

### Post by mostwanted on 2006-08-23
How can this be done? I specifically need it to be an .iso-file, not an .img-file (these are not identical!).

I tried first copying to an .img using k3b and then using ccd2iso to convert it, but it aborts with this error:

```
Unrecognized sector mode (40) at sector 1!
```

---

### Post by peabody on 2006-08-23
Unfortunately I cannot recommend a gui program off-hand for such a purpose.  I can however, relate a bit of shell magic that accomplishes the same thing.

```
dd if=/dev/hdc of=my.iso
```

/dev/hdc must be the Unix device name of your cdrom drive.  In most typical setups this will /dev/hdc, but YMMV.  my.iso is the filename and can be changed to anything.  This may not be convenient but it has gotten the job done countless times for me.

---

### Post by mostwanted on 2006-08-23
> **peabody said:**
> Unfortunately I cannot recommend a gui program off-hand for such a purpose.  I can however, relate a bit of shell magic that accomplishes the same thing.

```
dd if=/dev/hdc of=my.iso
```

/dev/hdc must be the Unix device name of your cdrom drive.  In most typical setups this will /dev/hdc, but YMMV.  my.iso is the filename and can be changed to anything.  This may not be convenient but it has gotten the job done countless times for me.

Well, I'm no GUI sucker so if that accomplishes the task, I'll be very happy :)

Thanks, I shall try it out immediately.

---

### Post by DeShark on 2006-08-23
Er... Ubuntu has this built in. Right click the CD when it appears on your desktop. Select copy. Instead of selecting a drive choose "write to image". Then select somewhere to save it and voila!

---

### Post by mostwanted on 2006-08-23
The CD doesn't appear as a device (and thus doesn't display in Places or on the desktop either), but it mounts correctly to /media/cdrom which is kinda odd.

So neither solutions work as of now. I'm trying to copy the ISO off a PSX CD-ROM by the way, if that makes any difference.

---

### Post by Fully216 on 2006-08-23
Won't k9copy do the trick?

---

### Post by peabody on 2006-08-23
> **mostwanted said:**
> The CD doesn't appear as a device (and thus doesn't display in Places or on the desktop either), but it mounts correctly to /media/cdrom which is kinda odd.

So neither solutions work as of now. I'm trying to copy the ISO off a PSX CD-ROM by the way, if that makes any difference.

All CD-ROM devices have a device file, it may not be shown in the gui, but it is definitely there.  Try /dev/cdrom or /dev/dvd instead, that should be a symlink to your cd-rom or dvd respectively (it is on my system anyway).

To DeShark: Thanks!  I never knew that before!

---

### Post by DeShark on 2006-08-23
> **mostwanted said:**
> The CD doesn't appear as a device

Is it being mounted in /media/cdrom0? If not... that may be why it's not showing up as a device on the desktop. It's also symlinked to /media/cdrom and /cdrom. I don't know if that's what's meaning that it doesn't show up as a device or not, but it may be.

---

### Post by yopnono on 2006-08-23
Put your disk in the drive and then when it's mounted run this in the terminal. mount

Now you will see all mounted drives inc the optical

---

### Post by mostwanted on 2006-08-23
Ok, it's device /dev/hdb (I did try cdrom and dvd, which are both symlinks to the same place) and mounts to /media/cdrom0.

Here's the output of the dd:
> 
simon@SIMONGRAY:~/isos$ sudo dd if=/dev/hdb of=~/isos/mmv3.iso
dd: læser '/dev/hdb': Ind/ud-fejl
0+0 records in
0+0 records out
%<PRIuMAX> bytes ((null)) copied, 0,00317 seconds, 0,0 kB/s

It basically says, input/output error, nothing happened and I end up with an empty file.

---

### Post by yopnono on 2006-08-23
> **mostwanted said:**
> Ok, it's device /dev/hdb (I did try cdrom and dvd, which are both symlinks to the same place) and mounts to /media/cdrom0.

Here's the output of the dd:


It basically says, input/output error, nothing happened and I end up with an empty file.

Use: dd if=/dev/hdb of=/path_to_folder/name_of_iso.iso

---

### Post by peabody on 2006-08-23
This is very strange, could you try it with another cd?

---

### Post by mostwanted on 2006-08-24
> **yopnono said:**
> Use: dd if=/dev/hdb of=/path_to_folder/name_of_iso.iso

D'oh, forgot about the sudo. Unfortunately, that still solves nothing.

```
simon@SIMONGRAY:~$ sudo dd if=/dev/hdb of=/home/simon/isos/mmv3.iso
Password:
dd: læser '/dev/hdb': Ind/ud-fejl
0+0 records in
0+0 records out
%<PRIuMAX> bytes ((null)) copied, 3,93147 seconds, 0,0 kB/s
simon@SIMONGRAY:~$

```

```
simon@SIMONGRAY:~$ mount
/dev/hda3 on / type ext3 (rw,user_xattr,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-686/volatile type tmpfs (rw)
/dev/hda2 on /media/windows type fuse (rw,nosuid,nodev,noatime,allow_other)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
**/dev/hdb on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=simon)**
simon@SIMONGRAY:~$
```

---

### Post by yopnono on 2006-08-24
Are you using gnome or kde, if gnome try rightclick on the mounted drive (cd) and select copy disk. Then just select drive to copy to, save as file Image.
In KDE ??? maybe the same.

Anyhow try to download Nerolinux and copy the disk and save the img, this will save it as .NRG (not ISO) then use nrg2iso to convert it.

[http://www.nero.com/eng/nerolinux-prog.html](http://www.nero.com/eng/nerolinux-prog.html)

nrg2iso is in the synaptic.
[http://gregory.kokanosky.free.fr/v4/linux/nrg2iso.en.html](http://gregory.kokanosky.free.fr/v4/linux/nrg2iso.en.html)

---

### Post by peabody on 2006-08-25
> **mostwanted said:**
> D'oh, forgot about the sudo. Unfortunately, that still solves nothing.



If you're the default user setup from the initial Ubuntu install, you should probably have the permissions to read without sudo priviledges.  Did it ever work on another CD?

---

### Post by ridetheteapot on 2006-08-29
hey, i don't know to much about this, but i ran into a similar plroblem ripping a psx cd. dd if=/dev/hdd of=/storage/cd.iso always put out a io error. I read that the cd is multitrack and you need a toc or cue file along with the image (i dont really know the details of this but it seems to be true). So i used cdrdao: 

cdrdao read-cd --read-raw --datafile ./cd.bin --device /dev/hdd --driver generic-mmc-raw ./cd.toc

i guess you need to change the /dev/hdd to /dev/hdc
i think you said it must be iso. but i think, that it CANNOT be an iso.

ripping a multi track with dd OR cat or ubuntu's gui method (right click the mounted drive in COMPUTER) will not work

check this [http://linuxreviews.org/howtos/cdrecording/#toc11](http://linuxreviews.org/howtos/cdrecording/#toc11)

---

### Post by orb9220 on 2006-08-29
Am I missing something here in gnome I insert the cd or dvd and right click cd on desktop and select copy disc, select file image instead of default  then point it to a folder and walla I have an .iso file.

---

### Post by ridetheteapot on 2006-08-29
the gnome cd ripper uses (or functions the same as) dd. dd won't work so the gnome cd ripper won't work. that is the part i think you missed

dd will work on a normal cd like your ubuntu install disc (without sudo), but won't play nice with multitrack cds (cd-rom xa).
cdrdao will make an exact copy of your multitrack disc as a bin file and put the information about the placement of the tracks in the toc file.

if it must be an iso file in the end, you can use a program called bchunk that will help to do that.

---

### Post by orb9220 on 2006-08-29
AHhh! Like learning something new everyday Thanks!

---

### Post by msak007 on 2006-08-29
Have you tried **mkisofs** (it's in the repos)? If you're using KDE, there's a GUI called KISO that's a GUI for making ISO files out of CDs. Not sure if either will work for you but I would suggest mkisofs.

---

### Post by Mr. Magoo5 on 2007-03-20
> **peabody said:**
> Unfortunately I cannot recommend a gui program off-hand for such a purpose.  I can however, relate a bit of shell magic that accomplishes the same thing.

```
dd if=/dev/hdc of=my.iso
```

/dev/hdc must be the Unix device name of your cdrom drive.  In most typical setups this will /dev/hdc, but YMMV.  my.iso is the filename and can be changed to anything.  This may not be convenient but it has gotten the job done countless times for me.
Where does the iso go?

---

### Post by Mr. Magoo5 on 2007-03-20
nvm, i found it. duh.

---

