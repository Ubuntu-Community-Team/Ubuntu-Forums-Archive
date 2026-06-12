---
title: "Can't access tty -- SOLUTION"
date: 2007-04-10
forum: General Help
---

### Post by Aero9000 on 2007-04-10
Hi Folks,

When attempting to boot the Live CD (Feisty) I got the dreaded "/bin/sh: can't acces tty" and the CD was unable to continue.

I looked all over the forum here and found that a lot of people have this problem and some write they got this problem after a certain kernel update. So I downloaded the herd5 version of Feisty, hoping this one would be old enough to let me boot from the Live CD, but to no avail.

Here's a brief description of what happened on my system.

I downloaded a daily build of Ubuntu64 (March 7, 2007) and successfully installed it to my computer.

Then, a week later I was forced to reinstall Windows XP :(

Afterwards grub was gone and I wanted to reboot from the Live CD to repair grub and then I got the "/bin/sh: can't acces tty" !!! (And please note, this was using the same Live CD I had installed from successfully before!)

After tinkering with BIOS settings and what have you not, I was getting nowhere. But then I recalled that after installing XP, XP had run a chkdsk on one of my partitions. Could this be it?

Well, actually I think not. :) 

And now how I fixed it....
**THE SOLUTION**

Here are the steps.
Before you apply the patch below, you should first back up any important data you have and can't afford to lose. :)

Read through the steps and understand what you are doing.

Next, GET YOUR EMERGENCY RECOVERY TOOLS and FAMILIARIZE yourself with those. Since we will replace the so called Master Boot Record ([http://en.wikipedia.org/wiki/Mbr](http://en.wikipedia.org/wiki/Mbr)) there is a (very) remote chance you will lose access to your disk. An emergency tool you could use is TestDisk by Cgsecurity -- this is not a test programme, it is in fact a powerful recovery software. See [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk). The second tool you will want to keep at hand is Super Grub Disk. This tool will reinstall Grub to the harddisk in case it gets overwritten. See [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/). Oh, by the way, be smart and create bootable media with the emergency tools BEFORE you start. :)

Now you will need to boot from your Windows set up CD. Just wait for Windows to load all of it's useless drivers. When the setup procedure finally starts, the first thing Windows will ask you is if you want to set up or recover using the Recovery Console. The latter is exactly what we want, so press R to start the Recovery Console.

When the Recovery Console starts, it will ask you for a keyboard layout (chances are you will just want to wait this one out) and then Windows will ask you to which Windows version you want to log on to. Important! Press 1 (or 2, or whatever is applicable) and THEN press Enter. If you press Enter without keying in a digit, your computer will reboot and you will have to boot from the CD again.

Next, the Recovery Console will ask you for the Administrator password. Key it in and press Enter or just press Enter if you have no administrator password.

Now you should see something like C:\Windows>. This is good, this is what we want.

The next step is to identify how Windows sees your harddisks. Type MAP and press Enter. This will give you some output with drive letters and locations. What you will need to focus on is something like "\Device\HardDisk0", "\Device\HardDisk1", etc. On my system, by the way, the numbers were 4, 5 and 6 (numbers 0 through 3 were not listed, I don't know why, but it doesn't really matter anyway).

Now you will replace the MBR (Master Boot Record). Starting with the highest number, type "FIXMBR \Device\HardDisk2" (or 1, or 0) and press Enter. The command prompt will either return immediately (which is good) or Windows will warn you a nonstandard partition table signature was detected and continuing may result in your partitions no longer being accessible. OK, this leaves you with 2 choices. Either skip this disk and repeat the FIXMBR command for disk 1 (or 0), or continue anyway. Chances are the unrecognized partition table signature is the root cause of the "/bin/sh: can't acces tty" problem, so you need to fix it. I recommend you process one disk at a time. So after you fixed the MBR on disk 2 (or 1, or 0) type EXIT and press Enter. Your computer will now reboot.

Replace the Windows CD by your Ubuntu Live CD and see if you can boot. If you can then there is NO NEED to run FIXMBR against your other harddrives.

If you have to do "FIXMBR \Device\HardDisk0", then there is a good chance Grub no longer works. In this case you will have to run Super Grub Disk to restore Grub, or if you prefer manual recovery, see here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation).

**I ran FIXMBR against all of my harddisks and I STILL CAN'T BOOT! What can I do?**
OK, I'm going into speculative mode now, but bear with me. Prior to the release of Windows XP SP1, Windows was not able to address more than 137 GiB. I really don't know if this has an impact on the MBR, but if your disk/s has/have more capacity, then you need to install the Recovery Console to your harddisk. Unfortunately the version on your CD is too old and you will have to take the following steps (see also: "http://support.microsoft.com/kb/307654", "http://support.microsoft.com/kb/898594" and "http://support.microsoft.com/kb/900871").

Copy the I386 directory and all of its subdirectories from your Windows setup CD to your HD into its own directory (e.g. C:\XPCD).
Download SP2 for XP -- the full package (266MiB). Get it here: [http://www.microsoft.com/downloads/details.aspx?FamilyID=049c9dbe-3b8e-4f30-8245-9e368d3cdb5a&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=049c9dbe-3b8e-4f30-8245-9e368d3cdb5a&DisplayLang=en)
and save it to (for example) C:\XPSP2.
Open a command prompt and execute "C:\XPSP2\WindowsXP-KB835935-SP2-ENU.exe /integrate:C:\XPCD" -- this will merge the SP2 files with the files you copied from your XP CD.
At the command prompt exectute "C:\XPCD\i386\winnt32.exe /cmdcons -- this will install the Recovery Console to your harddisk (Windows boot partition).
Restart your computer. When Windows boots you will be presented with a menu allowing you to boot Windows or the Recovery Console. Choose the Recovery Console. Then follow the steps outlined above.

Feel free to delete C:\XPSP2 and all of its subdirectories after you installed the Recovery Console. The actual Recovery Console files are stored in C:\CMDCONS. If you want to get rid of the Recovery Console afterwards, Open the Control Panel and then open System. Go to Advanced -> Startup and recovery Settings. Verify or set Windows XP as the default operating system and clear the 2 checkboxes.


That's all.


Just one final request. Please post a reply if this fixed your problem or if it didn't.

---

