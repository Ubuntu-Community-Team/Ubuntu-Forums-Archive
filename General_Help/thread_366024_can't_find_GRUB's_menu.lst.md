---
title: "can't find GRUB's menu.lst"
date: 2007-02-20
forum: General Help
---

### Post by DMAthlon on 2007-02-20
i just reinstalled grub onto my machine after installing vista. i added a 50mb partition for /boot and installed it to that but the pro0blem is that i can't locate the menu.lst file anywhere! any help please?

---

### Post by taurus on 2007-02-20
You don't see it in /boot/grub/menu.lst!  What's the output of this command from a terminal then?

```
df -h
```

---

### Post by DMAthlon on 2007-02-20
```
collin@collin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              17G   11G  5.8G  65% /
varrun               1014M   80K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-11-386/volatile
/dev/sda9              45M  9.4M   33M  23% /boot
/dev/sda1              25G   19G  6.3G  75% /media/sda1
/dev/sda5              49G   17G   33G  34% /media/sda5
/dev/sda6             142G   75G   68G  53% /media/sda6
collin@collin-desktop:~$ 

```

---

### Post by taurus on 2007-02-20
What about

```
ls -la /boot
```

---

### Post by Ramses de Norre on 2007-02-20
This should reveal it's location:
```
sudo updatedb && locate menu.lst
```

---

### Post by DMAthlon on 2007-02-20
> **taurus said:**
> What about

```
ls -la /boot
```

```
collin@collin-desktop:~$ ls -la /boot
total 9415
drwxr-xr-x  6 root root    1024 2007-02-20 09:42 .
drwxr-xr-x 21 root root    4096 2007-02-20 02:11 ..
-rw-r--r--  1 root root  266619 2006-05-23 11:56 abi-2.6.15-23-386
-rw-r--r--  1 root root   69878 2006-05-23 08:47 config-2.6.15-23-386
drwxr-xr-x  2 root root    1024 2007-02-20 09:26 dev
drwxr-xr-x  2 root root    1024 2007-02-20 09:45 grub
-rw-r--r--  1 root root 7002131 2006-05-30 20:07 initrd.img-2.6.15-23-386
drwxr-xr-x  2 root root   12288 2007-02-20 02:10 lost+found
-rw-r--r--  1 root root   94760 2005-10-25 05:32 memtest86+.bin
drwxr-xr-x  2 root root    1024 2007-02-20 09:25 proc
-rw-r--r--  1 root root  725460 2006-05-23 11:56 System.map-2.6.15-23-386
-rw-r--r--  1 root root 1414477 2006-05-23 11:56 vmlinuz-2.6.15-23-386
collin@collin-desktop:~$ 

```
looks kinda like grub. that's all i can pick apart there other than the date & time.
what now?
thanks.

------
> **Ramses de Norre said:**
> This should reveal it's location:
```
sudo updatedb && locate menu.lst
```

```
collin@collin-desktop:~$ sudo updatedb && locate menu.lst
Password:
/usr/share/doc/grub/examples/menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
/usr/share/gnome/help/desktopguide/sample/menu.lst_addwindowsentrygrubmenu
/usr/share/gnome/help/desktopguide/sample/menu.lst_changegrubpasswordforgotten
/usr/share/gnome/help/desktopguide/sample/menu.lst_displaysplashimagegrub
collin@collin-desktop:~$ 

```

thanks for tryin but those are all samples and examples. I'm looked at em all.

](*,) ](*,) ](*,) ](*,) I just got done installing all of my programs I'll ever need on Vista, last night, and I can't get into it. ](*,) ](*,) ](*,) ](*,)

---

### Post by taurus on 2007-02-20
```
ls -la /boot/grub
```

---

### Post by DMAthlon on 2007-02-20
> **taurus said:**
> ```
ls -la /boot/grub
```
```
collin@collin-desktop:~$ ls -la /boot/grub
total 160
drwxr-xr-x 2 root root   1024 2007-02-20 09:45 .
drwxr-xr-x 6 root root   1024 2007-02-20 09:42 ..
-rw-r--r-- 1 root root    197 2007-02-20 09:45 default
-rw-r--r-- 1 root root     30 2007-02-20 09:42 device.map
-rw-r--r-- 1 root root   7508 2007-02-20 09:45 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2007-02-20 09:45 fat_stage1_5
-rw-r--r-- 1 root root     16 2007-02-20 09:45 installed-version
-rw-r--r-- 1 root root   8128 2007-02-20 09:45 jfs_stage1_5
-rw-r--r-- 1 root root   6804 2007-02-20 09:45 minix_stage1_5
-rw-r--r-- 1 root root   9076 2007-02-20 09:45 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-02-20 09:45 stage1
-rw-r--r-- 1 root root 105652 2007-02-20 09:45 stage2
-rw-r--r-- 1 root root   8764 2007-02-20 09:45 xfs_stage1_5
collin@collin-desktop:~$ 

```

tis no where to be found - looked for it for hours. i think i need to properly mount sda9 (/boot) so i can explore everything. where else could the file be hidden.

---

### Post by taurus on 2007-02-20
Well, if you just created a /boot partition after you already installed Ubuntu, then perhaps you have mount it over the original /boot.  Therefore, try boot with the LiveCD and see if there is  /boot/grub/menu.lst on the / partition, NOT on /boot partition.

Otherwise, copy the sample menu.lst to /boot/grub and modify it for your machine.

```
sudo cp /usr/share/doc/grub/examples/menu.lst  /boot/grub/menu.lst
gksudo /boot/grub/menu.lst
```

---

### Post by DMAthlon on 2007-02-20
i was thinking about that but there isn't enough to build a menu.lst from it.

---

### Post by taurus on 2007-02-20
See if the original menu.lst is still there.  Boot with the LiveCD and mount your / to somewhere.  Then, look in /boot/grub/menu.lst to see if there is one.  Again, don't mount /boot from the LiveCD.

---

### Post by DMAthlon on 2007-02-20
how do i mount / in live cd?

---

### Post by taurus on 2007-02-20
Do you know what partition / is located?  For now, I will assume /dev/hda1.  From the LiveCD, do

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
ls -la /mnt/ubuntu/boot/grub
```

---

### Post by DMAthlon on 2007-02-20
Wow, thanks a lot - i'm amazed that actually got fixed properly. if you want to take on a real challenge - this is what else i'm up against on this machine right now:

[http://forums.bit-tech.net/showthread.php?t=129676](http://forums.bit-tech.net/showthread.php?t=129676)
thats other vista related stuff to my mishaps of last night.

---

### Post by taurus on 2007-02-20
Sorry but I don't use Vista and don't really care much about Vista.  And if I have too much money, I would rather donate it the homeless shelter here than buying Vista.

---

### Post by DMAthlon on 2007-02-20
yeah well i didnt even waste my money on it - my uncle gave it to me. 

microsoft is getting more and more evil - Vista plain looks evil. lol.

---

