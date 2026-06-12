---
title: "black screen after BIOS"
date: 2015-01-02
forum: General Help
---

### Post by maxyman3400 on 2015-01-02
My computer goes black screen after BIOS runs and never gets to login menu. I dont think I can access the GRUB menu I did it once but it was frozen so I really don't know. I got a new graphics card to try and fix this but it did not help. PLEASE SOMEONE HELP ME! I have Ubuntu 14.04 64 bit and gtx 645. This happened after I messed with the drivers because the graphics card was acting weird so I tried to fix it by changing the driver. I am way over my head here and need help PLEASE HELP.

---

### Post by Bashing-om on 2015-01-02
maxyman3400; Hello;

It is what you have not said that matters here,
What card 'did' you have ? Did you purge the old driver ?
Is there an old " /etc/X11/Xorg.conf " file at play here ?

Let's look and see what we can make of the situation. what returns from terminal commands:
```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l  | grep nvidia
dpkg -l | grep fglrx
ls -al /etc/X11/Xorg.conf
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
Please use code tags for the outputs:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

A good place to start, then we see what there is to be done.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-02
As sad I cannot access the GRUB menu as sad and I could not purge the drivers because my old graphics card broke and had the same problem.

Also I have no idea what you mean by [COLOR=#000000]/etc/X11/Xorg.conf [/COLOR]

---

### Post by maxyman3400 on 2015-01-02
As sad I cannot access the GRUB menu as sad and I could not purge the drivers because my old graphics card broke and had the same problem.

Also I have no idea what you mean by [COLOR=#000000]/etc/X11/Xorg.conf [/COLOR]

---

### Post by Bashing-om on 2015-01-02
maxyman3400; Humm ...

Let us try and get you to at least the grub menu.

Boot the install and as soon as the bios screen clears, depress and hold the right -shift- key.

Do you now get the grub menu ?
 IF yes, we try and get you to a terminal.

[INDENT][INDENT]which way did he go, George[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-02
Hey ok got into the grub menu (had to switch out keyboards because for some reason my new one refuses to work in the grub menu)

here is some output 
(first and third command does nothing)
[http://m.imgur.com/nxfYZPz,QHIlmlb,kTnAoEn,0nngz55,6bj72Qg,xLeoMza,IvHCaaF,SgQ2RUw](http://m.imgur.com/nxfYZPz,QHIlmlb,kTnAoEn,0nngz55,6bj72Qg,xLeoMza,IvHCaaF,SgQ2RUw)

Here you go

---

### Post by Bashing-om on 2015-01-02
maxyman3400; Ok,

A bit of progress. 1st:
> 
Hey ok got into the grub menu (had to switch out keyboards because for some reason my new one refuses to work in the grub menu)

Likely that bios is not communicating to grub what the actual keyboard is in use.
Try resetting USB settings in bios, and also insure that "plug and play" is enabled.

2nd: Graphics situation - Nvidia-prime installed ! Are we talking hybrid graphics here .. that do take special handling.

OK, let's get ya to a terminal:
Boot to that grub boot menu, with the latest kernel with an asterisk on the left depress the 'e' key for edit mode -> boot options screen.
In this boot options screen arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff "
arrow across to the terms "quiet splash" and replace these terms with the term 'text' - without the quotes.
Key combo ctl+x to continue the boot process to the TTY1 terminal.
Login here with user name and password - there is no response to the screen at all when password is entered - security measure - enter the password blindly and hit the enter key. 
Now we need to know what we are dealing with.
what results:
```

ls -al /etc/X11/Xorg.conf
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

Maybe all we have here is a graphics driver issue .. 

