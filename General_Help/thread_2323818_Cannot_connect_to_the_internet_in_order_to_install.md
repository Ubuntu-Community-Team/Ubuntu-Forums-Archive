---
title: "Cannot connect to the internet in order to install Nvidia drivers"
date: 2016-05-08
forum: General Help
---

### Post by Chelsey_Martin on 2016-05-08
Hey all, forgive me for the long post. I've done and tried a lot of things over the last two weeks of trying to figure this out on my own with google and have finally gotten to the point where I need help.

First, let me explain that  I can't copy and paste code/results/what-have-you from the desktop with Ubuntu currently installed on it because I can't use it outside of the terminal (normal boot) or Recovery Mode. So until I get a functional GUI (which I'm under the impression requires functioning video drivers), all my troubleshooting and reporting has to be done by hand. (I'm on a separate laptop right now)

So, on to the problem.

First my biggest problem is the Nvidia driver issue. I boot into a black screen, and if I press some combination of Alt+Ctrl+Fn (some F-number key, but I'm not sure which one) I get the Low Graphics error (all of the options on the prompt loop back to the original screen, so there isn't a solution there). If I press Alt+Ctrl+F1 I get into a text-only interface where I can login successfully and then start using commands (I think that's the terminal, but I'm not sure). All of my debugging and gathering information and trying things has been done via this terminal screen. Occasionally my monitor will flash and pop up a movable cursor before flashing back into either a blinking cursor that doesn't do anything or a black screen. From there I can just Alt+Ctrl+F1 back to the terminal and continue typing/reading where I left off.

So the first thing I tried was the nomodeset from the Grub (I think?) menu, by selecting ubuntu-normal, pressing e, and doing the quiet splash edit. This doesn't do anything except prevent me from getting into the what I'm calling terminal but not sure what it's actually called. I end up having to Ctrl+Alt+Delete to reboot and start over with something else.

Next I tried the Recovery Mode boot, but Enabling Networking either bugs out the Recovery Menu (I can't select other options without the screen breaking and filling with previously used commands, like I'm in a terminal typing and using the up arrow to scroll through previous commands, it's a weird graphical glitch that doesn't allow me to do anything but reboot via Ctrl+Alt+Delete) or it says 'Starting NetworkManager' (or something along those lines) and does nothing for a very long time (half an hour is average) before sending me back to the Recovery Menu.

I can't sudo apt-get update because I get a 'temporary failure to resolve' error when trying to connect to us.ubuntu.com or security.ubuntu.com (forgive me if either of these are wrong, I'm typing from memory and don't have the actual errors in front of me right now).

I can ping localhost, but I can't reach any network outside of my own modem/connection/what-have-you, and traceroute just tells me to install a package that contains it, but I can't because I get the same connection error as above.

I tried to fix the connection and found out that instead of eth0 or wlan0, my wireless device is called wlp3s0 and with that information I was able to use wpa_supplicant to force a connection and that works but it doesn't stick. It connects, disconnects, connects, disconnects, etc etc etc without the command ever finishing. I left it up last night running while I slept just to see what happens, and woke up to it in the same place as I left it (a loop of connects and disconnects) and have to force stop it to continue trying anything else (which disconnects me even if I had previously be connected) with Ctrl+C. The wpa_supplicant conf file is only setup with the name of the wireless (SSID, whatever it's called) and the password.

Extra information that may be relevant:
2 hard drives, but I can't touch my 1TB because I'm trying to set up this 500GB so I can back that one up before reinstalling windows (I got a glitch I can't fix without wiping from the last update which locked me out of my account because there are no power options in the log-in screen and I can't force a shift+restart like you're supposed to do to fix it, and the windows 10 recovery mode won't let me just refresh the operating system without wiping the files, so blah).
I've lost count of how many times I've had to reinstall ubuntu on my 500GB for various different errors I was getting, and yeah I probably should try to use a different hard drive at this point but I don't have another hard drive to use. The live-usb runs fine, if that means anything.
I finally got it to install without any errors by partitioning the 500GB in a very specific way.

I have a / partition (operating system is installed onto)
            /boot partition
            /home partition
and a swap partition
Without the /boot partition the bootloader wasn't installing, and without the /home partition I was getting a read-only error that resulted in the install failing every time.

