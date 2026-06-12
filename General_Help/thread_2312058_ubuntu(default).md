---
title: "ubuntu(default)"
date: 2016-02-01
forum: General Help
---

### Post by wyndlass on 2016-02-01
ok, i don't have any idea what i did wrong( can't recall doing anything that could cause this) but here's what's going on, my login into ubuntu(default) ( not fallback to compiz or metacity) has some how gotten messed up. 1 day it was fine, the the next i noticed that after logging in the the little network status screen in the upper right corner had the text and icon shifting positions in the status box. after the login is done, either my desktop icons will flash or just my wallpaper is visible. 

i can ctrl-alt-f1, alt-r/shift-sysrq-reisub and move the highlight/select from icon to another. but nothing else.

i'm using a samsung np-nc10 with a 250 gb hd, 2 gb ram, intel 945 graphics, with an external display since i broke the screen on my laptop. 

i've tried xorg -configure, says the xorg isn't there. tried checking .*authority and had to fix the permissions for those do to a problem with my compiz login that i'm having now.
sudo xrandr says can't open display. i even tried getting rid of monitors.xml so that can be recreated and hoped that would fix the problem,nope didn't. 

the external monitor is an old crt so i can't go carting that around or else i'd try doing updating this os  at the library to see if that would work. i'm out of ideas as to what to try. thanx for any help. i wouldn't be surprised if i accidentally corrupted something w/o knowing i did.

---

### Post by Bashing-om on 2016-02-02
wyndlass; OK ..

1st up is that we have to have internet connectivity - else will be a real pain piggy-back'n files from an alternate box . Yuk ! 
So, can you get us a terminal (ctl+alt+F1) from the login screen ?
and now do we have contact with the outside world:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

Then we start look'n at the log files and see if we get any hints on what is not taking place.

[INDENT][INDENT]mamma I broke it
[INDENT][INDENT][INDENT]son, it's 'buntu, we can fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-02
ctrl-alt-f1 works. but no internet at home. right now i use a crt as an external display so i can't get my laptop to the library. i'd probably have been alot further along in solving this if i had internet access. i like that tag lines at the end of you post.

i just recently hear of the paste bin. how do i get to that when i have logs that are too big for posting. and how do i use it when posting?

---

### Post by Bashing-om on 2016-02-02
wyndlass; Ouch >

With no internet .. going to be a challenge and time consuming to gather info > With no access to info, not much we can do to help.

So, the problem confronting us is how to get required info to us from this crippled machine.
How are you presently communicating with us ?... can we use this medium to transfer files ?
Presently would behoove us to read the log files of the crippled system to get a hint of what is not taking place .
From a PM I am advised the log files are to large to upload to the forum and we must utilize external means.

