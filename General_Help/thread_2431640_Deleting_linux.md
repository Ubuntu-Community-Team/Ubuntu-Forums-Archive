---
title: "Deleting linux"
date: 2019-11-19
forum: General Help
---

### Post by muamerba on 2019-11-19
Hello everyone, I am new to forums in general and I need help big time. The thing is, I installed Ubuntu a few days ago due to my Windows licence expiring and I wanted to change to try something new. So with my stupidity and ignorance I went completely into the dark and installed Ubuntu SOMEHOW. Everything went good and I didn't liked it so I decided to switch back and then the problems started. I was searching the web for days trying to find some solutions but to no avail. I tried everything. 

Literally everything. I made and USB live with windows 10 on it and meanwhile i made it through "unetbootin" and meanwhile booting it got stuck in the never-ending 10 seconds loop. So I went to another solution. I tried to delete partitions but it turns out I didn't made any partitions i installed it directly on my HDD it seems. So I tried to partition my HDD and to make space for the WIN 10 system to try and make a Dual boot but no avail I can't seem to do anything with my HDD as it says that it is in use nor can I partition it as it does not allow me to (see screenshot). Please can someone help me I am going crazy as I just want to return to windows.

---

### Post by jetsam on 2019-11-19
Wiping the drive isn't hard from where that picture shows you.  When you're ready to wipe the drive, just select the big partition and reformat it to the filesystem of your choice.  NTFS is probably what you want for an eventual Windows install.

Reinstalling Windows requires the installation media.  I think you can make it if you have access to a DVD burner.  This article may be usefull to you:
[You Can Still Get Windows 10 for Free With a Windows 7, 8, or 8.1 Key]("https://www.howtogeek.com/266072/you-can-still-get-windows-10-for-free-with-a-windows-7-8-or-8.1-key/")

Validating your Windows install may be more difficult.  If you call Microsoft support, they are usually amenable to validating a licensed copy if they think you had a previous Windows version that was fully legal. If you have a product key stuck on your computer case, you should be able to use that and avoid the call...  just type in the product key when requested by the validation engine on your computer.

---

### Post by muamerba on 2019-11-19
I see but I can't do anything on GParted with my HDD and is confusing me

---

### Post by jetsam on 2019-11-19
It won't unmount the drive it booted from.  You need to use a live CD, but don't worry about it.  I'm pretty sure the Windows installer will happily delete Linux if you ask it nicely ;)

cheers,
jetsam

---

### Post by deadflowr on 2019-11-19
The key symbol means it's in use, which means it cannot be fiddled with.
Are you running gparted from the live usb session or from the install?

---

### Post by crip720 on 2019-11-19
Did you make the install Win 10 usb from Ubuntu?  If so you would need Woeusb to make it bootable.  You cannot change a partition that is mounted/being used, need to boot from a live usb to change partition.

---

### Post by TheFu on 2019-11-19
As others have stated, Unix cannot alter partitions that are *in use*. If they are mounted, they are in-use.  So, if you had more than 1 partition and only 1 was in-use, then you'd be able to modify those other partitions from the running system.  With just 1 partition, if it is mounted, you cannot modify it unless it is unmounted, which usually means using alternate-boot media - booting from a flash drive or DVD.

You'll need to install whatever MS-Windows version you want.  The disk appears to be fully allocated with a single partition. Can't you tell the Windows installer to use the entire disk?  If not, you can always boot from the flash drive you used to install whatever Linux, then use **fdisk** or **parted** or **gparted** to delete all the partitions on the internal disk however you like.  I would probably use gparted and just create a new GPT partition table, write the changes, and shutdown.  Then boot with the Windows installer.

Or did you have some data on their you wanted to backup first?

I'm confused.

If you want a dual-boot setup, Windows insists that it be installed first.  Microsoft has a habit of ignoring other installations, so if they are actually paying attention now, I'd find that odd.

---

### Post by crip720 on 2019-11-19
Windows does seem to be playing nicer, on UEFI systems anyway.  Had to install Windows after Ubuntu and did not even have to reinstall grub.  Would not trust it not to mess up linux partition during an upgrade though.

---

### Post by mörgæs on 2019-11-19
Literally everything? Whoa, that must have taken literally forever. 

That aside: If you have only been using Ubuntu for a few days you could also give it a chance a little longer. People here would be happy to answer questions and help you get up and running.

---

### Post by yancek on 2019-11-19
> Windows does seem to be playing nicer, on UEFI systems anyway 

That's pretty much due to the way UEFI systems work.  THe windows efi files are on the EFI partition in a separate directory from any Linux OS so there is no boot code in the MBR being used.  I installed windows 10 a while back on an older Legacy/non-UEFI machine without problems but of course, it did overwrite the Grub code in the MBR.

---

### Post by HermanAB on 2019-11-20
Here is a simple trick:
If you zero the first bit of a disk drive, then Windows will think it is a new disk and will then install without any drama.

When booted off a Linux install disk or usb stick, you can zero a hard disk with something like this:
# cat /dev/zero > /dev/sda

After a few seconds, press Ctrl-C to quit the cat program.

Now, you can remove the Linux media, insert Windows media and install.

---

