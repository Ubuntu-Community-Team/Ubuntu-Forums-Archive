---
title: "can no longer boot"
date: 2014-08-09
forum: General Help
---

### Post by jgw on 2014-08-09
I am running with ubuntu 14.04.1  I have a motherboard with a built in radeon 300.  I decided to make a run at installing the driver for that.  I went out and searched for directions as to how, exactly, I should do that.  Wherever I was they said that I should download all the restricted drivers with the command sudo apt-get install ubuntu-restricted-extras    I did that (a really bad decision, I think).  It whizzed and wirred and then told me to reboot.  I rebotted and, no boot!

Anyway, I now have some choices and need help.  I am currently in "trying ubuntu" off my installation disk (14.04 amd64) If I need to I should, in theory, copy off my home page to my other drive and then reinstall (need the home page for settings, etc)  My problem with that one is that I do not know the password for trying ubuntu.   I can also take my main drive out and run it from a windows usb port on my laptop (if it can read it).  In either case, if I am going to reinstall I want to save my home directory first.

My other choice, hopefully, is that somebody can tell me how to fix my unbootable machine without destroying its existing installation.  

Thank you.....................

---

### Post by grahammechanical on 2014-08-09
Installing Ubuntu Restricted Extras does not bring in proprietary video and wireless drivers. It should not have required a reboot. I think that you followed some other instructions that may have been out of date, There is a lot of out of date information on the internet that no longer applies to the latest Ubuntu.

The better way to have done this would have been to go to System Settings>Software and Updates>Additional Drivers tab and allow the utility time to find some proprietary video drivers and then select one and click apply.

What do you mean "no boot." Give us a clue as to where the loading process stopped.

You could try at the Grub boot menu selecting Advanced Options for Ubuntu and then selecting Recovery mode and at the recovery menu selecting Resume. That may get you to a desktop using a fall back open source video driver. From there you can get to System Settings.

Regards.

---

### Post by jgw on 2014-08-09
Thank you for the reply.  

When trying to boot it gets the the ubuntu 4 dot thing then, after a bit, disk activity (the light) lights for about a second, then a quick light, and times between get longer and longer until it just hangs.  I let it run all night just in case it was doing something.  I am now trying the recovery thing suggested.  I suspect that might be a problem in that it gives me two options, each of which involve ubuntu 13.?  I choose recovery.  That is now hanging.  It said some stuff could not be downloaded and its either ignoring or using old.  Then it moved on to reading package list and building a dependency tree.  It did that twice, found nothing, and then said; upgraded 0, newly installed 0, 0 to remove and 0 updated.  I then got a prompt to press enter.  I told it to fix any broken packages and then to boot normally.  It came back telling me that my graphics were screwed up and would have to goto low graphics mode.  It is now hanging on that box.  I think I will do it again but, next time, I will try for the low graphics mode out of the box and see what happens.

Tried to run in default low graphics mode.  Let it run for about 5 minutes - nothing.
Now I will do it again and try each and every option in recovery mode to see what happens.  Perhaps I can get to a command prompt and be able to do something there.

I got rid of the quiet boot screen and then watched it.  I think it stopped at one line "set console font" (failed in red I was unable to get it to stop with pause so it was hard to make sure but it was within one line, up or down, of "set console font".

---

### Post by Bashing-om on 2014-08-09
jgw; Hello.

Perhaps try a simpler - to me - means to get to a terminal in your install.
How about:
Boot to the grub boot menu, with the latest kernel highlighted press the 'e' key for edit mode -> booting parameters screen.
Arrow down and across to the terms "quiet splash" replace these terms with " text nomodeset"; key combo ctl+x to continue the boot process.
Do you now boot to the text terminal (TTY1) ?

Can you log in here - username and your pass word ? ( no response to the screen when pass word is entered )

If so we can proceed to try and clean the mess up, and get the open source driver (RE-)installed.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]most likely
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jgw on 2014-08-09
Thank you again!!

I now have a prompt and was able to log in.  Next?

---

### Post by Bashing-om on 2014-08-09
jgw; Well...........

Here is the probable deal:
> 
 I have a motherboard with a built in radeon 300.

IF that card is of the X2,X3,X4 series there is no support from ATI. ATI dropped that support a couple of years back.
Let's look at what we at working with:
Terminal command:
```

lspci -nnk | grep -iA3 vga

``` of interest here is the card that you are running:
MY OUTPUT:
```

sysop@1404mini:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon
06:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1404mini:~$

```
where I am running " [AMD/ATI] RV515 [Radeon X1300/X1550] "
What is your card ?

Now we want to know if any driver at all is loaded; what results from terminal command:
```

sudo lshw -C display

```
MY OUTPUT:
```

sysop@1404mini:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display:0             
       description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       [color=red]configuration: driver=radeon latency=0[/color]
       resources: irq:16 memory:e0000000-efffffff memory:fd4f0000-fd4fffff ioport:4c00(size=256) memory:fd400000-fd41ffff

```
where in the line "configuration" I show I have the open source driver 'radeon' loaded.

