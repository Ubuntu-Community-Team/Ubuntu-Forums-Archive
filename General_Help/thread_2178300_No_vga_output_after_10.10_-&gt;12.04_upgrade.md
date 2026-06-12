---
title: "No vga output after 10.10 -&gt;12.04 upgrade"
date: 2013-10-02
forum: General Help
---

### Post by satpal_chander on 2013-10-02
Hi All,
I have a HP Microserve N36L which i've been running for about 3 years.
It's been running 10.10 all this time, so I thought it was about time to update to the latest LTS release of Ubuntu server (12.04)
So I performed the upgrades 10.10 -> 11.04 -> 11.10 -> 12.04. I have a big 27" 2560x1440 monitor with vga input fed by the n36l.
Up until the last release upgrade the output has been fine and I've been able to see a login screen after boot.

When I rebooted into 12.04 I saw the HP boot screen and the grub selection screen, after that though it goes dark and the login prompt doesn't appear.
I couldn't understand what was going on so I dug out an old 19" 1280x1024 monitor. Switched the cable from the 27" to the smaller monitor and got a signal out of range error. I then rebooted the box from a ssh session with the cable plugged into the smaller monitor and everything was fine, i could see the login screen.

Does anyone know what I need to do to get the login screen appearing again on my big monitor, as i'd rather not have two monitors sitting in the room.
Is it as simple as setting nomodeset in the /etc/default/grub GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

Thanks
Satpal

---

### Post by mörgæs on 2013-10-03
Moved, as it is not a server specific question.

---

### Post by satpal_chander on 2013-10-03
> **mörgæs said:**
> Moved, as it is not a server specific question.

I'm not quite sure why this was moved as i'm using Ubuntu Server, edition, LTS 12.04?

Thanks
satpal

---

### Post by grahammechanical on 2013-10-03
First of all you need to understand what is happening and what is not happening. Ubuntu 12.04 will use the VGA output in the same way that the other versions of Ubuntu did. But ask yourself this question: How does Ubuntu know the screen resolution of your monitor? During installation were we asked to give information about the screen resolution of the monitor? So, how does Ubuntu know this?

Modern monitor's have information about the optimum screen resolution stored in their electronic components. It is called EDID (Extended Display Identification Data). When Ubuntu loads it reads this EDID information and sets the screen resolution accordingly. Ubuntu sets the screen resolution after the Grub menu has loaded but before the login screen appears.

Now consider what happened in your case. You changed monitors after Ubuntu had set its screen resolution to that of the 27" monitor and you used a monitor that did not run at the same resolution as the 27" monitor. This is why you got a signal out of ranger error. And it is a good thing that you did get that error as continuing would have damaged the smaller monitor. But once you rebooted then Ubuntu was able to run the screen at the resolution appropriate for the smaller monitor because it read the EDID of the smaller monitor.

This problem is less likely to do with 12.04 not giving a VGA output (that is a function of the graphic card anyway) but more likely to do with the video driver that came with 12.04 not being compatible with the graphic adapter.

At the Grub menu select Recovery Mode. At the Recovery menu select Resume. That should bring you to a working desktop without using a proprietary video driver. In a way it is the same as using nomodeset. Then run Additional Drivers utility and experiment with the video drivers available. Often we need to experiment with video drivers. That is why we are offered a selection. As this is a server you may want to use Nouveau.

Regards.

---

### Post by mörgæs on 2013-10-03
> **satpal_chander said:**
> I'm not quite sure why this was moved as i'm using Ubuntu Server, edition, LTS 12.04?


The server forum is meant for server (as in "a computer listening for a request and giving an answer") *specific* questions like "how do I get write access to vsftpd?"

The problem you describe could also happen on a stand-alone desktop. Though you are working on a server the problem and the likely solution are the same as on a desktop.

---

### Post by Yellow Pasque on 2013-10-03
Give the /var/log/Xorg.0.log file. Use [ code ][ /code ] tags.

---

### Post by satpal_chander on 2013-10-03
> **mörgæs said:**
> The server forum is meant for server (as in "a computer listening for a request and giving an answer") *specific* questions like "how do I get write access to vsftpd?"

The problem you describe could also happen on a stand-alone desktop. Though you are working on a server the problem and the likely solution are the same as on a desktop.
Thanks for explaining that. Makes sense now.

> **grahammechanical said:**
> First of all you need to understand what is happening and what is not happening. Ubuntu 12.04 will use the VGA output in the same way that the other versions of Ubuntu did. But ask yourself this question: How does Ubuntu know the screen resolution of your monitor? During installation were we asked to give information about the screen resolution of the monitor? So, how does Ubuntu know this?

