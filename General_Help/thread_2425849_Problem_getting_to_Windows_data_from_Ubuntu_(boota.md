---
title: "Problem getting to Windows data from Ubuntu (bootable USB) after HD failure"
date: 2019-08-31
forum: General Help
---

### Post by doggo on 2019-08-31
Looking for a bit of help with a couple of problems - I've searched the forums but can't find quite the right answers.

I was an Ubuntu user for years, then unfortunately ended up back in Windows for a variety of reasons, but I've got a situation now where my six-week-old laptop (running Windows 10) has some kind of hard drive issue and won't boot. As it's under warranty, my plan is to just get the HDD replaced, but before I do I want to get some not-yet-backed-up data off there, if possible. So I've created a bootable Ubuntu on a USB stick and (despite a screenful of error messages before booting) it seems to work fine. In fact, it all feels so lovely that I'm now determined to go back to Ubuntu as soon as this is sorted. But first, I've got to sort this out and I've got two main problems. I was only ever a basic-level Ubuntu user, so please pitch any replies at one notch up from beginner level...

1. I can't seem to get at my Windows data. When I open Disks, along with the USB and the CD drive, it shows a 1TB hard drive (which is weird, because my hard drive is 2TB) with the option to mount it greyed out. (For what it's worth, I had no problem mounting and accessing an external hard drive.) In the command line, the hard drive showed up as dev/sdb but when I tried to mount it that way I just got a bunch of superblock errors. All this would make me think the thing is just totally corrupted - and if my hard drive is now a brick, I can live with that - but at the top of Disks the assessment is that the drive is OK. Considering the computer is only six weeks old, that makes sense. But I can't get into it. Please can anyone help me get to the files via Ubuntu? I don't really know what to do next.

2. I can't get online in Ubuntu. The wifi just doesn't show up. This obviously isn't a problem in terms of accessing my files, but it makes it impossible to use apt-get if I need it, and will make it a massive pain to copy command line output here if required. (I suppose I could copy it into a text editor, transfer that to a second USB stick and load it into the old laptop I'm using now.) I know this is a known problem with HP laptops - which is what mine is - but I couldn't actually find a solution anywhere.

Thanks in advance if anyone can help me out here. I'd really appreciate it.

---

### Post by SeijiSensei on 2019-08-31
I recommend downloading and booting from a [System-Rescue-CD]("http://www.system-rescue-cd.org/") ISO image. It includes the testdisk program which is designed for your problems.

Alternatively, you could try installing testdisk after booting from an Ubuntu ISO image and Try Ubuntu using "sudo apt install testdisk".  

If you cannot get online with wifi, do you have an Ethernet cable that you could use to connect the laptop directly to your router?  If not, they cost as little as $5 at [Amazon]("https://www.amazon.com/AmazonBasics-RJ45-Cat-6-Ethernet-Patch-Cable-5-Feet-1-5-Meters/dp/B00N2VILDM/").  Everyone who uses networking should have at least one Ethernet cable around for just these situations.

---

### Post by ajgreeny on 2019-08-31
If your Windows OS crashed or was part way through booting and then gave up, it is possible that your live Ubuntu is seeing the ntfs partition as still in use, thereby making it impossible to mount using a Linux OS; this is to avoid damage to the filesystem.

I do not , unfortunately, know of any safe or certain way of overcoming that situation other than by using a Windows OS to attempt a repair of the disk in question. You could try the package ntfsfix in the live ubuntu but I have no experience of that, so wait for other responses before doing anything drastic which could leave you in bigger trouble than you already are.

I assume you have tried booting to safe-mode, assuming that is still an option in Windows 10, about which I know nothing; XP was my last real use of a Windows OS.

---

### Post by doggo on 2019-08-31
Thanks for the quick replies. I do have an ethernet cable so I can try that. Not sure why it didn't occur to me...

