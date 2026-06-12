---
title: "How to disable NTFS access of Ubuntu?"
date: 2007-12-04
forum: General Help
---

### Post by perixx on 2007-12-04
Hi!

I want to **DISABLE** the NTFS-access under Ubuntu (meaning: uninstall NTFS-support); which package(s) would I have to remove for that purpose?

Would de-installing 'libntfs9' and 'ntfsprogs' do the trick? 
Gparted should still be able to have NTFS-creation-capabilities - will removing those packages also strip NTFS-access for Gparted? 


perixx

---

### Post by banewman on 2007-12-04
If you installed ntfs-3g then uninstalling that would be the first port of call.
In terminal type      gksu gedit /etc/fstab    and comment out -   #    - the line that shows your ntfs mount point. That should make it hard :)

---

### Post by perixx on 2007-12-04
hi banewman!

I'm referring to a Xubuntu standard installation; the packagaes I mentioned were the only ones that contained 'ntfs' when searching in Synaptic. I don't know if ntfs-3g is installed by default, at least it's not installed at my system, according to Synaptic.


perixx

---

### Post by banewman on 2007-12-04
Then follow my second point and the partition won't be mounted - so no access for anyone :)

---

### Post by nqsonk9 on 2007-12-04
Uhmm, I'm not sure if ntfs-3g is installed by default in Gutsy but right after installation, I have access to all ntfs partitions in my driver. Moreover, as you can see, in fstab, there no entry using the ntfs-3g type. So, I dont think the uninstall trick will work

The simpliest solution is to comment out the ntfs partitions entries in the /etc/fstab.

I wonder is ther any file that control that mouting stuff in linux, i'm using FC8 and in that system, by default the fstab look like a white page, the system auto-mount every partition you have, no matter it has an entry in fstab or not. Any ideal, guys ?

---

### Post by perixx on 2007-12-04
> the system auto-mount every partition you have, no matter it has an entry in fstab or not. Any ideal, guys ?

Sorry, I haven't.

Ok, banewman I'll try that fstab trick. But can you also give some comment to the packages I mentioned above please?


perixx

---

### Post by KIAaze on 2007-12-04
Here's the package info:
[libntfs9]("http://packages.ubuntu.com/gutsy/libs/libntfs9")
[ntfsprogs]("http://packages.ubuntu.com/gutsy/otherosfs/ntfsprogs")

So, yes, I think that uninstalling libntfs will remove access to NTFS partitions.
In any case, I don't think there's any danger in uninstalling it.

---

### Post by gazj on 2007-12-04
just a note, if you do uninstall the ntfs support, i would still recommend commenting out the ntfs lines in /etc/fstab otherwise ubuntu will try to mount the partition on startup and may hang trying to mount them.

Not certain this will happen but i would still do it, you can always change it back later if needed. :)

---

### Post by nqsonk9 on 2007-12-04
> Here's the package info:
libntfs9
ntfsprogs

So, yes, I think that uninstalling libntfs will remove access to NTFS partitions.
In any case, I don't think there's any danger in uninstalling it.

Thanks for that, i think it should be helpful in FC too :)

Is there any other file than **fstab** to configure the mouting stuffs, guys ?

---

### Post by perixx on 2007-12-04
thanks, gazj and KIAze!

I'll do that... do you know if I'll still be able to create/delete NTFS partitions with Gparted?

Edit: oh, and does the combination of libntfs9/ntfsprogs have any advantages or disadvantages compared against ntfs-3g? As far as I can see, the first has a vaster set of funcionality? But what about stability - anyone knows about them?

---

### Post by KIAaze on 2007-12-04
As far as I know, NTFS-3g is needed if you want to write to NTFS partitions.

I don't know if gparted can still create NTFS partitions without libntfs.
But why would you want to do that anyway? Create ext3, FAT32 or other partitions. :p
Windows can do the NTFS partitioning itself when you install it.

Using packages.ubuntu.com again:
[http://packages.ubuntu.com/gutsy/gnome/gparted](http://packages.ubuntu.com/gutsy/gnome/gparted)

=>gparted doesn't depend directly on libntfs and ntfsprogs is only suggested.

I suppose that ntfsprogs is only needed if you want to resize NTFS partitions with gparted, which can be very useful.

---

### Post by gazj on 2007-12-04
> **nqsonk9 said:**
> Thanks for that, i think it should be helpful in FC too :)

Is there any other file than **fstab** to configure the mouting stuffs, guys ?

/etc/fstab is the default file for defining partition mounting at startup amongst every linux distro i have ever used,  I can't see why FC would be any different.

