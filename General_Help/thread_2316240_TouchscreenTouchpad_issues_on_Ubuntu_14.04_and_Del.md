---
title: "Touchscreen/Touchpad issues on Ubuntu 14.04 and Dell XPS 13"
date: 2016-03-06
forum: General Help
---

### Post by maka on 2016-03-06
Hi all,  I recently installed ubuntu 14.04 on my Dell XPS 13 and most things are working well after a kernel 4.4.3 install and some other fixes for wifi, bluetooth that didn't work out of the box

Now, I am seeing that the the touchscreen does not seem to be working after a suspend.  I also noticed that syndaemon (which I use to disable the touchpad while typing via syndaemon -i 1 -KRd -t) works better after the suspend/resume vs cold boot

One thing I have been able to see a difference so far is that after a cold boot, I have two Touchpad input devices for some reason..

Just cold booted:
```

~  &#10140; xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; DLL0704:01 06CB:76AE Touchpad           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]
~  &#10140; 

```

After resume from suspend:
```

 &#10140; xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; DLL0704:01 06CB:76AE Touchpad           	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]

```

cat /proc/bus/input/devices
```

cat /proc/bus/input/devices                    
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 leds 
B: PROP=0
B: EV=120013
B: KEY=1100f02902000 8380307cf910f001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01a1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input8
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=13
B: KEY=101000b00000400 100000 e000000000000 0
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input9
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input10
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input11
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input12
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0003 Vendor=04f3 Product=20d0 Version=0110
N: Name="ELAN Touchscreen"
P: Phys=usb-0000:00:14.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:04F3:20D0.0001/input/input13
U: Uniq=
H: Handlers=mouse1 event12 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3273800000000003

I: Bus=0018 Vendor=06cb Product=76ae Version=0100
N: Name="DLL0704:01 06CB:76AE Touchpad"
P: Phys=i2c-DLL0704:01
S: Sysfs=/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-7/i2c-DLL0704:01/0018:06CB:76AE.0002/input/input15
U: Uniq=
H: Handlers=mouse2 event13 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=260800000000003

I: Bus=0003 Vendor=0c45 Product=670c Version=5626
N: Name="Integrated_Webcam_HD"
P: Phys=usb-0000:00:14.0-5/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input17
U: Uniq=
H: Handlers=kbd event14 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

```

Should I have 2 Touchpad input devices in the first place? Tailing the mouse handler in /dev/input (mouse0,mouse1,mouse2) the Synaptics mouse handler does not capture any events even when the touchpad is working.  So I assume that means that one is extraneous and the other one is the actual one used by kernel/OS.  My question is if it is not needed, how do I get rid of it since it may also be what is causing my conflicts with syndaemon not working?  Can this be related to why my touchscreen is also not working after resume from suspend...

Thanks!!

---

### Post by maka on 2016-03-07
Bump.. Anyone?

---

