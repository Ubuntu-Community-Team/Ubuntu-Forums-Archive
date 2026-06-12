---
title: "XP no longer boots under Dual Boot."
date: 2007-05-24
forum: General Help
---

### Post by Fubie on 2007-05-24
For 3 weeks now I have had Feisty and XP running via dual boot without issue.

Last night when booting up my machine and going into Feisty I noticed it was doing a mandatory drive check.  The check completed and booted Feisty.  Because this happened several months ago on a different PC I quickly rebooted and selected XP.

All I get is a black screen.  The HD runs like it's booting but I get nothing.

Any ideas to get XP running again?

Thanks for any help.

---

### Post by dbott67 on 2007-05-24
Getting XP running again may render Ubuntu unable to boot (you would need to re-install grub).

Microsoft likes to 'own' the master boot record (MBR), which is where grub (Grand Unified Boot Loader) installs itself.  grub plays quite nicely with other OSes and will create entries for most other installations so that you can boot to them.

When you install Windows (or in this case, try to fix it) it's going to stomp all over the MBR and eliminate grub.  There are some tutorials in the forums on how to re-install grub from the Live CD.

Anyhow, on to fixing Windows:

1. Insert your Windows XP CD & boot from it.
2. Select R (repair) and get to a command prompt.
3. From the command prompt type one of the following:
```
fixmbr
```
or
```
fdisk /mbr
```
Both commands do the same thing.

-Dave

---

### Post by Fubie on 2007-05-25
Thank you very much for your help.

Is there a way I can prevent this from happening again?

---

### Post by starbase1 on 2007-05-25
It might be even easier - I had a very, very similar problem. When I managed to borrow a proper XP disk and boot from it, (as opposed to the alledged recovery disk it came with), it spotted the problem and corrected it without me doing anything.

---

### Post by Fubie on 2007-05-25
I have my original XP disk.

So you think booting it will just fix my XP issue?

I'm not sure how that would work since just booting it doesn't do anything to the system.

I'm willing to test it tho.

Thanks for the reply.

---

### Post by dbott67 on 2007-05-25
I guess it depends on what caused it.

I've never had any issues with my multi-boot laptop (Ubuntu 6.10, XP Pro, XP MCE, Vista Ultimate & Server 2003), but any sort of crash may cause problems.

By default, Ubuntu runs the file check (fsck) every 30 boots or so and you should let it finish before doing anything.  Also, not allowing your linux install access to NTFS partitions (i.e. mounting your Windows partition so that you have read/write access to your files) might also prevent troubles.

The best advice, though, is to always prepare for disaster: **backup your important data regularly**.  Buy a portable USB drive or NAS device (they're relatively cheap and have lots of storage); use a Ghost-like application to image your drive (such as [Ghost for Linux]("http://sourceforge.net/projects/g4l")); burn data out to CD or DVD.

You can also create a separate 'home' partition in Linux.  Then, if disaster strikes you can just re-install and not worry about losing data as the /home partition can be re-mounted.

-Dave

---

### Post by Fubie on 2007-05-25
Thanks Dave,

I don't let Linux touch my XP Partition because I use a fat32 usb drive for shared files.

There was no crash of any type.  Upon boot of Ubuntu it just stated that a file check had not been performed in 43 boot sequences.  I let it complete.  Later I rebooted and Windows not properly boot.  I get no errors at all, just a black screen.

I will play with it tonight to see if I can get it going.

I'm a long time computer tech and I know Winders damn well.  I've only been using Linux for the past year and I now only use Winders for a few things.  So I am still learning the Linux ways of geekdom.  I'm incredibly happy so far and the support here just makes things so much better.

Thank you again.

---

### Post by dbott67 on 2007-05-25
No problem for the help... anytime.

> **Fubie said:**
> ... Upon boot of Ubuntu it just stated that a file check had not been performed in 43 boot sequences.  I let it complete... 

As mentioned, this is a normal occurance so nothing unusual about it.

Of course, the unusual part is that Windows stopped booting right after.

A few things before you begin your journey:

1. Make a backup of any data in Ubuntu that you don't want to lose!
2. Make a backup of /boot/grub/menu.lst (your current grub menu)
3. Print out the instructions for re-installing grub (or have another computer handy with this thread):

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

4. Boot from the Windows CD & run fdisk /mbr or fixmbr (this will over-write grub)
5. Re-boot your computer and try to get into Windows.  If all works properly, then proceed to re-install grub.
6. If Windows does not boot, it is more than likely a coincidental issue between linux & Windows and you'll need to repair the Windows install using the usual methods.  If all goes well, then try re-installing grub again.

Good luck.

-Dave

---

### Post by starbase1 on 2007-05-25
> **Fubie said:**
> I have my original XP disk.

So you think booting it will just fix my XP issue?

I'm not sure how that would work since just booting it doesn't do anything to the system.

I'm willing to test it tho.

Thanks for the reply.

Well that's what I thought! But I stuck the CD in, turned on the machine, and it did the problem without me choosing anything, (which is prbably not what you would really want...)

I don't know if it will work for you, it probably depends on the nature of the problem. But it's worth a try...

Nick

---

### Post by Fubie on 2007-05-29
I wanted to give an update on my issue which is now resolved.

Before performing any changes to the system I unplugged everything (External USB Mouse, 2GB Corsair GT USB Key, and 500GB USB OneToch drive) from the laptop and rebooted.

Winders started without a problem.

So I started plugging in 1 thing at a time and rebooting to see which device was the culprit.  Winders booted successfully with the mouse plugged in.  But if either the  2GB Corsair GT USB Key or the 500GB USB OneToch drive were plugged in before booting Winders would hang in a black screen.

I guess that's Microslop for you.  I only need Winders for a few things.  But I'm hopefull I'll be able to drop it completely this year yet.

Thanks to everyone for all the help!

---