[INDENT][INDENT]then
[INDENT][INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-03
[FONT=arial]Ok so after I change quite splash to text and control x it shows a bunch of lines of code and when it seems like it stops the entire screen turns black and at no point is there any input from me. I don't think its supposed to happen but if it is then tell me what to do from this point[/FONT]

---

### Post by Bashing-om on 2015-01-03
maxyman3400; Yuk;

Correct, It is not supposed to happen like that.
Now I am beginning to wonder how much of this is graphics related. But, let's try:
At the grub boot's boot parameter screen, instead of replacing "quiet splash" after these terms add the term "nomodeset" - with out the quotes; ctl+x to continue the boot process to the GUI login. Can you log in here ? - degraded graphics is OK at this point. IF you can get to the GUI we see what we can do about loading a graphics driver.

[INDENT]sometimes, not what I expect
[INDENT][INDENT][INDENT]work with what we got
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-03
Also I would just like to say that a couple of things that are happening now

Geting into the grub menu is so much harder than before for some reason and some times even when I did get it it then says loading grub but then nothing happens. 

Also I have had to re-install Ubuntu several times for a variety of reason (probably all dating back to a windstorm that messed up an update and then there was a button called factory reset on the grub menu so I pressed that and then everything was messed up so I re-installed then this happened)

So once I do this the screen turns black then a green messed up flash appears in the middle of the bottom half of the screen then a thing that appears the be a loading screen with Ubuntu 14.04 and then 4 or 5 dots bellow it (I forgot the exact number) then the screen just turns black after that poping up for a couple of seconds.

---

### Post by Bashing-om on 2015-01-03
maxyman3400; Humm,
As the plot thickens .

> **maxyman3400 said:**
> Also I would just like to say that a couple of things that are happening now

Geting into the grub menu is so much harder than before for some reason and some times even when I did get it it then says loading grub but then nothing happens. 

Also I have had to re-install Ubuntu several times for a variety of reason (probably all dating back to a windstorm that messed up an update and then there was a button called factory reset on the grub menu so I pressed that and then everything was messed up so I re-installed then this happened)

So once I do this the screen turns black then a green messed up flash appears in the middle of the bottom half of the screen then a thing that appears the be a loading screen with Ubuntu 14.04 and then 4 or 5 dots bellow it (I forgot the exact number) then the screen just turns black after that poping up for a couple of seconds.

UEFI system ? I think now is a good time to look and see what the partitioning is, and maybe then take a closer look at the boot process.

Boot up the liveDVD(USB) to "try ubuntu" mode -> terminal:

post back:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

[INDENT][INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-04
Hey booting from a USB is not working trying dvd

(sorry for late reply did not see that there was a second page)

Also still having problems with the keyboard and mouse which is a problem when I tried to boot low graphics mode for you need a mouse to proceed

---

### Post by Bashing-om on 2015-01-04
maxyman3400; Hey;


Hang'n with you !
Some background info for you:
> 
The <install> iso is Linux kernel and so it the installed system. So the keyboard is BIOS to Grub2. Grub2 has kb and basic USB drivers.. Note that LILO doesn't recognized USB keyboards... Then hands off to kernel (kb drivers there also). Then if there are graphics layers, as in a desktop edition, then there are additional keyboard drivers in X11.

After installing <on a bunch of systems>... I can confirm that "some" main boards don't like a USB keyboard on the install disk. ...and not all BIOS'es will pick up a USB keyboard in post. USB support on the motherboards has layers... So you have more of a chance on picking up USB keyboard through one of the USB root hub ports than through the second layer or an extension...Those root ports are normally on the back of the motherboard, near the keyboard/mouse PS2 ports. Usually ports on the front of a PC are on a higher layer or on an extension. But those same ports do pick up when the kernel boots through the HID drivers.

I have 2 server boards here that are opposite and would only POST with a USB keyboard, but those are oddballs and not the norm. A ASUS and a Dell 960 server. Funny thing is I have 2 Dell 960 Servers and the other is fine/normal. But with both those 960's, the USB keyboard is not recognized in enough time to be able to get into BIOS Settings using a USB keyboard, so it doesn't recognize them early enough on those...

I have access to both PS2 and USB keyboards here, but I "do" a lot of dev testing. Traditionally, you are going to have more of a chance for success with a PS2 keyboard during POST and the early boot process. I get keyboards (both usb or ps2) for about $10 each at a Recycler. I also have USB/PS2 adapters for my USB mice and keyboards. They plug into the mouse/keyboard PS2 ports of the motherboard and the USB mouse or keyboard plug into them. 

----------------
The 1st line of troubleshooting is " what is set in bios " to pass onto grub, to pass on to the operating system.

As to booting the liveDVD
Have you confirmed the .iso's md5sum ?
Did you "burn" as an image ?
Did you " check disk for defects"
Did you set in bios for the liveDVD as 1st boot priority ?

Then that liveDVD will boot  IF your bios supports DVD hardware - older systems do not ; they were conceived of before DVDs were ..

[INDENT][INDENT]it all starts in bios
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-04
Ok The dvd does not have any defects because I have used it before and I just burned a new one and tried it and I did burn it onto the dvd but not as an image (I think). And I do not know how to set dvd as first priority or what that means and same with [COLOR=#000000]Have you confirmed the .iso's md5sum.

And thanks for the info (I will have to get my old mouse and keep my old keyboard) 
[/COLOR]

---

### Post by Bashing-om on 2015-01-04
maxyman3400; And the troubles keep piling up.

You are going to get the more familiar with your bios.
When you boot there is an advisory on the bios boot screen what bios is installed and the version.
Google that and "read the manual".
No one can tell you how to change any settings in a bios we do not know. Each bios is different and the same bios is different in an alternate version.

Your mission is to learn
how to change the boot priority
how to change USB preferences
how to enable "plug and play"
how to reset back to factory defaults .

As you are not presently comfortable with bios. make plenty of notes of what screen you are in, how you got to that screen AND what you have changed.
One can make the system un-bootable, exercise care and caution. Be prepared before hand to know how to "reset to default".

What is the system you are communicating with at this time ? The same as you will use to "burn" another DVD . IF you know ( can boot with the liveDVD in another machine) this liveDVD is good there is no need to burn another .

Once you have a idea of what your bios is and have an idea of how to change the settings, we will continue.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-04
Hey and also My boot mode is set to legacy. Should I change this or to UEFI? I looked it up and I can only seem to see that it does not change much besides booting options and boot time. The thing is that my computer has this big warning message that says changing this could destroy everything. Also I cannot see any thing close to a pnp option anywhere in my bios. _Disregard what was here (If your seeing the underlined part for the first time do not pay attention to it)_

And also I am having a bit of trouble with understanding what PCIE Express 3 does, could help me understand that as it is currently disabled and it seems like it probably should be enabled from what I have seen but I can't tell and I am afraid of what will happen if it enable it.


As an interesting side note the computer never goes blackscreen! it just stays with the blinking cursor in the top right forever with cd having highest boot priority

---

### Post by Bashing-om on 2015-01-04
maxyman3400; Hey;

Regret the delay in getting back to you. Busy forum here of late.

IF this is a UEFI system then it becomes a whole new ball of wax.
Are you dual booting Windows ?
Whatever mode (EFI/MBR - legacy) that Windows was installed in, one should match when installing ubuntu.
 PCIE Express 3 : -> is the form-factor for an add-on card .. say a high powered graphics card . Will not hurt to enable that ability and if you DO have that slot in-use will surely help a bunch.

You have never been able to boot a liveDVD ? 
If this is some Microsoft monkery, turn of secure boot, and make sure, IF Windows is a factor, that you have shut down Windows completely as Windows in fast boot "hibernates" and will not boot up anything else. This might be the cause of " blinking cursor in the top right forever with cd having highest boot priority"; The system can not boot another operating system .

[INDENT][INDENT]try'n to get to the bottom of things
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-04
I do not have a dual bot here and before this I have always been able to boot CD/DVDs.

Hey I turned on PCIE and that seems to have changed to blinking cursor to it just being black screen like before

And its cool with you being busy just as long we can fix this :D

---

### Post by Bashing-om on 2015-01-04
maxyman3400; Hey,

We work on getting you booting, If we can not we will know the reason why.

Is this a UEFI system ?
What operating system was installed on it initially ?

As you have a known good liveDVD, boot priority is set to 1st CD?DVD, and you have been able to boot from DVD before, then it must be a firmware situation.

[INDENT][INDENT]it is all in that process
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-04
It originally had Ubuntu installed on it (12.04 if that matters)

And is there anyway to find out what firmware is corrupt or broken and then how to fix it? (Or is this what we are doing right now)

---

### Post by Bashing-om on 2015-01-04
maxyman3400; Wellll ..

This started out as a simple graphics driver issue as you had only changed the graphics card.
Now we are trying to boot the liveDVD .. And yes using that new card could be a factor. Particularly so IF it uses that PCIE Express 3 slot on the main board.
With that slot enabled in bios, it should be recognized. 
I guess I had best do some research and see what that 'gtx 645' card is. Maybe it takes an additional power source that has not been added ( can your power supply support it ?) Maybe it is PCIE express3 form format.

And yes, the boot process is different between that of UEFI and the legacy bios booting. The method in firmware to change the boot priority is also different. UEFI is not a simple "one thing does it all" . Different manufacturers implement the specification (that is not to this time 'specified') in different ways.

The thing we are working on now is to boot that liveDVD, as the easiest means to get a display working. With no working display ( or a means to SSH into this machine) there is nothing we can do. We have to have that display so we can find out what to do, huh ? 

[INDENT][INDENT]I be back
[INDENT][INDENT][INDENT]when I know more - gtx 645 wise -
([/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-01-04
maxyman3400; Hey;

So far so bad for the home team !
that card is " Bus Support 1 PCI Express 3.0" and as well takes a greater than stock power supply:
"Minimum System Power Requirement 450 W"
[http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-645-oem/specifications](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-645-oem/specifications)

I still looking and as I find more will edit this post ..

EDIT1: Card released April 2013 -> can we find drivers for it ?
Still also looking at what powers the card.

EDIT2: Drivers are available from:
sudo apt-add-repository ppa:xorg-edgers/ppa
If we need to go that far.
But we do not have to resort to the PPA, Dell advises that the graphics driver is available in the repository .. great !
[INDENT][INDENT]out of the frying pan and into the fire ?
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-04
So should I change that out to be disabled? I'm going to do it anyway but if not just tell me in a later post. And also its from only Nvidia I had to order from dell in a live chat. Same as the stock one on my PC so no power issues there or incapability.

So wait how should we install these drivers now or make them the drivers used?

---

### Post by Bashing-om on 2015-01-04
maxyman3400; HO Kay;

Proceed ....
Check the rating on your power supply that it is great enough to support that card ;
Make sure it is properly seated in the PCIE3 slot;
In bios the PCIE3 slot is enabled;
In bios check that the PCIE3 slot has video priority;
Now boot the liveDVD ( bios set to boot the DVD) and
try this: as soon as the bios screen clears depress and hold the right -shift- key -> language screen, escape key to accept the default ->
Boot options screen -> F6 key -> choose "nomodeset" ;
enter key to continue the boot process,
Do you now reach the desk top ? OR at what point do you fail ?

[INDENT][INDENT]That card is supported, and we will
[INDENT][INDENT][INDENT]make it work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-04
Wait I am hung up on these 3 lines 
[COLOR=#000000]Make sure it is properly seated in the PCIE3 slot;[/COLOR]
[COLOR=#000000]In bios the PCIE3 slot is enabled;[/COLOR]
[COLOR=#000000]In bios check that the PCIE3 slot has video priority;
[/COLOR]
The first and second I don't quite understand. Please elaborate!

(I will be not responding in the next 12+ hours so feel free to take your time responding!)

---

### Post by maxyman3400 on 2015-01-04
Hey forum not letting me update my post so here it is (This would be the updated version ignore the post above)

Wait I am hung up on these 3 lines 
[COLOR=#000000]Make sure it is properly seated in the PCIE3 slot;[/COLOR]
[COLOR=#000000]In bios the PCIE3 slot is enabled;[/COLOR]
[COLOR=#000000]In bios check that the PCIE3 slot has video priority;
[/COLOR]
The first and second I don't quite understand. Please elaborate!

(I will be not responding in the next 12+ hours so feel free to take your time responding!)

---

### Post by maxyman3400 on 2015-01-04
Forum is not letting me update me post please treat this as the post above updated version

Wait I am hung up on these 3 lines 
[COLOR=#000000]Make sure it is properly seated in the PCIE3 slot;[/COLOR]
[COLOR=#000000]In bios the PCIE3 slot is enabled;[/COLOR]
[COLOR=#000000]In bios check that the PCIE3 slot has video priority;
[/COLOR]
The first and second I don't quite understand. Please elaborate!

(I will be not responding in the next 12+ hours so feel free to take your time responding!)

---

### Post by Bashing-om on 2015-01-04
maxyman3400; Welp;

1) Did you not install the Nvidia card ? Make sure it is fully seated and the locks are clicked into place on that slot
2) You had earlier advised that you had enabled/disabled PCIE express 3 in bios, make sure that it is now enabled
3) I have seen bios' where it is possible to re-arrange the video priorities. Check and see what your bios provides, You want it set to the PCEI3 slot as the 1st parameter .

[INDENT]computers are dumber than we are
[INDENT][INDENT][INDENT]have to tell them what to do
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-05
Hey REALLY sorry for late reply (I had school in the mourning so I could not work on this. So im going to check to make sure that the graphics card is in properly and I Don't think I can change the video priority (As there is only one priority slider and that's for boot priority and that does not have anything video related (I have searched every menu and there are not that many so I know there is not a video priority)

---

### Post by Bashing-om on 2015-01-05
maxyman3400; K;

Then we are back to post #24, see if you can boot that DVD to "try ubuntu" mode using the F6 "nomodeset" boot parameter .

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-05
Sooooo Now my Disc drive is not sending out the disk. I tried to take the disc out and see what would happen if i put the other one in. Now it appears that I cannot take or put anything into the disc reader. I'm going to change it so disc goes second after the hard drive and see what happens. Will edit results.

Same as before cannot eject the disc.

(Also just a quick question what do you mean by language screen, do you mean in the Ubuntu re-install and how would you get to that in the grub menu?)

Also secure boot is disabled so unless you say so I will enable it.

---

### Post by Bashing-om on 2015-01-05
maxyman3400; Yuk ..

Disk not ejecting is not a good indication. What you can do is manually open the disk drive:
There is a very small hole generally toward the right side of the drive - stick a tooth pick or paper clip in the hole to release the lock.

If this is a UEFI system, try :
As soon as ubuntu's screen initially appears, depress repeatedly and release the escape key .. the next screen I expect is a language selection screen. press the escape key here to accept the default. The next screen is the boot options screen .. here the F^ key will pop up a preset bott options box .. choose "nomodeset" , the enter key will continue the boot process to the GUI .. In the GUI one can install a graphics driver from the "Additional Drivers" utility located in the software Sources tab.

What we are doing here is establishing that you can boot ubuntu. What it takes to get ya a graphics driver in this liveDVD indicates what we must do for the install.

And no, you want secure boot disabled.

[INDENT][INDENT]whatever it takes
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-05
Ok so I will try to get the CD out today but that might not happen so it might be tomorrow. So just to clarify its on legacy so should I follow those instructions or stick to post 24?

---

### Post by Bashing-om on 2015-01-05
maxyman3400; Well ..

can not say .. what works to boot the liveDVD is what works, try both means.
Once you have booted the liveDVD then we can look and see what the boot process is.

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]one at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-05
OK a development!

In the grub menu I was able to eject the disc!

With the disc in and setting quite splash to quite splash nomodeset.  it seems to boot up the disc for just a second! it shows the Ubuntu loading with Ubuntu 14.04 and four dots below it. Although after this it appears to crash go black screen.

---

### Post by Bashing-om on 2015-01-05
maxyman3400;Progress .

I honestly do not know more.
You can try an additional boot parameter "acpi=off"; see if you can boot.

[INDENT][INDENT]I am not a Know-it-all
[/INDENT][/INDENT]

---

### Post by maxyman3400 on 2015-01-05
Sooooo thanks for your help! As that last options have not been working I am going to ask a few other people to help me! If that doesn't work I will just bring it to a local computer repair specialist! You have been really great and it sucks that we can not seem to fix this. Well thanks anyways and bye!

If anyone else wants to help me on this feel free!

---

