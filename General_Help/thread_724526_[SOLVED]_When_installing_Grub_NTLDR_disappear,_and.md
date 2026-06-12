---
title: "[SOLVED] When installing Grub NTLDR disappear, and viceversa"
date: 2008-03-14
forum: General Help
---

### Post by Tasc0 on 2008-03-14
I know this issue has been poted several times, I've searched to get some help but I didn't find any.

The "solution" I've found is removing Ubuntu, or removing Windows or restoring NTLDR back.

I'd like to have Ubuntu and Windows working properly. The thing is that if I restore Grub I only can use Ubuntu, and if I restore NTLDR the Grub screen disappear, so I only can use Windows.

How can I fix this? Any reply would be appreciated it. I have Ubuntu 7.10 and Windows XP SP:2.

Thanks in advance.

[SIZE="5"][COLOR="Red"]_**Solved:**_[/COLOR][/SIZE]
**Solution can be found on the post # 21, [here]("http://ubuntuforums.org/showpost.php?p=4527975&postcount=21").**

---

### Post by Tasc0 on 2008-03-14
No suggestions? I'm stucked here.

---

### Post by confused57 on 2008-03-14
When you say "restore NTLDR", do you mean issuing FIXMBR from an XP install cd?
I assume you're reinstalling grub's IPL to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Maybe someone can help if you post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

and your menu.lst:
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list

Are you getting a "NTLDR missing" error message when you try to boot Windows from grub?  Any other error messages, etc would be helpful...

---

### Post by Sef on 2008-03-14
> I'd like to have Ubuntu and Windows working properly. The thing is that if I restore Grub I only can use Ubuntu, and if I restore NTLDR the Grub screen disappear, so I only can use Windows.

The NTLDR will only recognize Windows OSes.   GRUB will recognize both GNU/Linix and Windows.  To get GRUB to recognize Windows, check the Illustrated Dual Boot section on '[How to Boot Windows using GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way")'.

---

### Post by ATIuser on 2008-03-14
The way I have my dual boot setup is that I had windows installed first, then I installed Ubuntu and let Grub install with the default options. never had an issue with it.

---

### Post by Tasc0 on 2008-03-15
Thanks for everyone's replies.

Yeah, WIndows was installed first and then I installed Ubuntu. Afther the instal was done, I restarted the computer and I couldn't see the Grub screen, so I "re-installed" it from the Live CD using this:
```

grub> find /boot/grub/stage1

grub> root (hd1,1) 

grub> setup (hd1)

grub> quit 

```

With this I installed Grub in the MBR so the NTLDR was gone, Grub detected the Windows OS, but when I tried to execute it I get the message "NTLDR missing". So a couple of days later I decided to restore the MBR using the XP booting CD wiht the FIXMBR command, thus I can't see the Grub screen.

Now (again) I restored Grub with the commands  above and I get the same error, And a new problem: I can't see the NTFS partitions. I'm in Linux right now :S

This is my menu.lst:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=172acf91-38c6-4a48-ad5a-701da06df9f8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=172acf91-38c6-4a48-ad5a-701da06df9f8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by Tasc0 on 2008-03-15
I think my problem is that I installed Grub in the MBR and by doing that, NTLDR was deleted. So I need to restore NTLDR and install Grub in some place else.

Any ideas?

---

### Post by sandysandy on 2008-03-16
> **Tasc0 said:**
> I think my problem is that I installed Grub in the MBR and by doing that, NTLDR was deleted. So I need to restore NTLDR and install Grub in some place else.

Any ideas?

Make entry for Windows in menu.lst file of Ubuntu.

with that the GRUB will give u options for both Windows and Ubuntu.

regards

---

### Post by confused57 on 2008-03-16
Might help if you can post the output of:
```
sudo fdisk -l
```

Also, do you have a mix of IDE & SATA drives?

---

### Post by sandysandy on 2008-03-16
have a look at this thread also

