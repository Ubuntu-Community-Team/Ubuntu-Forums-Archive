---
title: "Flumoxxed by Dual Boot Installation ..."
date: 2020-01-17
forum: General Help
---

### Post by Langstracht on 2020-01-17
I want to get a dual boot of Win 10 and ubuntu 18.04 on a Lenovo IdeaPad.

There is 20 Gig of unallocated space on the HD.

After choosing a language, the installation wants me to "configure the interface", then "enter a proxy if required", and then an "alternative mirror if required".

I have no idea whether any of these are required or not and, if they are, have no idea how to do any of them.

It then goes on to ask whether I want to partition the "whole disk", "the whole disk and set up LVM" or do this "manually".  I would think I would want to do it manually but choosing this option does not permit choosing the unallocated space.  The option is greyed out.

Can someone please get me out of this dilemma?

I don't know ... perhaps I'm just using the wrong file to boot from ...

TIA

Allan

---

### Post by CelticWarrior on 2020-01-17
Is Windows 10 installed in BIOS or UEFI mode?

If the former, how many partitions are already in the drive?

---

### Post by Langstracht on 2020-01-17
It's UEFI.

---

### Post by CelticWarrior on 2020-01-17
If it's UEFI you need to assure the Ubuntu installer is booting in UEFI mode (better disable Legacy/CSM in UEFI settings). Apparently it's booting in Legacy mode.

---

### Post by Langstracht on 2020-01-17
I'm afraid I have no idea how to do that.

Can you further assist?

---

### Post by CelticWarrior on 2020-01-17
How to do that depends entirely on your hardware. Please check your manual before anything else.

If Legacy/CSM is enabled you're likely to see two different entries for the external media you're trying to boot like the Ubuntu installer. Without disabling Legacy/CSM and having those two entries you need to choose the one that says "UEFI:".

There are other settings that you need to change in UEFI so better to get familiar with yours. No one ignoring this should be trying to install any OS.

---

### Post by dragonfly41 on 2020-01-17
Not knowing Lenovo IdeaPad I used Google to search and found this rather wierd method of getting into bios.

[https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/How-to-enter-bios-boot-menu-ideapad-110-17IKB/td-p/4168291](https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/How-to-enter-bios-boot-menu-ideapad-110-17IKB/td-p/4168291)
Search the Lenovo forum for instructions.

In my Dell PC I tap F2 immediately after switching on (within seconds of the Dell logo being visible).

Lenovo might need Fn+F2 buttons from what I read.

---

### Post by CelticWarrior on 2020-01-17
> **dragonfly41 said:**
> Lenovo might need Fn+F2 buttons from what I read.

Yes, very likely. My own experience with a few Lenovos confirms it.

This is because of the fad of changing the function keys (F1-F12) from their default actions to the additional actions that before required FN. Some UEFIs allow changing this new faddish behavior back to what we were used to, some don't. This is the reason for FN+F2 - normally it would be just F2 - but because the actions are inverted we need FN even to open the firmware settings.

---

### Post by Langstracht on 2020-01-17
Thank you both for your inputs.

And the link.  I'm afraid I found nothing there that deals with disabling Legacy/CSM.

I've spent the last while repeatedly re-starting the Lenovo and trying to access the BIOS. Totally unsuccessfully.  I'll keep trying but it seems to be a bit of a lost cause.  Why DO manufacturers make it so difficult?

And that said why don't they supply manuals anymore?  My 2 month old IdeaPad has no manual ...

All of this said, if I do FINALLY get into the BIOS, is that where I disable Legacy/CSM?  Is it obvious, even to a septuagenarian like me how to do it?

---

### Post by CelticWarrior on 2020-01-17
Manuals are available online. Manufacturers always try to cut costs in anything they can. In this case it's actually a good thing because most users will never need them and we all save on paper.

You need to press FN before powering on and, while keeping FN pressed, spam the F2 key immediatelly after pressing the ON button.

Now, nitpicking, you don't have BIOS, you have UEFI but for all intended purposes UEFI is what replaced BIOS a decade ago. Unfortunately many manufacturers still call it "BIOS" or "UEFI BIOS". I guess it will take another decade to re-educate everybody about the correct terminology. That said, UEFI ("BIOS") settings is where you should find the setting but where exactly depends on your model and I'm not familiar with it. Typically but not necessarily it will be in the Boot menu or Advanced Settings (or anywhere else the firmware vendor decided to put it). 

