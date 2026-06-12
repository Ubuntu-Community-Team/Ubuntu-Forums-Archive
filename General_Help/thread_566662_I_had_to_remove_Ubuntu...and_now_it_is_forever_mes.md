---
title: "I had to remove Ubuntu...and now it is forever messed up!"
date: 2007-10-03
forum: General Help
---

### Post by lenovolove on 2007-10-03
OK. I have a ToshibaM45. It had Ubuntu 7.04 installed. Due to circumstance, I wanted to remove Ubuntu and put Windows XP back on the hard drive (it was not a dual-boot system).

I asked in another forum how to do this. The person told me to type this into terminal:

[PHP]sudo dd if=/dev/zero of=/dev/hda bs=521 count=1[/PHP]

I did this & restarted the computer. The very first message I got was:

[PHP] "Operating system not found". [/PHP]

Ok, so I put in a bootable Windows XP recovery CD & restarted. I made sure in the BIOS it booted from the CD-ROM. Now I get this message:

[PHP]Invalid system disk. Please remove the disk and press a key[/PHP]

WTF? Now I can't even reinstall Ubuntu! The liveCD says the same thing!

Now when I remove the CD from the drive & power the system on, I still get the "Invalid disk" message...even though there isn't a disk inside.

Am I F****ed? Do I need to buy a new hard drive? I am so upset :(

---

### Post by rsambuca on 2007-10-03
Enter your BIOS and make sure it is set to boot from the CD drive first.

---

### Post by Buffalo Soldier on 2007-10-03
> **lenovolove said:**
> OK. I have a ToshibaM45. It had Ubuntu 7.04 installed. Due to circumstance, I wanted to remove Ubuntu and put Windows XP back on the hard drive (it was not a dual-boot system).

I asked in another forum how to do this. The person told me to type this into terminal:

```
sudo dd if=/dev/zero of=/dev/hda bs=521 count=1
```(To reinstall Windows XP all you need is to just put in the CD and format/install as you would usually do.

What's the command for? I mean, what did you asked about previously?

---

### Post by lenovolove on 2007-10-03
> **rsambuca said:**
> Enter your BIOS and make sure it is set to boot from the CD drive first.

I did this already :(

My BIOS looks like this:

CD-ROM
+Hard Drive
Realtek 
Removable media

(I can't get the + sign next to the CD...that said, pressing F12 loads a menu & I can manually select what I want to boot from --- alas, even with a bootable Windows recovery CD nothing happens except that error message)

> **Buffalo Soldier said:**
> To reinstall Windows XP all you need is to just put in the CD and format/install as you would usually do.

This didn't work for me :( I tried that the first time. The Toshiba recovery CD finished & asked me to reboot. When I did, I got this message:

**Loading Grub 1.5 please wait....Error**

At which point the computer would restart & repeat that message over and over. I had to use the Ubuntu LiveCD to reinstall Linux...and it was then that I used the code mentioned above in my first post. Now all this happened....

PS: I was told that the command mentioned in the OP was to delete the MBR/bootloader so that Windows could install its own...and boot into Windows. I was told this would "fix my hard drive for a clean slate -- a fresh install of whatever OS". By a moderator on another linux forum no less :D

---

### Post by American_Outcast on 2007-10-03
Strange that XP won't install. Try using the Gparted live disk and format the hard drive with a fat32 file system and then see if XP recognizes it, or for that matter if the gparted livecd recognizes it.

---

### Post by DDuong on 2007-10-03
You don't need a new hard drive :)

Hopefully you didn't wipe out your recovery partition for windows  (unless recovery dvd is the true windows xp cd)
 
I noticed that recovery cd/dvd are not the actual true windows xp cd.

See if you can contact Toshiba/Microsoft and let them know that you got hit with a virus and it wiped out your system :P  Just to be sure as some manufacturers don't support people who wipe their laptops and install linux :(

Good Luck!

---

### Post by lenovolove on 2007-10-03
> **American_Outcast said:**
> Strange that XP won't install. Try using the Gparted live disk and format the hard drive with a fat32 file system and then see if XP recognizes it, or for that matter if the gparted livecd recognizes it.

:) glad we're thinking on the same page here. I just finished burning the GParted ISO to CD...and I still get the "Invalid System disk...." message. Not a single bootable CD is working for me...I think I have to sing myself a song :guitar: and buy another hard drive :(

PS.: Yes I was the stupid idiot who deleted his Windows partition (hey 80gigs isn't enough HDD space...I needed that ~5gb of Windows! :D).

---

### Post by American_Outcast on 2007-10-03
> **lenovolove said:**
> :) glad we're thinking on the same page here. I just finished burning the GParted ISO to CD...and I still get the "Invalid System disk...." message. Not a single bootable CD is working for me...I think I have to sing myself a song :guitar: and buy another hard drive :(

PS.: Yes I was the stupid idiot who deleted his Windows partition (hey 80gigs isn't enough HDD space...I needed that ~5gb of Windows! :D).

:lolflag:

Did you try cfdisk in the terminal or fdisk as well? I have had various issues with gparted itself at times but cfdisk and fdisk worked fine.

---

### Post by lenovolove on 2007-10-03
> **American_Outcast said:**
> :lolflag:

Did you try cfdisk in the terminal or fdisk as well? I have had various issues with gparted itself at times but cfdisk and fdisk worked fine.

If I could only get into terminal...Ubuntu no longer loads anymore](*,)

---

### Post by American_Outcast on 2007-10-03
> **lenovolove said:**
> If I could only get into terminal...Ubuntu no longer loads anymore](*,)


It doesn't load with the livecd either? If not it might be something other then the hard drive.

---

### Post by lenovolove on 2007-10-03
No sir, nothing at all shows up on the screen ---- nothing but "Invalid system disk" ---- no matter what bootable CD is in the drive (or not, still get that message). My only "GUI" is the BIOS menus (F2 and F12)....and that awful invalid disk error :frown:

---

### Post by Samhain13 on 2007-10-03
Maybe the CD drive got messed up too?

---

### Post by lenovolove on 2007-10-03
I don't think the CD drive is messed up. The laptop is fairly new. In addition to this, the CD drive and the hard drive were 100% working before I used that code in my OP.

Here is the brilliant advice given from Linuxforums.org that messed up my HDD :lolflag:
[http://www.linuxforums.org/forum/ubuntu-help/104826-uninstalling-ubuntu-how.html]("http://www.linuxforums.org/forum/ubuntu-help/104826-uninstalling-ubuntu-how.html")

---

### Post by jrusso2 on 2007-10-03
I think you need to find a windows cd and fix the master boot record

---

### Post by American_Outcast on 2007-10-03
> **lenovolove said:**
> No sir, nothing at all shows up on the screen ---- nothing but "Invalid system disk" ---- no matter what bootable CD is in the drive (or not, still get that message). My only "GUI" is the BIOS menus (F2 and F12)....and that awful invalid disk error :frown:

Can you unhook the hard drive and then try and boot the livecd? It is strange that you can't install either XP or Ubuntu and can't even get a livecd to work. Maybe it is one of those strange little laptop things.

I have had hard drives messed up so nothing would install on them. I was able to use livecd's (various ones, Ubuntu livecd, Gparted, SystemRescueCD, etc,) and go into the terminal and format, partition and make a file system, (using cfdisk, fdisk, the command line, etc.) when gparted failed. That usually fixed the problem so I could install which ever OS.

But like you said nothing is working. You can't install Ubuntu, XP or even use a livecd.

No wonder your banging your head against the wall, :lolflag:

---

### Post by scruff on 2007-10-03
It is because GRUB is installed to your MBR (master boot record). You need to run this command from windows recovery, a DOS floppy, Win98 disk, or something of the like:

   1. Restart your computer with the Windows XP Setup disk in the CDROM drive.
   2. If you are prompted to press a key to start the computer from CDROM, do so quickly. Otherwise it may try to boot from the hard drive.
   3. After a few minutes, you'll see a prompt to press the R key to start the Recovery Console.
   4. When Recovery Console starts, it will prompt you to enter a number corresponding to the Windows XP installation that you need to repair. In most cases, you'll enter "1" (which will be the only choice). If you press ENTER without typing a number, Recovery Console will quit and restart your computer.
   5. Enter your Administrator password. If you don't enter the correct password, you cannot continue.
   6. At the Recovery Console command prompt, type fixmbr and then verify that you want to proceed.

EDIT: this assumes the windows install completed properly, I forgot. No biggie though. Like I said, get any startup disk that has some DOS utilities on it (there's a hundred for download on the net) and once booted, do the fixmbr command.

[http://www.google.com/search?num=100&hl=en&safe=off&q=fixmbr+boot+disk&btnG=Search](http://www.google.com/search?num=100&hl=en&safe=off&q=fixmbr+boot+disk&btnG=Search)

---

### Post by strabes on 2007-10-04
Check the GRUB link in my signature for more detailed information about what scruff posted.

---

### Post by lenovolove on 2007-10-04
Thanks everyone who has tried to help out :guitar:

I did everything listed here.....and no luck......I'm going to the computer rinky dink store in my area and getting another 80gb HDD....problem solved! :popcorn:

---

### Post by iWolverine on 2008-06-16
I had the same problem with my old Toshiba Satellite 1805-S274 during Xubutu 8.04 installation.

The solution was adding acpi=off bootloader parameter.

I hope It'll help to somebody.

---

