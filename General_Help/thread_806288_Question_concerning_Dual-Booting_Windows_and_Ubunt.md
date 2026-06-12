---
title: "Question concerning Dual-Booting Windows and Ubuntu 7.10"
date: 2008-05-24
forum: General Help
---

### Post by randell6564 on 2008-05-24
I am getting ready once again to re-install Windows, along with Ubuntu on my box.  I have a 120gig ID master, and a 20gig ID slave. In the past, I have always housed Windows on my 120Gig drive, and Ubuntu on my 20Gig. This time around, I want to give my 120gig to Ubuntu, and put ol' Bill Gates in the backroom!  But I want to accomplish this without changing my current drive configuration. (120Gig Master/20Gig Slave)

I am about to wipe my Slave drive first, and install Windows. THEN, I want to install Ubuntu onto my Master.  I'm hoping that Ubuntu will install Grub like it always has before with the dual-boot options.

My question is.,Do I HAVE to install to my Master drive first, or can I install to my Slave, then install to my Master.

(I'm simply trying to flip things around by putting Windows on my Slave,and Ubuntu on my Master)

---

### Post by ibuclaw on 2008-05-24
Ubuntu installs itself seamlessly to any partition/harddrive, so you should have no worries there.

As for Windows, you may want to disable the current Master Drive in BIOS first (leaving only the 20GB one enabled).
As I think that Windows always tries to install on the Primary Master Disk by default.

Regards
Iain

---

### Post by randell6564 on 2008-05-24
> As for Windows, you may want to disable the current Master Drive in BIOS first (leaving only the 20GB one enabled).
As I think that Windows always tries to install on the Primary Master Disk by default.

Regards
Iain
So, what you are saying is..go into bios, disable the master then install Windows to Slave. THEN enable master, and install Ubuntu?
Thanks!

---

### Post by randell6564 on 2008-05-24
Worked just fine without disabling my master. (Just finished installing Windows to my Slave)

I am now booted to the Ubuntu 7.10 Live CD, and about to install it to my Master.

---

### Post by strabes on 2008-05-25
Good luck. Let us know if ubuntu correctly writes your MBR and you can successfully access both windows and ubuntu.

---

### Post by randell6564 on 2008-05-25
> **strabes said:**
> Good luck. Let us know if ubuntu correctly writes your MBR and you can successfully access both windows and ubuntu.
Installed perfectly, but failed to get my dualboot option. Time to break out my SuperGrub disk! :)

---

### Post by bodhi.zazen on 2008-05-25
windows does not like being on a slave drive.

You need to "map" or rather re-map your dirves in youw windows boot stanza

```
Windows
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloder +1
boot
```

---

### Post by randell6564 on 2008-05-25
> **bodhi.zazen said:**
> windows does not like being on a slave drive.

You need to "map" or rather re-map your dirves in youw windows boot stanza