But I must also stress that disabling Legacy/CSM is for your convenience only, it's not mandatory for UEFI installations as long as you know what you're doing. As I mentioned before, if you see your USB stick twice then just choose the entry that mentions UEFI. This always works if the USB stick has been burned with most recommended tools but if done with Rufus in Windows it will also depend on having selected the correct settings before burning and those settings are not the Rufus defaults, users must change them to GPT/UEFI otherwise the stick will only boot in older BIOS based machines or UEFI ones with Legacy/CSM enabled.

---

### Post by Langstracht on 2020-01-17
Thanks for bearing with me on this.

Yes, Fn & F2 is what I have been repeatedly doing - but, maybe, just not fast enough.  I'll keep at it for as long as my patience holds.

The stick was loaded in ubuntu from ubuntu - so no Rufus involved.

I have not seen a binary choice (which would allow choosing UEFI) and I take it that I should not pursue the route I started this thread with.

So, given no Rufus and that the Legacy/CSM thing is for my convenience (AND it being blindingly obvious I have no idea what I am doing) are my proposed actions 

       to gain access to the UEFI settings, 

       disable Legacy/CSM 

       and then boot from the USB?

Once again TIA

---

### Post by CelticWarrior on 2020-01-17
Again... Just make sure you're booting in the correct mode (UEFI). Any USB done the normal way will boot in either mode, it depends on the machine utself being BIOS or UEFI except in the cases where a UEFI machine has Legacy/CSM enabled. In this situation it normally shows up twice in the list of bootable devices, one with "UEFI" in the name, one without it. Selecting the former assures you're booting in UEFI mode.

But you should also make an effort to access the UEFI settings because you may need to change other settings.

And something that hasn't been discussed before - my bad - is the Fast Startup feature Windows has by default. Disable it and shutdown Windows before attempting any Ubuntu installation in dual-boot. That setting alone may be responsible for the Ubuntu installer not detect Windows even if booted in the correct UEFI mode.

---

### Post by oldfred on 2020-01-17
What model IdeaPad?

