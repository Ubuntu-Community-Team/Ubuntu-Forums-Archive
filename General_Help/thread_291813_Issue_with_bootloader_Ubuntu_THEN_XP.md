---
title: "Issue with bootloader Ubuntu THEN XP"
date: 2006-11-03
forum: General Help
---

### Post by prophet11 on 2006-11-03
Hey fellas i did the exact same this his person did

[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

then after fallowing that suggestion i got this error it says HAL.DLL is missing or currpt.. 

should i reinstall windows or do i have to do something else?

---

### Post by Joe_CoT on 2006-11-03
According to [this](http://gentoo-wiki.com/Talk:HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why), it might be that the Windows partition is not set as active
Ripping right from that how-to, and assuming you've installed onto your first hard drive.
```

# sudo fdisk /dev/hdb
# Command (m for help):   <enter ‘a’>
# Partition number (1-4): <enter /boot partition number> (probably 1)
# Command (m for help):   <enter ‘p’ and check your /boot partition has an asterisk next to it.
# Command (m for help): w (Save the new schema)

```

now run
```
sudo update-grub
```

And try again.

---

### Post by prophet11 on 2006-11-03
> **Joe_CoT said:**
> According to [this](http://gentoo-wiki.com/Talk:HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why), it might be that the Windows partition is not set as active
Ripping right from that how-to, and assuming you've installed onto your first hard drive.
```

# sudo fdisk /dev/hdb
# Command (m for help):   <enter &#8216;a&#8217;>
# Partition number (1-4): <enter /boot partition number> (probably 1)
# Command (m for help):   <enter &#8216;p&#8217; and check your /boot partition has an asterisk next to it.
# Command (m for help): w (Save the new schema)

```

now run
```
sudo update-grub
```

And try again.

installed what on my main drive? Ubuntu or Windows..

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw)
/dev/hdb1 on /mnt/windows type ntfs (rw,noexec,nosuid,nodev,umask=0000,dmask=0000,uid=0002,gid=100)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdd on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=prophet)

hda1 is my ubuntu drive

hdb1 is my 2nd HD NTFS music and other stuff on there

hdc1 is the HD i installed XP on..

im not sure what order they are on the controller.. 

should i fallow the above if this is my setup?

---

### Post by Joe_CoT on 2006-11-03
In that case, it would be:

```
sudo fdisk /dev/hdb
```

type p to list partitions. the first partition should have an asterisk next to it, and no others should.

If they do, or the first does not, type a <enter>, the partition number <enter> and then p to list partitions. Type w <enter> to save when done.

Since windows is on the second hard drive, you need to map it to the first drive in order for it to load.

```
sudo nano -w /boot/grub/menu.lst
```

go to the windows option. you need to make it look like this:

```

title = Windows
root = (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

```

The key is remapping the drives so that Windows is virtually the first drive. Then

```
sudo update-grub
```
To save.

---

### Post by prophet11 on 2006-11-04
actually hdb just has music and such, 

hc1 is the one with XP..

ive done all that..

when i got into grub and select windows to boot it says that there is a missing hal.dll and just sits there

---

### Post by confused57 on 2006-11-04
You could try an entry similar to this:

```
title      Windows
root      (hd2,0)
map      (hd0) (hd2)
map      (hd2) (hd0)
makeactive
chainloader +1
```

---

