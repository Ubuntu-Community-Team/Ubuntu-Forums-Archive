---
title: "Gparted"
date: 2007-03-10
forum: General Help
---

### Post by RDUBBALO on 2007-03-10
I have windows installed on my second partition and somehow I have a file missing to start it. I just want to know how I can get into Gparted and and partition it so as I can use that space for storage with Ubuntu. I want the whole hard drive for it. I dont want the windows at all. Also if anyone knows how I can get internet explore to work on Linux. I have this website for school I need to do algebra homework and it say must use IE and I only have firefox on here. thanks for the help.

---

### Post by taurus on 2007-03-10
Yes, you can use gparted from Ubuntu to format that space into ext3 and mount it so you can use it.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by RDUBBALO on 2007-03-10
Thank you so much one more question how do I know what the partition is called and the filesystem

---

### Post by RDUBBALO on 2007-03-10
ok nevermind I got gpated up and now i need to deleted that ntfs partition of windows, but it cant be unmounted. Im not sure what to do here.

---

### Post by taurus on 2007-03-10
Close gparted and post the outputs of these two commands here.

```
sudo fdisk -l
df -h
```

---

### Post by JohnPhys on 2007-03-10
Depending on what partition and drive the ntfs is on, you can just issue an umount command in the terminal.

To find out what drive/partition your ntfs is on, you can use gparted, or just type "mount" from the terminal, here's my output from "mount",

```
:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-k7/volatile type tmpfs (rw)
/dev/hdd1 on /media/Share type vfat (rw,noexec,nosuid,nodev,uid=1000,gid=1000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/WinXP type ntfs (rw,noexec,nosuid,nodev,uid=1000,gid=1000,user=XXXXXX)
:~$

```

so my ntfs partition is on /dev/sda1.  To unmount, I would just type

```
sudo umount /dev/sda1
```

---

### Post by RDUBBALO on 2007-03-10
> **JohnPhys said:**
> Depending on what partition and drive the ntfs is on, you can just issue an umount command in the terminal.

To find out what drive/partition your ntfs is on, you can use gparted, or just type "mount" from the terminal, here's my output from "mount",

```
:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-k7/volatile type tmpfs (rw)
/dev/hdd1 on /media/Share type vfat (rw,noexec,nosuid,nodev,uid=1000,gid=1000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/WinXP type ntfs (rw,noexec,nosuid,nodev,uid=1000,gid=1000,user=XXXXXX)
:~$

```

so my ntfs partition is on /dev/sda1.  To unmount, I would just type

```
sudo umount /dev/sda1
```

Yes that last line of code was it. I used it but i did not put the space after unmount. thank you so much. Alright now i got everything working just right. thanks again

---

### Post by enopepsoo on 2007-03-10
for your ie issue, you could change your user agent and see if the site works.  There is a firefox extension that will do this for you.

if that does not work, I would suggest following a tutorial on installing ie in wine, or just downloading the multibrowser appliance and installing vmware player or vmware server.  You can install vmware player with automatix.  The server install is not much harder.  To find the appliance, just do a google search, it should come right up.

---

### Post by RDUBBALO on 2007-03-11
ok now I dont know iof this is a problem but before I had an icon that said sda2 on my desktop and now it is gone after i formated that partition I dont see where the storage partition is that i created eathir and i mounted it and had it named storege. it show it in gparted but i cant find it from the desktop. any ideas

---

### Post by RDUBBALO on 2007-03-11
also I am now showing an icon that says floppy and i dont have a floppy and I cant remove this.

---

### Post by taurus on 2007-03-11
What does your /etc/fstab look like?  Did you try to mount your /dev/sda2 through /etc/fstab?

```
cat /etc/fstab
```

---

### Post by RDUBBALO on 2007-03-11
# /dev/sda2
UUID=c6d7475a-28aa-4fe3-9e9f-ac7eb12a725b /               ext3    defaults,errors=remount-ro 0       1

---

### Post by taurus on 2007-03-11
> **RDUBBALO said:**
> # /dev/sda2
UUID=c6d7475a-28aa-4fe3-9e9f-ac7eb12a725b /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2 is your root!

Which partition did you just convert from ntfs to ext3?  What's the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by RDUBBALO on 2007-03-11
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           6        8988    72155947+  83  Linux
/dev/sda2            8989       19452    84052080   83  Linux
/dev/sda3               1           5       40131   82  Linux swap / Solaris

---

### Post by RDUBBALO on 2007-03-11
i converted the ntfs to ext3 i alredy had the root and swap made I just got rif of the one i had windows on

---

### Post by taurus on 2007-03-11
Which partition did you do the conversion?  Was it /dev/sda1 or /dev/sda2?  What is the complete output of this command?

```
cat /etc/fstab
```
Otherwise, post this command and I will figure it out myself.

```
df -h
```

---