Some early models (100) were pretty difficult to install. A poster said the 100s was much better.
And those early models were 64 bit, but used a 32bit UEFI boot loader.
LENOVO Ideapad 100 Laptop 16.04 Dual Boot 
[https://ubuntuforums.org/showthread.php?t=2336544](https://ubuntuforums.org/showthread.php?t=2336544)
LENOVO Ideapad 100S Laptop  32 bit UEFI bootia32.efi
[https://ubuntuforums.org/showthread.php?t=2350606](https://ubuntuforums.org/showthread.php?t=2350606)

Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

---

### Post by kevdog on 2020-01-17
If you have 20Gb of space -- is that 20Gb of unpartitioned space? Ubuntu needs to install on an empty partition. 
In terms of UEFI boot -- I'd recommend you do a lot of reading about what you are trying to do. It doesn't sound like you are off to a great start, but that's OK since you can gain knowledge with time.  Working with UEFI boot, Grub, windows is definitely tricky and its possible you can wipe out your entire disc partitioning table making your Windows partition inaccessible.  Take your time and READ.

---

### Post by dragonfly41 on 2020-01-17
[Reading this might help in getting into BIOS]("https://support.lenovo.com/in/en/solutions/ht500216").

---

### Post by Langstracht on 2020-01-17
Thank you all for getting involved in this.  I wish that it weren't necessary ...

That said  I've tried to get into UEFI another dozen times and have yet to succeed.  Can but keep trying ...

The machine is an IdeaPad S145.  I'll see if I can find  out anything about that specifically in one of the ubuntu links provided.

I'd thought that this Fast Startup thing would have been accessible in Windows (i.e. NOT in UEFI)  If that's true I can't find it.

The 20 Gig is one empty partition.courtesy of Windows "Shrink".

So I guess I'll just plugging away at this unless someone has any other advice to give.  

The last time I installed a dual boot was on a Windoze 7 machine.  Seems to me it was a cakewalk and I had no trouble at all.  Thanks Windows (Lenovo?).

---

### Post by CelticWarrior on 2020-01-17
Fast Startup is a Windows feature, noting to do with UEFI or BIOS. Here, I've done your homework for you: [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

How to access UEFI, again... Press FN before powering on and keep it pressed. Immediately after touching the power ON button and keeping FN pressed also press repeatedly F2. This works on most Lenovos. If your is different please check the user's manual available online.

We can't help you further if you don't make an effort. And please answer what was asked in #13. Olfred is one of the experts here so pay special attention to what he says or asks, some 75% of what I know about UEFI I've learned from reading his post going back several years.

---

### Post by dragonfly41 on 2020-01-17
There really is a lot of advice at Lenovo site.

[[COLOR=#0000ff]**CLICK HERE**[/COLOR]]("https://support.lenovo.com/in/en/solutions/ht103672")[COLOR=#0000ff].

[/COLOR]Incidentally ..[COLOR=#0000ff]

[/COLOR][COLOR=#000000]> How to access UEFI, again... Press FN before powering on and keep it pressed. Immediately after touching the power ON button and keeping FN pressed also press repeatedly F2. This works on most Lenovos. If your is different please check the user's manual available online.

I have briefly seen one YouTube tutorial which advises that keeping Fn depressed while hitting F2 does not work.

Instead the tutorial showed tapping Fn and F2 at same time, over and over again. A wierd dance.

[Here is the video I watched.]("https://www.youtube.com/watch?v=P-mO932W3Ts")


[/COLOR]

---

### Post by Langstracht on 2020-01-17
Thanks to all for continuing to help with this.  I understand though that patience maybe wearing a bit thin all round (mine too I have to say).  But again thanks.

I found and disabled Fast Startup - thanks for finding and providing the link!

Visual acuity was never my strong suit but I think there is only one question in post 13.  Which I answered.  IdeaPad S145.  Am I missing something?

All of that said I am FINALLY into the UEFI/BIOS and, not surprisingly for me I guess, there's nothing there that I can see regarding Legacy/CSM.  Anyone have any idea what I may be missing this time?

Oh, and for what it's worth, The User Manual has repeated calls for "UEFI/BIOS setup utility" to be initiated.  But no instruction as to how to do so.  And darned if can find a way.

Yet again help greatly appreciated.

---

### Post by Ralph L on 2020-01-17
I don't know if you are still having problems or not, but I had considerable problems multi-booting Window10 with Xubuntu on my new Acer with UEFI a few years ago.  Whether your computer is anything like my Acer, I don't know.  However, here is the website that chronicles my problems.  One problem I solved getting my Windows backup to work is described near the beginning of the thread.  The solution to the main problem is described near the end of the thread.  There were lots of intermediate tries.  [https://ubuntuforums.org/showthread.php?t=2362911](https://ubuntuforums.org/showthread.php?t=2362911)  I am also an oldster (78) fiddling with Linux; I don't know why.  Good luck in getting it to run. 

ralphl

---

### Post by oldfred on 2020-01-17
It looks like it installs, these users installed but then had issues with Wi-Fi.
[https://askubuntu.com/questions/1165499/lenovo-ideapad-s145-i-can-get-touchpad-or-wireless-to-work-but-not-at-same-time](https://askubuntu.com/questions/1165499/lenovo-ideapad-s145-i-can-get-touchpad-or-wireless-to-work-but-not-at-same-time)
[https://dev.to/k4ml/comment/fk72](https://dev.to/k4ml/comment/fk72)
[https://forums.linuxmint.com/viewtopic.php?t=294322](https://forums.linuxmint.com/viewtopic.php?t=294322)

Fast Boot in UEFI, is different than Windows fast start up hibernation.
Fast Boot assumes no system changes, so UEFI does not have to scan system to copy to drive for operating system. Then you often do not have time to press any function key. Cold boot or full power down usually sets a full start up check of configuration, and you have just a few seconds to press correct keys to get into UEFI to make changes or UEFI one time boot key to boot flash drive or directly boot anything other than default set in UEFI.
Often even more difficult with tablet type systems as you cannot remove battery and force cold boot. Some have a tiny reset button on back.

---

### Post by Langstracht on 2020-01-18
Tx oldfred and Ralph L for hanging in with me.  Much appreciated.  And you've given me much more to grapple with.

That said, I've gotten a "private'" e-mail from someone who, I guess, must have seen my dilemma.

And I'm not sure if it simplifies or complicates things.

He said I should forget about this dual booting thing and instead install a "VirtualBox" on Windows and run ubuntu from there.  Apparently with identical functionality.  

Sounds good, great even, to me.  Except I have to wonder why no one "here" has made that suggestion.  And that maybe it's not such a good idea after all

Does anyone have any knowledge/experience of VirtualBox that can nudge me in one direction or the other?

Again, many thanks in advance.

---

### Post by oldfred on 2020-01-18
I have always dual booted. I have lots of RAM on this system, and have planned for several years to try a virtual install.

But many here do recommend virtual installs, but you need the hardware to support it. Each virtual install needs RAM, if just a server, you can get by with 1GB for a server in a virtual install. Not sure what is best for typical gui install. I am sure then one of the lighter weight versions would be better.

Light weight flavors
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

I am also running a light weight gui that is not really advertised. It is fallback or gnome-panel. When Ubuntu changed to Unity, the old gnome with top & bottom panel was kept as fallback. Mint did similar thing, but gnome-panel has been updated to be based on gnome3. 
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
[https://en.wikipedia.org/wiki/GNOME_Panel](https://en.wikipedia.org/wiki/GNOME_Panel)

---

### Post by dragonfly41 on 2020-01-18
Actually you may not realise this, but with Windows 10 you already have a native copy of Ubuntu running. It is called Windows Subsystem Linux. But it is not for you I would guess.

I am of the opinion that sharing a common drive between Windows 10 and Ubuntu (commonly called dual boot)  is not such a good idea these days. I have used that for years but not now.

You can get good results running Ubuntu if you simply configure an external drive to run Ubuntu, leaving Windows 10 untouched in its own dedicated drive. It costs a bit more .. but compared with the hassle of shared dual booting that is my route.  I am writing this with Ubuntu running on an elderly external drive in a USB container.  Windows 10 is in /dev/sda. If you venture to add a portable external SSD you need to understand the requirement for fast USB 3.1 connecting the portable SSD to your PC.  So the PC spec is critical.

Or you can run Ubuntu in a VirtualBox within Windows.

[P.S.} I am now studying how to run a Ubuntu image in Docker Hub (in the cloud).

---

### Post by oldfred on 2020-01-18
I have been putting full installs on USB3 flash drives more for emergency boot.
And knew they would be slower.

But had an old 60GB SSD and purchased a SATA to USB cable. Tried it with HDD, but not enough power from USB port. But with SSD, it was almost as fast as internal SSD on my system.

I just purchased a new NVMe drive. When I built system, M.2 NVMe was very expensive but M.2 SATA was not a lot more than standard SATA. 
I now also purchased a M.2 SATA to USB adapter for M.2 drive.  Have not yet really experimented with it, but if as good as my test with older SATA drive, I may not do many new installs to flash drives. I have a lot of flash drives already, so will just use for data backup.

---

### Post by dragonfly41 on 2020-01-18
@oldfred
I posted my SSD configuration in [post#5 here]("https://ubuntuforums.org/showthread.php?t=2433815&highlight=StarTech").

An external dual bay docking station (with its own PSU) is very useful.
Running Ubuntu
Cloning HDD/SSD
Backup
Interfacing to very, very old IDE drives (Iomega Jazz?) to recover archives.

Yet another idea posted in this forum was to add an inline power switch into host PC to totally isolate the Windows drive when booting up external Ubuntu.
An idea I have yet to try but it appeals to me.  [post#15 here]("https://ubuntuforums.org/showthread.php?t=2434378&page=2").

---

### Post by Langstracht on 2020-01-18
Running ubuntu from an ext HD sure works for me.

No surprise that I have no idea how to accomplish that.

Guess I've got some googling and some reading to do ...

---

### Post by dragonfly41 on 2020-01-18
> [COLOR=#000000]I want to get a dual boot of Win 10 and ubuntu 18.04 on a Lenovo IdeaPad.[/COLOR]

[COLOR=#000000]There is 20 Gig of unallocated space on the HD.[/COLOR]

You need more precision in the definition of your laptop. You are describing a family rather than the member of the family.
Exact information on laptop can be used to search for a portable device which matches the specification.
Best place for this research is Lenova site, then explore USB ports (best if they are USB 3.1), power rating, memory,
size of internal hard drive.

After that choose the external drive (my preference would be SSD) and check with Lenovo support forum if that is compatible with your Lenovo. 
Check that Lenovo can support external from internal power supply. If not aim for a device with its own portable power supply unit to avoid draining your Lenovo.

Decide if this will sit at your home base or whether it needs to travel. This is a balance.

After that it is downhill. Use Rufus in Windows 10 to burn a distro into LiveUSB.
Boot into LiveUSB and use "Try Ubuntu" first (not "Install Ubuntu").
Use GParted to create partitions in your external HDD/SSD.
I created partions as follows:
/dev/sdb1 fat32 500MB with flags .. boot, esp
/dev/sdb2  ext4  choose size for /
/dev/sdb3  linux-swap

and if an SSD leave at least 10% of space unallocated.  That is your usable space will be about 90% of the gross size of SSD.

Now you can use LiveUSB to install Ubuntu into target /dev/sdb2 with /dev/sdb1 as your ESP partition.

When booting into the device use the "one time boot option" (in my Dell it is seen when hitting F12. this might be Fn+F10 in Lenovo. i'm guessing).

---

