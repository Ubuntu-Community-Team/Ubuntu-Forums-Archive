---
title: "Usplash switches to text mode during boot after installing another OS"
date: 2008-05-01
forum: General Help
---

### Post by Perpetual on 2008-05-01
I have a problem when I install a new OS my Ubuntu usplash starts acting up.  During boot, my usplash image stops and boot switches to text mode saying "reading files needed to boot".  From there it is in text mode until gdm login starts.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004db38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          33      265041   83  /boot
/dev/sda2              34       19457   156023280    5  Extended
/dev/sda5              34         301     2152678+  82  Linux swap / Solaris
/dev/sda6           12907       19457    52620876   83  /media/MyData
/dev/sda7             302        1455     9269473+  83  Ubuntu
/dev/sda8            1456        2609     9269473+  83  Debian
/dev/sda9            2610        3763     9269473+  83  Fedora
/dev/sda10  *        3764        4917     9269473+  83  Foresight
```

Can anyone point me in the right direction to fix this?

Thanks,

Landon

---

### Post by -Zeus- on 2008-05-01
> **Perpetual said:**
> I have a problem when I install a new OS my Ubuntu usplash starts acting up.  During boot, my usplash image stops and boot switches to text mode saying "reading files needed to boot".  From there it is in text mode until gdm login starts.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004db38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          33      265041   83  Linux
/dev/sda2              34       19457   156023280    5  Extended
/dev/sda5              34         301     2152678+  82  Linux swap / Solaris
/dev/sda6           12907       19457    52620876   83  Linux
/dev/sda7             302        1455     9269473+  83  Ubuntu
/dev/sda8            1456        2609     9269473+  83  Debian
/dev/sda9            2610        3763     9269473+  83  Fedora
/dev/sda10  *        3764        4917     9269473+  83  Foresight
```

Can anyone point me in the right direction to fix this?

Thanks,

Landon

Wow that's quite a setup you have there!!!  I assume that the splash is still enabled in /boot/grub/menu.lst?

---

### Post by Perpetual on 2008-05-01
> **-Zeus- said:**
> Wow that's quite a setup you have there!!!  I assume that the splash is still enabled in /boot/grub/menu.lst?

Yes.  And the usplash image does start but stops about 10 seconds in.  The usplash image works during shut down.

---

### Post by warp99 on 2008-05-01
> **Perpetual said:**
> Yes.  And the usplash image does start but stops about 10 seconds in.  The usplash image works during shut down.

Try updating the initrd.img file:
```
sudo update-initramfs -u 
```
since the usplash file is located in initrd.img, which is extracted and run during boot. If that does not work you may need to change a few things in your fstab on checking the other partitions:

