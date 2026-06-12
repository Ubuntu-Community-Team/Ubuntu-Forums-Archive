---
title: "Dual Ubuntu/Windows Notebook crash while updating Windows"
date: 2020-01-30
forum: General Help
---

### Post by Richard_York on 2020-01-30
My HP Notebook has been running Ubuntu 18.04 on dual boot with Windows quite smoothly since 2018. (I must add that installing Ubuntu this way represents the outer edge of my technical ability!)
Because I use Windows only very occasionally, it needs to update itself each time. This takes a while but usually works perfectly. When it gets to the stages where Windows re-starts itself, then because I can't watch it permanently it comes up with Ubuntu and I just prod it back into Windows mode, when it carries on installing and updating.

This time, on the second re-start, instead I got 

[B]error: unknown filesystem.
Entering rescue mode&#8230;.
grub rescue>[/B]

  
and it stayed that way for several hours.  So powering off/on was the only way to get any change.   
Pressing Esc at that stage gets me 

  [B]F1 System Information
F2 System Diagnostics

F7 HP SpareKey
F9 Boot Device Options
[/B]
**F10 BIOS Setup**
**F12 Network Boot**
**ENTER - Continue Startup**
 
 
  but pressing Enter just gets back to the first message. System Diagnostics went round a memory test, and appeared to be simply re-running the same tests over and over.  I haven't tried the others.

If need be I can ask my local computer mending shop to reinstall Windows, and then I fresh install Ubuntu to dual boot as before, but I guess I'd lose everything on the machine. (No very important data files, just things set up the way we like, so a nuisance.)

If there's a better, maybe cheaper way, within my skill level, I'll be very grateful for advice here.

Thanks.

                        Notebook Model -  HP ProBook 4530s
 Processor Type -  Intel Core i3-2330M CPU
 Processor Speed &#8211; 2.2GHz
 Memory &#8211; 4096 MB RAM

---

### Post by yancek on 2020-01-30
So what happens when you select F9 for boot options?  Do you have an option to boot Ubuntu or windows and do either boot?  If not do you have an Ubuntu or other Linux live system to boot to get more detailed information?

Windows major updates usually require several updates so before doing it you could set windows to the default boot until the update is finished.

---

### Post by Richard_York on 2020-01-30
F9 gives me a Header "Boot Error" and a stack of bars offering:  

[B]Notebook Upgrade Bay (UEFI)
OS Boot Manager
Boot from EFI File
Notebook Hard Drive
Notebook Upgrade Bay
Notebook Ethernet[/B]

What you say makes sense if I can get into it.  I'm always reluctant to press buttons hopefully but ignorantly, to see what happens, in case I get into deeper water!
But I tried "OS Boot Manager". This results in:

[B]An error occurred with the boot selection. 
verify media is present and retry

[/B]I don't know what media it wants here.
Thanks.

---

### Post by dragonfly41 on 2020-01-30
I was waiting for the UEFI S.W.A.T. to arrive before making suggestions since I am not immune to such boot errors myself.

In your shoes I would ..

