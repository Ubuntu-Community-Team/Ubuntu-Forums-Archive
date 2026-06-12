---
title: "Upgrading to a LCD monitor"
date: 2006-12-01
forum: General Help
---

### Post by DeanT on 2006-12-01
I've currently got a CRT monitor running on Edgy 6.10.  The display refresh rate is currently set at 85hz.

I've bought myself a new Dell LCD monitor.  Will Edgy automatically detect the new monitor or will I need to tweak some config files?

For example, I know that LCD monitors typically use a screen refresh rate of 60Hz.  I presume there is a config file somewhere which has my CRT monitor details stored in it.

I'm concerned that trying to simply plug the new LCD monitor in won't work because Ubuntu will still be trying to run at 85Hz.

Any hints/advice appreciated.

---

### Post by Cronjob on 2006-12-01
If it doesn't work automatically, then I believe you can run a xorg reconfig with this:

> sudo dpkg-reconfigure xserver-xorg


You can also just pop in a Live-CD to see if that will automatically detect and display on your monitor (most likely, it will) and then you could take the xorg.conf file from that and copy it to your installed version (or at least, take out and copy the important elements).

Note that I am uncertain if this is the "proper" way to accomplish this, but I think it should work. Take appropriate precautions like backing up your config file and such, of course.

---

### Post by frodon on 2006-12-01
Amazing i'm going to do the same thing in 3 hours :), i will just boot with my new LCD and run a : ```
sudo dpkg-reconfigure xserver-xorg
```Then i'll make few edits in my xorg.conf like adding the refresh rates parameter of my LCD but it's not inescapable.

---

### Post by princemackenzie on 2006-12-01
My widescreen monitor was never configured correctly with the xorg configurator :rolleyes: 

I had to use this

> Using the gtf Command

The gtf command outputs a ready-to-use Modeline statement for your monitor given the input of resolution and vertical refresh rate of your monitor. To create the correct information for the Modeline statement, look at your monitor's manual and determine its exact native resolution and precise vertical refresh rate for that resolution. For the Envision H193wk, it is listed as 1440 by 900 at 60Hz.

Plug these values into the gtf invocation:

[root@compy ~]# gtf 1440 900 60

yielding:

# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync

The first line is a comment and need not be transferred. Paste or transcribe the Modeline anywhere inside the "Monitor" section that is referred to by the "Screen" section. Then make sure the "Screen" section includes the mode defined by your Modeline statement:

Section "Monitor"
    Identifier    "h193wk"
    Modeline      "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync
EndSection

(...)

Section "Screen"
    Identifier    "Screen1"
    Device        "nvidia0"
    Monitor       "h193wk"
    Subsection "Display"
        Depth     24
        Modes     "1440x900_60.00"
        ViewPort  0 0
    EndSubsection
EndSection

Running startX should yield an X session matching your monitor's resolution.

Before inserting the Modeline statement into your xorg.conf file, create a copy of xorg.conf so you can revert to the machine generated file if necessary.

If you have a problem after starting X, you may kill the X session by pressing <ctrl-alt-Backspace>. 

Which I shamelessly ripped from the caos linux wiki, which is down.

---

### Post by DeanT on 2006-12-01
> **frodon said:**
> Amazing i'm going to do the same thing in 3 hours :), i will just boot with my new LCD and run a : ```
sudo dpkg-reconfigure xserver-xorg
```Then i'll make few edits in my xorg.conf like adding the refresh rates parameter of my LCD but it's not inescapable.

Does that mean you have to boot up to a command line?  

I'm thinking that when Ubuntu boots up, if it doesn't detect the LCD Monitor then I won't get to see the logon screen.  The display might be all garbled or not display at all.  Do I need to get to the command line before the login screen appears?

Thanks.

---

### Post by Cronjob on 2006-12-01
It's unlikely that your display won't work. It might not show at the right resolution, but you should at least come to the login screen without a problem. If for some reason it doesn't, you can always shut down and plug the other monitor back in and go the Live-CD route so you can use the xorg.conf the live-cd setups.

I've used several LCDs over time and they always show a display, even if it's at a wonky resolution and I have to mouse around to scroll the entire display -- so I think you'll be okay. And yes, you do need to run that from the command line, but you can just select "command line/shell" from the drop-down on the login menu (where you would choose to boot into another window manager, for example).

---

### Post by DeanT on 2006-12-04
As I expected when I plug the LCD monitor in I do not see any login screen.  The only time I see anything on the screen is when the PC boots up and I see the GRUB menu.  As soon as Ubuntu starts to boot up I see nothing.  I see the Ubuntu splash screen but that's it.  I don't see a login screen.  I get a message from the LCD monitor saying 'Cannot Display This Video Mode'.

I tried booting from the Live CD and choosing 'Install Ubuntu' but I get the same 'Cannot Display This Video Mode' message displayed on the screen.

I can boot into Windows XP no problem so the monitor is not faulty.

Is there any way I can get to a command line whilst Ubuntu is booting up but before the GUI login screen kicks in.

Thanks.

---

### Post by kaigarabushi on 2006-12-04
Please excuse this unsolicited attention but as you seem obviosly able to get a display and I think it has to do with a Sunfire V100 system you may be able to help me!
I don't know how to attach my Sunfire V100 to a standard monitor to get display??? as there arent any 15 pin VGA connections on the box. Do you understand my predicament? If you could point me in the right direction I would be very appreciative!!

---

### Post by Cronjob on 2006-12-06
> **kaigarabushi said:**
> Please excuse this unsolicited attention but as you seem obviosly able to get a display and I think it has to do with a Sunfire V100 system you may be able to help me!
I don't know how to attach my Sunfire V100 to a standard monitor to get display??? as there arent any 15 pin VGA connections on the box. Do you understand my predicament? If you could point me in the right direction I would be very appreciative!!

I'm a Sun guy, though not a hardware guy, but I believe you may need a Sun 13W3-VGA Adapter.

---

