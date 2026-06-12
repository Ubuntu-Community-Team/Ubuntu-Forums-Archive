---
title: "Ubuntu 16.04 on Lenovo Thinkpad X1 Tablet (May 2016 Edition)"
date: 2016-05-26
forum: General Help
---

### Post by kjano on 2016-05-26
FYI and in case you are interested in the device; this is actually hard to believe but Ubuntu 16.04 runs perfectly with almost all features out of the box on the new Lenovo Thinkpad X1 Tablet.

**Tested and works:**
[LIST]
[*]Plug-able keyboard
[*]Pen
[*]Touchscreen
[*]Sound and display brightness buttons
[*] Suspend (no kidding!)
[*] Detaching or attaching the keyboard
[*] Speakers and mic
[*] External screen (also via external battery module)
[/LIST]


**Tested and does not work (out of the box):**
[LIST]
[*] Webcam
[*] Rotating the screen without breaking touch (this should be easy to fix)
[/LIST]

**Not tested:**
[LIST]
[*] ...
[/LIST]

The performance of my i5, 8GB, 256 GB SSD version seems to be good so far. Battery seems good for about 5-6 hours.

I hope this is helpful. I will update the posting as I learn more about the device. Please feel free to ask questions. I will also test other Linux distributions like Arch Linux later.

---

### Post by nex2 on 2016-05-30
Hi kjano!

Nice to read this! I am interested in the X1 Tablet, too, and going to install ubuntu on it once i have it :)
Some questions / comments:
1)  in the title u say "May 2016 Edition". Are there other Editions on the X1 Tablet available for purchase which might cause problems regarding ubuntu installation?
2) Regarding the issue: "Rotation the screen without breaking touch". If you know the "easy to fix"-solution, please let us know! :)
3) What is your experience with battery runtimes when using Linux Ubuntu compared to using Windows 10? 

Thanks a lot!
nxs

---

### Post by kjano on 2016-05-31
Hi nex2,

I have never used Windows 10 before and my X1 Tablet is only running Linux so I cannot comment on that part of your posting -- sorry for that.

The battery is indeed not the strongest aspect of the X1. I have to use it a bit more to give you a useful estimate. So far I can get about 5-6 hours of runtime with 70% display brightness while running a tex editor and compiling medium-sized PDFs from time to time, browsing with about 20 open Firefox tabs, and using Java/Eclipse. I also have the external battery module but have not used it so far.

Wrt the screen rotation, I tried this one but it did not work: [http://linuxappfinder.com/blog/auto_screen_rotation_in_ubuntu](http://linuxappfinder.com/blog/auto_screen_rotation_in_ubuntu) . Of course, you can easily do this manually by running randr and a script every time but this is not fun.

---

### Post by nex2 on 2016-06-01
Hi kjano,

thanks for the response.
Meanwhile, i got my X1, too :)
I have installed ubuntu next to windows 10, so, lets see how ubuntu works in comparison on the x1.

I have not yet done more than just installing ubuntu so far.

However, so far, i have discovered the following issues already:

1) The keyboard's trackpoint does not work out-of-the box but only the trackpad. Any clue on how to configure that? And is it possible to disable the trackpad instead? I tend to accidentally touch the trackpad which results in unexpected actions :)
2) On ubuntu, it seems that the X1 cannot be used without a keyboard attached. Is there a way to configure a onscreen keyboard?
3) Usually, i am a fan of xfce but i expect more issues with a touchscreen device than with unity. Any experiences with in this regard?

Thanks,
nxs

---

### Post by gaussian on 2016-06-02
Nex2,

I am about to order mine, I have been encouraged by you and kjano reporting it works fairly well. Couple comments on your questions:

1) Trackpoint: As is often the case, Arch Linux documentation has some info on Thinkpad Trackpoints: [https://wiki.archlinux.org/index.php/TrackPoint](https://wiki.archlinux.org/index.php/TrackPoint)  
So it looks like there is hope that it can be done.

2) Install/configure Onboard for your screen keyboard. It is quite good.

---

### Post by nex2 on 2016-06-02
@gaussian

Thanks for the hints!