boot up with LiveUSB - select the LiveUSB device from F9 Boot Device Options
"Try Ubuntu" rather than "Install Ubuntu" ..[COLOR=#ff0000] important!

[/COLOR]When you are "Trying" Ubuntu install into LiveUSB boot-repair (have the PPA instructions handy)

Run boot-repair and you should keep note of the pastebin link.

Reboot.

---

### Post by yancek on 2020-01-30
I have an HP Notebook and the options OS Boot Manager and Notebook Hard Drive should boot windows 10.  Try highlighting and selecting the Boot from EFI file and see if you can find anything related to Ubuntu there.  Any option you select with the F9 is a one time change and will not repair problems with the bootloader(s) and the next time you boot you will need to use the same process until booting is repaired.  Also, you have not indicated whether Ubuntu or windows boot, I'm guessing neither?

The link below is to the boot repair software suggested above.  As recommended, go to that site from the Ubuntu install usb, read through the page then select the 2nd option described on the page, using the ppa and when you run boot repair make certain that you select the Create BootInfo Summary option and do NOT try any repairs.  When it finishes, it will give you a link you can post here and people will be able to access it and hopefully suggest a solution.

---

### Post by Richard_York on 2020-02-01
Thanks for these replies. Forgive a slow response - work got in the way.

I tried  selecting "Boot from EFI" and all I get is **Select File System  **and nothing else - no options  on an otherwise empty screen.

Ubuntu or Windows boot - at present, as you say, neither! It normally offers me the option, and if nothing is chosen, goes ahead with Ubuntu, but it's not getting that far, just giving the "grub rescue" message I quoted in post #1

When you write "the link below is to the boot repair...."     I'm not seeing a link below, should this be on your message, or something appearing on my screen?

Dragonfly41, I may well try this method in due course. I'd have to make a new LiveUSB first. Meanwhile I can see Yancek's point that I'd be stuck with it permanently.

---

### Post by westie457 on 2020-02-01
This is the link @yancek was referring to. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

As advised earlier 'do not attempt repairs' yet because automatic repairs sometimes causes other issues.
For now we just need the link to the 'pastebin' boot report.

---

### Post by Impavidus on 2020-02-01
OP hasn't told us what Windows version is on his computer. Now, I also have an HP Probook 4530s (although with an i5 CPU and no Windows) and if that's of about the same age (bought in 2011) it probably uses bios mode and Windows 7 (but maybe upgraded to a later Windows version). The boot info summary may give more details. What happened most likely is that Windows deleted the Ubuntu partition. With the Ubuntu partition gone, grub can no longer find the files it needs. There's a bug in Windows that can delete the Linux partition if that's the first logical partition. The data should still be there and it's probably possible to recover the partition with no need to reinstall. See [this link](https://help.ubuntu.com/community/DataRecovery) and read the part about Lost Partition. The command```
sudo fdisk -l
```executed in the live session can give a good estimate of where the partition used to be. This information is also in the boot info summary.

---

### Post by Richard_York on 2020-02-01
It' was on Windows 10. I bought it second hand so can only guess that's an upgrade.

Whichever course I take, it seems I need to create a new USB live stick. I will do that & come back... but why do these things happen just when one has least time to get involved in fixing ?!
Thanks for your patience and help.

---

### Post by yancek on 2020-02-01
Based on your last post, it does not seem that you have an EFI install so possibly an upgrade from windows 7?  Selecting boot from EFI file should give you an entry No Volume Label and highlighting that and hitting the Enter key should give you the option EFI and System Volume Information.  Highlighting EFI and hitting Enter should then give you several options for Microsoft, Boot and in your case Ubuntu.

---

### Post by Richard_York on 2020-02-01
Sadly it doesn't get that far - "Boot from EFI" option gives me "Select File System" in white on a grey bar across the head of the screen, then in smaller letters on the otherwise blank white body of the screen, "Select File System"  again.
Nothing else.
So do I go ahead & create a new live USB stick?

---

### Post by Richard_York on 2020-02-01
USB duly created.
Given the number of cautions I'm seeing, I'm  inclined to be very cautious! 
So I insert the live USB, run from there,  and in Terminal type
sudo fdisk -l


Then report back with what it shows, yes?

---

### Post by Impavidus on 2020-02-01
Yes, that's it. You can also run boot-repair and create the boot info summary, nothing else. Don't run the recommended repair. Boot-repair will run some diagnostic commands, including fdisk -l, to show us the status of your computer.

---

### Post by Richard_York on 2020-02-01
I started up the Notebook on USB live, in "Try Ubuntu" mode, and typed sudo fdisk -l into the terminal.
The read-out is quite long. 
Not knowing which bits are important, here it is in entirety. (copy & paste via "Libre Office" )

How do I run boot-repair and create the boot info summary, please? Is this to be typed into the terminal as well?
Thanks.

I got:

ubuntu@ubuntu:~$ sudo fdisk -l
 Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0xfd67cd6e
 
 
 Device     Boot     Start       End   Sectors   Size Id Type
 /dev/sda1  *         2048   1126399   1124352   549M  7 HPFS/NTFS/exFAT
 /dev/sda2         1126400 498121861 496995462   237G  7 HPFS/NTFS/exFAT
 /dev/sda3       498122752 499404799   1282048   626M 27 Hidden NTFS WinRE
 /dev/sda4       499406848 976771071 477364224 227.6G 83 Linux
 
 
 
 
 Disk /dev/sdb: 3.8 GiB, 4009754624 bytes, 7831552 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x663eb4c4
 
 
 Device     Boot   Start     End Sectors  Size Id Type
 /dev/sdb1  *          0 3815135 3815136  1.8G  0 Empty
 /dev/sdb2       3737268 3741939    4672  2.3M ef EFI (FAT-12/16/32)
 
 
 
 
 ubuntu@ubuntu:~$ sudo fdisk -l

---

### Post by yancek on 2020-02-01
I doubt you will find any better instructions on using boot repair than those on their site.  Use the 2nd option explained on the page then launch boot repair using either of the two method explained under Using Boot Repair then click on the tab in the window Create BootInfo Summary.

---

### Post by Impavidus on 2020-02-02
Here is the important part:
> **Richard_York said:**
> 
 Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0xfd67cd6e
 
 
 Device     Boot     Start       End   Sectors   Size Id Type
 /dev/sda1  *         2048   1126399   1124352   549M  7 HPFS/NTFS/exFAT
 /dev/sda2         1126400 498121861 496995462   237G  7 HPFS/NTFS/exFAT
 /dev/sda3       498122752 499404799   1282048   626M 27 Hidden NTFS WinRE
 /dev/sda4       499406848 976771071 477364224 227.6G 83 Linux
You do not suffer from the most common cause for your symptoms. All your partitions are still there and fill the entire hard drive. You use bios booting and you've got four primary partitions on an mbr partitioned drive. That's not very flexible, but it works and is hard to change, so keep it like that. Somehow grub's second stage has gone missing though, and boot-repair may be able to give more details.

---

### Post by Richard_York on 2020-02-02
It will take me a while to digest this, and act on it. With other stuff going on, this may take a few days. But I'll be back on the case.

---

### Post by Richard_York on 2020-02-07
[SIZE=2]Forgive the pause for a very busy week.

I opened the "Try Ubuntu" option from my USB, then typed, as in the 2nd option on the Boot-repair page: [/SIZE][SIZE=2][/SIZE]
    sudo add-apt-repository ppa:yannubuntu/boot-repair

What I get back is: 

Cannot add PPA: 'ppa:~yannubuntu/ubuntu/boot-repair'.      
ERROR: 'ppa:~yannubuntu' user or team does not exist.

Is something in this out of date, maybe, or did I type the wrong thing? I notice it's added an extra "ubuntu" into the ppa.
I tried typing this several times in case of typos caused by end of week tiredness, but I get the same each time.

---

### Post by coffeecat on 2020-02-07
> **Richard_York said:**
> 
I opened the "Try Ubuntu" option from my USB, then typed, as in the 2nd option on the Boot-repair page: 
    sudo add-apt-repository ppa:yannubuntu/boot-repair

What I get back is: 

Cannot add PPA: 'ppa:~yannubuntu/ubuntu/boot-repair'.      
ERROR: 'ppa:~yannubuntu' user or team does not exist.

Try connecting to the internet. That's the error you get if you are not connected.

By the way, there is no need to add size=2 BBCode tags to your text. The forum software defaults to size 2. Just type your post, and limit your use of non-standard font options for highlighting purposes.

---

### Post by Richard_York on 2020-02-07
Thank you for this very tactful reply, much appreciated! (So used to the HP being connected I forgot that was broken too!)

The result of BootInfoSummary is
[http://paste.ubuntu.com/p/6TycBgDW6C/](http://paste.ubuntu.com/p/6TycBgDW6C/)

This is mostly unintelligible to me, but I look forward to advice on what action to take.

---

### Post by Richard_York on 2020-02-10
With apologies for re-posting - here's the BootInfoSummary link: [URL="http://paste.ubuntu.com/p/6TycBgDW6C/"]http://paste.ubuntu.com/p/6TycBgDW6C/   

[/URL]I will be very grateful for any advice, please. 

If having read it, you reckon it's too mangled, and it's best to simply cut my losses, I'll take the Notebook to my local dealer for a Windows re-install, after which I'll re-install Ubuntu, We'd be sad to lose stuff that's on there, but we'd like to be able to start using the machine again.

Or if you think it's something I can sort out with advice from these forums, I'll be delighted, and will get to work here.

With thanks

---

### Post by dragonfly41 on 2020-02-10
I resort now to posting links to other clips I have written recently on trying rEFInd as an alternative to grub.

[post#3 in this thread]("https://ubuntuforums.org/showthread.php?t=2436555").

Worth a try.

---

### Post by Richard_York on 2020-02-10
Thank you Dragonfly41.

I guess from this that the BootInfoSummary doesn't lead to a clear "do x and y will follow" course of action then?

And while I've looked at the posts you kindly link to, I admit I'm instantly way out of my depth there - they are written for those with deeper understanding than mine. 

I suspect this confirms that I'm stuck with the "take it to the dealer and start again" line.

---

### Post by dragonfly41 on 2020-02-10
It can be daunting but if you have nothing to lose try these steps:

[1] Run these commands

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

[2] Reboot

[3] Look for rEFInd in boot options and place this at top.

[4] Boot into rEFInd boot option.



[P.S.] to answer this point ..

> [COLOR=#000000]clear "do x and y will follow" course of action[/COLOR]

Clips read from your boot-repair log

[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


[COLOR=#666666]===================[/COLOR] Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda4 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

---

### Post by Richard_York on 2020-02-10
Thanks for these clear steps, which I'm trying.

When I get to        [2] Re-boot and [3]  place rEFind at the top,      should I have the Ubuntu Live USB in or out?

---

### Post by Richard_York on 2020-02-10
Thanks for these clear steps, which I'm trying.

When I get to        [2] Re-boot and [3]  place rEFind at the top,      should I have the Ubuntu Live USB in or out?... or does that make no difference?

---

### Post by dragonfly41 on 2020-02-10
[COLOR=#000000]> or does that make no difference?

preferably unmounted and out to avoid it being an unwanted boot option.[/COLOR]

---

### Post by Richard_York on 2020-02-10
Trying this, step [1]  appeared to go well.
 On Rebooting  I get  options:
 Notebook upgrade Bay (UEFI)    / OS Boot Manager   / Boot from EFI File   /  Notebook Hard Drive  / Notebook Upgrade Bay  / Notebook Ethernet / 

but not rEFInd

(edit 1)  It strikes me that in switching off to re-boot I might have lost the installation? 
I'll try it again from step [1]

(Edit 2, a ) ... which was maybe an unwise step, since it's now just sitting there failing to install anything now while the "ubuntu" logo & coloured dots sit there, the dots changing colour but not getting anywhere, after 10+ minutes...

---

### Post by yancek on 2020-02-10
Your boot repair output from post 21 clearly shows that you have a Legacy install of both Ubuntu and windows 10 on an msdos drive.  I'm not sure what is going on here but you do have Grub in the MBR which is correct for a Legacy install.  You also have the grub.cfg file on the Ubuntu partition with an entry for windows which points to the correct partition.  Problem is, look at the very top of boot repair and you will see "looks for (,msdos3)/boot/grub".  Scroll down and you will see that sda3 (which is equivalent to msdos3) is a windows partition with an ntfs filesystem.  That will never work.  Not sure how that happened but if you want to try, you could boot the Ubuntu install media and create a mount point for sda4, then mount it and go to the /boot/grub/grub.cfg file using a text editor as root (use sudo) and put the correct entry there.for the Ubuntu menuentry(s):  set root='hd0,msdos4;    See the link below which explain Grub2 naming conventions which would explain your problem but not how it was accomplished?

    [https://docs.oracle.com/cd/E36784_01/html/E36801/gkvii.html](https://docs.oracle.com/cd/E36784_01/html/E36801/gkvii.html)

The UUIDs for the Ubuntu menuentries as well as windows are correct so you should just need to change the above.  I'm not sure why you chose to install windows and Ubuntu in the older Legacy mode.  If you want UEFI and a GPT drive the instructions at the Ubuntu site below explain that process.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by dragonfly41 on 2020-02-10
There are other reports of "coloured dots" in this forum .. boot stuck

I would try running LiveUSB again and remember that it is not persistent and so you will need to go through the rEFInd installation commands again.

After reinstalling rEFInd run this command while in LiveUSB "Try Ubuntu" mode.

efibootmgr -v

and post output here.

[P.S.] Since yancek chipped in first, try that advice first. rEFInd and grub can coexist.

---

### Post by Impavidus on 2020-02-10
> **yancek said:**
>  Problem is, look at the very top of boot repair and you will see "looks for (,msdos3)/boot/grub".  Scroll down and you will see that sda3 (which is equivalent to msdos3) is a windows partition with an ntfs filesystem.Well spotted. Boot-Repair's default repair should fix that. It appears that Ubuntu was originally installed on sda3 (so says the comment in /etc/fstab) and now lives in sda4, and the UUID is still correct. I know that Windows can accidentally delete the Ubuntu partition during upgrades, but moving it to the next entry in the partition table is new for me.

Other than that I see no problems in the Boot-Repair summary.
> I'm not sure why you chose to install windows and Ubuntu in the older Legacy mode.
My guess is Windows was already installed in that mode when the computer left the shop all those years ago, before it was upgraded to Windows 10.

---

### Post by Richard_York on 2020-02-10
Thanks for all these and your patience. You'll realise the discussion of partitions, Legacy mode, etc, mostly goes over my understanding level.

Indeed I bought the machine within the last couple of years, so Windows 10 had indeed already been set up as an upgrade before it came to me. 
When installing Ubuntu I am still a beginner driver, following instructions without understanding why, so may have set up its partitions in a way you'd avoid.

Meanwhile, I have reinstalled rEFInd 
Along the way it asks me whether to install it to the EFI system partition (ESP), and I accept the default "Yes" here.

Typing
efibootmgr -v
results in
EFI variables are not supported on this system.

Typing 
sudo reboot

gets me into a loop.... I admit to trying all this through a haze of a heavy cold bug, so even less comprehending than usual ! but from there I get a black screen with "Please remove the installation medium, then reboot" top left.

As far as I know, the only way of doing that is to lean on the power switch and start again, which loses me the rEFInd installation, of course.

I've tried this a few times now,

[Edit}.... and after 15 minutes or so, it briefly added more lines on screen, went into the HP splash screen and offered the ESC option  so quickly that I missed it!
I'll try again, and sit and watch longer this time....

---

### Post by Richard_York on 2020-02-10
Ok, I  caught it  in time eventually. I am again offered 
Notebook upgrade bay (UEFI)  / OS Boot manager / Boot from EFI  file /  Notebook hard drive / Notebook Upgrade Bay / Notebook Ethernet. 
But no rEFInd.
It is tempting to try EFI file option in case rEFInd is in there. Or maybe my earlier result from 
efibootmgr -v means I don't have that option.

---

### Post by dragonfly41 on 2020-02-10
Good to see that you have the grit to navigate through these obstacles.

I will try to answer the points relating to [rEFInd]("https://ubuntuforums.org/rEFInd.html") (bearing in mind that you are learning).

The report from running efibootmgr

“EFI variables are not supported on this system”.

confirms that you are running in Legacy mode and not EFI mode. This was also confirmed by your last boot-repair report.

***Progress cannot be made with [rEFInd]("https://ubuntuforums.org/rEFInd.html") until you have your boot set to in EFI mode instead of Legacy mode.***

> Along the way it asks me whether to install it to the EFI system partition (ESP), and I accept the default "Yes" here.

This simply installs [rEFInd]("https://ubuntuforums.org/rEFInd.html") files in your ESP partition in /dev/sda.

I take it from post#1 that cost might be an issue.

“If there's a better, maybe cheaper way”

My question is do you have a spare drive in an external container lying around somewhere? If yes, we can get Ubuntu up and running and return later to Windows.


Researching your HP ProBook 4530s (listed in post #1).

[https://superuser.com/questions/1034108/does-hp-probook-4730s-have-uefi-or-bios](https://superuser.com/questions/1034108/does-hp-probook-4730s-have-uefi-or-bios)


Now if you go into Boot Settings and set BIOS to **UEFI mode**, **Secure Boot off**

yaneck back in post #5 and post #10 suggested setting EFI mode.

But in post #11 you confirm that you cannot do this. And so the thread forked into boot-repair discussion.

I would persevere until you can set EFI mode in boot options.

Then you can take off from that airstrip.  [rEFInd]("https://ubuntuforums.org/rEFInd.html") will follow. Windows will follow. Concentrate on booting up Ubuntu.

---

### Post by Richard_York on 2020-02-10
Thank you for this encouragement! 
Cost is relevant but if going to the shop is needed for Windows Reinstallation, not unbearable.
I have an external hard drive, yes, with enough capacity to swallow everything on the HP notebook.
I will return to this tomorrow. The germs are currently shutting down any hope of following instructions just now!

---

### Post by Richard_York on 2020-02-11
I understood  just enough of that superuser discussion of HP Notebooks to realise that mistakes could render my machine unusable, so am going cautiously.
F10 BIOS setup from Start-up menu offers options but I am not finding UEFI mode with secure boot off.
Random experiment seems unwise here.

---

### Post by dragonfly41 on 2020-02-11
I have no experience with HP and my understanding comes from just researching the subject.

  Updating the BIOS might be beyond your ken.

[https://support.hp.com/gb-en/document/c00034791](https://support.hp.com/gb-en/document/c00034791)


I would post a message to HP Support (after collecting information about your HP ProBook 4530s)

"How do I make my HP ProBook 4530s laptop UEFI compatible?"


You wrote in post #1 ...

> If need be I can ask my local computer mending shop to reinstall Windows

but I suspect that they might be stringing you along as a return customer. They should have provided you with a Windows recovery disk so that you should have no need to go to the mending shop to reinstall Windows.

Given that you can run LiveUSB a Windows reinstall can be downloaded (if really necessary).

I suspect that a BIOS reset might restore UEFI but check with HP. Or try the recommended boot-repair to try to fix (sans UEFI). You can launch LiveUSB, and install and run boot-repair - going beyond just giving the report.  See also Advanced Boot Options tab in boot-repair GUI. Unfortunately you need to do this each time in LiveUSB since boot-repair has to be re-installed each session.

Coming back to the last idea to add an external bootable drive (you confirmed that you have one), attach that to your laptop and in LiveUSB session inspect all disks with Disks or Gparted. I would then copy any files you wish to retain and then using Gparted, partition the external drive for Ubunti installation. I would create the first partition in this external drive as local ESP (500 MB in size).

---

### Post by Richard_York on 2020-02-11
Thank you - as ever, I'm extremely impressed by the patience and helpful  thoroughness of those on this forum.

This sounds like an avenue worth exploring. 
In fairness to my local computer guy, he did suggest when I bought the machine that I could download and install Windows  myself if ever it crashed, but I lack confidence in this!

Again, thanks.

---

### Post by dragonfly41 on 2020-02-11
Stick with the HP advice to reinstall Windows in your primary drive.

[https://support.hp.com/gb-en/document/c03330139](https://support.hp.com/gb-en/document/c03330139)

And in parallel (or later) install external Ubuntu using LiveUSB.

rEFInd can follow when you have UEFI enabled.

---

### Post by yancek on 2020-02-11
I'm not sure why you are bothering with rEFInd as your boot repair output in post 21 clearly shows that you have NO EFI installation of EITHER ubuntu or windows.  Your computer is EFI capable but your installs are not EFI.  Do you have Legacy/CSM booting enabled in the BIOS?  Did you make the change to the /boot/grub/grub.cfg file I suggested above since you have it pointing to the wrong partition? Do you know how to do that?   If you want to use UEFI, you would need to convert the drive to GPT and convert both windows and Ubuntu to UEFI and that will be a complicated process.

---

### Post by Richard_York on 2020-02-15
I am truly grateful for all the careful and helpful replies here. 

I have to confess that between my germ-ridden brain, the need to have the machine working again, and the realisation that the remedy was getting more and more out of my depth, I ended up paying for a Windows re-installation. Luckily "Try Ubuntu" gave me access to all the documents, if not the settings, so they're safe.    And if I'd been thinking clearer I could possibly have unloaded the settings too.

 I've re-installed Ubuntu18.04 in dual boot again, while allowing Windows a bigger partition than it had, in case I'd helped it to crash by not leaving it enough headroom when updating.

I'll mark this as solved. 
Thanks again. I think it's the first time I've not been able to turn advice here into success, and that's not your failing.

---

