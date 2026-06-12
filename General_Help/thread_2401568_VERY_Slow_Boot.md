---
title: "VERY Slow Boot"
date: 2018-09-19
forum: General Help
---

### Post by Quarkrad on 2018-09-19
Running Mate 18.04.  I have had to rebuild my dual boot machine and now have a clean install of / and /home of mate 18.04 with everything (sudo upgrade) up to date.  I have no other hds connected at the moment so everything is running off a SSD.  I have tried everything suggested on the web (e.g, adding noatime to fstab, checking win10 hibernation is off, etc,etc).  At the moment, from the grub screen, ubuntu is taking about 62sec to boot to the Desktop whereas win10 is taking about 14 secs.  Prior to the rebuild ubuntu use to boot quickly, never really timed it but always seemed pretty quick since installing the SSD - I cannot understand why it is now taking so long with a clean build.   The output of systemd-analyze blame is all in ms apart from **1.861s NetworkManager-wait-online.service**. Any help appreciated.

---

### Post by Autodave on 2018-09-19
Windows booting in 14 seconds is definitely not correct.  On my dual boot (8 core overclocked to 4.0, 8 gig RAM) Windows takes well over a full minute to boot.  Xubuntu about 15 secs.  Are you sure that *fast boot *was disabled?

---

### Post by Quarkrad on 2018-09-20
I think you are right - I'm on the win10 forum now trying to get the thing turned off - I see the win10 boot screen less than 1 sec after choosing win10 in grub.  It's proving very difficult to turn off.

---

### Post by Quarkrad on 2018-09-22
Looks like I'm stumped.  The guys on the windows forum cannot help me - I cannot turn off FastBoot.  Played about with my bios and if anything win is booting even faster - about 11s for win and 62s for ubuntu on SSD.  Appears MS reverses any settings in previous 1709 version so new 1803 version forces FastBoot.  To make matters worst - I have Windows10 Home which has limited options (change wise).  Thought about regressing to previous 1709 version but it seems many people (not all though) eventually get forced back up to 1803.  One of my reason for win10 is a live streaming application and having playing with it on a Ubuntu/VM the quality is not really there.

---

### Post by oldfred on 2018-09-22
There is fast boot which is an UEFI setting.
And there is fast start up which is a Windows setting.
Microsoft wants both on, since Windows is so slow booting.
And Windows updates, which may be in background, will turn fast start up back on. Grub then will not boot Windows & you will not be able to mount any NTFS partition read/write.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation) 
    
Best to also have fast boot off in UEFI. The system then does not check for hardware or configuration changes, assumes no changes so data already written to drive for operating system is correct & immediately starts system boot. But then you may not have time to press any key to get into UEFI or UEFI boot menu. Once configured & if you know the ways to get into UEFI if really needed, you can turn fast boot in UEFI back on. My motherboard has a setting for time, somewhat like grub, so I set for 3 sec. I do not think most systems have that.

What brand/model system?
What video card/chip?

---

### Post by Quarkrad on 2018-09-22
Thank you.   My pc is home built - the motherboard is a gigabyte H81M - DS2v (rev 1.0) and the onboard graphic card is Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06).  I hate to say this but I've been round all those pages - also, it was the tens forum that I went to for help.  This is typical of my problem:

Quote
You have to disable "Fast Startup" in Windows 10 Pro to solve this problem!

You can do this by going to "Control Panel -> Hardware and Sound -> Power Options -> Choose what the power buttons do -> Change settings that are currently unavailable"

Then scroll to the bottom of the window and uncheck "Turn on fast startup (recommended)" box. After that shutdown Windows 10 Pro.
Unquote

The is great but Windows 10 Home does not the option "Turn on fast startup (recommended)" - appears this check box is a Pro version thing.

When you say 'turn off in uefi' - if you mean in bios I have done that.

---

### Post by oldfred on 2018-09-22
Are you booting in UEFI or BIOS boot mode?

May be similar?
 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[[[http://www.rodsbooks.com/gb-hybrid-efi/|rod]]](http://www.rodsbooks.com/gb-hybrid-efi/|rod]])[[sbooks.com/gb-hybrid-efi/]]
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.

Also post link to summary report. You can add ppa to any working Ubuntu. 
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Quarkrad on 2018-09-23
Thank you - your help appreciated.  Frustrating for me because dual booting has been working fine until this last ubuntu rebuild (so it points perhaps to something I have done/is missing).  As far as I am aware I fully boot in uefi mode.  I added both amendments to grub but have commented out nomodeset as the graphics were all over the place.  I also do not think my motherboard has hybrid-efi - looks like  mine is prior that feature.  The link to my summary report is:  [http://paste.ubuntu.com/p/9Y5G8KCrnS](http://paste.ubuntu.com/p/9Y5G8KCrnS)
I have also attached some prints of my bios & grub that may, or not, be of assistance.

note:  difficulty attaching - will try in next post (was one of my ff addons!)

---

### Post by Quarkrad on 2018-09-23
here are the images

---

### Post by Quarkrad on 2018-09-23
Two more

---

### Post by HermanAB on 2018-09-23
Well, why do want to make Windows start slower?

Rather make Linux start faster and that is as simple as using suspend and hibernate.  With suspend, the machine should be ready to run in less than a second.

---

### Post by Quarkrad on 2018-09-23
I have Desktop pc and given the choice, would prefer to actually completely power down my machine rather than leaving it on - even if at a low level.

---

### Post by HermanAB on 2018-09-23
OK, then use hibernate rather than suspend.

---

### Post by oldfred on 2018-09-23
It looks like you have a setting for which video & it is on Intel, so do you change that when using nVidia? 
Screen 4 shows Intel vitalization & VT-D enabled. On my Asus I have those off.
I know that some Intel SRT or caching settings can cause issues.

Other than having some old BIOS boot bootloaders in MBR which will not work but are not used as long as you do not try to boot in BIOS boot mode, I do not see anything in Boot-Repair's report that looks out of place.

---

### Post by Quarkrad on 2018-09-23
I'm intrigued re me using nVidia.  I do not use nVidia graphics - I have no graphics card; I use the onboard intel graphics.  Do I have a config somewhere saying I have nVidia?  I have intel virtualization & VT-D enabled because I use Virtualbox - perhaps I do not need these enabled(?).

---

### Post by Quarkrad on 2018-09-23
SORTED - it was my usb card reader and extra USB ports on the front of my pc!  Oldfred gave me the lead by suggesting I turn off *Quiet Splash* in grub - this enabled me to see where in the boot process there was a slowing down.  I noticed *USB1-7  usb device descriptor read/64, error -110* - that appeared a number of times.  This gave me the clue to disconnect these devices from my motherboard - ubuntu now boots to Desktop in 8s.  I have reconnected and the boot time is unaffected so it was related to bad connections to the motherboard.  Thank you to all that have helped me with this issue.

---