> thanks, gazj and KIAze!

I'll do that... do you know if I'll still be able to create/delete NTFS partitions with Gparted?

Edit: oh, and does the combination of libntfs9/ntfsprogs have any advantages or disadvantages compared against ntfs-3g? As far as I can see, the first has a vaster set of funcionality? But what about stability - anyone knows about them?

Your very welcome, if you just comment out the line in your fstab and do not uninstall any ntfs packages then you will be fine with gparted (in fact i think the packages in question probably would not effect gparted they are only for reading / writing ntfs data, try it you can always reinstall them i guess)

---

### Post by perixx on 2007-12-04
> Windows can do the NTFS partitioning itself when you install it.


Right! In fact, I've encountered issues with NTFS-partitions created by Gparted (Windows wouldn't recognize it as such and I had to re-format it as NTFS at the installation).

> in fact i think the packages in question probably would not effect gparted they are only for reading / writing ntfs data,
Similarly, its the NTFS-writing of Linux seems to have bugs and that I don't really trust, I have to admit. Screwed up an XP-installation by writing a 'bootsect.lnx' to C:\ and editing the boot.ini from Linux lately and received a 'no bootable disk' at startup -- 
it took me quite some time till I ironed this out (the bootsector was faulty,  nt-bootloader had been gone)...    

So, I'm convinced that I can proceed now :] 
Erm, btw., my NTFS partition apparently isn't auto-mounted at boot, so I can skip the fstab-edit. Besides, what's 'mtab' good for? 


perixx

---

### Post by KIAaze on 2007-12-04
> **perixx said:**
> 
Besides, what's 'mtab' good for? 


Just google it:
[http://brunolinux.com/02-The_Terminal/Fstab_and_Mtab.html](http://brunolinux.com/02-The_Terminal/Fstab_and_Mtab.html)

---

### Post by perixx on 2007-12-04
> Parted can also detect and remove HFS (Mac OS), JFS, NTFS,
UFS (Sun and HP), XFS and ASFS/AFFS/APFS (Amiga) filesystems,
but cannot create, resize or check these filesystems yet.

I was looking up in Synaptic for Gparted; so you two were right about Gparted partly includes NTFS capabilities.

Btw., can you perhaps help on this topics as well?
[http://ubuntuforums.org/showthread.php?t=601847]("http://ubuntuforums.org/showthread.php?t=601847")
[http://ubuntuforums.org/showthread.php?t=630714]("http://ubuntuforums.org/showthread.php?t=630714")


perixx

---

### Post by KIAaze on 2007-12-04
Gparted can definitely resize NTFS partitions. I used it several times for that.

---

### Post by perixx on 2007-12-06
The problem is: I've removed all 'ntfs'-like packages and can STILL mount and READ ntfs-partitions - but I don't want that!!

Please don't tell me that ntfs is supported natively by the Linux-kernel??

perixx

---

### Post by KIAaze on 2007-12-07
I did some research and it's quite possible that it's supported natively by the kernel.
However, it should still be possible to configure your kernel so that it doesn't support NTFS. :)

My knowledge about the kernel is still pretty limited but here's the basics:
The Linux kernel loads modules, which are the equivalent of drivers.
Two possible cases:
1)The module is loaded at startup by the kernel
2)The module is compiled into the kernel.

Case 1:
The module should be listed when you run "lsmod".
```
lsmod | grep ntfs
```
Should tell you if the ntfs module is loaded or not.
You can load/unload it with the "modprobe" command.

Case 2:
You will probably have to recompile the kernel without the NTFS module.

Here are some links I found that might help you (haven't read through all of them completely):
[http://www.linuxforums.org/forum/linux-newbie/667-adding-ntfs-modular-support-linux-kernel.html](http://www.linuxforums.org/forum/linux-newbie/667-adding-ntfs-modular-support-linux-kernel.html)
[http://www.freeos.com/articles/4051/](http://www.freeos.com/articles/4051/)
[http://www.arm.linux.org.uk/docs/kerncomp.php](http://www.arm.linux.org.uk/docs/kerncomp.php)
[http://www.captain.at/programming/kernel-2.6/](http://www.captain.at/programming/kernel-2.6/)

Note: The NTFS module seems to be called "ntfs.ko" (or ntfs.so or ntfs.o).
I found "ntfs.ko" here:
```
/lib/modules/2.6.22-14-generic/kernel/fs/ntfs
```
You could try simply deleting/renaming this file and see what happens at startup, but **it's at your own risk.**

May I ask why you don't want to be able to read NTFS partitions at all?
If you just want to deny users access to your NTFS partition, you could either encrypt the files on it, don't give users permission to mount it or don't give their user accounts read access to it.

---

### Post by perixx on 2007-12-07
KIAZE, you're shocking me!!:o 

> lsmod | grep ntfs
gives no output... ARGH!!

I can't compile a new kernel --- :shock:
:)

perixx

---

### Post by perixx on 2007-12-12
*bump* isn't there an easier solution ?? ;(

---

### Post by perixx on 2007-12-16
Doesn't anybody know of some sort of 'bootup-switch' for the kernel, that deactivates its NTFS-capabilities?

Thinking of having to compile a new kernel because of this seems to be a bit frightening to me.. ;)

perixx

---

### Post by perixx on 2008-01-09
**gives it another try**

---

### Post by KIAaze on 2008-01-09
I fear you may have to ask the Gentoo gurus for this. ^^'

You never explained why you want to disable access to NTFS so badly by the way...
If you want unaccessible data, there may be easier ways. (and better ones, considering that using a Live-CD gives NTFS access :roll: (but then you can disable booting from a CD and lock the BIOS with a password ^^))

P.S:
"lsmod | grep ntfs" corresponds to 2 commands ("piped together" with "|"):
1)lsmod -> lists modules
2)grep ntfs ->searches the output of the previous command for lines containing "ntfs"

This means that if "lsmod | grep ntfs" shows no output in your case, you could still search the output of lsmod for other words like NTFS or Ntfs.

To make the searching of the output easier, store it in a text file by doing:
```
lsmod > modules.txt
```
You can then open modules.txt in the text editor of your choice.

If there still doesn't seem to be anything related to NTFS, I really don't know what else can be done except recompiling a customized kernel...

Maybe other distributions like Gnewsense or Gobuntu (i.e. completely Free/libre distros without any proprietary stuff) are without NTFS capability by default. :)

---

### Post by perixx on 2008-01-09
Hi KIAze!

Thanks for your suggestions. None of the commands you stated returned any output. 
Well, I simply want to have a 'STRICT' division of Windows and Linux, so neither OS can access the filesystem of the other (of course not mentioning Grub), that's all. Should one of the systems somehow get penetrated, there's still a second barrier to prevent damage to the other system.

perixx

---

### Post by Slim Odds on 2008-01-09
> **perixx said:**
> 
Well, I simply want to have a 'STRICT' division of Windows and Linux, so neither OS can access the filesystem of the other (of course not mentioning Grub), that's all. Should one of the systems somehow get penetrated, there's still a second barrier to prevent damage to the other system.

perixx

If one of the systems get "penetrated" (i.e., compromised), what's to keep the penetrator from installing the drivers and accessing the drive?

Nothing.

---

### Post by perixx on 2008-01-09
I knew you would say that :]