```
Windows
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloder +1
boot
```
Thanks, but I'm not sure that I understand.  Is this something that I can do on the Linux side ,via a terminal, or do I need to do what you suggest in a Windows command line?
Here are the results of:```
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloder +1 boot
```
> bigboss@Bigboss:~$ sudo rootnoverify (hd1,0)
bash: syntax error near unexpected token `('
bigboss@Bigboss:~$ makeactive
bash: makeactive: command not found
bigboss@Bigboss:~$ map (hd0) (hd1)
bash: syntax error near unexpected token `hd0'
bigboss@Bigboss:~$ map (hd1) (hd0)
bash: syntax error near unexpected token `hd1'
bigboss@Bigboss:~$ chainloder +1 boot

---

### Post by Warmask on 2008-05-25
> **randell6564 said:**
> Thanks, but I'm not sure that I understand.  Is this something that I can do on the Linux side ,via a terminal, or do I need to do what you suggest in a Windows command line?

I think he means you need to edit the /boot/grub/menu.lst to look similar to that submitted code.

If you want only 20gB for Windows, you could put it on ur master drive, but only give it 20gB partition. Then give ubuntu the remaining 100gB and use the 20gB slave as a shared drive formated as NTFS or FAT32, so that both ubuntu and windows can use it.

---

### Post by bodhi.zazen on 2008-05-26
Yes, sorry ...

Boot Ubuntu and edit /boot/grub/menu.lst

```
gksu gedit /boot/grub/menu.lst
```

Add the information re mapping to your windows stanza, or write one if necessary.

---

### Post by randell6564 on 2008-05-26
Strange that Windows does not even show up in my /boot/grub/menu.lst, yet I can access my windows drive/files from Ubuntu. Was not sure where to enter the maping info, so I placed it at the bottom of my menu.lst:
> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=558e6dec-88fe-42ad-8959-638453e8c803 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=558e6dec-88fe-42ad-8959-638453e8c803 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[B]Windows
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloder +1
boot[/B]
At any rate, it did not work.  Maybe I placed it incorrectly?
Thanks!

---

### Post by randell6564 on 2008-05-26
I searched around a bit, and found this:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1
Windows now appears in the grub options at boot up, but I get this error:
> 
NTLDR is missing


---

### Post by randell6564 on 2008-05-26
"bump"

---

### Post by adrian15 on 2008-05-27
> **randell6564 said:**
> I searched around a bit, and found this:

Windows now appears in the grub options at boot up, but I get this error:

Can you please post: sfdisk -lu, I would bet you have a recovery partition and you need **rootnoverify (hd1,1)**.

Please check:
[How to boot Windows from my second hard disk without problems Howto](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_From_A_Second_Hard_Disk#Grub_solution__.28Windows_installation_with_a_recovery_partition.29)

adrian15

---

### Post by bodhi.zazen on 2008-05-28
I do not know if this link will help :

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by randell6564 on 2008-05-28
> **adrian15 said:**
> Can you please post: sfdisk -lu, I would bet you have a recovery partition and you need **rootnoverify (hd1,1)**.

Please check:
[How to boot Windows from my second hard disk without problems Howto](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_From_A_Second_Hard_Disk#Grub_solution__.28Windows_installation_with_a_recovery_partition.29)

adrian15
bigboss@Bigboss:~$ sudo fdisk -lu
[sudo] password for bigboss:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b6f3b6e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   234067049   117033493+  83  Linux
/dev/hda2       234067050   240107489     3020220    5  Extended
/dev/hda5       234067113   240107489     3020188+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ba93ba8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    39857264    19928601    7  HPFS/NTFS
bigboss@Bigboss:~$

---

### Post by randell6564 on 2008-05-28
> **bodhi.zazen said:**
> I do not know if this link will help :

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
Thanks bodhi.zazen, I will look into it.

---

### Post by Nameless Neko on 2008-05-28
You might have to reinstall Windows again, but physically unplug the drive you installed Ubuntu to until you're done installing (or disable it in the bios if you have an option to, but I'd rather not take any chances).  I think what happened is Windows did it's usual trick of spewing files on both drives even though that's not what you wanted, so ntldr ended up on the 120 GB drive, and was subsequently wiped out by the Ubuntu install.

I've learned the hard way about Windoze installations, and always unplug any drives I don't want touched when I have to reinstall now.  I've ended up wasting so many hours of my life because XP decided to make a completely unrelated drive house system files that it's not even remotely funny.

---

### Post by adrian15 on 2008-05-28
> **randell6564 said:**
> 
Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ba93ba8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    39857264    19928601    7  HPFS/NTFS
bigboss@Bigboss:~$

If the map trick has not worked this means that your Windows is installed ok (in the second disk... which was before the first hard disk) you need to read that ntldr is missing howto and probably you will need to edit your boot.ini to reflect your "new" Windows partition.

adrian15

---

### Post by randell6564 on 2008-05-28
> **adrian15 said:**
> If the map trick has not worked this means that your Windows is installed ok (in the second disk... which was before the first hard disk) you need to read that ntldr is missing howto and probably you will need to edit your boot.ini to reflect your "new" Windows partition.

adrian15
Thank you adrian15.
My second disk was never the first disk. It has always been the slave drive. 
Windows has always been on my 120g primary IDE, and Ubuntu took the backseat (being my 20g secondary IDE). I wanted to finally switch things around so that Ubuntu could have 120g. What I did was wipe both drives, install Windows first to second/slave drive, then installed Ubuntu to primary hoping that grub would stick itself in the right place for a dual boot option.  But like
Nameless Neko said, Windows not liking to be in the backseat, it "spewed" it's files all over the place, including onto the other drive!

This is not a huge problem for me. I can very easily crack open my box, adjust the straps, and jumper settings on the drives, reinstall Windows on the new master (20g IDE.) Of course, I will then need to use my supergrub disk again to rewrite the MBR because Windows will screw that up and not give me access to Ubuntu! 

I would not have attempted to install this way if I had known that Windows does not like to ride in the backseat. Guess I should have done my homework first.
Thanks so much to all of you! Don't change the channel, because I just might be back with some more questions if things don't go as planned. :)

---

### Post by randell6564 on 2008-06-01
Well now that I have my dual-boot option, Something is wrong again.  When I boot to Ubuntu, it loads just fine, but then I get a Black screen. (No Desktop) Any ideas?

---