Windows 10 is funny about Safe Mode. But I've looked up how to get into Safe Mode and it won't work anyway. I can get into a pre-boot system check, which first told me that there was no hard drive installed (which suggests it's definitely failing) and then later told me that there was a hard drive installed, but the disc test freezes at 99% every time. Not much help. Safe mode is definitely not working though.

---

### Post by doggo on 2019-08-31
The computer is now only starting up 10% of the time when I push the start button. When I finally did get it started, with the SystemRescueCD USB stick in, I got a message saying "The selected boot device failed. Press enter to continue." I pressed enter and the computer instantly shut down. 

Tried booting into the Ubuntu USB again and that worked ok, with the usual chatter of error messages first (failed to enable AA, revalidation failed, DRDY DF ERR, etc). 

Got online with the ethernet cable, did "sudo apt install testdisk"... and it said "E: Unable to locate package testdisk." 

At a loss. But ntfsfix is there, so if anyone knows how that works, I could give it a try. I need to get this done before Tuesday (which is when the man from HP comes to replace the hard drive), so I'd be quite prepared to run the risk of bricking the drive if there's no other obvious solution.

---

### Post by Autodave on 2019-08-31
Superblock errors are usually telling you that the drive and all of its contents are toast.  Sometimes the drive can be reformatted and live well, but again, all data is lost.

---

### Post by yancek on 2019-08-31
>  In the command line, the hard drive showed up as dev/sdb but when I  tried to mount it that way I just got a bunch of superblock errors.]

That's the physical hard drive and it should have partitions on it which is what you would want to use, such as /dev/sdb1/ /dev/sdb2, etc.  Boot Ubuntu and run this command to list partitions and post the output here:

```
sudo parted -l
```

---

### Post by DuckHook on 2019-08-31
> **Autodave said:**
> Superblock errors are usually telling you that the drive and all of its contents are toast.  Sometimes the drive can be reformatted and live well, but again, all data is lost.
…and even then, I would not trust that drive with my critical data ever again. I have found that failed HDDs are just bad news.

Yes, it's hard to treat an expensive HDD as toast when it still looks so pristine and usable, and only gives the occasional hiccup, but I've had too many experiences with entrusting data to marginal drives only to eventually have to bury the dead bodies, that I no longer trust them. Once a HDD starts misbehaving, I'm no longer tempted to salvage it; I just buy a new one. The theoretical "savings" are almost invariably penny-wise-pound-foolish.

---

### Post by doggo on 2019-08-31
> **yancek said:**
> That's the physical hard drive and it should have partitions on it which is what you would want to use, such as /dev/sdb1/ /dev/sdb2, etc.  Boot Ubuntu and run this command to list partitions and post the output here:

```
sudo parted -l
```

here's the output:

Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sda: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.5GB  15.5GB  primary  fat32        boot, lba


