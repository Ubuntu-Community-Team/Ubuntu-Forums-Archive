---
title: "Bad /etc/fstab even after formatting the my pc"
date: 2015-10-04
forum: General Help
---

### Post by douglas-almeida12 on 2015-10-04
Hey there.

Besides my Linux partition, I have two others in my notebook, one for all my files and other for Windows, both on auto mounting in specific folders that I created. Other day when I was using ubuntu 14.04 it crashed completely, so I forced the computer to reboot. When it initialized again I got the following error:


```
Error mounting system-managed device /dev/sda6: Command-line `mount "/media/doug/Files"' exited with non-zero exit status 1: 
Error mounting system-managed device /dev/sda4: Command-line `mount "/media/doug/Windows"' exited with non-zero exit status 1:
[mntent]: line 18 in /etc/fstab is bad
[mntent]: line 21 in /etc/fstab is bad
mount: can't find /media/doug/Files in /etc/fstab or /etc/mtab 
mount: can't find /media/doug/Windows in /etc/fstab or /etc/mtab
```

That's my /etc/fstab

```
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=3b14d64f-251b-4615-90b6-cc15d3ba224d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=285A-D2BA  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda8 during installation
UUID=32717d3c-b15c-4a34-96fe-2fbce1b08484 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=802d5f81-261e-44d2-a1c7-8dac3ea9d3f2 none            swap    sw              0       0


#File Partition
#/dev/sda6   /media/doug/Files              nfts    defaults, auto  0      0


#Windows Partition
#/dev/sda4  /media/doug/Windows                  nfts    defaults, auto  0      0

```

However, if I comment those last lines on fstab and do the commands bellow it mounts normally.
[COLOR=#333333][FONT=Helvetica Neue]mount -t ntfs-3g /dev/sda6 /media/doug/Files

[/FONT][/COLOR]Tired of digging on the internet for a solution and not find it, I reinstalled the whole Operating System, and believe or not, the problem continues. 
Do you guys have any idea of what is going on? I don't know what else to try.

Thanks.

---

### Post by sisco311 on 2015-10-04
The filesystem type should be **ntfs** not **nfts**.

And you should use UUIDs instead of device names: [uhelp]community/UsingUUID[/uhelp]

---

### Post by steeldriver on 2015-10-04
... also the list of mount options mustn't contain spaces i.e.

```

/dev/sda6   /media/doug/Files              nfts    **defaults[COLOR=#ff0000], [/COLOR]auto**  0      0

```

needs to be 
```

/dev/sda6   /media/doug/Files              ntfs    **defaults,auto**  0      0

```

(However AFAIK 'auto' is the default, so you can simply omit it.)

---

### Post by oldfred on 2015-10-04
Also good to add windows_names

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

   For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by douglas-almeida12 on 2015-10-04
Thank you, guys. I don't know why I put **nfts** even though I know it's **ntfs**. I didn't pay attention to that when I was editing the file, so thanks for correcting that. However, I think my real problem was the space in **defaults, auto. **I had no idea this could be a problem and I didn't find any citation to this in all the forums I've read. Well, can't deny I feel a little embarrassed. Again, thank you all.

---

