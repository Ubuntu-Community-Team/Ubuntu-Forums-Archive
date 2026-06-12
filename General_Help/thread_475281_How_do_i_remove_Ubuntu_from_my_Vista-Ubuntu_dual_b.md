---
title: "How do i remove Ubuntu from my Vista-Ubuntu dual boot setup?"
date: 2007-06-15
forum: General Help
---

### Post by BL00dFox on 2007-06-15
Hi all

I have decided that i will install Ubuntu on my old comp (which i will use for my work, etc) and keep vista on this comp (to do everything else). I need to delete Ubuntu from this computer, since i have a dual boot going at the moment.

I have 4 partitions:

VISTA
OUR FILES <---- My personal stuff
UBUNTU
UBUNTU SWAP

I heard it isnt safe to just delete the Ubuntu and ubuntu swap partitions - the GRUB boot loader will still start. Does anyone else know how to completely remove Ubuntu from this comp (and leave only VISTA and OUR FILES partition)

Thanks

---

### Post by DizzyTech on 2007-06-15
Do you have a Vista CD?

What you need to do is use a Vista-based recovery console to reinstall NTLDR (or whatever Vista uses, I'm versed with XP).  Then you can use the Ubuntu CD's GNOME Partition editor (or another Vista-based utility) to get rid of your Ubuntu partition.  I think Vista has the ability built-in to enlarge its own partitions, so you'll be okay from there.

---

### Post by Makinen on 2007-06-17
OK same problem here, I have triple boot with Ubuntu-Vista-XP. GRUB though, only sees the Vista boot loader, and has one option (Vista loader) which I select and then launches the second boot loader, the one that has the options Vista and XP. So I wanted to delete Ubuntu (I didn't get my 8800 GTX to work) and I deleted the Linux partitions, though as I originally feared the GRUB loader remained, but the system now locks, showin error 22. So, I inserted my vista dvd, since it's the vista boot loader i want to save, and I went to repair options. In startup repair though, it didn't find any problems as it said and thus my system is now unusable until I can do something with the MBR. Vista disk doesn't work on its own, I need some command or something to fix the MBR:( Please help, I'm starting exams today and I need my pc immediately :(:(

---

### Post by binarybird on 2007-06-17
Why mess with deleting the loader? If grub will boot Vista without problems, leave your MBR alone and just use a partition editor to format the "82" and "83" type partitions and then reclaim it inside Vista. Just a suggestion. :)

---

### Post by Makinen on 2007-06-17
Well, if you read my post you might see that it doesn't boot anything. It says error 22 and it just freezes there...
Still, I finally found the solution. Use your Vista disk, and instead of selecting auto-repair of startup problems which will find no problems (...) select command promt and there type  bootrec.exe /fixmbr
That did it for me at once Vista boot loader with Vista and XP again:)
Too bad I'm leaving Linux once more, but they're not quite there yet:(

---

### Post by pratyk on 2007-06-23
i think u can use FixMBR.exe to fix the master boot record for vista .. and then simply delete the unwanted partitions by using a partition manager like GParted or Partition MAgic ... 
hope this helps ...

---

### Post by computer_user_au on 2007-06-29
> **pratyk said:**
> i think u can use FixMBR.exe to fix the master boot record for vista .. and then simply delete the unwanted partitions by using a partition manager like GParted or Partition MAgic ... 
hope this helps ...

You are indeed correct... Had the same grub 22 error. Rebooted the system with the windows disk, used the recovery tool to logon onto the windows partition. Ran fixmbr from the console, it wrote the new member and rebooted computer. Bang... windows started successfully. Thx for the tip.....:D

---

### Post by mouseboyx on 2007-06-30
> **binarybird said:**
> Why mess with deleting the loader? If grub will boot Vista without problems, leave your MBR alone and just use a partition editor to format the "82" and "83" type partitions and then reclaim it inside Vista. Just a suggestion. :)


i think the settings for the boot loader are inside the Ubuntu partition making it a very bad idea.

---

### Post by computer_user_au on 2007-07-02
> **mouseboyx said:**
> i think the settings for the boot loader are inside the Ubuntu partition making it a very bad idea.

Yep, the settings for the boot loader are inside Ubuntu... So if you happen to delete your Ubuntu partition before reconfiguring the MBR so that windows is the default partition and to be the boot loader... this is a good way to fix the problem and recover your windows partition. 

Now for future reference, does anyone know a way to use Ubuntu to uninstall Grub before removing the Ubuntu partition?

---

### Post by computer_user_au on 2007-07-06
Located an alternative solution via: [http://ubuntuforums.org/showthread.php?t=486394&highlight=remove+dual+boot]("http://ubuntuforums.org/showthread.php?t=486394&highlight=remove+dual+boot"). There is a super grub utility available [http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/") to help boot into the windows partition.

---

### Post by chrisfisehr on 2007-07-28
I have a Kubuntu 7.04 and Vista dual boot system.  Disappointedly, I have to uninstall Kubuntu because I could never get my Nvidia 6150LE graphics driver to configure properly (weird). I spent several days going through various solutions with no success. Moreover, I ended up seriously screwing something up because I can't even get Kubuntu to fully launch now.   Time to uninstall..........

I just completed the reconfiguring of my master boot record and removing Grub. It was even more simple than posted here.  You don't even need your Vista install disk. When Vista boots, there is an option (flashes quickly) to go straight to the Vista Recovery Console - no CD necessary.  I am going off of memory but here are the steps to do this:

1. Select the Vista Recovery Console at normal Vista startup
2. Select the Windows installation drive - you need to enter by number (not by drive letter)
3. Enter your admin password. I didn't have one so I just hit enter.
4. After #3, you seemingly are just sitting on a C: pathway (assuming C: is where the Vista install resides). However, Vista is waiting for your next command! Enter fixmbr, and hit enter... done! I did receive a Windows style warning not to do this if you were not experiencing problems.... 
5.  On restart my system booted straight to Vista.

I look forward to the next Kubuntu release later this year. I absolutely love how fast it runs on my system and could see me eventually only using Kubuntu. Given the huge amount of issues out there with graphics drivers, I have to say it is simply not ready for prime time just yet.

off to delete my Kubuntu partitions...

---

### Post by LuisPT on 2008-02-13
Great tip, this should go to a Fix Topic.

I installed Kubuntu, but now I want do uninstall it so I can make a clean install of Ubuntu Gutsy Gibbon :D

[B]Just one slight doubt:
How do I select the Vista Recovery Console at normal Vista startup (point one of your post)??.[/B]

When you say "off to delete my Kubuntu partitions...", you mean to go to Vista, access Disk Management and delete all Kubuntu partitions and format them in NTFS format, so we can use the option "Use the Large free space..." in Ubuntu install, right?

Thanks in advance for your help.

---

### Post by joeray on 2008-04-05
I want to do a complete wipe out of my ubuntu ultimate distro to try out kubuntu 8.04. I found a way to get rid of the grub loader with a vista-ubuntu dual boot set up that is very easy. Because I couldn't boot into recovery vista mode, I used recovery manager program in vista. Once os boots into recovery mode with manager on first page is an "advanced" option button-press it. On the menu option list is a "fix startup" option. I chose that and hit the proper prompts. That's it. Viola!! The next boot went directly into vista. No grub loader page option menu. I hope this works for everyone with vista. It just is too simple to believe. Thanks to all in the forums for lots of assistance in the past. It was nice to contribute for a change. Joeray says freedom is everything and is certainly not free!!

---

### Post by strydermed on 2008-07-19
If you are stuck in a dual boot with Ubuntu/VIsta or triple boot with Ubuntu/Vista/XP and want to remove Linux without affecting XP and /or Vista , there are many options..
If u have a Vista DVD, just boot off it and use the recovery console. Type *bootrec /fixmbr*
That's it you are done. If you don't have Vista DVD, then there are a few options. 
If you have deleted your Ubuntu partition from Windows you might that your system refuses to boot. Download Super Grub Disk and burn it to a cdrom, you can restore Windows after booting from that.
If you can boot into Vista then, there is a easy way. Just follow the steps below:
1. Download MBRFIX.EXE from [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx) 
2. Put it in your C or D drive. It does not matter where. Now right click on it and select security tab. Make it "Run as Administrator"
3. Type cmd in vista search box in start menu and right click it and select run Run as Administrator. 
4. In the command prompt go the directory where u have MBRFIX and now type *MbrFix /drive [COLOR="DarkOrange"]0[/COLOR] fixmbr /vista /yes* . This wont work without administrator permissions. Replace 0 with the number of ur drive. Just leave it if u have only one hard disk
That's it reboot and Vista boot manager will be back in  place of Grub. Now you can go into Diskmanager and format Linux partitions and reclaim the space

---

### Post by strydermed on 2008-07-19
VistaBootPro does not work in this situation, but you can use it to do lots of other cool stuff.

---

