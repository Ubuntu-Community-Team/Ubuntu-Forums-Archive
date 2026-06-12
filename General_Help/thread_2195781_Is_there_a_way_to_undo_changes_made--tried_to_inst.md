---
title: "Is there a way to undo changes made--tried to install Bamboo tablet"
date: 2013-12-26
forum: General Help
---

### Post by m3ATmeX on 2013-12-26
I followed this post [http://ubuntuforums.org/showthread.php?t=1515562&highlight=wacom+bamboo+pen+touch+tablet](http://ubuntuforums.org/showthread.php?t=1515562&highlight=wacom+bamboo+pen+touch+tablet) and only did step 1, following the directions for [B][SIZE=3] Install input-wacom-0.13.0's wacom.ko 

[/SIZE][/B][SIZE=2]When I tried to restart as directed[/SIZE], I had a black screen (did not take note of what it said--yes, stupid I know) and a blinking cursor for typing. I tried to restart it again, and the second time (and subsequent times) I will get the purple screen like it's going to start normally, and then the name ubuntu (still on the purple screen) flashes, then goes off. Then it comes on again and then the screen turns black and stays that way. Did I screw up the graphics card? I was going to reinstall 12.4 again but my screen was messed up and the install screens were not legible enough for me to feel comfortable doing anything. (I also tried with a disk for 11.10 I believe it was, but that screen was even MORE messed up.) Is there a way to get a terminal up early on in the startup or am I screwed?

Thank you. And please be patient with me. I know--I know only enough to be dangerous.

---

### Post by ian-weisser on 2013-12-26
When the graphical system fails, try CTRL+ALT+F1 to reach a login terminal.
If the terminal comes up, then you can disable that kernel module.
If the terminal does not come up, please let us know.

---

### Post by m3ATmeX on 2013-12-26
ian-weisser, thank you for your response!
I did manage to get to login and now it's a black screen that says "wecome to ubuntu 12.04.3 LTS GNU/Linux 3.5.0-44-generic x86_64...documentation https://help.ubuntu.com/" etc. So now it has a terminal line for me, but I am not sure how to disable the kernel module and don't want to screw it up more. Can you walk me through that part?
Thank you!!!

---

### Post by m3ATmeX on 2013-12-26
Or maybe walk me through undoing ALL the things I inputted into terminal from that post?...

---

### Post by steeldriver on 2013-12-26
How about you start by posting the output of 

```
lsmod | grep wacom
```

---

### Post by m3ATmeX on 2013-12-27
Well, here's a problem. Apparently I know even less than I thought I did. I tried lsmod | grep wacom and got nothing, nada. So I have only part of whatever was installing for the wacom tablet actually installed. I guess getting it (whatever it is) off/out of my computer is my goal. I obviously have no business installing something on a machine I don't want screwed up. Ideas?

---

### Post by steeldriver on 2013-12-27
Perhaps the issue is unrelated (or only tangentially related) to the wacom driver build? There have been several reports of recent updates breaking proprietary nvidia graphics drivers, it's possible that your system got updated (e.g. when you installed the kernel headers) and that's what caused it - what graphics do you have?

```
lshw -sanitize -C display
```

---

### Post by m3ATmeX on 2013-12-27
I have to type this out because the pictures I took were unclear...
The first time I put in the code, I got a warning to use this program as super-user, so I redid it with sudo and this is what I got.

description: VGA compatible controller
product: Xeon E3-1200 v2/3rd Gen Core Processor Graphics Controller
vendor: Intel Corporation
physical id:2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f0000 (size=64)

I am not sure what video driver I am using quite honestly. I just know it's a Dell (had windows 8 until I deleted it for ubuntu).

---

### Post by m3ATmeX on 2013-12-30
Anyone have ANY suggestions?

---

### Post by steeldriver on 2013-12-30
I'm not aware of any recent problems with the Intel i915 driver

You can try to see why the X server apparently isn't able to start by looking at the most recent Xorg log file

```
tail /var/log/Xorg.0.log
```
or
```
grep '(EE)' /var/log/Xorg.0.log
```

---

### Post by m3ATmeX on 2013-12-30
I put in tail /var/log/Xorg.0.log and got this:

[   8455.236] (II) UnloadModule: "evdev"
[   8455.236] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Close
[   8455.236] (II) UnloadModule: "evdev"
[   8455.236] (II) evdev: Power Button: Close
[   8455.236] (II) UnloadModule: "evdev"
[   8455.236] (II) evdev: Video Bus: Close
[   8455.236] (II) UnloadModule: "evdev"
[   8455.236] (II) evdev: Power Button: Close
[   8455.236] (II) UnloadModule: "evdev"
[   8455.441] Server terminated successfully (0). Closing log file.

Of course being curious I put in the second command you gave me and now all I have are >'s when I hit enter. How do I get back to being able to put commands in again? :( Sorry! (And thank you for your response!!)

---

### Post by steeldriver on 2013-12-30
maybe you missed a closing quote around the '(EE)'? in any case, you can get back to the command prompt using Ctrl-C

---

### Post by m3ATmeX on 2013-12-30
Thanks, that worked for the command prompt.

---

### Post by m3ATmeX on 2013-12-30
I am not sure what I'm looking at in this log. Does it tell you anything about why it isn't starting? Or is that not the problem?

---

### Post by steeldriver on 2013-12-30
(EE) denotes errors - there shouldn't be any except a header line like "(WW) warning, (EE) error, (NI) not implemented, (??) unknown."

The 'tail' didn't really show enough to tell us anything - you could try tailing more lines e.g.

```
tail **-20** /var/log/Xorg.0.log
```

---

### Post by m3ATmeX on 2013-12-31
I tried to put in the grep `(EE)` command--I do not know which key you are using for the single quote mark and I THINK I've tried them all. Regardless, I managed to get a picture of the screen this time with the results of that as well as the results of the last code entered. Apologies for the size of the picture--I did make it smaller, I guess not small enough.
[IMG]https://dl.dropboxusercontent.com/u/22753245/2013-12-31%2018.36.36.jpg[/IMG]

---

### Post by steeldriver on 2013-12-31
The correct quotes were the ones that gave you the red [COLOR=#ff0000]'(EE)'[/COLOR] - the fact that you only got the header line means there were no errors. So we can close down that line of inquiry.

I've read the webpage more carefully now - can you remember exactly how far you got? did you copy the new wacom.ko module to your system /lib/modules directory and run depmod? I'm just trying to see if re-installing the kernel image package will correct that... standby

---

### Post by m3ATmeX on 2013-12-31
I did all of this:

cd Desktop

wget [http://prdownloads.sourceforge.net/linuxwacom/input-wacom-0.13.0.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/input-wacom-0.13.0.tar.bz2)

sudo apt-get update

*(For **Mint** use **libX11-dev** instead of libx11-dev in the following command)*
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool

sudo apt-get upgrade

uname -r

*(If you have the generic kernel which most do.)*
sudo apt-get install linux-headers-generic

*(If you have the rt or pae kernel.)*
sudo apt-get install linux-headers-rt
**or**
sudo apt-get install linux-headers-generic-pae

tar xjvf input-wacom-0.13.0.tar.bz2

cd input-wacom-0.13.0

./configure --prefix=/usr

not realizing there was more before shutting down!! STUPID I know!...Well, that's what I believe happened anyway. It's definitely something I WOULD do.

---

### Post by steeldriver on 2013-12-31
If you stopped short of

```
sudo cp ./2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

then as far as I can see you didn't make any permanent changes to your system apart from the 'sudo apt-get upgrade', and the problems you're having now must be related to **that **rather than to the wacom module

If you're not sure whether you did the `cp` or not, have a look at the datestamp on the file 

```
ls -l /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

---

### Post by m3ATmeX on 2013-12-31
This is what I got when I put the second code in:

-rw-r--r-- 1 root root 87856 Nov 13 11:37 /lib/modules/3.5.0-44-generic/kernel/drivers/input/tablet/wacom.ko


I do not believe I got to that step in the process before I shut down. I am not even sure at this point if I want to continue the install. I think I would rather "purge" the system of all the steps. Is there a way to do that?

---

### Post by m3ATmeX on 2014-01-03
Anyone know if there is a way to "purge" the install from my computer?

---

### Post by steeldriver on 2014-01-03
Based on those instructions, the only thing you actually installed were the standard system packages and headers (you didn't do any 'sudo' commands involving the downloaded wacom package)

I think you should concentrate on why the X server isn't starting and not assume it's related to the downloaded wacom package - you could try starting lightdm manually from the virtual terminal

```
sudo service lightdm start
```

and making a note of any errors, and/or 

```
pastebinit /var/log/Xorg.0.log
```

and post the URL for us to look at

---

### Post by m3ATmeX on 2014-01-03
I put in sudo service lightdm start and got: 
-bash: /home/leanne: Is a directory

I then tried the pastebinit command and had to install pastebinit (just as a note to you) and got this url:
[http://paste.ubuntu.com/6685233](http://paste.ubuntu.com/6685233)

---

### Post by steeldriver on 2014-01-03
Is that the only message you get from the lightdm start attempt? 

Do you have auto-login enabled for user leanne? You can check with

```
cat /etc/lightdm/lightdm.conf
```

---

### Post by m3ATmeX on 2014-01-03
Yes, that is the only message I got from the lightdm start attempt

when I put in the cat command, this is what I got:

[SeatDefaults]
autologin-guest-false
autologin-user=leanne
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu

---

### Post by steeldriver on 2014-01-03
OK can we try disabling your autologin for now, just to see if lightdm is able to start? that would narrow the problem down to something screwed up in your user session, rather then the system as a whole

You can use

```
sudo nano /etc/lightdm/lightdm.conf
```

to edit the file in the console, and comment out all the autologin lines by putting # characters in front

```

[SeatDefaults]
# autologin-guest-false
# autologin-user=leanne
# autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=unity-greeter
user-session=ubuntu

```

or if you want a command to do that

```
sudo sed -i '/^autologin/ s//# &/' /etc/lightdm/lightdm.conf
```

and then try

```
sudo service lightdm start
```

again

---

### Post by m3ATmeX on 2014-01-03
Ok, I put in the # but can't get out of that screen it shows ^X for quit (among others) but that didn't get me out of that screen... and there are command prompts for me at the moment. I tried control C and that didn't work either.

---

### Post by steeldriver on 2014-01-03
^X is shorthand for Control-X

---

### Post by m3ATmeX on 2014-01-03
Thank you. :-P
I put in the last line and it said:
Start: Job is already running: lightdm

---

### Post by steeldriver on 2014-01-03
OK how about

```
sudo service lightdm restart
```

or

```

sudo service lightdm stop

sudo service lightdm start

```

---

### Post by m3ATmeX on 2014-01-03
I guess it's also a good idea to mention that I also have accounts on the machine for my two kids (also auto login I believe). Will that matter or was that part of the whole autologin with the #?

---

### Post by m3ATmeX on 2014-01-03
I got:
 lightdm stop/waiting
lightdm start/running, process 14489

---

### Post by m3ATmeX on 2014-01-05
Ok, I went back and reread all your posts and tried the command sudo service lightdm stop and got:
stop: Unknown instance

I take it that means more than one of us was logged in when I was messing with the system ?
My son did say he may have been and forgot to log himself out...

---

### Post by steeldriver on 2014-01-05
If you rebooted after the attempted driver install then nobody would have been logged on to the system - "stop: unknown instance" just means that lightdm wasn't running (we're trying to find out why) and "lightdm start/running, process 14489" means it apparently started OK - but didn't (I assume) take you to a GUI login screen 

Can we double check that your lightdm conf file is now free from the autologin stuff?

```
cat /etc/lightdm/lightdm.conf
```

---

### Post by m3ATmeX on 2014-01-05
Yes, all the autologins are commented out.

---

### Post by m3ATmeX on 2014-01-05
should I try restarting again to see if the login screen comes on?

---

### Post by steeldriver on 2014-01-05
yes worth a try ...

---

### Post by m3ATmeX on 2014-01-05
ok, now it's stuck on the purple ubuntu screen with the dots turning from white to red... the dots do keep going through white to red to white, does that mean the computer is thinking or is that just automatic?

---

### Post by m3ATmeX on 2014-01-05
I hit esc and among all the lines it says
Starting LightDM Display Manager [COLOR=#ff0000]Fail[/COLOR]
and 
Starting Recovery option if display manager fails to start [COLOR=#ff0000]Fail[/COLOR]

---

### Post by m3ATmeX on 2014-01-05
I am posting a picture (sorry for the blur, but it is still readable)--I find it odd the first instance of "starting lightdm display manager" was marked ok, then three lines down "starting lightdm display manager" failed, right under that the "Starting recovery options if display manager fails to start" was marked ok but at the very end it failed as well (those are the only two instance on the "page" marked as failed.)
[ATTACH=CONFIG]249245[/ATTACH]

---

### Post by m3ATmeX on 2014-01-06
Should I try this?

[HR][/HR]sudo apt-get remove --purge lightdm

sudo apt-get install lightdm

Edit: I tried to purge and reinstall lightdm and this is what happened at boot:
[ATTACH=CONFIG]249298[/ATTACH]

---

### Post by m3ATmeX on 2014-01-11
Is it possible to fix this with a live cd? Or does 12.04 not have a live cd?

---