What is the contents of your output for that line ?

// Depending is how to remove the proprietary FGLRX components from the system .//

[INDENT][INDENT]see, feel, then do
[/INDENT][/INDENT]

---

### Post by jgw on 2014-08-09
Thank you again.  Whilst waiting I went and purged fglrx and rebooted (probably should have deal with xorg.conf file too but never messed with it).  Anyway, I then rebooted and now have my screen back up and running.  I then did the suggested lspci thing and got:
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000] [1002:9616]
	Subsystem: ASRock Incorporation Device [1849:9616]
	Kernel driver in use: radeon
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)

Then I did:
greg@greg-desktop:~$ sudo lshw -C display
[sudo] password for greg: 
  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff

I should mention that I am basically having this grief as I swapped out my motherboard (later learned the only thing wrong was the battery <sigh>) and bought this one.  It only has one pci express connection and I wanted to save that for a usb3 card (I was not paying attention and its missing the small pcie connector) so I am trying to not have to put a display card in this one.  I am planning no real whiz bang display stuff.   This all started when I thought that it would be nice to have a better display than the max displayed (1024x768) Anyway, what will be the next step?

---

### Post by Bashing-om on 2014-08-09
jgw; Hey,

You do good work ! You are done - have done all with this card that you can.
There is no better long term option than what you presently have ( NO ATI support for any other driver).

Reboot normally, and let's see what you have . 

[INDENT][INDENT]when you are good
[INDENT][INDENT][INDENT][INDENT]you are good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jgw on 2014-08-09
Here is what I got (same, I think, as I had):
greg@greg-desktop:~$ lspci -nnk | grep -iA3 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000] [1002:9616]
	Subsystem: ASRock Incorporation Device [1849:9616]
	Kernel driver in use: radeon
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
greg@greg-desktop:~$ sudo lshw -C display
[sudo] password for greg: 
  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff

Then, for the heck of it:
greg@greg-desktop:~$ dmesg | egrep 'drm|radeon'
[   11.059316] [drm] Initialized drm 1.1.0 20060810
[   11.496295] [drm] radeon kernel modesetting enabled.
[   11.496364] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[   11.496781] [drm] initializing kernel modesetting (RS780 0x1002:0x9616 0x1849:0x9616).
[   11.496803] [drm] register mmio base: 0xFE9F0000
[   11.496804] [drm] register mmio size: 65536
[   11.497587] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[   11.497590] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[   11.497594] [drm] Detected VRAM RAM=256M, BAR=256M
[   11.497595] [drm] RAM width 32bits DDR
[   11.497707] [drm] radeon: 256M of VRAM memory ready
[   11.497709] [drm] radeon: 512M of GTT memory ready.
[   11.497718] [drm] Loading RS780 Microcode
[   11.691188] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   11.696741] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[   11.696787] radeon 0000:01:05.0: WB enabled
[   11.696790] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff880117517c00
[   11.696792] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff880117517c0c
[   11.696793] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   11.696794] [drm] Driver supports precise vblank timestamp query.
[   11.696808] [drm] radeon: irq initialized.
[   11.728765] [drm] ring test on 0 succeeded in 1 usecs
[   11.728824] [drm] ring test on 3 succeeded in 1 usecs
[   11.728937] [drm] Enabling audio 0 support
[   11.728952] [drm] ib test on ring 0 succeeded in 0 usecs
[   11.728966] [drm] ib test on ring 3 succeeded in 0 usecs
[   11.729253] [drm] Radeon Display Connectors
[   11.729254] [drm] Connector 0:
[   11.729256] [drm]   VGA-1
[   11.729259] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   11.729260] [drm]   Encoders:
[   11.729261] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   11.729262] [drm] Connector 1:
[   11.729264] [drm]   HDMI-A-1
[   11.729265] [drm]   HPD3
[   11.729267] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   11.729268] [drm]   Encoders:
[   11.729269] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[   11.729289] [drm] radeon: power management initialized
[   11.875611] [drm] fb mappable at 0xD0141000
[   11.875614] [drm] vram apper at 0xD0000000
[   11.875615] [drm] size 3145728
[   11.875616] [drm] fb depth is 24
[   11.875617] [drm]    pitch is 4096
[   11.875727] fbcon: radeondrmfb (fb0) is primary device
[   11.894885] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[   11.894887] radeon 0000:01:05.0: registered panic notifier
[   11.894973] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:05.0 on mino

My display is, apparently, a radeon RS780L which, according to Ubuntu documentation is a currently supported display at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).   I think you are saying that the driver I have is the driver I want and I should quit messing with it?  (I am one of those wherein a little bit of knowledge becomes a very dangerous thing - its how I got in the mess I had and you so kindly walked me out of <G>)  Anyway - Should I just stop messing with this one?  (I need direction or I will screw it up for sure <G>)