[
MAYBE OFFTOPIC:
I tested a bit installation / performance of Android Emulators / OSes on my X1 with m7 CPU.  I did that because I have one Android App (LectureNotes) which i really would miss if i couldn't use it anymore. (LectureNotes is an notebook app for taking notes with a pen. The best I have seen so far :) ) So, I tested BlueStacks (perfermance ok, freezes too often) for Windows and Andy (perfomance ok & stable) for Windows AND Linux. Unfortunately, i couldn't yet test Andy on ubuntu but it runs pretty stable on windows and in a decent performance -- though, for using LectureNotes it is not ideal (-- not necessarily due to the performance. If someone wants to know more, ask me in private. I am not sure if people are happy in an ubuntu forum when I am talking about android emulation advantages and disadvantages). The best I can recommend, however, is RemixOS. When installed on an own partition, extremely fast on the X1 and rock stable.
]

So, all in all, I am pleased with the performance when running ubuntu, too, although, I have not yet done anything that is really CPU hungry. I just observed that the tablet gets very, very hot when used it a lot. How and if that influences CPU performance, I don't know yet. I mainly installed, removed, restarted, copied from USB to SSD, restarted OS, etc but almost constantly for about 4-5h. By doing that, the battery lasted not very long at most those 4-5h. On the surprising side, the battery charging is extremely quick! I haven't measured the time but it felt like back to 90% in 30 minutes or even faster :).

I couldn't test yet the included WiGig-Dock with ubuntu. My guess is, that it won't work on ubuntu because even on windows u need to start a dedicated program for establishing the connection -- and it didn't even work on windows for me. I have not invested too much time on that, though. 

What really is a big fail: My screen shows color errors on bright backgrounds. The X1 comes with a black windows desktop background, so I didn't realized that immediately. However, when using something with a white background (like LectureNotes ;) ) the edges and especially the corners of the display are yellow instead. Hence, i removed everything from my X1 tablet again (sigh :( ) and sent it back. So, watch your display corners ;). Nevertheless, I will buy another one when I get back my money because I enjoyed using it and having a system capable of running windows 10 pro, (x)ubuntu and android is pretty cool :)

cheers,
nxs

---

### Post by ahmed-guellil on 2016-06-07
Hi,

I can confirm that there is only a few problems with Ubuntu 16.04 on the Lenovo X1 Tablet.

I have the LTE version and I don't know if it's possible but it would be great if one could install Ubuntu Touch on it ; the modem is a Sierra EM7455.

As said before, Cameras and Trackpoint don't work out of the box, and it's the same for the Fingerprint Scanner. Also, the three buttons located between the Space key and the Touchpad are not mapped correctly.

Right now I'm trying to get the Trackpoint working, but no success so far...

Here is what I found :
- Both the Touchpad and Trackpoint are detected by the BIOS. There is no option to activate/deactivate them.
- The Touchpad works in Ubuntu 16.04 but doesn't appear in the "Mouse & Touchpad" settings.
- The **xinput** command gives me the following output :
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PRIMAX ThinkPad X1 Tablet Thin Keyboard     id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 5077 Pen stylus                   id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 5077 Finger touch                 id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 5077 Pen eraser                   id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; PRIMAX ThinkPad X1 Tablet Thin Keyboard     id=9    [slave  keyboard (3)]
    &#8627; PRIMAX ThinkPad X1 Tablet Thin Keyboard     id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=15    [slave  keyboard (3)]

```
The Trackpoint doesn't seem to be listed, but when the slave pointer 11 is disabled, the Trackpad and the buttons associated with the Trackpoint are deactivated.
- The **sudo dmidecode -t 21** command gives me this output :
```

# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.

Handle 0x0034, DMI type 21, 7 bytes
Built-in Pointing Device
    Type: Track Point
    Interface: PS/2
    Buttons: 3

Handle 0x0035, DMI type 21, 7 bytes
Built-in Pointing Device
    Type: Touch Pad
    Interface: PS/2
    Buttons: 2

```

---

### Post by ahmed-guellil on 2016-06-08
I think I made some progress for the Trackpoint.

The **xinput --list-props 11** command gives me :
```

