---
title: "Problem using 'Disks' to format 32GB Cruzer memory stick"
date: 2018-01-13
forum: General Help
---

### Post by grey1beard on 2018-01-13
I've just installed 'Disks' software onto my laptop running 14.04, in order to re-format a memory stick. 
I've attached a screen shot of the problem, and would be grateful for advice.
John

---

### Post by dragonfly41 on 2018-01-13
Use Gparted   (Partition Editor) to format and ensure that memory stick is unmounted.

[https://askubuntu.com/questions/377253/unable-to-format-usb-drive-with-disks-udisks-error-quark-0](https://askubuntu.com/questions/377253/unable-to-format-usb-drive-with-disks-udisks-error-quark-0)

---

### Post by grey1beard on 2018-01-13
Thanks.
I see there are several add-ons in the Software centre. Would you recommend any of them as useful/required ?
John

---

### Post by dragonfly41 on 2018-01-13
When I launch Synaptic Package Manager I don't see any "add-ons" (for gparted).
Just use it as it is.

---

### Post by grey1beard on 2018-01-13
I admit that I'm tired, having just been travelling for 24 hours across the Atlantic(no. I didn't row !), but I'm baffled by this process.
I've created a msdos partition, but I' don't really know what I need to do next.
Can't even remember why I started this in the first place, so I think I'll take a break.
John

---

### Post by dragonfly41 on 2018-01-13
[COLOR=#000000]> I admit that I'm tired, having just been travelling for 24 hours across the Atlantic.
[/COLOR]Bring back Concorde, I say.

You did not explain what you are trying to do.
If you are trying to create a LiveUSB to install Ubuntu use tools such as unetbootin which will recognise your flash drive and format and install selected distro on the flash drive.

---

### Post by grey1beard on 2018-01-13
I think you may have hit the button.
I am struggling to learn how to use an Android tablet, and was looking at the possibility of running Ubuntu on it, and that may be why I started down this path.
At 79, it's a bit of a steep learning curve, but I've managed worse, so I'll plod on, and assume that's what I'm trying to do !
'Unetbootin' sounds promising - I'll have a look.
John

---

### Post by grey1beard on 2018-01-13
I see that I need to format it as Fat 32. Do I also need to create an MBR partition, or does Unetbootin create that automagically ?
John

---

### Post by dragonfly41 on 2018-01-13
Unetbootin should handle this automatically.

Since you mentioned Android also explore DriveDroid.

[https://softwarebakery.com/projects/drivedroid](https://softwarebakery.com/projects/drivedroid)

[https://play.google.com/store/apps/details?id=com.softwarebakery.drivedroid&hl=en](https://play.google.com/store/apps/details?id=com.softwarebakery.drivedroid&hl=en)

---

### Post by grey1beard on 2018-01-13
It's on its way !
Unfortunately, my connection seems to be throttled back at the moment, so it's going to take hours.
But then, I can always do the washing up, etc.
Thanks again for your help.
John
PS Going for the live usb first.

---

### Post by grey1beard on 2018-01-15
So far so good, and I expect the headache will subside soon !

The throttling mentioned above is my router nosediving - replacement on its way.

I now have a 32Gb stick with 16.04 on it, my Android tablet is rooted and I am the Superuser - ah the sense of power.

Next hurdle is how to find my way into the boot menu, and see if it's even possible for the tablet to boot up from a usb stick.
I've done a lot of googling, but not found anything definitive for my tablet, an Irulu x10 with Android 4.4.2 installed.
Seems to be a combination of several keys being pressed at the same time, or in some weird sequence.
Perhaps before I try that, a system back up would be in order.
No data to worry about, but just want to avoid finishing up with a brick.
Any thoughts or pointers ?
John

---

### Post by dragonfly41 on 2018-01-15
I have not done what you are trying to do with Android but I read here from a quick google ...

[https://askubuntu.com/questions/243718/boot-into-ubuntu-from-android-tablet-with-live-usb-drive](https://askubuntu.com/questions/243718/boot-into-ubuntu-from-android-tablet-with-live-usb-drive)

> [COLOR=#111111][FONT=Ubuntu]First of all things understand this. The Android tablets use ARM processors, SoC as they are called. Your regular Desktop Ubuntu is for x86 CPU's, so of course you don't see anything moreover, Does your Android tablet support dual boot?, Does your ROM support it?, Do you have a kernel that supports it?, etc. Not that if it does it will boot Ubuntu at all, you need the ARM Ubuntu image if at anything, and that doesn't mean you will get to boot it. I'd suggest you go to XDA-developers.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
So first question is have you installed ARM Ubuntu?

[/FONT][/COLOR][https://www.ubuntu.com/download/server/arm](https://www.ubuntu.com/download/server/arm)

Some more research I guess but you have at least done a first dry run.

Dig around in Android forums.

[https://androidforums.com/threads/how-to-use-smartphone-as-ubuntu-liveusb.547107/](https://androidforums.com/threads/how-to-use-smartphone-as-ubuntu-liveusb.547107/)

---

### Post by grey1beard on 2018-01-15
I've been to the first link, and in fact now subscribe to the xda site. The 'Arm' reference I noted, but got lost in the tiredness, I guess.
Thanks for the 2nd link, and will be my next research step, before going on to your 3rd.
John
EDIT
I think I may have seen that, and chose to download 16.04 because of it.
However, I see that mentions 64 bit processors, and I'm pretty certain the tablet is 32bit.
More anon.
EDIT 2
CPU: Quad Core ARM Cortex-A7 CPU (4X1.3 GHZ)
EDIT 3
ARM Cortex-A7 MPCore is a 32-bit microprocessor core 

Ah, now what ?
EDIT 4
Looked in your 3rd link and interesting read from 2012, but his 'how to' never got posted :(
> Finally I got it working!

- put Ubuntu as liveUSB on the SD-card (using format)
- reboot android in ClockworkMod Recovery
select : mounts and storage -> mount USB storage
- Reboot PC, booting from USB
Now Ubuntu LiveUSB boots.

Now looking for his mention of** ClockworkMod Recovery** reference.

I think I' on the way -
[https://www.xda-developers.com/how-to-install-clockworkmod/](https://www.xda-developers.com/how-to-install-clockworkmod/)

:)

---

