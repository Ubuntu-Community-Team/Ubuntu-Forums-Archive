---
title: "Unable to install ubuntu a second time."
date: 2013-12-05
forum: General Help
---

### Post by aggrokidd on 2013-12-05
Hi guys,

I am very not a tech-savy guy, but I gave a shot at Ubuntu a week ago. I bought a Live-CD on ebay, the 12.04 version. The first time I installed it, it went like a charm. I booted it alongside windows 8. When I inserted the disk, it first pre-installed couple things, then it restarted the computer and the real installation took place until I give myself a username, a password. Then I was set. After that, I restarted my computer it thought it would be super easy to go on windows, but I had the purple screen and couldnt go on windows. Until I found about how to start Bios, then I went it the Boot section and selected EFI instead of legacy mode. After that I emptied the partition where I thought Ubuntu was located. On a F: disk that wasnt there before. At that point I thought ubuntu wasn't there anymore. Now, for a particuliar reason I need to use ubuntu again so today I thought I would just run the CD again and everything would work out like the last time. Well it didn't. And I spent the entire day trying to install it. The only step I was able to achieve all day was the pre-installation on windows. I was inserting the disk on windows, it was pre-instaling a couple things which was taking like 10 minutes, after that I had to restart my computer and BAM, every ****ing time I was hitting a wall immediately after the initial lenovo picture I first get when I turn on my laptop. The wall was the following: error unknown filesystem grub rescue. I looked everywhere on forums and people often had that error, but I think it was not at the same moment. Me it's not when I try to boot it, it's when I'm installing it and it's right at the beginning. Anyway while trying different stuff I looked at my partitions on windows and found 2 other partitions who were ubuntu-related so I deleted them and now they are one 171GO partition formated exfat. I dont really know how I should format those so I tried everything. NTES partition, Raw partition etc. When I started messing with the partitions and tried to install ubuntu, at one point unknown file system error grub rescue message wasn't there anymore. One time it was [COLOR=#333333][FONT=Ubuntu]"no such partition[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]".. after that it was only a blinking underscore and now with the 171GB exfat partition what I get when I restart the laptop to install Ubuntu is the letter [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]"[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]e[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]" with a blinking underscore. Remember that all those messages are right after I restart my computer to install ubuntu. I can't even begin to install it. I tried changing couple things in Bios like disable secure boot but nothing worked.
I really have no clue what to do anymore. If that could help, this is how my partitions are setup: 1000Mo recovery partition(can't touch) , 260Mo EFI system partition(can't touch) , 1000Mo OEM partition (can't touch) , Windows8_OS 247.15Go (C : NTFS partition (dont think I need to touch) , 171.28Go exFAT partition including the old ubuntu partitions and Lenovo (D : 25GO NTFS principal partition (Can't touch). Finally under that obviously there is the ubuntu 12.04.2 live-CD partition in CD-Rom 0 , 693Mo CDFS in E: .

Wow that was long. Thank you for those who take the time to read. Ive been trying to re-install ubuntu all day, tried alot of things and looked on pretty much every ubuntu forums post who seemed to have the same problems I did but like I said they all seemed to have problems further in the process than me so I'm at the point where I need to come here by myself and post my problem since it seems like alot are differents with different cause. If you have some infos that could help, it would be more than welcome.

And I'm my first langage is french so sorry if some parts are unclear.

Thanks[/FONT][/COLOR]

---

### Post by fantab on 2013-12-06
Boot with your Ubuntu CD and "Try Ubuntu Without installing", open Terminal [ctrl + alt + T], run the following and post its output:
```
sudo parted -l
sudo fdisk -l
```

Also post a Screenshot of your HDD and its Partitions from Windows.

Tell us more about your desktop/laptop hardware, like CPU, RAM, Graphics Card, Brand/model, etc.
Did Windows 8 came pre-installed with the computer? if you installed it, how did you do that? What mode does it use to boot, UEFI or Legacy/CSM?
Have you disabled '[FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")' in Win8?
Have you disabled '[Fastboot]("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm")' in UEFI/BIOS?

---

### Post by Bucky Ball on 2013-12-06
Welcome. Please use paragraphs! Many people will just not bother reading the 'big black blobs' of text (including myself). This will improve your chances of getting help as it gives your support request some clarity. Thanks. ;)

---