Device 'PRIMAX ThinkPad X1 Tablet Thin Keyboard':
    Device Enabled (137):    1
    Coordinate Transformation Matrix (139):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (262):    0
    Device Accel Constant Deceleration (263):    1.000000
    Device Accel Adaptive Deceleration (264):    1.000000
    Device Accel Velocity Scaling (265):    10.000000
    Device Product ID (257):    6127, 24709
    Device Node (258):    "/dev/input/event9"
    Evdev Axis Inversion (266):    0, 0
    Evdev Axes Swap (268):    0
    Axis Labels (269):    "Rel X" (147), "Rel Y" (148), "Rel Z" (274), "Rel Rotary X" (275)
    Button Labels (276):    "Button Left" (140), "Button Middle" (141), "Button Right" (142), "Button Wheel Up" (143), "Button Wheel Down" (144), "Button Horiz Wheel Left" (145), "Button Horiz Wheel Right" (146), "Button Side" (272), "Button Extra" (273)
    Evdev Scrolling Distance (270):    0, 0, 0
    Evdev Middle Button Emulation (277):    0
    Evdev Middle Button Timeout (278):    50
    Evdev Third Button Emulation (279):    0
    Evdev Third Button Emulation Timeout (280):    1000
    Evdev Third Button Emulation Button (281):    3
    Evdev Third Button Emulation Threshold (282):    20
    Evdev Wheel Emulation (283):    0
    Evdev Wheel Emulation Axes (284):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (285):    10
    Evdev Wheel Emulation Timeout (286):    200
    Evdev Wheel Emulation Button (287):    4
    Evdev Drag Lock Buttons (288):    0