Currently I have successfully booted into Recovery Mode, ran grub bootloader update, then repair broken packages (internet error, it quit on it's own and returned me to the recovery menu), ran enable networking (no error or bug breaking this time, but also no confirmation of success), and have returned to repair broken packages where I am currently stuck at 50% [Connecting to security.ubuntu.com] [us.archive.ubuntu.com] and then get the temporary failure resolving errors and it loops back to try again. Been there for about an hour now.

Sorry for the tons of information, I've just tried a lot of stuff up to now and wanted to make sure everyone was filled in on what I've tried.

Thanks,
Chey

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Hello;

My condolences for all the trials troubles and tribulations.

On A - Wired - internet connection, what results:
```

ping -c3 127.0.1.1
ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
These show that the hardware works, If you are getting out of house .. and IF/Not Domain Name Service is resolving.

Gotta start somewhere ->
[INDENT][INDENT]looks like a good place to me
[/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
I don't have a wired internet connection option, only the wireless (no broadband cable or whatever it's called).

I also don't know how to get out of the screen it's currently stuck in and get back to a working terminal. =/

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Ouch !

A hard row to hoe to piggy back wireless drivers from a working system onto the install. I am not much help to you in this respect .. I have no wireless experience.
But Ii will give it a nudge in the direction so others can better advise:
```

sudo lshw -C network
ls /sys/class/net
ip link ls

```

See if key combo ctl+alt+F1 will return you to the terminal.


[INDENT][INDENT]one of those times
[INDENT][INDENT]I do not know better
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
Nope, ctrl+alt+F1 doesn't do anything, and ctrl+c doesn't stop the attempting to connect. I was able to force a reboot though, so I'll let it boot like normal until I get back into a working terminal and I'll be able to post my results to the above command then. It'll take a little while to get to a functioning terminal though, but shouldn't take too terribly long.

My process: Boots directly into a GRU menu listing boot options, select first one (Ubuntu 16.04 LTS normal).
Screen died, have to go to the back of my tower to switch the monitor cable from one slot to the second.
Screen back on, but black.
ctrl+alt+F1 currently does nothing.
I'll leave her alone to go through whatever running/booting/setting up she's currently doing.

Okay, now ctrl+at+F1 brings up a flashing unmoving cursor in the far upper left-hand side of the screen.
Nothing else does anything else.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Well ...

As a tentative poke at getting to a reliable terminal; what results:
Boot to grub boot menu ; 'e' key for edit mode -> boot parameters screen.
Arrow down to the line starting with linux and across to "quiet splash" .
remove quiet splash and all after and insert:
systemd.unit=multi-user.target
key combo ctl+x to continue the boot process to TTY1 .
Login here with your credentials. There will be no response to the screen when pass word is entered . Enter blindly and hit enter key.

With this boot parameter, only essential service for the kernel are loaded and available . However, we have full control of what we start from this terminal .
If you can get this far, we see what happens when we start the GUI .

[INDENT][INDENT]longest journey begins
[INDENT][INDENT][INDENT]even with small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
Alright, loading. No black screen error yet, just long list of different processes starting and running and all that fun jazz.
The system automatically ran a fsck scan, came back clean with no errors.

Welcome to Ubuntu 16.04 LTS
System hostname set

Now just blinking cursor at the bottom of the screen, loading and background processes occurring I imagine.

Usually at this point a bunch of processes/programs start to be turned on, with the [OK] in green message if there isn't a problem. The only problem I've been getting ([FAILURE] in red) have been for the Braille device stuff... which, I guess I would be getting because my computer doesn't have any braille device stuff anyway?

Yeah, just
[FAILED] Failed to start Braille Device Support

A bunch of dependencies just failed and it's booted me into emergency mode.
This is the first time I've seen the dependencies fail on this installation attempt. I was getting them before, and it seemed like (at the time) the reinstall had solved those problems. I'm not sure what is causing them or how to fix it.

I was given an option to press Enter for maintenance, and I pressed enter.

Now I'm at a root@chey-OC:~# command line. Does this have the same function as a terminal?

---

### Post by deadflowr on 2016-05-08
2 quick questions.

Do you know the machine make and model? Can be helpful to know.

Did the gui function properly during the install? 
If you boot the installer and use the Try Ubuntu option does it work?

---

### Post by Chelsey_Martin on 2016-05-08
Machine make and model? It's an Alienware Area-51 desktop. So... dell? I think? I've since changed her case a few times so I don't have easy access to any of her motherboard information without pulling it up via device manager or BIOS.

GUI functioned correctly during install, and the try Ubuntu option works perfectly without any problems. The GUI fails to load (even to just a basic login screen) only after the first reboot after the install is complete, which I had read is due to the not-default-included nVidia drivers (my graphics card is an nVidia GeForce GTX560; if I'm remembering correctly.)

---

### Post by grahammechanical on 2016-05-08
I would like to give clarity on a few things. Ctrl+Alt +F1 = Linux command line = Linux console. 

> returned me to the recovery menu),

That is correct procedure. When we run options from recovery menu such as Network and Update Grub we are actually running a script which in turn runs a command or two. When the command has finished the script returns us to the recovery menu where we can select Resume (loading). The only option that does not return us to the recovery menu is Root shell prompt. To get back to the recovery menu from Root shell prompt we type exit.

Resume is useful because it will load to the desktop using a fall back open source video driver. And that is just the thing we need if there is a conflict with the proprietary video driver.

If we install and tick the box "Install third party software" we get some audio & video codecs but also a proprietary video driver. So, if you ticked that box at the start of the installation process then you should already be using a proprietary (Nvidia) driver. And there might be a conflict with it.

You do not mention what happened when you selected Resume. Selecting Resume is the only way out of recovery mode. If we don't include a hard power off. To find out if you do have the Nvidia driver installed run this from recovery>root

```
ubuntu-drivers debug
```

At the bottom of the long printout you will see "matching driver packages." This is what I see on my machine.

> === matching driver packages ===
nvidia-304: installed: <none>   available: 304.131-0ubuntu3  [distro]  non-free  modalias: pci:v000010DEd00000A20sv00001043sd0000830Fbc03sc00i00  path: /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0  vendor: NVIDIA Corporation  model: GT216 [GeForce GT 220] 
intel-microcode: installed: 3.20151106.2   available: 3.20151106.2 (auto-install)  [distro]  non-free 
nvidia-304-updates: installed: <none>   available: 304.131-0ubuntu3  [distro]  non-free  modalias: pci:v000010DEd00000A20sv00001043sd0000830Fbc03sc00i00  path: /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0  vendor: NVIDIA Corporation  model: GT216 [GeForce GT 220] 
nvidia-340: installed: <none>   available: 340.96-0ubuntu3 (auto-install)  [distro]  non-free  modalias: pci:v000010DEd00000A20sv00001043sd0000830Fbc03sc00i00  path: /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0  vendor: NVIDIA Corporation  model: GT216 [GeForce GT 220] 


Notice two things. 1) My video adapter is Nvidia GT216 [GeForec GT 220]. What video adapter do you have? 2) Each of the Nvidia drivers  (304; 304 updates; 340) are listed as "installed: <none>" And that is because I am using an open source video driver (Nouveau). Do you get the same or is one Nvidia driver listed as <installed>?

Regards.

---

### Post by Chelsey_Martin on 2016-05-08
When installing ubuntu I did tick that box.

I'm currently still on the step last brought up by Bashing-om; looking at a screen that says root@chey-PC:~#
I'm guessing it's the terminal, but I'm not sure.

I typed in ubuntu-drivers debug and the output it too long to handtype here. It also just went past the screen that I can see (I don't know how to scroll back).

It says I have an nvidia GeForce GTX 580 (on none of the lines is the entire model shown because it gets cut off somewhere, so from piecing together it says GF110, but I'm not sure if that's missing any details or not)
I have an intel-microcode installed (3.20151106.1) but of the nvidia drivers listed, it says installed: <none>
nvidia-304, nvidia-361, nvidia-304-updates, nvidia-340.

Hope that helps. =3

Edit: And oh yeah, the only way I've been able to get out of recovery menu so far has been to force a reboot (ctrl+alt+delete). I've only ever gotten stuck/frozen/bugged out, and never actually successfully solved or finished anything through the recovery menu.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Huh ?

> 
I'm currently still on the step last brought up by Bashing-om; looking at a screen that says root@chey-PC:~#
I'm guessing it's the terminal, but I'm not sure.

" root@chey-PC:~#" would not be available in the process I directed. looks like a root prompt from "recovery mode" .

Back up, regroup, reboot, and try again .

Albeit, we can work from either the grub edit to get a terminal .. or by activating the root shell console from the recovery option..

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
> **Bashing-om said:**
> Chelsey_Martin; Huh ?


" root@chey-PC:~#" would not be available in the process I directed. looks like a root prompt from "recovery mode" .

Back up, regroup, reboot, and try again .

Albeit, we can work from either the grub edit to get a terminal .. or by activating the root shell console from the recovery option..
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


It came up during the process I was following via your steps. I got an error, the computer continued into emergency mode, and then asked me to press Enter for Maintenance. I pressed Enter, and the "root@chey-PC:~#" came up immediately afterwards.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Ouweee ,,,

Thanks for the explanation .  I can only consider a file system problem to produce such an event.
How did you install ubuntu ? and did you verify the install medium ?

Known good installer
[INDENT][INDENT][INDENT]good foundation
[/INDENT][/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
I was able to boot into Recovery Mode successfully, but I can't move the on screen selection via any method (the arrow keys don't do anything, it's just frozen in place).

I used a bootable USB, and tried about 10 different iso's and reboots/USB drives. Every one of them scanned clean and perfect, and every one of them installed fine once I solved the errors I was getting (disk drive errors, fixed via wiping the disk via Windows installer, then fixed with the partitioning I have currently set up). The errors don't occur until after the first reboot. (Installation complete, okay, computer reboots automatically, boot to blank screen).

The live-USB ubuntu trial mode also worked fine, and I installed from there rather than the bootloader option (installing before trying first).

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Yuk .

I do not know what really to think .
Reduce to simplest terms -
wired keyboard
wired mouse
1 monitor connected

and nothing else .

Boot now to the login screen:
what results : key combo ctl+alt+F1 ?

[INDENT][INDENT]KISS I do believe applies to this situation
[/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
That's all I currently have connected to the computer. Still trying to get into Recovery Mode (after it bugging out last time, I immediately forced reboot with the ctrl+alt+delete combination and tried again). It's putting me back into maintenance mode.

Alright, keyboard rebooted again. Still have nothing connected. It's currently running through a long list of rebooting/shutting down processes.

If it makes any difference I don't have access to 'plain' or 'simple' keyboard/mouse. I have an Alienware keyboard and a razor gaming mouse. They both connect via USB (not wireless), but they also aren't 'simple'.

Other than that, everything else currently connected is a card. Wireless card, wired card, video card, and 16 GB of ram. Oh yeah, and my CD drive.

Computer still working on the shutting down thing.

Her blah. I'm not really sure what happened. It was rebooting when I left the room, and I came back to a black screen with...

/dev/sda1: clean, some number of files, some number of blocks.
_ (but blinking)

And ctrl+alt+F1 doesn't do anything.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; K;


Once you can get to a terminal.
```

systemd-analyze blame

``` can you glean anything useful from the log ?

[INDENT][INDENT]when all else fails
[INDENT][INDENT]start reading instructions
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
I'm currently stuck on a screen with a bunch of [OK] and currently at Starting Nameserver information manager...

alt+ctrl+F2 brings me to a blank screen with a blinking cursor.
alt+ctrl+F1 brings m back to the previous screen.

Nothing does anything else.

Edit: I'm just trying to get to a functional terminal and have been unsuccessful so far.

Heads up: Partner is going to be home soon with some extra computer stuff including additional harddrives and portables. Depending on if I successfully get into a terminal or not I may try installing ubuntu on a different harddrive or same harddrive but with his computer, just to see if it's a hard drive or a hardware/motherboard issue.

I'm currently trying to boot into nomodeset, because that was a successfully way to get into the terminal for me last night.

Force booted into emergency mode again, but it gives me a functional command line so I think it's the best I can do until we can figure out why it keeps force booting into emergency mode now.

Was able to type "systemd-analyze blame" and the output is too extensive to fill one screen, and I also don't understand any of it. Except for the brltty.service, which kept popping up every time the Braille Device failed on boot.

Lets see, I'll just type up everything with some shorthand since I can't just copy and paste it over.

2min 48.231s apparmor.service
2min 30.477s dev-sda1.device (which is odd, because my harddrive is on sdb. The flashdrive was on sda because my computer recognized it as another hard drive in order to boot from it)
1min 19.376s [email]systemd-fsck@dev-disk-by/x2duuid-001fb182/etc...etc...etc[/email]
        52.052s home.mount
        xxx [email]system-fsck@dex-disk-by/etc...etc...etc[/email]
        xxx systemd-modules-load.service
        xxx systemd-tmpfiles-setup-dev.service
        xxx systemd-journald.service
        xxx systemd-tmpfiles-setup.service
        xxx boot.mount
        xxx systemd-udevd.service
        xxx dev-disk-by/etc...etc...etc
        xxx plymouth-read-write.service
        xxx console-setup.service
        xxx unreadahead-stop.service
        xxx networking.service
        xxx dev-hugepages.mount
        xxx sys-kernel-debug.mount
        xxx dev-mqueue.mount
        xxx kmod-static-nodes.service
        xxx systemd-update-utmp.service
        xxx ufw.service
        xxx brltty.service
        xxx systemd-sysct1.service
        xxx systemd-remount-fs.service
        xxx systemd-rfkill.service
        xxx systemd-udev-trigger.service
        xxx systemd-random-seed.service
        xxx resolvconf.service
        xxx systemd-journal-flush.service
        xxx systemd-timesynced.service
        xxx systemd-update-utmp-runlevel.service
        xxx sys-fs-fuse-connections.mount

And those are the results.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Welk;

I do not have a mail reader installed on this particular install.
I see nothing amiss in what the log relates.
How does a " Braille Device" device come into play here ?

Questions just because
[INDENT][INDENT]I do not have the answers
[/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
It just keeps failing to load and telling me that the log report is kept in that file/location/what-have-you. I don't have or need a braille device though, so I'm not sure.

I have been able to get a hold of an Ethernet cable, and can ping 127.0.1.1 but not google or ubuntu.

8.8.8.8 gets a connect:Network is unreachable.
unbuntu.com gets a unknown host error.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Welp.

Depending on where you got that terminal . I can accept that the networking service is not enabled.
In the TTY1 terminal try:
```

systemctl enable NetworkManager.service
systemctl start NetworkManager.service
ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

What now brown cow .

---

### Post by Chelsey_Martin on 2016-05-08
I was able to run enable Network Manager, but running the start command hasn't resulted in anything except for a blinking _. System isn't frozen, but it also isn't currently doing anything visible that I can see processing.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Yikes ..

Back up again and reqroup.

On that wired connection, reboot to the grub boot menu; activate the TTY1 terminal;
'e' key, substitute " systemd.unit=multi-user.target " ,ctl+x.

Once logged in on TTY1 run:
```

systemctl enable NetworkManager.service
systemctl start NetworkManager.service
ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

If you can not .. I do not know what else to advise than ...
start afresh, verified .iso file
verified copy to the USB
wired connection
re-install ...do not check "updates" .

[INDENT][INDENT]just what I think
[INDENT][INDENT][INDENT]other opinions may vary
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
Nope, dependencies failed again. For /boot, Local File Systems, Clean up, File System Check, /home, and File System check.

Automatically booted me into maintenance mode again.

I got a "The ext4 file system creation in partition #4 of SCS111 (0,0,0) (sdb) failed"
So now I'm trying the entire install on an external hard drive I have to see if it was my hard drive itself having the issues.

I am able to successfully load the Try Ubuntu program still, and so far the install process has been flawless.

No updates and no other software installs. I didn't check either box.

So far: holy cow the install is 10000x faster. I'm almost done already, and almost literally just started the entire process.

Installation finished, restart now.

So the installation finished successfully, but my computer itself can't boot from the portable. It just says to insert Boot Media Device and press a key.

Next try is to use a second computer with my hard drive and see if that works.

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Hey !

Got to be aware of where grub ( GRand Unified Bootloader) gets installed to . In a standard " erase disk and install ubuntu" that location is 'sda' .. That may or may not be what you want.
```

sudo pated -l

```
To identify your devices.
If this is a legacy partition scheme , I can assist in properly installing grub if it not installed to the drive that ubuntu is installed to .

[INDENT][INDENT]bios is point a
[INDENT][INDENT]the kernel is point g
[INDENT][INDENT][INDENT]a lot must happen between a and g
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-08
Alrighty, well....

I was able to backup my hard drive onto my partner's computer. Then I switched out my hard drive for that one, and ubuntu installed fine and is currently up and running on my pc with no problems. So my only logical guess at this point is that my 500GB is shot and no longer any good. =/

---

### Post by Bashing-om on 2016-05-08
Chelsey_Martin; Hey !

Look at the progress you have made ! You do good work . Up and running .

To check your suspect drive:
[https://en.wikipedia.org/wiki/S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T).
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)

[INDENT]hard drives
[INDENT][INDENT][INDENT]live hard, die young
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Chelsey_Martin on 2016-05-09
I'll check that out later today! Thanks so much! Since my original issue has been solved I'm going to go ahead and mark this thread as solved.

Thanks for sticking it out with me <3

---

### Post by Bashing-om on 2016-05-09
Chelsey_Martin; Great !

Help is what we do .

All's well
[INDENT][INDENT]that ends well
[/INDENT][/INDENT]

---