### Post by RDUBBALO on 2007-03-11
according to mtab, /dev/sda1 is already mounted on /storage
could it be that sda1 is mounted on sda2 because that sda2 is what i named storage

---

### Post by RDUBBALO on 2007-03-11
/dev/sda1 /storage ext3 defaults 0 0

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c6d7475a-28aa-4fe3-9e9f-ac7eb12a725b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A49414B894148EC4 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=7d11b120-2638-4dac-b4f1-d0b823e6de30 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by RDUBBALO on 2007-03-11
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
mulrooneymark@mulrooneymark:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              79G  8.4G   67G  12% /
varrun                502M   80K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  168K  9.9M   2% /proc/bus/usb
udev                   10M  168K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   18M  484M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1              68G  181M   65G   1% /storage

---

### Post by taurus on 2007-03-11
Since you mount /dev/sda1 on /storage, you will not see an icon on your desktop.  If you want to see a little icon on your desktop for /dev/sda1, then you need to mount it to /media.  Remove this line from your /etc/fstab

```
/dev/sda1 /storage ext3 defaults 0 0
```
and add this one to the end of it.  (It's better to mount root, /, first and then everything else after.)

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
Then, create a new mount point for it.

```
sudo mkdir /media/sda1
```
Reboot and you should see an icon for /media/sda1 on your desktop now.

---

### Post by RDUBBALO on 2007-03-11
how do i get into that to change the line

---

### Post by taurus on 2007-03-11
```
gksudo gedit /etc/fstab
```

---

### Post by RDUBBALO on 2007-03-11
I dont know what happened i tried it and it said already had that directory so i changed the name and now I dont have any sounf from my sound card. I dont know what happeneed.

---

### Post by RDUBBALO on 2007-03-11
ok i got the sound back I dont know what happened my sound card wasnt selected anymore. Basically I just would like to get my  whole hard drive in two partitions and be able to see where i am saving things. i dont know if i have full use of it all. seems like everything is being saved on the root partition and I dont know if i can use the second one i made. maybe i should just start that one over?

---

### Post by RDUBBALO on 2007-03-11
ok now it is unmounted and not set to anything so I guess we can start fresh with it.

---

### Post by taurus on 2007-03-11
I need to see your /etc/fstab again/

```
cat /etc/fstab
```
Also, post the outputs of these two commands from a terminl as well.

```
id 
ls -la /media
```

---

### Post by RDUBBALO on 2007-03-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c6d7475a-28aa-4fe3-9e9f-ac7eb12a725b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1     /media/sda1     ext3    defaults        0       0
UUID=A49414B894148EC4 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=7d11b120-2638-4dac-b4f1-d0b823e6de30 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


uid=1000(mulrooneymark) gid=1000(mulrooneymark) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(mulrooneymark)

total 18
drwxr-xr-x  5 root          root          4096 2007-03-10 18:59 .
drwxr-xr-x 22 root          root          4096 2007-03-11 21:08 ..
lrwxrwxrwx  1 root          root             6 2005-10-07 20:12 cdrom -> cdrom0
dr-xr-xr-x  1 root          root          2048 2005-06-18 11:17 cdrom0
lrwxrwxrwx  1 root          root             7 2005-10-07 20:12 floppy -> floppy0
drwxr-xr-x  2 root          root          4096 2005-10-07 20:12 floppy0
drwxr-xr-x  3 mulrooneymark mulrooneymark 4096 2007-03-11 21:19 sda1

---

### Post by RDUBBALO on 2007-03-11
i basically just want it to have the two partitions and show it so i can save there. i see the files but they all say they have the same amount of storage and not what is the actual partition.

---

### Post by taurus on 2007-03-11
Is your /dev/sda1 a ntfs or ext3?  You told me that it is ext3 but you have an entry in /etc/fstab as ntfs?  I am having a headache trying to figure out what is your filesystem for /dev/sda1.  Can you post this output again?

```
sudo fdisk -l
```

---

### Post by RDUBBALO on 2007-03-11
Im positive I formatted it as ext3 but your right i see the ntfs. i also edited that line for the sda1 i added the media/sda1  ext3 defaults 0 0 becaus eit said in that link you sent me here is the outputs from the fdisk -1 
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               6        8988    72155947+  83  Linux
/dev/sda2   *        8989       19452    84052080   83  Linux
/dev/sda3               1           5       40131   82  Linux swap / Solaris

---

### Post by taurus on 2007-03-11
Can you edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and change this line

```
UUID=A49414B894148EC4 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
back to 

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
Save it and reboot.

---

### Post by RDUBBALO on 2007-03-11
alright thanks that was it. i see it now that line with the ntfs. You really helped me alot. Here is a question what would my sda2 be called filesytem? anyway the nembers match up now the amount of disk space. thanks again. i learned alot here with the code and all.

---