```

As you can see, the slave pointer 11 is associated with the node [I]/dev/input/event9.
[/I]
I typed **sudo cat /dev/input/event9** to monitor the input devices and it displays characters when I use the Trackpoint, the Trackpoint-related buttons, the Touchpad, and the Touchpad embedded buttons.

Then I typed **sudo cat /dev/input/mice** and it would display characters only for the Touchpad and its embedded buttons.

So, I think that the Touchpad, the Trackpoint and their buttons are all linked to the same device node, but for some reason only the Touchpad and its buttons are taken into account.

I'm not a Linux expert so it would be great if someone could help me understand this.

---

### Post by leanux7 on 2016-06-19
Hi, thank you very much for sharing your experiences with the X1 tablet.


I'm very interested in the tablet for replace mi old but very trusty ThinkPad X60 that has 10 years old now. I'm a Debian user since 2002 and ThinkPad user from a long time ago. My question is if any of you can test the displayport on a external monitor, for me is very very important, I read that in the Surface Pro 4 the displayport doesn't work in Ubuntu out of the box, and otherwise crashes X server ramdom. If any of you have the time for test the displayport on Linux I would be very grateful.


I'm not a native english speaker, so, sorry if any of my words aren't correct

---

### Post by Etrnls on 2016-06-19
Same issue with Trackpoint here, basically the trackpoint movements are mapped to "Rel Z" and "Rel Rotary X" instead of "Rel X" and "Rel Y", you can confirm this by running evtest /dev/input/event9.

And I found the solution here [https://bbs.archlinux.org/viewtopic.php?pid=1202655#p1202655](https://bbs.archlinux.org/viewtopic.php?pid=1202655#p1202655), it's a different device but exactly the same problem and the solution works here as well: add this to kernel boot param "usbhid.quirks=0x17ef:0x6085:0x40" (or at module loading time "modprobe usbhid quirks=0x17ef:0x6085:0x40")
0x17ef is vender id of LENOVO
0x6085 is product id of PRIMAX ThinkPad X1 Tablet Thin Keyboard
0x40 is HID_QUIRK_MULTI_INPUT

---

### Post by nex2 on 2016-06-24
Hi Etrnls,

thanks for the solution hint! I still do not have my thinkpad X1 tablet back, but I am glad there is a easy workaround.
Do you also know if it is possible to disable the trackpad and only enable the usage of the trackpoint?

Thanks!
nxs

---

### Post by h3ndrik on 2016-06-28
Is the touchpad even working correctly? I think it is supported via some generic driver, because I'm missing out on scrolling (two-finger/edge both not working) too.
("synclient -l" doesn't show anything.)

---

### Post by leif-dkstat on 2016-07-06
@h3ndrik Yes that support is mouse emulation. The touchpad is supported under Windows with a Synaptics driver and I have tried to get the Linux Synaptics driver to work with it without success. Under Windows it shows up as "USB Composite Device" with VID:PID 17EF:6085. The Linux Synaptics driver only looks at devices with VID=[COLOR=#000000]06CB.[/COLOR]

---

### Post by nex2 on 2016-07-07
> **Etrnls said:**
> Same issue with Trackpoint here, basically the trackpoint movements are mapped to "Rel Z" and "Rel Rotary X" instead of "Rel X" and "Rel Y", you can confirm this by running evtest /dev/input/event9.

And I found the solution here [https://bbs.archlinux.org/viewtopic.php?pid=1202655#p1202655](https://bbs.archlinux.org/viewtopic.php?pid=1202655#p1202655), it's a different device but exactly the same problem and the solution works here as well: add this to kernel boot param "usbhid.quirks=0x17ef:0x6085:0x40" (or at module loading time "modprobe usbhid quirks=0x17ef:0x6085:0x40")
0x17ef is vender id of LENOVO
0x6085 is product id of PRIMAX ThinkPad X1 Tablet Thin Keyboard
0x40 is HID_QUIRK_MULTI_INPUT

I finally got back my Thinkpad X1 Tablet. However, the fix u mentioned here seems not to work (or I am doing something in a wrong way). Could u elaborate more exactly how the kernel boot parameter can/should be set to the existing ones in the grub config?

---

### Post by leif-dkstat on 2016-07-07
It looks like this is an RMI4 device but it uses the F12 function rather than the F11 function. This patch may help:

[https://github.com/aduggan/linux/commit/8446f962ba918df9aa77ec8e4363e2a51dfbef09](https://github.com/aduggan/linux/commit/8446f962ba918df9aa77ec8e4363e2a51dfbef09)

---

### Post by nex2 on 2016-07-08
> **nex2 said:**
> I finally got back my Thinkpad X1 Tablet. However, the fix u mentioned here seems not to work (or I am doing something in a wrong way). Could u elaborate more exactly how the kernel boot parameter can/should be set to the existing ones in the grub config?

I have to correct myself. I just mistyped the parameters :(
So, indeed the trackpoint is working correctly afterwards.

Nevertheless, I have to send back my X1 tablet another time. The new one I got suffered from the same yellow-corner problem on bright backgrounds :( 
Do I have so much bad luck or is this a general problem of the X1 display? Anyone else with such display color problems? :(

cheers,
nxs

---

### Post by laigood12345 on 2016-07-18
I think the yellow-corner problem is a common problem,my x1t the same,but only in white background

---

### Post by gaussian on 2016-08-22
Finally got mine. Couple of questions, some general, some Ubuntu specific:

1) Has anyone had any progress getting the touchpad gestures (scrolling) working?

2) Anyone know how to configure the touchscreen so that "single-finger hold and move" scrolls the screen?

3) Any other ideas how to configure scrolling on this device (I know you can hack the scroll bars to be wider)? I know you can scroll with two fingers on the touchscreen or with holding down the (tiny) scroll bar button.

4) Not an Ubuntu question: Does anyone have an issue of the keyboard disconnecting from slightest (or even not at all) movement? I guess I have to ship it back to Lenovo. Just to clarify: I have used a Surface Pro 4 and never had this issue.

---

### Post by gmalone on 2016-08-30
I would love to know if this possible solution to touchscreen for Surface Pro 4 has been tried, and if successful, with what parms.  Will continue reviewing threads here to see.  Thanks if any help.

---

### Post by gaussian on 2016-09-01
Gmalone: Do you mean some Surface Pro 4 fix should be relevant here for Thinkpad X1 Tablet? The hardware, while superficially similar, is very different. Or are you talking about Surface Pro 4 and its (many many many) problems with Ubuntu?

Sadly I don't have my Tablet X1 right now, I am also Gaussian in this thread [https://forums.lenovo.com/t5/ThinkPad-X-Series-Tablet-and/Lenovo-X1-tablet-keyboard-stops-working/td-p/3398194](https://forums.lenovo.com/t5/ThinkPad-X-Series-Tablet-and/Lenovo-X1-tablet-keyboard-stops-working/td-p/3398194)
I am hoping it is a hardware problem they can fix.

---

### Post by gmalone on 2016-09-01
gaussian:  Thanks for the followup.  I had seen your reference to having used an SP4 before -- presumably w/ Ubuntu.  However, looking back over this thread I realize it was a stupid question I asked... because of course the SP4 and Lenovo Thinkpad X1 are entirely different devices.  Duh.  Sometimes when casting about for info -- in this case, for info on getting the touchscreen working in Ubuntu 16.04 on a Surface Pro 4 -- I (we?) err.  Haste makes waste, no?

While I'm here, I'll say that I did get the Type Cover keyboard working on the SP4 w/ 16.04... using the tigerite solution found in many places.  The touchscreen (and associated stylus) is all that remains in my quest.

Thanks again.

---

### Post by gaussian on 2016-09-01
No problem. I tried a Surface Pro 4 and decided that I don't want one due to the touchscreen/pen situation. For me, the main reason for getting a 2-in-1 was the pen. Basically, I wanted a dedicated Xournal machine.

---

### Post by m.bousherie on 2016-10-05
Hi Guys,

I followed this thread quite a while and it was my major motivation to actually buy the Lenovo X1 Tablet. The threat made me very confident that it is possible to run Ubuntu in case Windows10 is as bad as expected.
Very soon after purchasing the device it turned out that Windows is not usable at a glance. Only for the star: I could not connect to my Wi-Fi ([Radius]("https://support.microsoft.com/en-us/kb/3121002")[-()... (Don’t worry Wi-Fi at Starbucks is working:shock:)

However with Ubuntu I can use the device basically as a Laptop. Really great Job!!! (I have to admit, that I am not a Debian geek. So my ability’s to solve problems are very limited...) my interest to use Ubuntu is super high because the dispossession conducted by the leading software houses is not longer acceptable. (Despite the fact that most OS are just not optimized to be used but to spy on the user)

However, there is one mayor issue I got with Ubuntu:
The device(CoreM7 version) is heating up like a "deep fat fryer" and there is nothing I can do about it. At least, I did not find any way to tune down this behavior. Also the battery is burned down super quick (like 1.5-2h). Is there a way to activate a power save mode as it is active on Windows?

I also found that the following hardware is not working out of the box:
Webcam (Back and front)
Flash light (I did not find a way to activate it)
The wigig dock (It does not react if you put it close to the wigig dock :confused:... I don’t know how to approach this either)
The TrackPoint
Fingerprint scanner

I did not test:
the LTE module
NFC
Bluetooth
... if there is some interest I could test it.

If there are any suggestion or at least some hope that the missing features will be added. Please let me know.

---

### Post by gaussian on 2016-10-06
Hello m.bousherie:

Battery/heat issue:

1. I personally ordered an M5 version because I had read some reviews that complained about heat issues with (in Windows use) the M7.

2. Linux often (but not always) has slightly worse battery life than Windows

3. I get about 5-6 hours with M5, I think. Haven't been paying attention and now Lenovo has my machine for totally unrelated repairs.

4. Having said that: your experience is not normal. And I don't think this is about the powersave mode. An Intel CPU should be on the "On Demand" mode without any tweaking. There are lengthy debates online on whether the other modes 
actually even save any energy (beyond downclocking). My hunch is that something is wrong with your installation, some program/process is running and using all that CPU power. I would start hunting for the runaway process issue with the command-line command top. It might take some time to actually pin down what is wrong.

5. If you want to squeeze every last volt out of your battery, then there are two tools: powertop and laptopmode that are useful. But tweaking those is often unnecessary, I have not used them for my X1 Tablet.


As for your list of hardware that does not work: check this thread for how to fix the trackpoint. For me the much bigger issue is the fact that none of the gestures work with the touchpad, since the touchpad is recognized only as a standard mouse. So no two-finger scrolling etc.

---

### Post by m.bousherie on 2016-10-10
Thanks for your reply and the good hint with Program consuming on idle! Using TOP I see a kworker thread that remains on 50% of my CPU power (which might be 100% depending on how the multi-threadin is counted:confused:). I tried to find the reason for that thread using the following [page...]("https://raw.githubusercontent.com/torvalds/linux/master/Documentation/workqueue.txt") I did not find what process is behind this...

I also updated the system... but it did not changed the issue...

However if this issue can be solved as quickly as I think Ubuntu will become my no1 option for this convertible. 

Still I will have to figure out some ways to use Ubuntu in tablet mode but that should be fine... like a working onboard kebort for signin.

---

### Post by gaussian on 2016-12-19
Bump: Has anyone made any progress with the touchpad, getting the gestures to work? I got my X1 back after months at Lenovo and I currently have only Windows 10 and WSL (Ubuntu on Windows) thing going on, but wondering if there is any hope with a newer version of proper Ubuntu or other distro to get things working.

EDIT: I tried several live edition of competing distributions. I tried Fedora 25, OpenSuse Tumbleweed, Manjora and Mageia. None of them recognized the touchpad as a touchpad. They all recognized as a PS/2 mouse. So right now it is not looking too promising.

---

### Post by brettpim on 2017-08-31
I have a ThinkPad X1 Tablet 2nd Gen running Ubuntu 17.04.  The detachable keyboard and the trackpad work but the trackpoint nor its three buttons do not work.  The output of **xinput** is 
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 5115 Pen stylus               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 5115 Finger touch             	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom HID 5115 Pen eraser               	id=18	[slave  pointer  (2)]
&#9116;   &#8627; PRIMAX ThinkPad X1 Tablet Thin Keyboard Gen 2 Touchpad	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Intel Virtual Button driver             	id=14	[slave  keyboard (3)]
    &#8627; Intel HID events                        	id=15	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=16	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=17	[slave  keyboard (3)]
    &#8627; PRIMAX ThinkPad X1 Tablet Thin Keyboard Gen 2	id=9	[slave  keyboard (3)]
    &#8627; PRIMAX ThinkPad X1 Tablet Thin Keyboard Gen 2	id=10	[slave  keyboard (3)]


```