### Post by ddarling on 2016-03-26
Hi [COLOR=#000000]maka,

I picked up a Dell XPS 13 (9350) last week, and I've been having the same problem with syndaemon. It can make for a miserable experience if you can't get "disable touchpad while typing" to work.

To get things working properly, I needed to disable the second touchpad device "SynPS/2 Synaptics TouchPad".  I think it was mostly being ignored, and syndaemon was attaching to it instead of "DLL0704:01 06CB:76AE Touchpad", which was actually managing the touchpad.

I disabled it in the Xorg config file.  I opened:

[FONT=courier new]/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
[/FONT]
and added this entry:

[/COLOR]```

# Disable generic Synaptics device, as we're using
# "DLL0704:01 06CB:76AE Touchpad"
# Having multiple touchpad devices running confuses syndaemon
Section "InputClass"
        Identifier "SynPS/2 Synaptics TouchPad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/event*"
        Option "Ignore" "on"
EndSection

```[COLOR=#000000]

Then I restarted Xorg by typing:

[FONT=courier new]# sudo systemctl restart lightdm[/FONT]

And all was well.  I'm not an Xorg config guru, so there might be a more precise way to do this, but it got the job done.

The file location and restarting Xorg might be slightly different on 14.04 -- I'm on 16.04 Beta 2 since it has the 4.4 kernel which is needed for Wifi to work.

I hope this helps you keep typing in the window you intended!  FWIW, your hint at looking at "xinput list" is what got me going in the right direction for the fix, so thanks!



[/COLOR]

---

### Post by vanadium on 2016-05-20
@ddarling. I bumped into your answer, and this is it! I thank you very much! Indeed, disabling the Synaptics driver causes syndaemon to interact with the driver that is actually used, and finally disable touchpad while typing is working. I am also on a fresh install of Ubuntu 16.04 on the Dell XPS 13 9350, so I could adopt your instructions without any modication. 
>  And all was well. I'm not an Xorg config guru, so there might be a more precise way to do this, but it got the job done.
Looks like a very elegant solution to me, but then, I am even much less an Xorg config guru :)

---

### Post by Spud37 on 2016-09-13
I'm only seeing one touchpad on my Thinkpad and I'm having the issue of the touchpad not disabling so that i don't have to worry about accidentally bumping it. Any helps would be great. I figured asking here would be better then starting a new thread

---

### Post by ltrtiger2 on 2016-09-16
> **ddarling said:**
> Hi [COLOR=#000000]maka,  I picked up a Dell XPS 13 (9350) last week, and I've been having the same problem with syndaemon. It can make for a miserable experience if you can't get "disable touchpad while typing" to work.  To get things working properly, I needed to disable the second touchpad device "SynPS/2 Synaptics TouchPad".  I think it was mostly being ignored, and syndaemon was attaching to it instead of "DLL0704:01 06CB:76AE Touchpad", which was actually managing the touchpad.  I disabled it in the Xorg config file.  I opened:  [FONT=courier new]/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf [/FONT] and added this entry:  [/COLOR]```
 # Disable generic Synaptics device, as we're using # "DLL0704:01 06CB:76AE Touchpad" # Having multiple touchpad devices running confuses syndaemon Section "InputClass"         Identifier "SynPS/2 Synaptics TouchPad"         MatchProduct "SynPS/2 Synaptics TouchPad"         MatchIsTouchpad "on"         MatchOS "Linux"         MatchDevicePath "/dev/input/event*"         Option "Ignore" "on" EndSection 
```[COLOR=#000000]  Then I restarted Xorg by typing:  [FONT=courier new]# sudo systemctl restart lightdm[/FONT]  And all was well.  I'm not an Xorg config guru, so there might be a more precise way to do this, but it got the job done.  The file location and restarting Xorg might be slightly different on 14.04 -- I'm on 16.04 Beta 2 since it has the 4.4 kernel which is needed for Wifi to work.  I hope this helps you keep typing in the window you intended!  FWIW, your hint at looking at "xinput list" is what got me going in the right direction for the fix, so thanks!    [/COLOR]  Fantastic! This had been driving me crazy.  Thank you!!

---

### Post by mlabieniec on 2016-09-29
> **ddarling said:**
> Hi [COLOR=#000000]maka,

I picked up a Dell XPS 13 (9350) last week, and I've been having the same problem with syndaemon. It can make for a miserable experience if you can't get "disable touchpad while typing" to work.

To get things working properly, I needed to disable the second touchpad device "SynPS/2 Synaptics TouchPad".  I think it was mostly being ignored, and syndaemon was attaching to it instead of "DLL0704:01 06CB:76AE Touchpad", which was actually managing the touchpad.

I disabled it in the Xorg config file.  I opened:

[FONT=courier new]/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
[/FONT]
and added this entry:

[/COLOR]```

# Disable generic Synaptics device, as we're using
# "DLL0704:01 06CB:76AE Touchpad"
# Having multiple touchpad devices running confuses syndaemon
Section "InputClass"
        Identifier "SynPS/2 Synaptics TouchPad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/event*"
        Option "Ignore" "on"
EndSection

```[COLOR=#000000]

Then I restarted Xorg by typing:

[FONT=courier new]# sudo systemctl restart lightdm[/FONT]

And all was well.  I'm not an Xorg config guru, so there might be a more precise way to do this, but it got the job done.

The file location and restarting Xorg might be slightly different on 14.04 -- I'm on 16.04 Beta 2 since it has the 4.4 kernel which is needed for Wifi to work.

I hope this helps you keep typing in the window you intended!  FWIW, your hint at looking at "xinput list" is what got me going in the right direction for the fix, so thanks!



[/COLOR] 
 
Thank you! This worked for me as well on a dell xps 15 9550 running Ubuntu gnome 16.04 with kernel 4.6

---

### Post by piotrekot3 on 2016-12-14
Dell XPS13 MLK (9360), Ubuntu 16.04, solution worked very well. Thanks.

---

### Post by davduf2 on 2016-12-18
Hello All,

I get the ;ast XPS 13 Dev Edition (9360)
Everything's OK except the Mulitouch gesture with the Touchpad...
How to set up to get my touchpad working with 3 or 4 fingers...

I am on Ubuntu Gnome

All my best,
David

---

### Post by jas8n on 2017-01-17
Thank you, thank you, thank you, thank you....

Thank you for writing this and thank you to Google for helping me find this while I still have some hair in my head. This time last week I had a mane to be proud of...

---

### Post by corsseir on 2017-03-10
Dell Inspirion 5378 - works as well. Thank you for this solution.

---

### Post by alx-g on 2017-04-23
@ddarling

Thank you!!! This was driving me crazy. I did notice two touchpads when i ran xinput list but all the other "solutions" I found did not address that and didn't work for me. 

I'm running Ubuntu 16.04 on a dell xps 13 9350.

> **ddarling said:**
> Hi [COLOR=#000000]maka,

I picked up a Dell XPS 13 (9350) last week, and I've been having the same problem with syndaemon. It can make for a miserable experience if you can't get "disable touchpad while typing" to work.

To get things working properly, I needed to disable the second touchpad device "SynPS/2 Synaptics TouchPad".  I think it was mostly being ignored, and syndaemon was attaching to it instead of "DLL0704:01 06CB:76AE Touchpad", which was actually managing the touchpad.

I disabled it in the Xorg config file.  I opened:

[FONT=courier new]/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
[/FONT]
and added this entry:

[/COLOR]```

# Disable generic Synaptics device, as we're using
# "DLL0704:01 06CB:76AE Touchpad"
# Having multiple touchpad devices running confuses syndaemon
Section "InputClass"
        Identifier "SynPS/2 Synaptics TouchPad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/event*"
        Option "Ignore" "on"
EndSection

```[COLOR=#000000]

Then I restarted Xorg by typing:

[FONT=courier new]# sudo systemctl restart lightdm[/FONT]

And all was well.  I'm not an Xorg config guru, so there might be a more precise way to do this, but it got the job done.

The file location and restarting Xorg might be slightly different on 14.04 -- I'm on 16.04 Beta 2 since it has the 4.4 kernel which is needed for Wifi to work.

I hope this helps you keep typing in the window you intended!  FWIW, your hint at looking at "xinput list" is what got me going in the right direction for the fix, so thanks!



[/COLOR]

---

### Post by ncav2 on 2017-04-23
Hello!  I have a brand new Dell Inspiron 15 7579 2-in-1.  I've tried running both the following: USB Flash Drive with 17.04, USB external hard drive with 16.04 LTS.  In both the cursor jumps backwards when typing often.  I'm using external devices because I want to make sure ubuntu will work or I'll return the computer. Syndaemon and the touchpad app don't do anything to disable the touchpad when typing.  This solution looks promising so I tried entering in terminal "[COLOR=#000000] [FONT=courier new]/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf" and when I do this message appears:[/FONT][/COLOR]  "bash: /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf: Permission denied".  Not sure what I'm missing.  I would like to try this solution if possible!

I'm not too well-versed in the inner workings of using terminal in ubuntu.  Please let me know if you can help.  Thank you!!!


> **ddarling said:**
> Hi [COLOR=#000000]maka,

I picked up a Dell XPS 13 (9350) last week, and I've been having the same problem with syndaemon. It can make for a miserable experience if you can't get "disable touchpad while typing" to work.

To get things working properly, I needed to disable the second touchpad device "SynPS/2 Synaptics TouchPad".  I think it was mostly being ignored, and syndaemon was attaching to it instead of "DLL0704:01 06CB:76AE Touchpad", which was actually managing the touchpad.

I disabled it in the Xorg config file.  I opened:

[FONT=courier new]/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
[/FONT]
and added this entry:

[/COLOR]```

# Disable generic Synaptics device, as we're using
# "DLL0704:01 06CB:76AE Touchpad"
# Having multiple touchpad devices running confuses syndaemon
Section "InputClass"
        Identifier "SynPS/2 Synaptics TouchPad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/event*"
        Option "Ignore" "on"
EndSection

```[COLOR=#000000]

Then I restarted Xorg by typing:

[FONT=courier new]# sudo systemctl restart lightdm[/FONT]

And all was well.  I'm not an Xorg config guru, so there might be a more precise way to do this, but it got the job done.

The file location and restarting Xorg might be slightly different on 14.04 -- I'm on 16.04 Beta 2 since it has the 4.4 kernel which is needed for Wifi to work.

I hope this helps you keep typing in the window you intended!  FWIW, your hint at looking at "xinput list" is what got me going in the right direction for the fix, so thanks!



[/COLOR]

---

### Post by bernard-moreton-1 on 2017-04-30
I had the same problem on a Dell Inspiron 17 5000.  Taking out the second TouchPad worked, but sadly didn't solve the problem.  FTTB I've had to plug in a mouse and disable the touchpad...

---

### Post by 8086 on 2017-05-15
I thought I could just as well post an easier way: just disable the driver! [FONT=Courier New]lsmod[/FONT] showed psmouse as being loaded (but unused). [FONT=Courier New]rmmod psmouse[/FONT] will remove the driver, but you want this to happen automatically. In that case, just blacklist it by adding the following line to [FONT=Courier New]/etc/modprobe.d/blacklist.conf[/FONT]

```
blacklist psmouse
```

---

### Post by augustin-riedinger on 2017-06-08
Many thanks it worked for me too with XPS 13 (9360). Previously the synclient parameters were not taken in account, now they are!

---

### Post by gusm on 2017-06-15
Thanks ddarling!

syndaemon was getting confused with both input devices, disabling Synaptics' did solve the issue. I also noticed, that the Synaptic's input device was not appearing after the laptop is suspended, before the fix.

Thanks!

---

### Post by knerlington on 2017-08-09
Having LL0704:01 06CB:76AE Touchpad and SynPS/2 Touchpad listed in xinput and having entries for both in /proc/bus/input/devices this fix works, but after a while tapping and scrolling stops working. The cursor still works and of course the physical clicks.
Never happens in Windows or w/o the Section in the syn quirks config.
Ubuntu 17.04. Tried both 4.10, 4.11, 4.12 and 4.13 for a kernel. Driving me crazy. 
Palm detection and the ability to disable the touchpad while typing is crucial.

Since both touchpads show up in /proc/bus/input/devices the kernel supports or at least acknowledges them right?
Which one am I supposed to use? Is LL0704:01 06CB:76AE the real one and SynPS/2 just a generic one?

---

### Post by mest on 2017-11-16
> **knerlington said:**
> [...], but after a while tapping and scrolling stops working. The cursor still works and of course the physical clicks.[...]


Had the same behaviour on Dell XPS 13 9360 on Ubuntu 16.04 after disabling the generic Synaptics driver in xorg config and afterwards launching syndaemon with
```
syndaemon -i 1 -R
```

Meanwhile – the generic Synaptic driver still disabled – I start syndaemon with
```
syndaemon -i 1 -d -t -K
```
and everything works as expected, incl. tap-to-click and two-finger-scrolling.

---

### Post by smitherz822 on 2018-01-28
Thank you so much. I bought an Inspiron 15 the other week. Excellent hardware.
The ONLY problem I was facing with ubuntu was having to constantly watch there the cursor was after resting my palms.
It didn't even occur to me there would be two devices!

---

### Post by stefanmikulaj-k on 2018-01-29
> **mlabieniec said:**
> Thank you! This worked for me as well on a dell xps 15 9550 running Ubuntu gnome 16.04 with kernel 4.6

that worked like a charm! No more touchpad interference while typing. Thanks. :D

---

### Post by Tacuabe on 2018-06-19
I also have a Dell XPS13 9350 but my problem was how to _completely disable_ the Touchpad which, for my kind of work (CAD drawing), is useless and a nuisance.

I followed ddarling instructions to the letter as my xinput was identical. However, after a reboot or shutdown, the generical driver reappears in xinput. Moreover, commands such as Synaptic TouchpadOff=0 does not work. I also had a small batch program which used the id=# provided by xinput to turn off the Touchpad but this created a different issue because id=# change after booting and sometimes left me without keyboard.

The final solution was using the _name_ of the driver instead of its id. The bash file named TouchpadDis.sh ended as: 

#! /bin/bash
xinput set-prop 'DLL0704:01 06CB:76AE Touchpad' "Device Enabled" 0

Note that the name _must_ be enclosed within single quotes to work. I'm using Lubuntu 18.04 LTS so, besides adding TouchpadDis.sh to autostart, I also copied it to /usr/bin. Very happy with the end result.

---