### Post by aggrokidd on 2013-12-06
Hi fantab,

Like I said, I can't boot and [COLOR=#000000]"try without installing[/COLOR][COLOR=#000000]" because I can't make it to that point. When I insert the Live-CD on windows, it tells me that I can just try it and not install it, so I click on that then it says we will need to restart the computer so I do that. Before it restarts it pre-install stuff during 9-10 minuts and then they say you are ready to restart and install it. 

[/COLOR][COLOR=#000000]So I restart it, then I have a message that says windows cannot run ubuntu/blabla can't remember exactly that page but that issue I can resolve it. It did this the first time too. I just need to press esc. , then the BIOS menu appears, I go to [/COLOR][COLOR=#000000]"boot[/COLOR][COLOR=#000000]" and replace EFI by legacy support or something like that. The first time, just doing that resolved everything! Then I was able to install ubuntu and run it. 

This time though it is different. I am guessing it's because of the partition. I may not have deleted my last ubuntu properly or something like that you know because if I did, it would work again. Nothing changed since the last time(one week ago) except that. So now after I choose legacy support in BIOS and save changes with F10, it restarts, I see my Lenovo picture for 3-4 seconds (the brand of my laptop which is the first thing that show up when I turn on my computer) and this time instead of installing and everything, all I see is the letter [/COLOR][COLOR=#000000]"e[/COLOR][COLOR=#000000]" with a flashing underscore. I can't go further than that.

So that would make me unable to [/COLOR][COLOR=#000000]Boot with my Ubuntu CD and "Try Ubuntu Without installing" right? Correct me if I am missing something.

Here is a screenshot of my partitions [/COLOR][IMG]http://i44.tinypic.com/2n74f9d.jpg[/IMG]

My laptop is a Lenovo IDEAPAD N580. CPU RAM graphic cards don't have much clue tbh.

And yes, windows 8 was pre-installed with the computer. As for the mode it uses to boot, I'm not sure but I think it would be UEFI with what I write above?

For the disabling of Faststartup in Win 8 and UEFI/BIOS I'll go to sleep it's very late and I'll try it tomorrow. Plus I'll see what you think from the clarifications I made and maybe something else with do it.



And thanks for the welcome Bucky, I tried to create a little more space this time :)

---

### Post by fantab on 2013-12-06
The problem you describe sounds like you need to disable 'Faststartup'. Faststartup is a Win8 feature which is some sort of Hybrid Hibernation. This won't let your Win8 'shutdown', even after you think you've shutdown. Disabling it will let you to actually shutdown the PC.
Check those links I have posted in my earlier thread and report back...

---

### Post by codenine75a on 2013-12-06
It looks like you have a valid internet connection since you are posting here.  Why not try to get a frest copy from the ubuntu site instead of buying burned copies from ebay.  Ah, you are French and I do not know the laws in France about downloading digital media.  There may be a problem with squeezing your copy of Ubuntu on your rig to work with Windows.  For those set ups, I recommend installing the OS on a fresh drive instead of sharing one.

---

### Post by oldfred on 2013-12-06
New systems need  the newest UEFI and Ubuntu has updated it a lot. Also vendors are updating their UEFI so confirm that your UEFI/BIOS is current.

So as suggested above better to download most current version of Ubuntu or 13.10 or 12.04.3. But even 12.04.3 does not have all the newest updates to UEFI and in Jan 12.04.4 will.

Since you are modifying partitions, you best do a full backup of your efi partition and your main Windows install.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And it is really a good idea to have a Windows repair flash drive.

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

For more info on installing with UEFI see all the links in my signature.

---

### Post by aggrokidd on 2013-12-06
I tried to disable fast startup and it didn't change anything. Still can't go further than that blinking underscore right when I turn on the computer to install it. So according to you guys the partitions are setup ok? Is there any place I should look for remaining Ubuntu pieces that I could delete so that everything is gone and I can boot it successfully like the first time?

---

### Post by oldfred on 2013-12-06
Lenovo Community Bios Access
[URL="http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2"]http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2

[/URL]
 screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[URL="http://ubuntuforums.org/showthread.php?t=2117760"]http://ubuntuforums.org/showthread.php?t=2117760

      [/URL]
  [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
    [URL="http://ubuntuforums.org/showthread.php?t=2117760"]
[/URL]

[URL="http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2"]
[/URL]

---