running **xinput --test** on any of these and then using the trackpoint or its buttons does not return any signals.  However running **cat /dev/hidraw2** does produce signals from the trackpoint and its buttons.

the output of **xinput --list-props 11** is
```

Device 'PRIMAX ThinkPad X1 Tablet Thin Keyboard Gen 2 Touchpad':
	Device Enabled (140):	1
	Coordinate Transformation Matrix (142):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (267):	1
	Device Accel Constant Deceleration (268):	2.500000
	Device Accel Adaptive Deceleration (269):	1.000000
	Device Accel Velocity Scaling (270):	12.500000
	Synaptics Edges (271):	41, 1005, 30, 527
	Synaptics Finger (272):	25, 30, 0
	Synaptics Tap Time (273):	180
	Synaptics Tap Move (274):	52
	Synaptics Tap Durations (275):	180, 180, 100
	Synaptics ClickPad (276):	1
	Synaptics Middle Button Timeout (277):	0
	Synaptics Two-Finger Pressure (278):	282
	Synaptics Two-Finger Width (279):	7
	Synaptics Scrolling Distance (280):	-23, -23
	Synaptics Edge Scrolling (281):	0, 0, 0
	Synaptics Two-Finger Scrolling (282):	1, 1
	Synaptics Move Speed (283):	1.000000, 1.750000, 0.168776, 0.000000
	Synaptics Off (284):	2
	Synaptics Locked Drags (285):	0
	Synaptics Locked Drags Timeout (286):	5000
	Synaptics Tap Action (287):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (288):	1, 3, 0
	Synaptics Circular Scrolling (289):	0
	Synaptics Circular Scrolling Distance (290):	0.100000
	Synaptics Circular Scrolling Trigger (291):	0
	Synaptics Circular Pad (292):	0
	Synaptics Palm Detection (293):	0
	Synaptics Palm Dimensions (294):	10, 200
	Synaptics Coasting Speed (295):	20.000000, 50.000000
	Synaptics Pressure Motion (296):	30, 160
	Synaptics Pressure Motion Factor (297):	1.000000, 1.000000
	Synaptics Resolution Detect (298):	1
	Synaptics Grab Event Device (299):	0
	Synaptics Gestures (300):	1
	Synaptics Capabilities (301):	1, 0, 0, 1, 1, 0, 0
	Synaptics Pad Resolution (302):	12, 12
	Synaptics Area (303):	0, 0, 0,[ 0
	Synaptics Soft Button Areas (304):	523, 0, 456, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (305):	5, 5
	Device Product ID (264):	6127, 24739
	Device Node (263):	"/dev/input/event9"

```