I just checked the amd site and they said this is the support they have for my display: [http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64)    

I have not downloaded it as I have fear and do not want to screw up yet again <G>

Thanks again!!

---

### Post by Bashing-om on 2014-08-09
jgw; Humm,

Maybe I do stand in correction. but maybe
> 
All these Radeon(HD) cards and derivatives have good 3D acceleration support. This is not an exhaustive list:
##and the listing is:
RS780/RS880                 Radeon HD 3100/3200/3300/4100/4200/4250/4290

so yeah. maybe it has support; as " [Radeon 3000] " is not listed, maybe not.
However, I tend to agree that the "[AMD/ATI] RS780L" card should be well above the cut-off .
But I think, and others please correct my think'n if I am in error,  that " [Radeon 3000] " is the determining factor here, and no proprietary driver is available.
Let's test safely and see what the package manager thinks !
Clean everything up and make sure the open source diver is installed:
```

sudo apt-get update #just to sync the index files with the mirror##
sudo apt-get upgrade #just to make sure all installed packages are up-to-date
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

OK, now reboot as normal.
Once back to the desk top -> ubuntu Software Center -> software sources ( edit) -> Additional Drivers.

What does Additional Drivers relate in respect to available drivers ? I will not be a bit surprised if it advises there are no others available.

But hey, making sure the system is clean and up to date is a great thing to do, and then it only takes a moment to check with Additional Drivers and see .

Then we can know for sure !

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by jgw on 2014-08-09
I did all you suggested.  I posted the results at: [http://pastebin.com/RDqj2cus](http://pastebin.com/RDqj2cus)  (thought to save a bit of space here)

I then went to the ubuntu software center but could find no button for woftware sources.  I then went to system tools/software and updates and was told that there are no updates available so, I think, I am absolutely as far as I can get.  If you agree let me know and I will set this one as solved?

I REALLY appreciate your time and effort on this one!!!

---

### Post by Bashing-om on 2014-08-09
jgw; Hey:

All that runs clean and looks great !

Now, as to "additional Drivers" .. I do not run unity as my Desktop, so my instructions are subject to " I do not know ".
But I do expect IF you are running unity;
left side of screen is the 'launcher' activate it, in the task bar at the top of the screen is software sources, click on it and in the drop down is "edit" -> other software (??) -> Additional drivers tab. Or something like unto that.

I will not be truly happy 'till "additional Drivers" tells us there are none !

[INDENT][INDENT]it ain't done 'till the fat lady sings 
[/INDENT][/INDENT]

---

### Post by jgw on 2014-08-09
There is no edit option in addtional drivers.  I googled "ubuntu 14.04 additional drivers" and found several references but they all said that the way to get to it is the way I did.  I also went to unity and did a search and it gave me the same thing.  I have attached (at least I think I have) a picture of my screen and the additional driver thing.

[http://ubuntuforums.org/attachment.php?attachmentid=255356&d=1407632468&thumb=1&stc=1](http://ubuntuforums.org/attachment.php?attachmentid=255356&d=1407632468&thumb=1&stc=1) edit
I am not sure about what this is all about but I think its the attachment.  The attachment thing seems to have gained a bit of complexity <G>  (hope you get it)

I am being told its dinner time so I will shut this down until tomorrow (I was given no choice! <G>)

---

### Post by Bashing-om on 2014-08-09
jgw; Well !

Tell ya what, I DO have 14.04 ubuntu (standard) installed, When I reboot tonight I will reboot into that install and take detailed notes on finding that sucker.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-10
jgw; Well, a good morning to ya ;

I looked at the fresh 14.04 standard ubuntu install ( unity ) last night, and it is as I remembered to access " Additional Drivers".
Again: from just looking at it:
 launcher ( left side ) is Ubuntu Software Center, once activated mouse up to the task bar so that the task bar has focus and the application menues become available.
In these menus is "edit"; click on it and in the resulting popup last item is -> Software Sources .
In Software Sources window make sure that the check box for " Proprietary drivers for devices (restricted) " is checked. IF not close out all instances of the USC and back to terminal ( my way of thinking) to update the data bases and resync for the restricted drivers .
```

sudo apt-get update
sudo apt-get upgrade

``` [ because I want to see/know what is taking place and going on, do it from terminal]

-also from the dash, search term "additional" also brings up the "Additional Drivers" utility -
IF you now do not get that utility .. we do need to investigate !

OK now all is up-to-date; back to Software Sources and the far right tab is "Additional Drivers" -> select it, let it do it's thing giving it plenty of time to look . I fully expect the return to be " no additional drivers found";

Now for confirmation, from the terminal, in respect to only proprietary drivers !
What returns from:
```

ubuntu-drivers devices
ubuntu-drivers list

```
Giving it the time to look and see what it can find.
Again I expect no return ; nothing at all but a return to the command prompt.

[INDENT][INDENT]checking
[INDENT][INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