[http://ubuntuforums.org/showthread.php?t=615242](http://ubuntuforums.org/showthread.php?t=615242)

regards

---

### Post by Tasc0 on 2008-03-16
> **sandysandy said:**
> Make entry for Windows in menu.lst file of Ubuntu.

with that the GRUB will give u options for both Windows and Ubuntu.

regards
A Windows entry is already there, check my post above.
> **confused57 said:**
> Might help if you can post the output of:
```
sudo fdisk -l
```

Also, do you have a mix of IDE & SATA drives?

Yes, I do. I have SATA of 160 GB (Windows and Ubuntu are installed there) and I have an IDE of 80 GB with files. Here is the fdisk you asked (sorry, it's in Spanish):

```

Disco /dev/hdb: 80.0 GB, 80032038912 bytes
255 cabezas, 63 sectores/pistas, 9730 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8ca98c5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1   *           1        4502    36162283+   7  HPFS/NTFS

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pistas, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xac20e2d1

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       11415     9767520   83  Linux

```

Hope this helps.

---

### Post by sandysandy on 2008-03-16
r u getting windows option during booting, seeing that entry for windows is there in menu.lst file.

regards

---

### Post by Tasc0 on 2008-03-16
> **sandysandy said:**
> r u getting windows option during booting, seeing that entry for windows is there in menu.lst file.

regards
Yes, I have the Windows entry in the Grub screen. But when I select it and hit enter I get the error message "Error 22: NTLDR missing".

---

### Post by sandysandy on 2008-03-16
error22 as per [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

>  error 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

it is evident that ur windows entry in menu.lst need to be edited to reflect the correct partition number.

backup ur menu.lst and try changing windows entry to (0,0) etc
> 
title		Microsoft Windows XP Professional
root		(hd1,0) 

GRUB is installed on which harddisk. on which hard disk is windows ( can see 2 NTFS partitions)

regards

---

### Post by Tasc0 on 2008-03-16
Like I said, Windows and Ubuntu (and Grub) are installed in the SATA 160 GB hard drive. The other one is an IDE of 80 GB that only has files (NTFS), no OS.

And I'm afraid there's no need to edit the entry in menu.lst, the problem is that NTLDR is missing, therefor Windows can't start.

Now, if I restore NTLDR, Grub disappear. And if I restore Grub, NTLDR disapear. I thik I've made my point about that.

---

### Post by sandysandy on 2008-03-16
just re read ur post 11

>   Yes, I do. I have SATA of 160 GB (Windows and Ubuntu are installed there) and I have an IDE of 80 GB with files. 

since windows and Ubuntu are on same drive, and ubuntu is reflected as (hd 0,1) in menu.lst change windows to (hd0,0)

that should do the trick.

BACKUP menu.lst

regards

---

### Post by sandysandy on 2008-03-16
> **Tasc0 said:**
> Like I said, Windows and Ubuntu (and Grub) are installed in the SATA 160 GB hard drive. The other one is an IDE of 80 GB that only has files (NTFS), no OS.

And I'm afraid there's no need to edit the entry in menu.lst, the problem is that NTLDR is missing, therefor Windows can't start.

Now, if I restore NTLDR, Grub disappear. And if I restore Grub, NTLDR disapear. I thik I've made my point about that.

look at post 16.  give it a try.

it should work.

regards

---

### Post by Tasc0 on 2008-03-16
> **sandysandy said:**
> just re read ur post 11



since windows and Ubuntu are on same drive, and ubuntu is reflected as (hd 0,1) in menu.lst change windows to (hd0,0)

that should do the trick.

BACKUP menu.lst

regards
I just tried that and I get the same error.

---

### Post by sandysandy on 2008-03-16
>  Now, if I restore NTLDR, Grub disappear.  

have a look at this link

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

regards

---

### Post by Tasc0 on 2008-03-16
That's a long read and a lot of configurations. In addition, I'm on Linux right now so I'll have to restore NTLDR and do what it says there.

But I'm wondering if there's an easier way to fix this.

---

### Post by jocko on 2008-03-16
> **Tasc0 said:**
> 
And I'm afraid there's no need to edit the entry in menu.lst, **the problem is that NTLDR is missing, therefor Windows can't start.**

Now, if I restore NTLDR, Grub disappear. And if I restore Grub, NTLDR disapear. I thik I've made my point about that.

Are you sure? ntdlr is always on the same partition as windows is installed on.
As ubuntu didn't overwrite your windows partition, ntdlr is still there (mount your windows partition in linux and see for yourself).
But I do see a problem in your menu.lst.

```
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       11415     9767520   83  Linux
```If windows is installed on your sda1, grub will see this as (**hd0,0**), but in your menu.lst:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```This tells grub to look for ntdlr on a different hard drive (your hdb1), and then it re-maps your hard drives so that hdb becomes your primary hard drive and sda becomes a secondary drive.
Make a backup of your menu.lst, and make it look like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (**hd0,0**)
savedefault
chainloader    +1
```Now grub will look for ntdlr on the correct hard drive, and hopefully windows will boot without problems.

---

### Post by confused57 on 2008-03-16
Here's how to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Change your Windows entry to the one jocko gave you...quit & save.

---

### Post by Tasc0 on 2008-03-16
To the two posters above:

I already tried editing menu.lst and I get the same error (22).

> **Tasc0 said:**
> I just tried that and I get the same error.

Like I said, Grub was installed in the MBR and it removed NTLDR.

---

### Post by confused57 on 2008-03-16
> **Tasc0 said:**
> To the two posters above:

I already tried editing menu.lst and I get the same error (22).



Like I said, Grub was installed in the MBR and it removed NTLDR.
Dual-booting Windows with an IDE & SATA mix can be troublesome.  I've seen others have success by disconnecting their IDE drive, reinstall Ubuntu to the SATA drive with Windows...make sure both OSes boot properly, then reconnect your IDE drive.

---

### Post by Tasc0 on 2008-03-16
> **confused57 said:**
> Dual-booting Windows with an IDE & SATA mix can be troublesome.  I've seen others have success by disconnecting their IDE drive, reinstall Ubuntu to the SATA drive with Windows...make sure both OSes boot properly, then reconnect your IDE drive.
I don't see how that's the problem. When I was installing Ubuntu I selected the SATA drive (where Windows is installed) and edited a new partion for ext3.

What do you think about [this]("http://users.bigpond.net.au/hermanzone/p9.html")?

---

### Post by jken146 on 2008-03-16
> **Tasc0 said:**
> To the two posters above:

I already tried editing menu.lst and I get the same error (22).



Like I said, Grub was installed in the MBR and it removed NTLDR.

Jocko's suggestion was different to what you tried earlier.

---

### Post by Tasc0 on 2008-03-16
> **jken146 said:**
> Jocko's suggestion was different to what you tried earlier.
Nope:
> **sandysandy said:**
> just re read ur post 11



since windows and Ubuntu are on same drive, and ubuntu is reflected as (hd 0,1) in menu.lst **change windows to (hd0,0)**

that should do the trick.

BACKUP menu.lst

regards

---

### Post by confused57 on 2008-03-16
> **Tasc0 said:**
> Nope:
jocko's suggestion **was** different in that the map lines were removed in the Windows entry he gave you...did you try without the map lines with root (hd0,0)?

---

### Post by Tasc0 on 2008-03-16
> **confused57 said:**
> jocko's suggestion **was** different in that the map lines were removed in the Windows entry he gave you...did you try without the map lines with root (hd0,0)?
You're right about that. Sorry.

I'm on Windows right now, so Jocko's suggestion worked.

What's weird, is why I can't see the NTFS partions on Linux. Do I have to mount them? If so, how?

---

### Post by confused57 on 2008-03-17
> **Tasc0 said:**
> You're right about that. Sorry.

I'm on Windows right now, so Jocko's suggestion worked.

What's weird, is why I can't see the NTFS partions on Linux. Do I have to mount them? If so, how?
Glad it worked for you...here's an excellent guide for mounting your Windows partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
there is also a guide for mounting Linux on this site, in case you ever need to.

Another guide for mounting different filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

Your initial problem wasn't that your ntldr was actually missing, but that was the error message because grub was trying to boot your ntfs partition on your other hard drive with the incorrect root(hd1,0) and/or the map lines...of course, there's no ntldr on a ntfs data partition.  Grub only installs it's IPL(Initial Program Loader) to the mbr of a hard drive for booting purposes, it never overwrites the bootloaders of other OSes, unless you specifically tell it to install grub's IPL to a different location.

---

### Post by Tasc0 on 2008-03-17
> **confused57 said:**
> Glad it worked for you...here's an excellent guide for mounting your Windows partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
there is also a guide for mounting Linux on this site, in case you ever need to.

Another guide for mounting different filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

Your initial problem wasn't that your ntldr was actually missing, but that was the error message because grub was trying to boot your ntfs partition on your other hard drive with the incorrect root(hd1,0) and/or the map lines...of course, there's no ntldr on a ntfs data partition.  Grub only installs it's IPL(Initial Program Loader) to the mbr of a hard drive for booting purposes, it never overwrites the bootloaders of other OSes, unless you specifically tell it to install grub's IPL to a different location.
Thanks for the links. Now, suddenly I turned up the computer, went to Ubuntu and the two NTFS appeared in the desktop, I can read files now and I didn't do nothing, no mount, no nothing. That's quite odd.

Now, I have a question. Let's say I reformat my SATA drive, and I want to install Windows and Ubuntu on it again, should I disconnect the IDE drive? I think that will avoid the problem.

---