the relevant portion on **lsusb -v** is 
```
Bus 001 Device 023: ID 17ef:60a3 Lenovo 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x17ef Lenovo
  idProduct          0x60a3 
  bcdDevice            0.18
  iManufacturer           1 PRIMAX
  iProduct                2 ThinkPad X1 Tablet Thin Keyboard Gen 2
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           91
    bNumInterfaces          3
    bConfigurationValue     1    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report          wDescriptorLength      79
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     247
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
    Interface Descriptor:      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     715
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)

```

I tried **modprobe  usbhid quriks=0x17ef:0x60a3:0x40** but this did not work.

Any help is appreciated.  If I need to show the output of some other command,s please let me know.

---

### Post by ashok6 on 2017-09-01
I don't have a solution to your problem but I have also been considering buying an X1 tablet gen. 2 and installing Ubuntu. Does everything work normally: suspend/resume, pen, etc.? And does multi-touch on the trackpad work or does it only function as a mouse as described above?

---

### Post by brettpim on 2017-09-01
> **ashok6 said:**
> I don't have a solution to your problem but I have also been considering buying an X1 tablet gen. 2 and installing Ubuntu. Does everything work normally: suspend/resume, pen, etc.? And does multi-touch on the trackpad work or does it only function as a mouse as described above?