---

### Post by KIAaze on 2008-01-09
> **perixx said:**
> 
Thanks for your suggestions. None of the commands you stated returned any output. 

"lsmod" didn't return any output???
There must be something wrong with your installation.

If you mean that "lsmod > modules.txt" didn't return any output, that's normal. It's because the output is written into the textfile "modules.txt".


And as Slim Odds said, if one of the systems is penetrated and the penetrator has admin permissions, he should be able to penetrate the other system too.

But disabling NTFS access should still make things safer in case of an automated attack (virus, spyware, etc) since they probably won't bother installing drivers. (specific drivers aren't necessary for formatting however I think)

---

### Post by Lostincyberspace on 2008-01-09
if you just comment out (or delete for that matter) the ntfs section in fstab then Linux will not do any thing there. and windows you have to install a driver to be able to even see ext3 drives. so if you do one of the two options I mentioned above they will be totally independent with no worries of messing something up.

---

### Post by perixx on 2008-01-10
Hi KIAze, you seem to get me wrong... I can do 'lsmod', but 'lsmod | grep ntfs' commands won't return anything (also I haven't seen anything on the list like that...

> But disabling NTFS access should still make things safer in case of an automated attack (virus, spyware, etc) since they probably won't bother installing drivers. (specific drivers aren't necessary for formatting however I think)
That is exactly what I intended to achieve, thanks for the support ;)

> if you just comment out (or delete for that matter) the ntfs section in fstab then Linux will not do any thing there.
Thanks for the hint, but I've already done so. But the drive is still visible in thunar (and possibly in /dev) and it's still possible to mount the drive via 'sudo mount' or Thunar and using the password. But it is 'there' (also using Gparted can still access the drive and alter it). I want Xubuntu to 'go blind' in this respect! 

perixx

---