[INDENT][INDENT]when the going gets tough
[INDENT][INDENT][INDENT]the tough get going
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-02
i'm using a library computer and my pos fon as a flash drive so not much mem there. yes the logs are too big to post to the forums. i already knew this was going to be time consuming. if i use my other fon(acts solely as an mp3 player now) and clear my music of it, i'll have approx 1.5 gb for use(maybe a little more since it's a 2gb micro sd). i might be able to use the lib computer for more than pdfing and such. depends on if the stuff will fit the sd card.

---

### Post by Bashing-om on 2016-02-02
wyndlass; Ho Kay ...

Going to be a long haul .. Are you up for it ?
For a 1st time getting started and a look'n:
From the crippled machine run:
```

cat /var/log/Xorg.0.log > xorg-txt

```
then copy the xorg-txt file to the micro sd and at the library console do:
```

cat <path_to_the_micro>/xorg-txt | nc termbin.com 9999

```
when all goes right .. that file is uploaded to a paste site, the result in terminal is a URL, pass that complete link back here into the thread.
With that link we can access the file and read the log .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by dragonfly41 on 2016-02-02
If you still have a LiveCD/DVD/USB lying around somewhere (which you used to install Ubuntu) that when booted up should give you Internet access.

---

### Post by wyndlass on 2016-02-03
dragonfly, i don't have internet at home, cable or satellite. if i did i would've been able to post from there instead of having to go to the library.

my .xsession-errors and .xsession-errors.old are right here:     

```
jad@jadaja-NC10:~$ cat .xsession-errors
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: upstart-event-bridge main process (3694) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (3714) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
jad@jadaja-NC10:~$ cat .xsession-errors.old
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: upstart-event-bridge main process (4775) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: unity-settings-daemon main process (4853) killed by HUP signal
upstart: at-spi2-registryd main process (4855) killed by HUP signal
upstart: gnome-session (GNOME-Flashback:Unity) main process (4856) killed by HUP signal
upstart: indicator-messages main process (4952) killed by HUP signal
upstart: indicator-bluetooth main process (4955) killed by TERM signal
upstart: indicator-power main process (4956) killed by TERM signal
upstart: indicator-datetime main process (4959) killed by TERM signal
upstart: indicator-keyboard main process (4963) killed by HUP signal
upstart: indicator-sound main process (4969) killed by HUP signal
upstart: indicator-session main process (4972) killed by TERM signal
upstart: indicator-application main process (4989) killed by TERM signal
upstart: indicator-application pre-stop process (9205) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
```

i'll have to do the cat cp thing later on and will post the results tomorrow. would be much easier if i could connect to a free internet server to do all this.

no i don't have a live usb(no dvd on my laptop) the last flash drive i lost and hadn't had the money to get a new yet, dragonfly. wouldn't matter since i don't have cable or satellite anyways. the only thing that it would help me with is getting some files off it.

since i currently can't use the net with my system, what do you guys think about my xsession logs? what are they saying that can help me?

---

### Post by Bashing-om on 2016-02-05
wyndlass; Well ..

The key to finding resolution is in obtaining information. The .xsession log does not give us much, And of what is
> 
upstart: indicator-application pre-stop process (9205) killed by TERM signal
upstart: Disconnected from notified D-Bus bus

I honestly do not know how relevant this is ..

What we might do, seeing as how we can not at this time get a look at the log file we really need to examine ( /var/log/Xorg.0.log) is see what results when attempting to start the GUI from terminal - We will need to see exactly what the system returns into the terminal .
We need to know what release you have installed, as 14.04 has upstart for the initiate system, and 15.10 has systemd. Differing means to start that GUI from terminal.

[INDENT][INDENT]maybe a long slow process
[INDENT][INDENT][INDENT]but, time and effort will produce
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-05
vivid (15.04. i haven't gone to 15.10, when my friend gives me her laptop, i am going to wait for 16.04 to come out in april before i upgrade. i'm gonna keep 15.04, on my current laptop tho, well the hard drive anyways.

---

### Post by Bashing-om on 2016-02-05
wyndlass; UHMMMM ....

15.04, not a good thought ... 15.04 is END_OF_LIFE now and has NO support . The software repository will be - if not already - turned down and away . security risk !

I strongly urge you at this time to install a supported release .. clean and fresh. Take the box and CRT to a friend's house with internet and install 14.04 or 15.10 ( short term support also ).

[INDENT][INDENT]beating a dead horse
[INDENT][INDENT][INDENT]has no point
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-06
in the next 2 posts will be my lightdm log file. had to break it up to post.

```

jad@jadaja-NC10:~$ sudo cat /var/log/lightdm/lightdm.log
[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.03s] DEBUG: Starting Light Display Manager 1.14.4, UID=0 PID=2564
[+0.03s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.03s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.03s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.03s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.03s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registered seat module xlocal
[+0.03s] DEBUG: Registered seat module xremote
[+0.03s] DEBUG: Registered seat module unity
[+0.05s] DEBUG: Monitoring logind for seats
[+0.05s] DEBUG: New seat added from logind: seat0
[+0.05s] DEBUG: Loading properties from config section SeatDefaults
[+0.05s] DEBUG: Seat seat0: Starting
[+0.05s] DEBUG: Seat seat0: Creating greeter session
[+0.13s] DEBUG: Seat seat0: Creating display server of type x
[+0.15s] DEBUG: Deactivating Plymouth
[+0.19s] DEBUG: Using VT 7
[+0.19s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.19s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.19s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.19s] DEBUG: DisplayServer x-0: Launching X Server
[+0.19s] DEBUG: Launching process 2595: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.19s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.20s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.20s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.25s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.25s] DEBUG: User /org/freedesktop/Accounts/User1002 added
[+0.81s] DEBUG: User /org/freedesktop/Accounts/User1001 added
[+0.81s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+1.95s] DEBUG: Got signal 10 from process 2595
[+1.95s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+1.95s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+1.95s] DEBUG: Quitting Plymouth; retaining splash
[+2.00s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+2.00s] DEBUG: Session pid=2621: Started with service 'lightdm-greeter', username 'lightdm'
[+2.15s] DEBUG: Session pid=2621: Authentication complete with return value 0: Success
[+2.15s] DEBUG: Seat seat0: Session authenticated, running command
[+2.15s] DEBUG: Session pid=2621: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+2.15s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+2.15s] DEBUG: Session pid=2621: Logging to /var/log/lightdm/x-0-greeter.log
[+3.55s] DEBUG: Activating VT 7
[+3.55s] DEBUG: Activating login1 session c1
[+3.55s] DEBUG: Seat seat0 changes active session to c1
[+3.55s] DEBUG: Session c1 is already active
[+5.37s] DEBUG: Session pid=2621: Greeter connected version=1.14.4 resettable=false
[+7.40s] DEBUG: Session pid=2621: Greeter start authentication for jad
[+7.40s] DEBUG: Session pid=2670: Started with service 'lightdm', username 'jad'
[+7.47s] DEBUG: Session pid=2670: Got 1 message(s) from PAM
[+7.47s] DEBUG: Session pid=2621: Prompt greeter with 1 message(s)
[+9.89s] DEBUG: User /org/freedesktop/Accounts/User119 added
[+36.06s] DEBUG: Session pid=2621: Continue authentication
[+36.29s] DEBUG: Session pid=2670: Authentication complete with return value 0: Success
[+36.29s] DEBUG: Session pid=2621: Authenticate result for user jad: Success
[+36.29s] DEBUG: Session pid=2621: User jad authorized
[+36.31s] DEBUG: Session pid=2621: Greeter requests session gnome-flashback-metacity
[+36.40s] DEBUG: Writing /home/jad/.dmrc
[+36.50s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+36.50s] DEBUG: Session pid=2621: Sending SIGTERM
[+36.63s] DEBUG: Session pid=2621: Exited with return value 0
[+36.63s] DEBUG: Seat seat0: Session stopped
[+36.63s] DEBUG: Seat seat0: Greeter stopped, running session
[+36.63s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+36.67s] DEBUG: Session pid=2670: Running command /usr/sbin/lightdm-session /usr/lib/gnome-flashback/gnome-flashback-metacity
[+36.67s] DEBUG: Creating shared data directory /var/lib/lightdm-data/jad
[+36.67s] DEBUG: Session pid=2670: Logging to .xsession-errors
[+38.36s] DEBUG: Activating VT 7
[+38.36s] DEBUG: Activating login1 session c2
[+38.36s] DEBUG: Seat seat0 changes active session to c2
[+38.36s] DEBUG: Session c2 is already active
```

i'll need to get my xorg log file again and break it up the same way. will post that on monday, i think. bashing, if i had a car, it wouldn't be as much as a problem taking the crt with me, but i have nothing like that, all on foot, bike, or bus. carrying a crt in either of those ways is unfeasible. i wish those things weren't so damned big and heavy. i hope the lightdm log file is very helpful in fixing my current problems.

---

### Post by Bashing-om on 2016-02-06
wyndlass; Welp ...

Upfront, with 15.04 only so long as the End_of_Life repository of 15.04 is still up do we have any chance of restoring this system . As soon as that repository goes off-line we are up that creek .

Presently; I myself do not perceive a problem reported in the lightdm log file .

The log reflects:
> 
[+36.63s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+36.67s] DEBUG: Session pid=2670: Running command /usr/sbin/lightdm-session /usr/lib/gnome-flashback/gnome-flashback-metacity
[+36.67s] DEBUG: Creating shared data directory /var/lib/lightdm-data/jad
[+36.67s] DEBUG: Session pid=2670: Logging to .xsession-errors
[+38.36s] DEBUG: Activating VT 7
[+38.36s] DEBUG: Activating login1 session c2
[+38.36s] DEBUG: Seat seat0 changes active session to c2
[+38.36s] DEBUG: Session c2 is already active

that you are activating the gnome-flashback DE. So what results when from the username login box you choose to start an alternate DE ? And what other (D)esktop (E)nvironments do you have installed ? Do we have a conflict of interest here ?

With out seeing the respective log files and examining the config files will be a real pain and most likely non-productive - hit and miss - to resolve this situation .
---------------------
Each session we start here, you are to verify that the 15.04 repo is still up and available.
Do terminal command:
```

sudo apt update

```
When the package manager returns files not found it is all over .. no use in even crying .
Lesson learned here is to place your operating system dependency on the Long_Term_Support releases .

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-02-07
wyndlass; Hey;

Still hanging with you, trying to come up with a solution.
An ooopps on my part:
> 
Each session we start here, you are to verify that the 15.04 repo is still up and available.
Do terminal command:
Code:
sudo apt update

as you do not have internet . It is difficult for me to think over this hurdle . At this present time, under the constraints of no internet AND no USB thumb drive to transfer files , and an EOL release..... I just do not see a way to proceed. Not to say we can not poke, stroke and hope. When we do find the fault, how can we replace the faulty packaging ? How do we get you up on a currently supported release ?

[INDENT][INDENT]there are those times
[/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-08
hey, bashing, i have a theory about fixing both the ubuntu(default) and this new login loop prob when my fallback(compiz) the .*authority files are under my ownership and that's not the problem there. i want to figure out what went wrong so i can create a new account and recreate the problems and test out my theory before trying it out on my account.  i don't know if my xorg log will fit in this message or not but here goes nothing.

```
[    92.201] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    92.201] X Protocol Version 11, Revision 0
[    92.201] Build Operating System: Linux 3.19.0-28-generic i686 Ubuntu
[    92.201] Current Operating System: Linux jadaja-NC10 3.19.0-43-generic #49-Ubuntu SMP Sun Dec 27 17:51:21 UTC 2015 i686
[    92.201] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-43-generic root=/dev/mapper/ubuntu--vg-root ro splash quiet video=LVDS-1:d video=VGA1:e
[    92.202] Build Date: 11 September 2015  10:31:05AM
[    92.202] xorg-server 2:1.17.1-0ubuntu3.1 (For technical support please see http://www.ubuntu.com/support) 
[    92.202] Current version of pixman: 0.32.6
[    92.202] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    92.202] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    92.202] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb  6 17:41:20 2016
[    92.345] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    92.612] (==) No Layout section.  Using the first Screen section.
[    92.613] (==) No screen section available. Using defaults.
[    92.613] (**) |-->Screen "Default Screen Section" (0)
[    92.613] (**) |   |-->Monitor "<default monitor>"
[    92.614] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    92.614] (==) Automatically adding devices
[    92.614] (==) Automatically enabling devices
[    92.614] (==) Automatically adding GPU devices
[    92.626] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    92.626] 	Entry deleted from font path.
[    92.741] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    92.741] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    92.741] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    92.741] (II) Loader magic: 0x802f0700
[    92.741] (II) Module ABI versions:
[    92.741] 	X.Org ANSI C Emulation: 0.4
[    92.741] 	X.Org Video Driver: 19.0
[    92.741] 	X.Org XInput driver : 21.0
[    92.741] 	X.Org Server Extension : 9.0
[    92.742] (II) xfree86: Adding drm device (/dev/dri/card0)
[    92.745] (--) PCI:*(0:0:2:0) 8086:27ae:144d:ca00 rev 3, Mem @ 0xf0000000/524288, 0xd0000000/268435456, 0xf0300000/262144, I/O @ 0x00001800/8
[    92.746] (--) PCI: (0:0:2:1) 8086:27a6:144d:ca00 rev 3, Mem @ 0xf0080000/524288
[    92.746] (II) LoadModule: "glx"
[    92.763] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    92.767] (II) Module glx: vendor="X.Org Foundation"
[    92.767] 	compiled for 1.17.1, module version = 1.0.0
[    92.767] 	ABI class: X.Org Server Extension, version 9.0
[    92.767] (==) AIGLX enabled
[    92.767] (==) Matched intel as autoconfigured driver 0
[    92.767] (==) Matched intel as autoconfigured driver 1
[    92.767] (==) Matched modesetting as autoconfigured driver 2
[    92.768] (==) Matched fbdev as autoconfigured driver 3
[    92.768] (==) Matched vesa as autoconfigured driver 4
[    92.768] (==) Assigned the driver to the xf86ConfigLayout
[    92.768] (II) LoadModule: "intel"
[    92.769] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    92.769] (II) Module intel: vendor="X.Org Foundation"
[    92.769] 	compiled for 1.17.1, module version = 2.99.917
[    92.769] 	Module class: X.Org Video Driver
[    92.770] 	ABI class: X.Org Video Driver, version 19.0
[    92.770] (II) LoadModule: "modesetting"
[    92.770] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    92.790] (II) Module modesetting: vendor="X.Org Foundation"
[    92.790] 	compiled for 1.17.1, module version = 1.17.1
[    92.790] 	Module class: X.Org Video Driver
[    92.790] 	ABI class: X.Org Video Driver, version 19.0
[    92.790] (II) LoadModule: "fbdev"
[    92.791] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    92.816] (II) Module fbdev: vendor="X.Org Foundation"
[    92.816] 	compiled for 1.17.1, module version = 0.4.4
[    92.816] 	Module class: X.Org Video Driver
[    92.816] 	ABI class: X.Org Video Driver, version 19.0
[    92.816] (II) LoadModule: "vesa"
[    92.817] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    92.820] (II) Module vesa: vendor="X.Org Foundation"
[    92.820] 	compiled for 1.17.1, module version = 2.3.3
[    92.820] 	Module class: X.Org Video Driver
[    92.820] 	ABI class: X.Org Video Driver, version 19.0
[    92.820] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,

	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    92.822] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    92.822] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    92.822] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    92.822] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    92.822] (II) FBDEV: driver for framebuffer: fbdev
[    92.823] (II) VESA: driver for VESA chipsets: vesa
[    92.823] (++) using VT number 7

[    92.823] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    92.823] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917-1~exp1ubuntu2.3 (Robert Hooker <sarvatt@ubuntu.com>)
[    92.824] (II) intel(0): SNA compiled for use with valgrind
[    92.824] (WW) Falling back to old probe method for modesetting
[    92.824] (WW) Falling back to old probe method for fbdev
[    92.824] (II) Loading sub module "fbdevhw"
[    92.824] (II) LoadModule: "fbdevhw"
[    92.825] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    92.851] (II) Module fbdevhw: vendor="X.Org Foundation"
[    92.851] 	compiled for 1.17.1, module version = 0.0.2
[    92.851] 	ABI class: X.Org Video Driver, version 19.0
[    92.851] (WW) Falling back to old probe method for vesa
[    92.852] (--) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
[    92.852] (--) intel(0): CPU: x86, sse2, sse3, ssse3
[    92.852] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    92.853] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    92.853] (==) intel(0): RGB weight 888
[    92.853] (==) intel(0): Default visual is TrueColor
[    92.853] (II) intel(0): Output LVDS1 has no monitor section
[    92.854] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output LVDS1
[    92.854] (II) intel(0): Enabled output LVDS1
[    92.854] (II) intel(0): Output VGA1 has no monitor section
[    92.854] (II) intel(0): Enabled output VGA1
[    92.855] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    92.855] (II) intel(0): Output VIRTUAL1 has no monitor section
[    92.855] (II) intel(0): Enabled output VIRTUAL1
[    92.856] (--) intel(0): Output VGA1 using initial mode 1024x768 on pipe 0
[    92.856] (==) intel(0): TearFree disabled
[    92.856] (==) intel(0): DPI set to (96, 96)
[    92.856] (II) Loading sub module "dri2"
[    92.856] (II) LoadModule: "dri2"
[    92.856] (II) Module "dri2" already built-in
[    92.856] (II) Loading sub module "present"
[    92.856] (II) LoadModule: "present"
[    92.856] (II) Module "present" already built-in
[    92.857] (II) UnloadModule: "modesetting"
[    92.857] (II) Unloading modesetting
[    92.857] (II) UnloadModule: "fbdev"
[    92.857] (II) Unloading fbdev
[    92.858] (II) UnloadSubModule: "fbdevhw"
[    92.858] (II) Unloading fbdevhw
[    92.858] (II) UnloadModule: "vesa"
[    92.858] (II) Unloading vesa
[    92.858] (==) Depth 24 pixmap format is 32 bpp
[    92.859] (II) intel(0): SNA initialized with Alviso (gen3) backend
[    92.859] (==) intel(0): Backing store enabled
[    92.859] (==) intel(0): Silken mouse enabled
[    92.859] (II) intel(0): HW Cursor enabled
[    92.859] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    92.860] (==) intel(0): DPMS enabled
[    92.860] (==) intel(0): display hotplug detection enabled
[    92.860] (II) intel(0): [XvMC] i915_xvmc driver initialized.
[    92.860] (II) intel(0): [DRI2] Setup complete
[    92.860] (II) intel(0): [DRI2]   DRI driver: i915
[    92.860] (II) intel(0): [DRI2]   VDPAU driver: i915
[    92.860] (II) intel(0): direct rendering: DRI2 enabled
[    92.860] (II) intel(0): hardware support for Present enabled
[    92.860] (--) RandR disabled
[    92.886] (II) SELinux: Disabled on system
[    93.024] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    93.024] (II) AIGLX: enabled GLX_ARB_create_context
[    93.024] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    93.024] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    93.024] (II) AIGLX: enabled GLX_INTEL_swap_event
[    93.024] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    93.024] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    93.024] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    93.024] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    93.024] (II) AIGLX: Loaded and initialized i915
[    93.025] (II) GLX: Initialized DRI2 GL provider for screen 0
[    93.034] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    93.049] (II) intel(0): Setting screen physical size to 270 x 203
[    93.677] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    93.692] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    93.692] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    93.692] (II) LoadModule: "evdev"
[    93.693] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    93.694] (II) Module evdev: vendor="X.Org Foundation"
[    93.694] 	compiled for 1.16.0, module version = 2.9.0
[    93.694] 	Module class: X.Org XInput Driver
[    93.694] 	ABI class: X.Org XInput driver, version 21.0
[    93.694] (II) Using input driver 'evdev' for 'Power Button'
[    93.694] (**) Power Button: always reports core events
[    93.694] (**) evdev: Power Button: Device: "/dev/input/event3"
[    93.695] (--) evdev: Power Button: Vendor 0 Product 0x1
[    93.695] (--) evdev: Power Button: Found keys
[    93.695] (II) evdev: Power Button: Configuring as keyboard
[    93.695] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    93.695] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    93.695] (**) Option "xkb_rules" "evdev"
[    93.695] (**) Option "xkb_model" "pc105"
[    93.695] (**) Option "xkb_layout" "us"
[    93.697] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    93.697] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    93.697] (II) Using input driver 'evdev' for 'Video Bus'
[    93.697] (**) Video Bus: always reports core events
[    93.697] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    93.698] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    93.698] (--) evdev: Video Bus: Found keys
[    93.698] (II) evdev: Video Bus: Configuring as keyboard
[    93.698] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input16/event9"
[    93.698] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    93.698] (**) Option "xkb_rules" "evdev"
[    93.698] (**) Option "xkb_model" "pc105"
[    93.698] (**) Option "xkb_layout" "us"
[    93.700] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    93.700] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    93.700] (II) Using input driver 'evdev' for 'Power Button'
[    93.700] (**) Power Button: always reports core events
[    93.700] (**) evdev: Power Button: Device: "/dev/input/event1"
[    93.701] (--) evdev: Power Button: Vendor 0 Product 0x1
[    93.701] (--) evdev: Power Button: Found keys
[    93.701] (II) evdev: Power Button: Configuring as keyboard
[    93.701] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    93.701] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    93.701] (**) Option "xkb_rules" "evdev"
[    93.701] (**) Option "xkb_model" "pc105"
[    93.701] (**) Option "xkb_layout" "us"
[    93.703] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    93.703] (II) No input driver specified, ignoring this device.
[    93.703] (II) This device may have been added with another device file.
[    93.704] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    93.704] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    93.704] (II) Using input driver 'evdev' for 'Sleep Button'
[    93.704] (**) Sleep Button: always reports core events
[    93.704] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    93.704] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    93.705] (--) evdev: Sleep Button: Found keys
[    93.705] (II) evdev: Sleep Button: Configuring as keyboard
[    93.705] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    93.705] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    93.705] (**) Option "xkb_rules" "evdev"
[    93.705] (**) Option "xkb_model" "pc105"
[    93.705] (**) Option "xkb_layout" "us"
[    93.707] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[    93.707] (II) No input driver specified, ignoring this device.
[    93.707] (II) This device may have been added with another device file.
[    93.708] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
[    93.709] (II) No input driver specified, ignoring this device.
[    93.709] (II) This device may have been added with another device file.
[    93.710] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event5)
[    93.710] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    93.710] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    93.710] (**) Logitech USB Keyboard: always reports core events
[    93.710] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event5"
[    93.710] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    93.710] (--) evdev: Logitech USB Keyboard: Found keys
[    93.710] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    93.710] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/0003:046D:C31C.0001/input/input13/event5"
[    93.711] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 10)
[    93.711] (**) Option "xkb_rules" "evdev"
[    93.711] (**) Option "xkb_model" "pc105"
[    93.711] (**) Option "xkb_layout" "us"
[    93.713] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event6)
[    93.713] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    93.713] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    93.713] (**) Logitech USB Keyboard: always reports core events
[    93.713] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event6"
[    93.714] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    93.714] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    93.714] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    93.714] (--) evdev: Logitech USB Keyboard: Found keys
[    93.714] (II) evdev: Logitech USB Keyboard: Forcing relative x/y axes to exist.
[    93.714] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    93.714] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    93.714] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/0003:046D:C31C.0002/input/input14/event6"
[    93.714] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 11)
[    93.714] (**) Option "xkb_rules" "evdev"
[    93.714] (**) Option "xkb_model" "pc105"
[    93.714] (**) Option "xkb_layout" "us"
[    93.715] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    93.715] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    93.715] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    93.715] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    93.716] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    93.717] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event8)
[    93.717] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    93.717] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    93.717] (**) Logitech USB Optical Mouse: always reports core events
[    93.717] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event8"
[    93.772] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc018
[    93.772] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[    93.772] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    93.772] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    93.772] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    93.772] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    93.772] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    93.772] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    93.772] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    93.772] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:046D:C018.0003/input/input15/event8"
[    93.773] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 12)
[    93.773] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    93.773] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    93.773] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    93.773] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    93.773] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    93.775] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[    93.775] (II) No input driver specified, ignoring this device.
[    93.775] (II) This device may have been added with another device file.
[    93.776] (II) config/udev: Adding input device Namuga 1.3M Webcam (/dev/input/event12)
[    93.776] (**) Namuga 1.3M Webcam: Applying InputClass "evdev keyboard catchall"
[    93.776] (II) Using input driver 'evdev' for 'Namuga 1.3M Webcam'
[    93.776] (**) Namuga 1.3M Webcam: always reports core events
[    93.776] (**) evdev: Namuga 1.3M Webcam: Device: "/dev/input/event12"
[    93.776] (--) evdev: Namuga 1.3M Webcam: Vendor 0xac8 Product 0xc326
[    93.776] (--) evdev: Namuga 1.3M Webcam: Found keys
[    93.776] (II) evdev: Namuga 1.3M Webcam: Configuring as keyboard
[    93.777] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input19/event12"
[    93.777] (II) XINPUT: Adding extended input device "Namuga 1.3M Webcam" (type: KEYBOARD, id 13)
[    93.777] (**) Option "xkb_rules" "evdev"
[    93.777] (**) Option "xkb_model" "pc105"
[    93.777] (**) Option "xkb_layout" "us"
[    93.779] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    93.779] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    93.779] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    93.779] (**) AT Translated Set 2 keyboard: always reports core events
[    93.779] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    93.779] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    93.779] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    93.779] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    93.780] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    93.780] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    93.780] (**) Option "xkb_rules" "evdev"
[    93.780] (**) Option "xkb_model" "pc105"
[    93.780] (**) Option "xkb_layout" "us"
[    93.782] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    93.782] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    93.782] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    93.782] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    93.782] (II) LoadModule: "synaptics"
[    93.783] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    93.783] (II) Module synaptics: vendor="X.Org Foundation"
[    93.783] 	compiled for 1.16.0, module version = 1.8.99
[    93.783] 	Module class: X.Org XInput Driver
[    93.783] 	ABI class: X.Org XInput driver, version 21.0
[    93.783] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    93.783] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    93.783] (**) Option "Device" "/dev/input/event7"
[    93.811] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    93.812] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5878 (res 89)
[    93.812] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5888 (res 249)
[    93.812] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    93.812] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    93.812] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    93.812] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    93.812] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    93.812] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    93.831] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input12/event7"
[    93.831] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[    93.831] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    93.831] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    93.831] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.032
[    93.832] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    93.832] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    93.832] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    93.832] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    93.832] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    93.833] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    93.833] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   100.824] (II) intel(0): EDID vendor "HWP", prod id 1283
[   100.824] (II) intel(0): Using EDID range info for horizontal sync
[   100.824] (II) intel(0): Using EDID range info for vertical refresh
[   100.824] (II) intel(0): Printing DDC gathered Modelines:
[   100.824] (II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz eP)
[   100.824] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   100.824] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   100.825] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   100.825] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   100.825] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   100.825] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   100.825] (II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz e)
[   100.825] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   100.825] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   100.825] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   100.825] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   100.825] (II) intel(0): Modeline "1024x768i"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz e)
[   100.825] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   100.826] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   100.826] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   100.826] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   100.826] (II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[   100.826] (II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[   100.826] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   102.098] (II) intel(0): switch to mode 1024x768@85.0 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[   133.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   135.777] (II) intel(0): switch to mode 1024x768@75.1 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[   136.832] (II) XKB: reuse xkmfile /var/lib/xkb/server-3B33493C824D4D3EC3ED474A229F8BABB01BB04E.xkm
[   137.144] (II) XKB: reuse xkmfile /var/lib/xkb/server-3B33493C824D4D3EC3ED474A229F8BABB01BB04E.xkm
[   137.215] (II) XKB: reuse xkmfile /var/lib/xkb/server-3B33493C824D4D3EC3ED474A229F8BABB01BB04E.xkm
[   137.328] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.755] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.772] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.788] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.805] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.823] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.841] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.861] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.882] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.894] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.937] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.957] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.978] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   137.998] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.020] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.039] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.059] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.077] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.097] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.114] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.133] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.155] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.175] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.195] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.215] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.236] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.256] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.276] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.296] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.314] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   138.328] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6F0877534703B147E21AF348FBE3774565AFB0F.xkm
[   151.709] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   151.816] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   266.882] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   268.167] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   273.772] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   275.258] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   333.464] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   334.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   343.123] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   347.611] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   348.454] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   350.594] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   351.777] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   388.673] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
[   390.669] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FE8377308D1D927A0999B0C8E95AEA775CB0F7E.xkm
```

cool it worked. just won't in pm cuz of the 5000 character limit there.

---

### Post by howefield on 2016-02-08
> **wyndlass said:**
> cool it worked. just won't in pm cuz of the 5000 character limit there.

Well, not quite.. you need a forward slash in the second tag.

Like this [/code]

---

### Post by wyndlass on 2016-02-08
yeah i forgot about that, thanx. i was meaning that i actually didn't have to split it up into more than 1 message. i'm glad it worked. i puts empty lines in it cuz i thought i would need to.

---

### Post by Bashing-om on 2016-02-08
wyndlass; Welp ..

This gets seeper and deeper .
A level of complexity that I can not overcome - if this is a part of the problem - :
> 
Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-43-generic root=/dev/mapper/ubuntu--vg-root ro splash quiet video=LVDS-1:d video=VGA1:e

where you have chosen to encrypt the file system . I have no idea how do get beyond the encryption .

then there are the added boot parameters " video=LVDS-1:d video=VGA1:e" explain why they are there as it does appear that loading the performance graphics driver is inhibited .
dual graphics as seen here :
> 
(--) PCI:*(0:0:2:0) 8086:27ae:144d:ca00 rev 3, Mem @ 0xf0000000/524288, 0xd0000000/268435456, 0xf0300000/262144, I/O @ 0x00001800/8
[    92.746] (--) PCI: (0:0:2:1) 8086:27a6:144d:ca00 rev 3, Mem @ 0xf0080000/524288

but instead of loading  a proper graphics driver you are falling back onto :
> 
92.768] (==) Matched fbdev as autoconfigured driver 3
[    92.768] (==) Matched vesa as autoconfigured driver 4


And currently the Intel graphic's chip set is in use. I do not know how the afor said boot parameters affects this chip set ! .. 

Presently we need to know what hardware we are dealing with for the graphic's :
```

sudo lshw -C display
lspci -k | grep -EA2 'VGA|3D'

```
and see what we can do about getting the proper graphic's drivers installed and loaded .

If the kernel can not talk to the hardware. 
[INDENT][INDENT][INDENT]just will not have a display
[/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-09
video=lvds-1:d disables my internal monitor, screen is broke and thus useless. video=vga1:e is for my external monitor, the crt. these 2 commands force the system to not see my internal monitor thus it thinks i only have the external one, which is true anyways. i can't see the bios setup screens so i can't do any changes there. 

i never setup /home/jad with encryption. if it is now then the system went wonking and did it on it's own.

i don't really like the intel video chipset, would rather have one of the nvidia or ati ones i'll do the commands you just suggested and redirect the outsputs to a file so i can cut/paste them here.

---

### Post by wyndlass on 2016-02-10
ok here's lshw and lspci, in that order.

```


  *-display:0
       description: VGA compatible controller
       product: Mobile 945GSE Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0000000-f007ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:f0300000-f033ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0080000-f00fffff


```


```


00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Device ca00
	Kernel driver in use: i915


```

---

### Post by wyndlass on 2016-02-10
this is off-topic i know, but, what is the max characters in the forums? i wanna know for future reference.

---

### Post by Bashing-om on 2016-02-10
wyndlass; Outstanding .

You are doing well .
However, I re-affirm I may be doing you a grave injustice by attempting to repair this End_OF_LIFE release . There will be no further updates available including any security fixes. But for the sake of your learning, we continue and see what we can do to fix this install .

We know that the system foundation is firm, else you would not have a terminal.
We know that the system identifies the graphic's hardware
We know that the system loads the graphic's driver, that said driver is Intel i915; Intel supports us very well and the driver is integrated into the kernel . Thus we can expect there to be no problem in this area.
We know we are looking at a problem within that X layer .

So, the next thing to look at is the Desktop Environment and see what results when we attempt to start the desktop (GUI) from terminal.
Show now what returns:
```

ls -al /usr/share/xsessions
cat /etc/X11/default-display-manager
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```
To see what the options are, and get a notion of what we are going to try and start.

I can accept that with the 'echo' request the system will balk and advise us how crazy we are . Maybe the system in telling us how nuts we are to look for a desktop that is not started, will provide us some info . That info may be relevant .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-10
will try this next, bashing. again thanx for your help.

here are the ls and cat results. should all those belong to root:root or mym ain?



```

total 48
drwxr-xr-x   2 root root  4096 Jun 20  2015 .
drwxr-xr-x 456 root root 20480 Jan 29 16:45 ..
-rw-r--r--   1 root root   235 May  7  2015 gnome.desktop
-rw-r--r--   1 root root   276 Mar 31  2015 gnome-flashback-compiz.desktop
-rw-r--r--   1 root root   284 Mar 31  2015 gnome-flashback-metacity.desktop
-rw-r--r--   1 root root   458 Mar 16  2013 LXDE.desktop
-rw-r--r--   1 root root   198 Oct 26  2014 openbox.desktop
-rw-r--r--   1 root root   232 May  7  2015 ubuntu.desktop

```



```

/usr/sbin/lightdm

```


here's what the echo says in metacity.

```

gnome-flashback-metacity   GNOME-Flashback:Unity

```


in crtl-alt-f1 it shows nothing for the echo command. just an empty line.

since inubuntu(default) won't let me use ctrl-alt-t or right click menu to get a terminal, the ctrl-alt-f1 is the only 1 i can use and still no report.

---

### Post by Bashing-om on 2016-02-11
wyndlass; Heym hey ..

Making progress ... We now know that the DE is lightdm.
Now we want to know what lightdm starts.

post back the result:
```

cat /etc/lightdm/lightdm.conf

```
And we then know what we are going to start from that F1 console.

[INDENT][INDENT]a process in learning
[/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-11
```

jad@jadaja-NC10:~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
autologin-user=



```

---

### Post by Bashing-om on 2016-02-11
wyndlass; Shucks,

My bad, not the file I thought ...
configured default session should be in " /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf "

Post back:
```

cat /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf

```

maybe I got it right this time , and we see if we can start a DE .

[INDENT][INDENT]there are those times
[/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-11
```


jad@jadaja-NC10:~$ cat /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[SeatDefaults]
user-session=ubuntu
jad@jadaja-NC10:~$ 


```

---

### Post by Bashing-om on 2016-02-11
wyndlass; Great !

Now we have a target .

What results from the F1 console with terminal commands:
```

sudo systemctl stop lightdm.service
sudo systemctl start lightdm.service

```
Please provide back what is output to the terminal, as maybe the GUI starts maybe not . If it does not start helpful hints will be provided.

[INDENT][INDENT]progress made
[INDENT][INDENT][INDENT]small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-11
start shows nothing, stop locks puter up during acpi event daemon. had to ctrl-alt-del.

---

### Post by Bashing-om on 2016-02-11
wyndlass; Yuk !

Absolutely no idea of what is not taking place, totally unexpected result.

Any hints in the log file ?
Post :
```

cat /var/log/lightdm/lightdm.log | nc termbin.com 9999

```


[INDENT][INDENT]multiple DEs
[INDENT][INDENT][INDENT]which way did he go George
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-12
look back at page 2 second post for lightdm.log.

---

### Post by Bashing-om on 2016-02-13
wyndlass; Yikes.

I have installed release 15.10, and To my consternation, I have been unable to start the GUI from the F1 console; in the manner I expect it to start. At this point I do not know how I can assist you . There is just to much that I do not know about systemd.

Regrets, but I just do not know enough to help further in your predicament.

[INDENT][INDENT]ignorance is not bliss
[/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-13
thanx anyways. theory i have is to delete  main account while keeping the home folder for it then recreate the main account to see if that works. what do you think?

---

### Post by Bashing-om on 2016-02-13
wyndlass; Well;

It is a good thought .. can you successfully login to the guest account at this time ? That would infer config issues in "your" user account . In that case that you can login to the guest account, resetting the DE to defaults might be effective .

[INDENT][INDENT]it is possible
[/INDENT][/INDENT]

---

### Post by wyndlass on 2016-02-13
how do i reset to default? i can login as guest, as well as another account.

---

### Post by wyndlass on 2016-02-13
do you think my idea will reset my configs?

---

### Post by Bashing-om on 2016-02-14
wyndlass; Well,

We can certainly try to reset the DE to defaults .
```

sudo systemctl stop lightdm.service
rm ~/.config/dconf ~/.config/compiz-1 ~/.dmrc

```
where we stop any lightdm services that might be started and remove the lightdm config files. They will be re-created when restating the system.

reboot from terminal at this time:
```

sudo reboot now

```

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by wyndlass on 2016-05-04
i quit trying to figure out what was wrong. i'm using 15.10 on my new(for me) puter. been trying to get rid of the hdd password on the samsung, no luck so far.

---