Suspend/resume works fine.  I do not seem to have a hibernate option.  I have been using it for over two months and this is the first I have noticed that I do not have hibernate so that shows you that I don;t really use it.  Anyone know how to enable hibernaet

With the pen I have both buttons functioning in Xournal but I for other uses around the desktop I only have one of the buttons working as a right mouse click.  I think I could probably figure out how to get the second pen button to be middle mouse click with xinput but I have not tried to do this yet.

On the trackpad two fingers works for scrolling horizontally and vertically.  If there are any other multitouch gestures you would like me to try, I will happily try them and report back.

I have not got the cameras nor the fingerprint reader working yet.  If anyone has tips on getting the cameras working, I would appreciate them.

the keyboard detaches and starts working when reattached with no problem.  

I have had a couple of times when the screen has gone blank and the computer becomes unresponsive (I can't even ssh into it) and I have had to poweroff by holding the power button down.

I am using a ThinkPad USB-C Dock which works well.

I have one complaint about Uuntu that I think must be related to the very high resolution of the screen.  The title bar on all my windows (gnome)  is in a font much larger than I would like as are many default fonts in other windows.  I think this is set by the OS because if it used the standard fonts the high resolution of the screen would make everything very small.  I have played around in the settings, gnome-tweak etc and I cannot find a way to fix this.  This is also an issue that I am confident of fixing when I put some more time into it.

---

### Post by ashok6 on 2017-09-01
Thanks, that's super helpful. It sounds like it's working well, with two finger scrolling working it seems like support is even better than 1st gen.

I would imagine the fonts are set at 2x scaling which probably is large on a 2160x1440 screen. I don't use GNOME so I don't know how good support for fractional scaling is yet.

---

### Post by greg53 on 2018-01-12
I have a X1 tablet 20GG which seems to be working fairly well. Pen works beautifully.

Not working yet:

 - Keyboard lights other than caps lock
 - webcams
 - fingerprint scanner

The trackpoint (all three buttons) seems to be magically working with ubuntu 17.10!

---