[http://ubuntuforums.org/showpost.php?p=4106720&postcount=1](http://ubuntuforums.org/showpost.php?p=4106720&postcount=1)

---

### Post by Perpetual on 2008-05-01
Thanks for the response warp99, unfortunately, no luck.  I will read the link you provided.

My fstab appears ok to me...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=efd83075-7bb0-40a5-a9e5-15aaf7f43485 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=825e8d0c-aec0-44c1-ad2c-5e5ab4b3067d /media/MyData   ext3    relatime        0       2
# /dev/sda5
UUID=15e21f39-579c-421b-87e5-e04bc98b9efd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by cubeist on 2008-05-01
what about a simple:
```
sudo dpkg-reconfigure usplash
```

---

### Post by warp99 on 2008-05-01
You could try creating a new initrd.img instead:
```
sudo update-initramfs -c -v -k $(uname -r)
```
just remember to backup the current file in your /boot directory **before** you try this at home.

---

### Post by Perpetual on 2008-05-01
Thanks cubeist and warp99.  Unfortunately no change.  Will keep tinkering.

---

### Post by cubeist on 2008-05-01
you could try completely removing usplash from within synaptic and then re-install...

the only downside to trying this is that it wants to remove ubuntu-desktop, but as far as I know, ubuntu-desktop is just a dummy package used to keep upgrades on track...BUT, ekiga and evolution are tied to ubuntu-desktop package and they will be removed too!

edit -
or just take the splash option out of your menu.lst
while I was playing around with bootchart this last weekend I discovered usplash added 4 seconds to my boot time, so I turned it off and I don't really miss it.  However, I will never succeed in getting my friends and family to switch to linux if they ever see the boot process... :)

---

### Post by warp99 on 2008-05-01
> **Perpetual said:**
> Thanks cubeist and warp99.  Unfortunately no change.  Will keep tinkering.

It's most likely a timeout issue with the wait state so usplash drops back to text mode. Do a search in the forums about extending the timeout period.

---

### Post by Perpetual on 2008-05-05
Argh.  Finally solved.

```
https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990
1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart
```

Thanks again all for trying to help me out.

Landon

---

### Post by Stunts on 2008-05-06
Hi!
I'm having the exact same problem over here!
I have followed the instructions shown on your post, but it din't do the trick for me. It is really annoying.
This started happening after I rearranged my partitions, so it even made full sense to me... Nevertheless, I've still got no usplash...
Any ideas, anyone?

Thanks in advance.

---

### Post by Perpetual on 2008-05-06
> **Stunts said:**
> Hi!
I'm having the exact same problem over here!
I have followed the instructions shown on your post, but it din't do the trick for me. It is really annoying.
This started happening after I rearranged my partitions, so it even made full sense to me... Nevertheless, I've still got no usplash...
Any ideas, anyone?

Thanks in advance.

Have you checked your fstab (/etc/fstab) against blkid to insure your UUID's are correct?  

Are you seeing the usplash at all?

Is 'quiet' enabled in /boot/grub/menu.lst?  Is the UUID in menu.lst correct?  Following is an example from my menu.lst.

```
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a3a1c312-11e0-4418-bcb7-cc74a32776f9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet
```

---

### Post by Stunts on 2008-05-07
Hi!I have taken all the steps you mentioned. My problem seemed exactly the same as yours. However it is fixed now. I installed startup manager, and dispite the fact that I didn't change anything, it seemed to solve my problem. Just like that. BTW, I used a simple procedure to check if my usplash was allready working. By typing ```
 sudo update-grub 
``` I could check if the usplash image was found.
Thanks anyway for your reply!

---

### Post by pablomme on 2008-06-06
The procedure above worked for me. I had repartitioned my hard drive and had already fixed the UUIDs in /etc/fstab, but didn't even think of checking the resume device (step 4), which indeed pointed to a non-existing device. Thanks!

---

### Post by andoni on 2008-08-13
> **warp99 said:**
> Try updating the initrd.img file:
```
sudo update-initramfs -u 
```
since the usplash file is located in initrd.img, which is extracted and run during boot. If that does not work you may need to change a few things in your fstab on checking the other partitions:

[http://ubuntuforums.org/showpost.php?p=4106720&postcount=1](http://ubuntuforums.org/showpost.php?p=4106720&postcount=1)

I know it's a bit late, however, I had the same problem(well, in my case, the usplash didn't appear at all) and your solution worked for me, thanks :).

Greetings from Spain.

---

### Post by arestivo on 2008-12-18
Perpetual's solution worked for me.

Thanks

---

### Post by WasMeHere on 2009-01-07
> **Perpetual said:**
> Argh.  Finally solved.

```
https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990
1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart
```

Thanks again all for trying to help me out.

Landon

I had the same problem and the same solution worked for me. The cause of the problem was that I changed the UUID of swap, when adding a new OS (64-bit ubuntu). I changed the fstab entry by myself, but could not find the resume entry.
Thank you, Perpetual, for this useful thread!
Olle

---

### Post by Perpetual on 2009-01-07
Olle Wiklund, you are welcome!

---

### Post by saratchandra on 2009-01-07
I don't have a swap entry at all in my fstab.

EDIT: Found it

EDIT 2: This is the content of my resume file. What should I edit?

> RESUME=/dev/sda4

---