Model: ATA WDC WD10SPZX-60Z (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB   16.8MB               Microsoft reserved partition  msftres
 3      290MB   999GB   999GB   ntfs         Basic data partition          msftdata
 4      999GB   1000GB  1028MB  ntfs         Basic data partition          hidden, diag


EDIT: So. should I attempt to mount dev/sda3?

---

### Post by doggo on 2019-08-31
OK, I did attempt to mount sda3, after creating mnt/wind, and this is what I got (after a long wait):


```
sudo mount /dev/sdb3 /mnt/wind
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
```

---

### Post by yancek on 2019-09-01
The message you posted in post 10 is what was suggested above in  post 3, your windows is still hibernated.  It reports first "refused to mount" and then "Falling back to read-only mount" so you might try navigating to the /mnt/wind directory to see if you can access.  My understanding is that a hibernated system will be inaccessible but I don't use windows so...?  SInce you are trying to get data off there is not reason to have to 'write' to the partition.

---

### Post by dragonfly41 on 2019-09-01
Post #5:-

> [COLOR=#000000]I need to get this done before Tuesday (which is when the man from HP comes to replace the hard drive), so I'd be quite prepared to run the risk of bricking the drive if there's no other obvious solution.[/COLOR]

My line of thought would be to keep the suspect drive (not give it to HP just yet) and explain to HP that you need to recover data.
Then when you have your PC working again put the suspect drive in a container as an external USB drive and take time in recovering data. Your HP man might supply a container if you advise on Monday. However is possible that HP man might insist on a swap to test it under warranty. Negotiate.

---

### Post by doggo on 2019-09-01
I already asked about keeping the drive, but they said it "becomes HP property" as soon as they give me a new one. I'm not happy about that, partly because I really do need this recent data for work, and partly because it has personal information etc on there, and while I'm sure HP employees don't recover data from faulty disks and go through it for the purpose of identity theft or whatever, it's just not something I'm comfortable with, so if I can't sort this by Tuesday I may well just use shred on the whole drive (call me paranoid). 

I've never known a hard drive on a six-week-old computer to fail, though. Does this seem more like a hardware problem or an OS problem? Everything seems to point to the former, but it seems odd, and I don't want to chuck the disk away before extracting the data unless I know for sure. Is there any way to tell for sure?

Thanks for all the advice so far. Any further suggestions would be very gratefully received.

---

### Post by ajgreeny on 2019-09-01
With no information so far on the cause of your inability to boot into the Windows OS it's impossible to know if this is a hardware or OS problem.

My gut feeling from what you report in post #10 is that it's probably a software/OS problem following some glitch during the boot process which has now made the disk/partitions impossible to mount in Linux for the reasons given in my post #3.

A second gut feeling is that if you could connect it to a Windows machine it would probably be relatively easily repaired, though as I no longer use Windows I can not tell you what is needed in order to carry out that repair.

---

### Post by SeijiSensei on 2019-09-01
ntfsfix is unlikely to fix these problems. It can only handle a very limited range of issues. If you could install the drive in a working Windows machine and use its native utilities you might have better luck. See the man page for ntfsfix for details. [https://linux.die.net/man/8/ntfsfix](https://linux.die.net/man/8/ntfsfix)

---

### Post by doggo on 2019-09-01
Argh. Last night I tried a bootable Windows USB and a bootable Windows recovery drive, neither of which worked. Would there be any simple way to connect this laptop to my other laptop? I presume it's not as simple as running a USB lead between them. 

Despite having had to use Windows for several years, I'm really not too familiar with it either when it comes to OS issues - far more comfortable tinkering with Ubuntu, even though it's been a while.

One more thing that's still confusing me: when Ubuntu sees what I presume is my internal hard drive, either in Disks or in the terminal, why is it saying it's a 1TB drive when it's actually a 2TB drive? That makes no sense at all to me. I can't think why it could possibly be.

---

### Post by dragonfly41 on 2019-09-01
You may not be in a position to further test/sanitise your suspect drive before HP man arrives on Tuesday.
In view of the short period since purchase of your laptop (?) you still have plenty of warranty time
left to explore this drive. If your laptop can take a second drive of same capacity then change your strategy by purchasing a
second drive (Windows 10 configured) to plugin. If there is no slot for a second drive explain to HP that you want to dualboot 
from two drives, using one as a backup. You do not want to claim against warranty just yet (you have possibly 10 months before warranty expires). If fact do you really need a visit by HP engineer at this stage? If you have a second drive which you purchase (not replace) it is within your own timeframe to analyse further. And worst case you have bought a second drive as a backup device.


[Later edit] being an experimental soul, this is the sort of wild idea I would try .
Install VirtualBox on your Ubuntu LiveUSB.
Install Windows as VM in VirtualBox.
Attempt to use Windows VM to access your stubborn resident Windows 10 on internal drive.

[https://www.groovypost.com/howto/windows-10-install-virtualbox/](https://www.groovypost.com/howto/windows-10-install-virtualbox/)

---

### Post by doggo on 2019-09-01
Sounds like a good idea, so I tried it. Couldn't download VirtualBox from the repository so I downloaded it online, clicked on it to install, but it still won't. SoftwareInstall opens, I click on the install button, and nothing happens. I don't know what's going on there. It's definitely the right version. Have I just been away from Ubuntu so long that I've missed something obvious?

Sorry this is dragging on. I really appreciate the help, though.

---

### Post by dragonfly41 on 2019-09-01
It has dawned on me that you might need to create a *persistent* Live USB to allow you to install extra apps such as VirtualBox, testdisk etc.  [Here is a link describing what is needed]("https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/"). You might also try GDebi Package Installer for installing downloaded *.deb files.

[More info here on installing VirtualBox in persistent Live USB]("https://askubuntu.com/questions/1016892/trying-to-set-up-virtualbox-with-live-persistent-usb-made-using-mkusb").

---

### Post by dragonfly41 on 2019-09-01
And here is another on [installing *.deb files]("https://itsfoss.com/install-deb-files-ubuntu/").

---

### Post by ajgreeny on 2019-09-01
Assuming VBox was downloaded to the Downloads folder of your live USB of Ubuntu try running command ```
sudo apt install Downloads/virtualbox-6.0_6.0.10-132072~Ubuntu~bionic_amd64.deb
``` Change the name of the virtualbox.deb file if it is not the same as shown in my example.

That should install Virtualbox, but it may still be rather difficult to get your problem solved that way as you will, I think, need a persistent live USB, and also may need to install "guest additions" in the guest Windows, and I'm not sure how easy that will be in a live install of Ubuntu, running Windows as a VM.

---

### Post by dragonfly41 on 2019-09-01
Returning to your earlier posts I ran a further search and [this pops up]("https://askubuntu.com/questions/462381/cant-mount-ntfs-drive-the-disk-contains-an-unclean-file-system") suggesting that the "unclean state" message in post#10 might point to a corrupt hibernation/shutdown of Windows. So your disk might not be the cause.
All very confusing I know. It is a matter of trying to find clues.


[And here ...]("https://itsfoss.com/solve-ntfs-mount-problem-ubuntu-windows-8-dual-boot/")

Based on above can you disable Fast Boot by going into BIOS settings.

---

### Post by doggo on 2019-09-01
Thanks very much, I'll try some of this out now.

One more thing - now when I type

```
sudo parted -l
```

...nothing happens. It just hangs - the cursor stops flashing, then if I press a key it starts flashing again for a bit, then stops again. Nothing ever appears in the terminal. Is this bad?

Oh, and I tried ntfsfix and got failure messages:

```
Failed to access '/dev/sda3': No such file or directory
Error opening '/dev/sda3': No such file or directory
Volume is corrupt. You should run chkdsk.
```

Not sure how I can, unfortunately...

Starting to really warm to the idea of just accepting I won't get my data back soon, paying for a new hard drive and keeping this one as an ongoing project. Perhaps HP will at least install it for me, seeing as so far as they're concerned, this is a hardware failure six weeks after purchase. 

(One positive thing: it's been so nice using Ubuntu again, even off this USB. So much nicer than the bloated drag of Windows 10.)

---

### Post by dragonfly41 on 2019-09-01
Read advice of [OldFred here]("https://ubuntuforums.org/showthread.php?t=1907603") (post#3) .. running chkdsk on Windows drive using external Windows recovery (you can download it).

More up to date .. Win 10 .. (although chkdsk is a very old tool available on old versions of windows if you have other recovery disks).
[URL="https://www.techradar.com/how-to/software/operating-systems/how-to-create-a-windows-10-recovery-disk-1302377"]
Creating windows 10 recovery disk/USB (to run chkdsk).[/URL]


Signing off for today ....

---

### Post by doggo on 2019-09-01
Update: Tried to run chkdsk from a Windows recovery USB and it helpfully told me there were errors, but then wouldn't fix them because "the drive is write protected".

Update 2: I was suddenly able to get into the HP system test by pressing F2 at boot. This had previously come up as a very basic text-on-black-screen thing and told me that the hard drive was not installed. Later it could see the disk, but the quick test stalled at 99%. Now it's a blue and grey GUI that you click on, with a lot of options. (Perhaps this change is because I fixed the boot configuration data from the Windows recovery drive.)

And now the System Quick Test is telling me that the hard drive has passed a SMART check... and then it's stalled at 98% (supposedly 31 seconds from the end), during a Hard Drive Short DST Check, the results of which never appear. The computer hadn't seized up, because I could press escape and get out of the test, but it wasn't going to complete.

Ran the Short DST Test on its own afterwards. Inevitably, it stalled at 99%, 1 second from the end. I pressed escape to get out of it, exited the GUI, the computer restarted... and sent me back into the text-on-black-screen telling me there was a hard disk error and to run System Diagnostics. Which is what I'd just done, except this time without the blue GUI. I did it again anyway, and guess what? It stalled at 99%, with 1 second remaining. 

(Incidentally, since this first happened, just switching the computer on and waiting has at various times resulted in three completely different outcomes: first the error message (BI initializeLibrary failed 0xc00000bb), then the Hard Drive Error - run System Diagnostics message, then that screen saying something like "The requested boot operation could not be performed", and now back to the System Diagnostics thing.)

So now I'm even more confused. Does that mean this is a hardware issue after all? Arghhh.


Final edit: The stalled-at-99% DST finally completed! Results of system diagnostics test:

SMART Check: PASSED
Short DST: WARNING

---

### Post by dragonfly41 on 2019-09-02
> [COLOR=#000000]SMART Check: PASSED[/COLOR]
[COLOR=#000000]Short DST: WARNING[/COLOR]

Always keep a note of the reports (clues) and put then into a google search. You find that you are not alone with these issues.

  SMART Check: PASSED Short DST: WARNING

[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Smart-check-PASSED-Short-DST-FAILED-Now-what/td-p/5769889](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Smart-check-PASSED-Short-DST-FAILED-Now-what/td-p/5769889)

[https://support.hp.com/us-en/document/c01443463](https://support.hp.com/us-en/document/c01443463)

> The Boot device not found error message can occur if the connections to the hard drive are loose.

[https://answers.microsoft.com/en-us/windows/forum/all/windows-10-disk-repair-wont-automatically-repair/4f65b662-e8c1-4cc6-9298-eb325820e467](https://answers.microsoft.com/en-us/windows/forum/all/windows-10-disk-repair-wont-automatically-repair/4f65b662-e8c1-4cc6-9298-eb325820e467)


And here ...

[https://community.spiceworks.com/topic/524333-is-anyone-here-familiar-with-hp-hdd-failure-codes](https://community.spiceworks.com/topic/524333-is-anyone-here-familiar-with-hp-hdd-failure-codes)

> [COLOR=#333333]Check to make sure [/COLOR][COLOR=#333333]UEFI[/COLOR][COLOR=#333333] and Secure boot are not enabled.[/COLOR]

> [COLOR=#333333]I rang the helpful folks up at HP support as the laptop is still under warranty and discovered that if you hit the [/COLOR][COLOR=#333333]esc[/COLOR][COLOR=#333333] key repeatedly when the laptop is booting up you can actually get into another [/COLOR][COLOR=#333333]seperate[/COLOR][COLOR=#333333] HP screen that allows you to troubleshoot issues even further, nothing else worked so thought what the hell and did a factory reset on the whole thing. It has been running fine since then and got everything running back on there with no problems[/COLOR]


**Conclusion**


[LIST]
[*]Make sure that your suspect disk drive is properly seated in its connector.
[/LIST]


[LIST]
[*]Several conclusions in HP forums above suggest faulty drive. But others point to Hiberation corruption.
[/LIST]
         i am inclined to give the drive the benefit of the doubt at this point.


[LIST]
[*]The [COLOR=#000000]blue and grey GUI  you refer to is the BIOS. As listed above .. [/COLOR][COLOR=#333333]Check to make sure [/COLOR][COLOR=#333333]UEFI[/COLOR][COLOR=#333333] and Secure boot are not enabled. Turn off hibernation.[/COLOR]
[/LIST]
[COLOR=#333333]
[/COLOR]
[LIST]
[*][COLOR=#333333]Try hitting Esc key rapidly several times when booting up to get into troubleshooting GUI.[/COLOR]
[/LIST]
[COLOR=#333333]

[LIST]
[*]Print notes for the HP engineer (get your money's worth).
[*]You will need to purchase at some stage a USB disk enclosure to place your backup (second) drive. Then this will be connected to your factory setting restored PC with fresh drive via USB connection cable. You can then attempt to recover data from the (now) external drive which has caused problems and decide if it needs to be replaced later under warranty. Make sure that HP engineer takes a record of its serial number to avoid later disputes when you try to send it back after sanitising to get a replacement.
[/LIST]


[/COLOR]

---

### Post by doggo on 2019-09-02
Thanks again (and sorry for posting right before crashing out last night, which might not be the best for writing clear and concise posts). Some of that stuff I'd tried already, some I hadn't, so I've been looking into it now.

I don't quite understand how to change settings re. UEFI - in the startup menu, if I go to Boot Options, what's selected is "OS boot Manager (UEFI) - Windows Boot Manager" and then a serial number of my drive. The other two options are Boot from EFI file, and Notebook Hard Drive. When I selected the first of those, the screen just showed a long number I didn't understand. When I selected the second, it immediately gave me a black screen with the words "No bootable device - insert boot disk and press any key." That was all I could find in the startup menu relating to UEFI.

Turned out that Secure boot was indeed enabled, so I disabled it, saved settings and exited.

Now if I just try to start up the computer normally, rather than giving me an error message, it prompts me to press Escape to go back into the startup menu. If I don't do that, it goes through to the Hard Drive Error -  Press F2 for System Diagnostics screen. But if I do press Escape, the message changes to "ESC... Pause Startup" and then nothing happens. It just hangs. But I can still get into the startup menu by pressing Escape repeatedly on startup before anything else happens.

Also,  when I try to run a test on the drive now, it gives me the "No hard drive installed" message again. So that's kind of gone backwards from last night.

I'm some way out of my depth now though, and this is veering away from Ubuntu and into the world of hardware, so I don't know what to do. It's a remarkable mess, isn't it...

---

### Post by dragonfly41 on 2019-09-02
I fear that the point has been reached where you need a new drive with factory settings of Windows 10.

[Refer to HP site]("https://support.hp.com/us-en/document/c04784866").   Read when to enable/disable Secure Boot.

Given that after Tuesday visit you have a working laptop your best hope is to apply the new Windows setup to try to access lost data in your previous drive which you will hold back.

Search google for UEFI explanation. It is the modern version of Bios.

A ward of caution. I have Windows 10 and Ubuntu 16.04 as dual boot on separate partitions in a 1TB drive on a Dell tower.  But I have not switched to running Windows 10 for many months. The reason is that Windows 10 updates at times screws up Ubuntu sitting in the same drive. Windows ignores alien Linux partitions and might move them. Later I will pull all my Ubuntu content into a separate drive so that Windows 10 sits on its own. Until then I will not take the risk of booting up Windows 10.

---

### Post by doggo on 2019-09-02
Thanks for all the help. I agree that this has probably gone as far as it can.

The good news is that HP have agreed to let me keep my old drive, so I'm going to stop worrying for now and have that as a long term project. I've lost some recent data I sort-of needed for work, but I can live with that.

I was considering setting up a dual boot, but that sounds horribly plausible about Windows 10. I think I might just spend time playing around with Ubuntu from the USB to refamiliarise myself with it, and then at some point in the future get rid of Windows 10 altogether and replace it with Ubuntu. Can't do it yet, as I need Windows-specific programs for work, but I'd like to be on Ubuntu again by the new year. 

Thanks again for trying to help. We might not have fixed the problem but it's been a nice refresher course, and running Ubuntu again, even from a Live CD, felt like coming home - from the cold blue mess of Windows 10 to a world of warm orange and burgundy and brown, where things actually seem to make sense...

---

### Post by dragonfly41 on 2019-09-02
One final tip.  You might be surprised to learn that Ubuntu can run inside Windows 10, in something called Windows Subsystem Linux (WSL).

[Described here]("https://docs.microsoft.com/en-us/windows/wsl/install-win10").

But it can be devilishly complicated to understand.

[https://devblogs.microsoft.com/commandline/do-not-change-linux-files-using-windows-apps-and-tools/](https://devblogs.microsoft.com/commandline/do-not-change-linux-files-using-windows-apps-and-tools/)

You might be better aiming to install Ubuntu on an external bootable USB drive (possibly your current drive).  You would use your Live USB to create the external Ubuntu and this definitely keeps the two worlds apart, not sharing the same drive.  My boot menu shows choice between Windows 10 (internal) and Ubuntu (external) - both bootable separately.  Boot-repair will give an insight.

---

### Post by ajgreeny on 2019-09-02
>  I think I might just spend time playing around with Ubuntu from the USB to refamiliarise myself with it, and then at some point in the future get rid of Windows 10 altogether and replace it with Ubuntu. Can't do it yet, as I need Windows-specific programs for work, but I'd like to be on Ubuntu again by the new year.
It seems to me as though you are a great candidate for running Windows as a VM in, for example, VirtualBox; this is something I have to do (or did in the past) to update my SatNav device which is impossible to do in Linux. It has been no problem at all, in fact I still use a VM Of WinXP for which I have a clean snapshot so if it should become infected with a virus or other malware I can just restore the clean snapshot.

I have to say, however, that in my 33 years of running my own computer, going back to Windows 3.# I have never suffered from a virus of any kind, maybe because I'm paranoid about clicking on anything I don't know that I can trust.

As always the weakest part of any computer system is the person using the keyboard!

---

### Post by doggo on 2019-09-02
Oh dear... I thought I was done here for now, but there's something else I need to ask. Not directly connected to the original problem but hopefully there's a simple answer (which I haven't found yet from Googling it, because all search terms lead to stuff about internal hard drive partitions).

I've booted into the Ubuntu USB because I have some old backup hard drives, full of data from my old Ubuntu machine. Some of that data was unrecoverable in Windows because it had file names with symbols in, e.g. question marks. So before the new drive arrives I was going to open them in Ubuntu and change the file names, so they work in Windows.

First drive auto-mounted and all went well. But the second drive didn't, and although it's showing up in Disks, under Partitioning it says "Master Boot Record". Above the Volumes graphic it says Size: 3.0TB, but then underneath it says Size: 8.4MB and Contents: Unallocated Space. It won't mount from there. I haven't tried mounting it from command line as I don't want to mess anything up. I'm fairly sure this drive is ok - it worked fine quite recently.

At the risk of getting tedious... is there a simple solution to this?

---

### Post by dragonfly41 on 2019-09-02
I would not dabble with changing filenames since something is bound to go belly up.

Instead .. install [R-Linux]("https://www.r-studio.com/free-linux-recovery/") on your (persistent) Live USB and use this as a file manager to inspect files in other drives (but only Linux ext formatted drives, not Windows).

There is also a version of R-Linux which can install in Windows to allow Linux files to be inspected.

It is possible that you might need a persistent Live USB for this game plan to work.  That subject was discussed earlier. So you might end up with a non-persistent Live USB which you are now using and a persistent Live USB (in which R-Linux is installed).

Clear as mud?

---

### Post by oldfred on 2019-09-02
It sounds like your 3TB drive is using some proprietary partitioning which was done to support XP as it could not read gpt drives and drives over 2TiB required gpt partitioning.

What does this show?
sudo gdisk -l /dev/sdX where sdX is your drive.

       Proprietary Seagate external
[URL="http://www.seagate.com/support/downloads/beyond-2tb/"]http://www.seagate.com/support/downloads/beyond-2tb/

      [/URL]
 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record) 
    [URL="http://www.seagate.com/support/downloads/beyond-2tb/"]
[/URL]

---

### Post by doggo on 2019-09-02
In terms of changing file names, this is only on movie files and mp3s (where I foolishly left question marks and so on in the titles, not realising that Windows would not be able to see them when I tried to copy them over). I was planning to copy them from the external drive to the Ubuntu desktop, remove the offending characters and then copy them onto another external drive (which is working fine). Seemed like a simple, foolproof plan.

Bit confused by the other stuff (and my brain is fried from a weekend spent fiddling fruitlessly, slightly out of my depth). This stuff is really not my strong point. I'll try to do what you suggested.

To clarify, this is just an external storage drive. It contains a mixture of files created on a Linux computer and files created on a Windows computer, but there's no OS-related stuff on there, just mp3s, mp4s, Office files etc. Last time I plugged it into my laptop (running Windows) it was fine. I just tried it again on my creaky old laptop running Windows 7, and there's nothing wrong with it.

It shows up in fdisk looking fairly normal. The main difference between this drive and the other one (which automounts and works fine) is that one has Disklabel type gpt, while the non-mounting drive has Disklabel type dos. 

The most glaring difference is in Disks, where I've just realised I slightly misreported the situation. The working drive has one large partition while the non-working drive has three: a large NTFS partition (called Seagate Expansion Drive) plus two very small ones (8.4 MB and 4.7 MB), labelled "Free Space". The small ones have all the mount options etc. greyed out, the contents listed as "unallocated space" and are both named /dev/sdc. The big partition is /dev/sdc1 and its contents are listed as "NTFS - Not Mounted". The only weird thing is at the top, where it says "Partitioning: Master Boot Record", which I don't understand, but it sounds significant.

As you can probably tell, I know NOTHING about partitioning. My dumb brain thinks that logically I should just be able to mount /dev/sdc1 and everything would work. Is that stupidly optimistic? Don't want to try it just yet in case something goes badly wrong. Failing that, is it a simple, fixable issue with the partition table or something? Apologies - I'm way out of my comfort zone on this.

---

### Post by doggo on 2019-09-02
Just found an ancient backup drive - which I thought was broken - with the exact same files on it, and it auto-mounts. So that last long post is now irrelevant - I'm sorry. If there really is a simple answer (e.g. just mount the partition with the data on it) then please let me know for the sake of my education. But if it's a complex thing, forget it, and I'm sorry if I wasted any of your time  Thanks again!

---

### Post by dragonfly41 on 2019-09-02
With your Live USB Ubuntu running launch menu **Accessories > Files**   (Nautilus File Manager opens).

You should see your running Live USB Ubuntu drive filesystem under **My Computer** and any other drives (mounted or unmounted) under **Devices**.

If you click on an item under **Devices** it should (with luck) mount.  Click again and it unmounts. 
 There is a mount arrow icon alongside. Right click to see mount/unmount.

...

Do respond if you can to the advice given by OldFred above post34.

Run the command as requested ...

[COLOR=#000000]sudo gdisk -l /dev/sdX where sdX is your drive.[/COLOR]

---

### Post by doggo on 2019-09-05
I'm not sure how I missed that post, OldFred, sorry. Here's the result of that command:

```
Warning! Read error 5; strange behavior now likely!

Warning! Read error 5; strange behavior now likely!

Partition table scan:
  
MBR: not present
  
BSD: not present
  
APM: not present
  
GPT: not present



Creating new GPT entries.

Disk /dev/sda1: 532480 sectors, 260.0 MiB
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 4022BB58-5D34-445E-A8F0-05A91A7D1202
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 532446
Partitions will be aligned on 2048-sector boundaries
Total free space is 532413 sectors (260.0 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
```

Been busy for a couple of days, and the drive is being replaced tomorrow. Not sure this data's ever coming back, but I'm keeping the drive just in case...

---

### Post by oldfred on 2019-09-05
Have not seen that type of error from gpt.
And that pretty much says it is a proprietary partitioning or drive partitioning is totally damaged.

---

### Post by doggo on 2019-09-05
I wonder how this has happened on a six week old computer? Is it just a faulty drive, is it possibly a Windows bug, or might there be something wrong with the laptop?

I've got a new drive fitted now, but I've still got the old one here and would be fascinated to see if I can get anything out of it in future.

---

### Post by dragonfly41 on 2019-09-05
> [COLOR=#000000]And that pretty much says it is a proprietary partitioning or drive partitioning is totally damaged.[/COLOR]

> [COLOR=#000000]I wonder how this has happened on a six week old computer?[/COLOR]

I would not rule out the possibility that in Windows you clicked on a malicious link which destroyed your partitioning.

Have you run virus check on your now replaced drive?  If you must run Windows ensure that you enable virus checking in future.
And keep Windows and Ubuntu in separate drives.


[Added note]
Exactly the same error report is [cited here]("https://superuser.com/questions/481196/cannot-access-disk-partition-table-broken").

> [COLOR=#242729][FONT=Arial]The disk is very new, just some moths, so I doubt it&#8217;s any bad sectors.[/FONT][/COLOR]

---

### Post by oldfred on 2019-09-05
Any drive over 2TiB should be gpt partitioned.
And one of advantages of gpt is that it has both a primary partition table and a backup gpt partition table at end of drive. And it has a protective MBR table, just to say it is gpt, so old MBR tools do not try to modify it (or at least see it having something).

But some vendors have a combination MBR for the first 2TB and then something else to allow use of the rest of the drive. Without those proprietary drivers for the configuration, you cannot open or use drive.

Photorec type tools that scan a drive for anything that looks like a file may work. But they are very slow on large drives and only recover by file type, not full file name. My much smaller drive took all night to scan, and I had saved some files many times & it recovered every deleted version. Lots of work trying to figure out which was newest. I had older backup that I used to compare those files that were most important.

---

### Post by doggo on 2019-09-05
> **dragonfly41 said:**
> I would not rule out the possibility that in Windows you clicked on a malicious link which destroyed your partitioning.

Have you run virus check on your now replaced drive?  If you must run Windows ensure that you enable virus checking in future.

I think I'd actually run a virus scan between the last time I'd used the browser and the time the hard drive stopped working. (In Windows, I run a virus / malware scan every couple of days, just to be sure.) When this hard drive frazzle happened, I'd just connected an MP3 player to the laptop and copied some music over. I left it connected via USB to recharge, and went off to do something else. When I left everything was fine; when I got back the screen was frozen and the only way out was to power down. Then when I tried to start up again, that's when things had gone wrong. No idea if the mp3 player had anything to do with this. Never had any problems with it before, in seven years.

That link is interesting - what I understand of it. When I looked at the hard drive in Ubuntu the other day it was showing three partitions (the sizes of which added up to more than the size of the disk). When I looked again today to show the HP engineer, there were four. The computer hadn't even been switched on in between times. That can't be good. Whatever happened must have been a pretty big deal.

---

### Post by dragonfly41 on 2019-09-06
[COLOR=#000000]> When I looked at the hard drive in Ubuntu the other day it was showing three partitions (the sizes of which added up to more than the size of the disk). When I looked again today to show the HP engineer, there were four. The computer hadn't even been switched on in between times. That can't be good. Whatever happened must have been a pretty big deal.

[/COLOR]I can't be sure since I have not booted up my dual boot Windows 10 for many months for fear of it screwing up my neighbouring Ubuntu in partition in same drive.

However my theory now is that Windows 10 1903 somehow adds a new recovery partition which screws up any existing Linux partitions. In your case my theory is that Windows 10 initiated a 1903 update during the time you "went off to do something else".

In support of this theory I refer to this thread which reported an unknown partition being added to the dual boot drive.

[https://ubuntuforums.org/showthread.php?t=2425027](https://ubuntuforums.org/showthread.php?t=2425027)

In any event it demonstrates the urgent need for backups to be organised. Read the advice from others on backups.


**[Added thought]**

> [COLOR=#000000] I left it connected via USB to recharge[/COLOR]

Note that the link I posted in #41 above also refers to faulty power source. I wonder if you charging MP3 player from USB port had some effect. Just musing.


**[Yet later thought]**

It seems that my hunch on Windows 10 1903 update is proven. Just search this pattern in google browser.

```
Windows 10 1903 adds partition destroys Linux
```

[https://superuser.com/questions/1464135/has-win10-1903-upgrade-destroyed-my-system-partition](https://superuser.com/questions/1464135/has-win10-1903-upgrade-destroyed-my-system-partition)

[https://www.makeuseof.com/tag/windows-update-delete-linux/](https://www.makeuseof.com/tag/windows-update-delete-linux/)



...

---