Modern monitor's have information about the optimum screen resolution stored in their electronic components. It is called EDID (Extended Display Identification Data). When Ubuntu loads it reads this EDID information and sets the screen resolution accordingly. Ubuntu sets the screen resolution after the Grub menu has loaded but before the login screen appears.

Now consider what happened in your case. You changed monitors after Ubuntu had set its screen resolution to that of the 27" monitor and you used a monitor that did not run at the same resolution as the 27" monitor. This is why you got a signal out of ranger error. And it is a good thing that you did get that error as continuing would have damaged the smaller monitor. But once you rebooted then Ubuntu was able to run the screen at the resolution appropriate for the smaller monitor because it read the EDID of the smaller monitor.

This problem is less likely to do with 12.04 not giving a VGA output (that is a function of the graphic card anyway) but more likely to do with the video driver that came with 12.04 not being compatible with the graphic adapter.

At the Grub menu select Recovery Mode. At the Recovery menu select Resume. That should bring you to a working desktop without using a proprietary video driver. In a way it is the same as using nomodeset. Then run Additional Drivers utility and experiment with the video drivers available. Often we need to experiment with video drivers. That is why we are offered a selection. As this is a server you may want to use Nouveau.

Regards.
Firstly thank you for your very detailed response. Yes your right about the driver. I did some more googling and found that setting nomodeset did infact solve the problem to an extent, I can see the server login screen now.  I understand what nomodeset does from [this answer]("http://askubuntu.com/a/207177") and was able to set it by editing the grub over ssh and rebooting.
I can't check the last bit easily as I don't have a windowing system installed on the box.
The output of a couple of command i found on the internet to try and decode what was going on: ```
sudo lshw -c video
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS880M [Mobility Radeon HD 4225/4250]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff ioport:e000(size=256) memory:fe8f0000-fe8fffff memory:fe700000-fe7fffff

```
```
dmesg | egrep 'drm|radeon'
[    3.026229] [drm] Initialized drm 1.1.0 20060810
[    3.085958] [drm] VGACON disable radeon kernel modesetting.
[    3.102311] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.102318] [drm] No driver support for vblank timestamp query.
[    3.102325] [drm] Initialized radeon 1.33.0 20080528 for 0000:01:05.0 on minor 0

``` 
```

udo get-edid |parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful


    VBE version 300
    VBE string at 0xc01d4 "ATI ATOMBIOS"


VBE/DDC service about to be called
    Report DDC capabilities


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful


    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer


Reading next EDID block


VBE/DDC service about to be called
    Read EDID


    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful


parse-edid: EDID checksum passed.


    # EDID version 1 revision 4
Section "Monitor"
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
    Identifier "DGM27 VGA"
    VendorName "DGM"
    ModelName "DGM27 VGA"
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fd
    HorizSync 15-99
    VertRefresh 23-76
    # Max dot clock (video bandwidth) 250 MHz
    # Block type: 2:0 3:fc
    # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes


    Mode     "2560x1440"    # vfreq 59.951Hz, hfreq 88.787kHz
        DotClock    241.500000
        HTimings    2560 2608 2640 2720
        VTimings    1440 1443 1448 1481
        Flags    "+HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:ff
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:fc
EndSection

```
It seems to me that default video driver in 12.04 doesn't support the gfx card in the microserver(n36l). Is there a driver for the radeon 4225/4250 on 12.04?
[COLOR=#000000]Nouveau is for Nvidia GFX card and not ATI.[/COLOR]

> **Temüjin said:**
> Give the /var/log/Xorg.0.log file. Use [ code ][ /code ] tags.
Unfortunatly as I say above I have no windowing system installed and therefore no /var/log/Xorg.0.log

Thanks for all you help on this.
Satpal

---

### Post by Yellow Pasque on 2013-10-03
> **satpal_chander said:**
> It seems to me that default video driver in 12.04 doesn't support the gfx card in the microserver(n36l).

It does, but it's not working well for some reason. Did you have proprietary drivers installed on the previous versions of Ubuntu?

---

### Post by satpal_chander on 2013-10-04
> **Temüjin said:**
> It does, but it's not working well for some reason. Did you have proprietary drivers installed on the previous versions of Ubuntu?
It was a stock install of 10.10 when i started and don't recall adding a gfx driver specifically. The problem only occured when I went from 11.10 to 12.04.
Which is the same time frame they moved some gfx stuff to the kernel if I read the stuff on internet correctly.

Thanks
Satpal

---

