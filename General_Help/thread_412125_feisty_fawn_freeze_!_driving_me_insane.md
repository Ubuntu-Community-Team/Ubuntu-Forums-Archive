---
title: "feisty fawn freeze ! driving me insane"
date: 2007-04-17
forum: General Help
---

### Post by Digitallysick on 2007-04-17
feisty fawn keeps freezing on me, at first i thought it was FF causeing the issue. But now i have tried opera and it still happens, at random. Mostly when it freezes i can still move the mouse, but thats it. Today it froze with the screen saver (gnome feet). How can i tell what is causing this? would it be in the system logs? i can't take it much longer

---

### Post by Stereotypical Rage on 2007-04-18
I am having the same issue and I don't know where to start either.

I too can move the mouse, but I can't click on anything. It just locks up. Yet the clock still counts up in seconds and all.

---

### Post by viciouslime on 2007-04-18
You should both file bug reports. Go to [http://launchpad.net]("http://launchpad.net") to do this. Also, did you upgrade to feisty or did you fresh install? If you upgraded I would recommend you do a fresh install instead.

---

### Post by Digitallysick on 2007-04-18
I did a fresh install of feisty beta , ive turned off beryl so im going to see if it happens again in the next few weeks

---

### Post by Stereotypical Rage on 2007-04-18
> **viciouslime said:**
> You should both file bug reports. Go to [http://launchpad.net]("http://launchpad.net") to do this. Also, did you upgrade to feisty or did you fresh install? If you upgraded I would recommend you do a fresh install instead.
I had to install the server version then upgrade to Gnome. 

I don't know where to start when filing bug report. Any particular place to start looking?

---

### Post by se2131 on 2007-04-20
I have also been having lots of random freezes after upgrading to Feisty Fawn.

The thing is, this happened to me a month ago as well, when i downloaded the Beta.  I was forced to downgrade to Edgy, and I was hoping that it would be fixed by now.  The Beta was a fresh install, this was an upgrade, so I don't think changing the method of installation would do anything.

From [http://ubuntuforums.org/showthread.php?t=392690](http://ubuntuforums.org/showthread.php?t=392690)

"I have been using Edgy, and yesterday I wiped it out and replaced it with the feisty beta installation. Under Edgy, my computer would freeze every once in a while (about once every day or two), but then I found that if I cooled it down w/ an external fan, then the freezing happened much less frequently. I attributed it to heat problems, and forgot about it.

Now after installing Feisty, it's freezing on me very often (about every hour or two), even with the cooling fan. What's more worrisome is that it seems to happen more or less randomly, I can't duplicate it at will.

So my question is: is there a way I can figure out why my computer freezes, after the fact (a log file or something of some sort)? I've done very little configuring since the installation, so I'm not sure if it's something that I've done. Should I go back to edgy until the feisty release comes out?

Additionally, when it freezes, I can still move the mouse, but I can't go to a virtual terminal, Ctrl-Alt-Backspace or anything. Only way to reboot it is to do a hard shut down or the Alt-PrtSc-S,Alt-PrtSc-U,Alt-PrtSc-B thing (which usually is successful at rebooting)

Btw, I have a Toshiba Satellite A75 computer, with a pentium 4 chip (probably why it's heating up too much)."

My graphics card is an ATI Radeon 9100

---

### Post by professor_chaos on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Im having similar problems on a new Darter Ultra that I upgraded to feisty from edgy.
My system is freezing every few minutes sometimes.

[http://system76.com/forums/viewtopic.php?t=1375](http://system76.com/forums/viewtopic.php?t=1375)

run the command 
```
tail -f /var/log/messages
```
to catch any errors you might be getting.

---

### Post by Digitallysick on 2007-04-21
I turned beryl off while a while, i thought it was more stable but nope, one day it went to screen saver, then the monitor went to sleep (as it should) but when i moved the mouse it was froze on my screen saver, and all i could do is move the mouse. (this is with beryl off) and the screen saver is gnome feet (not graphic intense by any means) I hear all this "jazz" about it being my ram, and cooling, im 99% sure its not ( i have 2 gb of geil mem) and a watercooled proc. So to debunk this what apps do i need to test my memory and stability???

---

### Post by Invius on 2007-04-21
Might you all be using ati restricted drivers? if so I believe that is the cause, I was rock solid till I enabled those drivers (more specifically, enabled those, then compiz, and later beryl) you all crash with things as simple as screensavers, I am guessing these are opengl related, either way, it is video related, I am currently downloading sabayon to play with it, if anyone is interested, you may wish to read this as it suggests a workaround for ati users.

[http://beranger.org/index.php?article=354](http://beranger.org/index.php?article=354)

---

### Post by derrekito on 2007-04-21
> **Digitallysick said:**
> I did a fresh install of feisty beta , ive turned off beryl so im going to see if it happens again in the next few weeks

This might sound like a dumb question but:  Feisty Fawn is not beta anymore, so have you tried installing the official release from scratch?

---

### Post by oomingmak on 2007-04-21
> **Digitallysick said:**
> feisty fawn keeps freezing on me, at first i thought it was FF causeing the issue. But now i have tried opera and it still happens, at random. Mostly when it freezes i can still move the mouse, but thats it. Today it froze with the screen saver (gnome feet). How can i tell what is causing this? would it be in the system logs? i can't take it much longer
I posted the same thing in the Feisty Problems thread last week:

See Link:  [http://ubuntuforums.org/showthread.php?p=2465694#post2465694](http://ubuntuforums.org/showthread.php?p=2465694#post2465694)

It's really irritating. It happens to me about every 10 minutes or so, usually when there is disk activity, or a few actions that I've done in quick succession (like opening several menu items).

---

### Post by Digitallysick on 2007-04-21
I still have the same issues, i tried with beryl off/on for a week or so, makes no difference it seems, i thought it was FF so i tried opera for a while and it still does the same. Im using nvidia drivers.

---

### Post by derrekito on 2007-04-21
> **Digitallysick said:**
> I still have the same issues, i tried with beryl off/on for a week or so, makes no difference it seems, i thought it was FF so i tried opera for a while and it still does the same. Im using nvidia drivers.

Could you offer more information about your hardware?  (e.g cpu, graphics card, anything else you think may be significant.)  Also let us know what drivers and version you are running for the graphics card. What distribution are you running? (e.g feisty fawn 64-bit, official release, beta ).  are you also running the default kernel, custom kernel, have you made any significant changes to it?

---

### Post by wacky_ninjas on 2007-04-21
> **Digitallysick said:**
> I still have the same issues, i tried with beryl off/on for a week or so, makes no difference it seems, i thought it was FF so i tried opera for a while and it still does the same. Im using nvidia drivers.

I had the _exact_ same problem in Edgy a few months ago (could move the mouse, but nothing else). I also use the nvidia drivers and I also thought it was Firefox at first. I was eventually able to fix it using instructions on this page:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

The specific fix for this issue is about 3/4 of the way down the page.

The short answer is: open /etc/X11/xorg.conf with your favorite editor (using sudo) and add the lines which begin with the word "Option" in this section of the file:

```
Section "Device"
 Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
 Driver "nvidia"
 BusID "PCI:1:0:0"
 Option "NvAGP" "0"
 Option "RenderAccel" "Off"
 Option "IgnoreDisplayDevices" "DFP,TV"
 Option "NoRenderExtension" "Off"
 Option "AllowGLXWithComposite" "Off"
EndSection
```

It stopped the freeze-ups for me, although it may have also slowed down my graphics a bit. But with my old GeForce 2 MX400, I'm not expecting all that much, anyway. I was hoping that Feisty would fix this as well, but apparently not... (haven't upgraded just yet)

Good luck.

---

### Post by Elcoco on 2007-04-21
Im having the same problem, so far it happens when i use the desktop effects or beryl my video card is good enough to handle beryl since i used it all the time in edgy. After i made a fresh feisty install i started having problems with the effects. i tried the changes to the .conf that where sugested but the xserver didnt even want to start up with them. ill include my .conf file incase any of you want to take a look
 PS. i installed the nvidia drivers using envy and added this to my conf
```
 sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GT/GTO]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GT/GTO]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by wacky_ninjas on 2007-04-21
Elcoco -

What suggested changes did you make to the .conf? The ones in my earlier post, or something else? I'm pretty sure that the changes I posted are intended to fix a _specific_ problem with the nvidia driver, which matches the OP's description very well. This is a freeze-up where you can move the mouse pointer, but nothing else seems to work. If your symptoms are different, then the solution I posted may not be the right one for you.

Also, I'm no expert on xorg.conf, but I'm fairly sure that you're not supposed to add commands like "nvidia-xconfig" to the .conf file. It's all "sections" that identify different aspects of your X system, like the "Option" lines in the nvidia Device section. I'd bet that adding a *command* to that file could cause the xserver to choke like that, if that's what you did.

BTW, I just found an update to the link I posted earlier:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy")

It still offers the same advice as before in the Problems section at the bottom. There's no Feisty update yet. There's other advice on that page that I didn't have to try, and a link to an nvidia-specific forum. The page was written by tseliot, the same guy who wrote the envy tool, I think.

---

### Post by Elcoco on 2007-04-21
first of all nvidia-config is behind ## so its commented, this is how it was made by the nvidia installer and the link you gave actually did help me out because now i can run enemy territory without it crashing but disabling composits makes it impossible to use beryl, it seems like this option may be whats causing everyones problems so if you are getting these freezes when trying to play games or other more graphics demanding programs try using this line
```
sudo nvidia-xconfig --no-composite
```

hope someone finds a way to fix this

---

### Post by wacky_ninjas on 2007-04-21
Elcoco-

Well, I'm glad I could offer *some* help. But I guess I misread your description of what you did in xorg.conf.

I've been poking around on launchpad and other places, and this seems to be quite the popular bug. There are several reports that match this description very closely.

On the nvidia forums, it appears that different options can help different users. For example, some people seem to have fixed their freeze-ups by only disabling the **RenderAccel** option. Check this thread in particular:
[http://www.nvnews.net/vbulletin/showthread.php?t=47502]("http://www.nvnews.net/vbulletin/showthread.php?t=47502")

If you try that, and it's stable, then maybe you can still have composites for Beryl. At this point it's all guesswork, though...

Also, I found these links very interesting - Ubuntu docs on how to debug a system crash (or at least collect a kernel log):
[https://help.ubuntu.com/community/DebuggingSystemCrash]("https://help.ubuntu.com/community/DebuggingSystemCrash")

and a full list of the "magic" Alt-SysRq commands, which should work even when commands like Alt-F1 don't:
[http://lxr.linux.no/source/Documentation/sysrq.txt]("http://lxr.linux.no/source/Documentation/sysrq.txt")

---

### Post by Vashu on 2007-04-22
Same problem here. Its really a issue.
It seems to be triggered by something with the mouse but i could be wrong. I also upgraded from edgy to feisty and keep getting these freezes constantly. I even accessed my machine (hp nw9440 laptop) from another pc in the network via ssh and it worked fine in console mode, ran a top and everything seemed fine...

then i tried to stop/killall/restart gdm. they were all successful but nothing changed on the laptop screen.

Then i "sudo reboot" and it restarted correctly. 

So it seems to be a problem with X. the rest of the services seems to work just fine. Maybe some damaged library? kernel?

Edit:
After reading some of the posts above I noticed most if not all of us have nvidia cards. althou im using the "nv" since i couldnt get the restricted ones working on my laptop.

---

### Post by FuturePilot on 2007-04-22
I've found that ```
Option "RenderAccel" "true"
```
caused freeze ups for me. I removed that line and never had a freeze up since.

---

### Post by se2131 on 2007-04-22
In case this affects anyone, I figured out how to fix my problem:

I was seeing an 8254 timer error at boot-up, I guess I should've focused more on it.  Some simple searching showed me to put in the "noapic" argument into my kernel line at boot-up, and since I did that, the computer hasn't frozen.

---

### Post by wacky_ninjas on 2007-04-22
> **Vashu said:**
> After reading some of the posts above I noticed most if not all of us have nvidia cards. althou im using the "nv" since i couldnt get the restricted ones working on my laptop.

Well, that's a bit different. Most of the reports I've seen indicate that they _don't_ freeze up with the default nv driver. But everyone wants the nvidia drivers for performance, of course.

Also, a lot of people report that they can ssh into their computer and kill X to recover. They might be doing something a bit different from killing gdm. When you ran top, did it look like X was using far too much processor time? (But I guess that wouldn't "seem fine" if you had seen it.) That's been reported by others, too.

FuturePilot - Thanks for the confirmation on RenderAccel. It's worth a try.

se2131 - Did you have the exact same freeze-up as the OP, with mouse pointer movement?

And to anyone else who gets this freeze-up, if tricks like Alt-F1 and Alt-Backspace don't work, the magic word to reboot without messing up your filesystem is "SUB":
- Alt-SysRq-S : sync mounted filesystems (wait for "Ok" and "Done")
- Alt-SysRq-U : remount filesystems as read-only (wait for "Ok" and "Done")
- Alt-SysRq-B : reboot!

Share and Enjoy! [SIZE="1"]TM[/SIZE]

---

### Post by se2131 on 2007-04-22
My crashes sound familiar, it would happen at random points and was unduplicatable.  The mouse was still responsive, but the applications would freeze up.  I could change the workspace occasionally, but I couldn't get to a text terminal, do ctrl-alt-backspace, or even alt-prtscr-k.  I talked to someone in the ubuntu chatroom on IRC, and he said that it might be related to I/O overload.  That made me remember that I do have a boot-up error that I've been ignoring:

"MP-BIOS: 8254 timer not connected to IO-APIC"

So I did the "noapci" thing and it's been fine since.


EDIT: Sorry, that should read "noapic"

---

### Post by Vashu on 2007-04-23
Tried the noapic solution, didn't work for me.

Then I ran another top and noticed Xorg was consuming 100% processor power. Also read around for more people with this problem and it doesn't seem to bee an nvidia specific problem.

But it does seem to only affect laptops since im posting from my desktop that hasn't frozen once since I upgraded. 

Any info I supply to help pinpoint the problem? 
Same symptoms unresponsive X with responsive mouse. Unable to ctrl+alt+backspace or any such combination and background services work fine. 

Here's the content of the TOP command:
top - 01:30:49 up 28 min,  1 user,  load average: 1.17, 1.03, 0.75Tasks: 126 total,   3 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.1%us,  0.0%sy,  0.0%ni, 49.6%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%stMem:   2075972k total,   765612k used,  1310360k free,    68004k buffers
Swap:        0k total,        0k used,        0k free,   521684k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
5274 root      25   0  306m  27m  10m R  100  1.3  14:07.75 Xorg               
    1 root      15   0  2908 1848  524 S    0  0.1   0:01.36 init                   2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0            4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1            6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1             8 root      10  -5     0    0    0 S    0  0.0   0:00.05 events/0           
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1              10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread               35 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   36 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1             37 root      12  -5     0    0    0 S    0  0.0   0:00.20 kacpid             
   38 root      12  -5     0    0    0 S    0  0.0   0:00.18 kacpi_notify         209 root      10  -5     0    0    0 S    0  0.0   0:00.04 kseriod

---

### Post by astronutties on 2007-04-23
I've been having the same problems. I just did a fresh install of Feisty last night. Unfortunately, I am new to all of this and don't really understand how to do a lot of the suggestions made to fix my problem.

What I have noticed is that it seems to happen when I run a lot of programs all at once. It seems to only happen when my memory becomes full with cache. I have only noticed this because I have a system monitor showing my memory usage.

I also have an ATI Radeon 9000 IGP but am not sure whether this is part of the problem or not. If any one can point me in a direction that's not too technical for my level, I would greatly appreciate it.

By the way...UBUNTU ROCKS!

---

### Post by Acknud on 2007-04-23
Vashu stated he thought the lockups were only in laptops.  It is happening in my desktop as well (AMD Athlon 3500+, 512 DDR 400, nVidia card).

---

### Post by Macuyiko on 2007-04-23
Feisty is freezing here too. Using a laptop (Thinkpad X60) with i810 driver. So no nv or ati. First I was happy that DRI and GLX where working on Feisty (I'm using dual screen). I've tried to disable them but I'm still getting crashes.

---

### Post by dawv on 2007-04-23
mine freezes every two and a half minutes or so, and the mouse dosen't move.. it just locks up the entire system, i havent even got to install it yet... it freezes and i have to reboot the hard way to try agian... feisty just isn't ready yet....

---

### Post by se2131 on 2007-04-23
astronutties:

I have an ATI Radeon 9100, so maybe my solution will work for you (see post #21 and #23)

I'm not sure how to do this the 'proper' way (editing the #defoptions line in /boot/grub/menu.lst is what I've been seeing, but the option never shows up the way it should when I do this), but here's what worked for me:

First do:

```
sudo nano /boot/grub/menu.lst
```

and scroll down until you see the line: ## ## End Default Options ## ##

After this, you will see lines that begin w/ title, root, kernel, initrd, and maybe quiet or savedefault.

What you need to do is find the kernel that you are using and edit the "kernel" line.

This is what my edits look like:

```


title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c8d81b8b-4a0a-4acb-b18f-6aa156583253 ro quiet splash **noapic**
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault


```

Make sure that you edit the kernel that you are planning to use.  If anyone knows how to make this option stick for all kernels, please provide your insight.

---

### Post by dawv on 2007-04-23
but its not JUST labtops that ae having trouble... im using a desktop and my freezing is worse.. so don't get conclusive after one result....

---

### Post by KrazyPenguin on 2007-04-23
> **dawv said:**
> but its not JUST labtops that ae having trouble... im using a desktop and my freezing is worse.. so don't get conclusive after one result....

Exactly.

Many people think it is a NVidia problem, but then people with ATI's and myself with Intel , along with many others are also experiencing freeze ups.

No one has figured out WHY??? yet !!! 
... and there doesn't seem to be a connection, except maybe for "Desktop Effects".

When I turn them off I don't freeze (at least I haven't in a while).

:twisted:

---

### Post by Macuyiko on 2007-04-23
I found a launchpad entry exactly describing my Intel problem here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/56501](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/56501) Maybe it's related to yours KrazyPenguin.

---

### Post by ghandi69_ on 2007-04-23
I am also having the same issue.  I have an nvidia 7600GT graphics card, and I did a fresh install.  Of note.. the first time I did a fresh install, without enabling anything.. the VERY first time I started it up, it said my x server crashed... So I just put the disc back in and tried again, and didn't have the issue the 2nd time.  I have the restricted drivers enabled, but I don't have beryl running.  I DID have desktop effects turned on however.  I have sinced turned off desktop effects, and havent had an issue, but that was only an hour ago.
edit::

I've noticed from others processor could be an issue..  I am an amd64 3200+ processor.

---

### Post by tgm4883 on 2007-04-23
> **KrazyPenguin said:**
> Exactly.

Many people think it is a NVidia problem, but then people with ATI's and myself with Intel , along with many others are also experiencing freeze ups.

No one has figured out WHY??? yet !!! 
... and there doesn't seem to be a connection, except maybe for "Desktop Effects".

When I turn them off I don't freeze (at least I haven't in a while).

:twisted:

Nope, freezes on mine all the time.  Never had desktop effects enabled

Core 2 Duo E6300
Nvidia GeForce 7300GS
Gigabyte 965P-DS3 Motherboard
Feisty 64-bit Fresh install from release

---

### Post by astronutties on 2007-04-23
Thanks for your help se2131. I have just made the changes logged in as root to the file as I couldn't work out how to do it in terminal. I haven't rebooted yet so I don't know whether it has worked or not. I will let you know when I am sure.

I made a mistake before when i said that I have an ATI Radeon 9000. My card is the same as yours, a 9100. Reading back through the thread again, I noticed that you own a Satellite A75. My lappy is also a Satellite A75 so I think we can confirm that this is not a random problem but a general issue among specific hardware.

Thanks again! :)

---

### Post by benner on 2007-04-23
i am having the same problems with mine.  ati x550 with fglrx enabled.  no desktop effects.  the machine has no heat problems.  i installed from the first proper feisty beta release and have upgraded each time.  i don't remember this from the first kernel but starting somewhere along the way when the updates started pouring in.  it freezes at boot time when the splash screen is there and the progress bar has moved up a bit.  it freezes when i have just opened a new program.  sometimes it just freezes when i'm doing nothing.  it froze int ehmiddloe of the night last night when it was downloading.  i have an amd4200+.  i forget the motherboard.  i'm not at home now.  it has been bugging me for a while.  some people have been blaming gaim.  i don't have it installed.  some blame desktop effect.  i don't use them.  some on nvidia.  some on ati.  some in intel cards.  it seems there is no pattern emerging yet.  unless there are a lot of problems with the same symptoms.  i can say that while i had a lot of problems with the beta when i first installed it, this was not one of them.  only when i solved the other problems did this one pop up.  i never seem to get any peace with thi9s thing.  i had nearly as many problems with edgy.  not enough to go back to microsoft but enough to spend way more time than i've got in here.  cheers everyone.  it's good we are all trying to help eachother.

---

### Post by Vashu on 2007-04-24
I wish they'd fix it. I cant even use my laptop for more than 15minutes while on fiesty. while windows works normally.

Since people with both ati and nvidia cards seem to experience it, people using both kubuntu and ubuntu and desktop and laptops the problem has become even more of a general issue. Maybe a service of the X server is eating up the resources or something, or maybe core/processor incompatibility. 

Here's the specs to my laptop:
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-3329741-1839859.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-3329741-1839859.html)

Is there any way to rollback to edgy until the problem is fixed?

---

### Post by astronutties on 2007-04-24
It may not necessarily have anything to do with the graphics card. That just seems to be the most likely cause. ATI, nVidia and Intell based card users are all having problems and as far as I am aware, those are the three most used companies... (Don't quote me on this). So it may have nothing to do with the graphics card.

I'm still not sure if the **noapic** fix has done anything or not. i havent crashed yet so thats a good sign. Hope we can work out whats going on soon.

---

### Post by tgm4883 on 2007-04-24
> **tgm4883 said:**
> Nope, freezes on mine all the time.  Never had desktop effects enabled

Core 2 Duo E6300
Nvidia GeForce 7300GS
Gigabyte 965P-DS3 Motherboard
Feisty 64-bit Fresh install from release

I really doubt this is what fixed it, but I didn't change anything else.

I renamed /etc/messages to /etc/messages.backup and created a new /etc/messages (I did this because I wanted to see what it said right before it crashed.

Now I have been trying to make it crash and can't for the life of me get it to.  Before it would crash within 2 minutes of powering on the computer

---

### Post by malegria on 2007-04-24
> **Invius said:**
> Might you all be using ati restricted drivers? if so I believe that is the cause, I was rock solid till I enabled those drivers (more specifically, enabled those, then compiz, and later beryl) you all crash with things as simple as screensavers, I am guessing these are opengl related, either way, it is video related, I am currently downloading sabayon to play with it, if anyone is interested, you may wish to read this as it suggests a workaround for ati users.

[http://beranger.org/index.php?article=354](http://beranger.org/index.php?article=354)

I've been using the ati restricted drivers via the Restricted Drivers Manager, and yes that's when my problems started. Ay caramba!:guitar:

---

### Post by mills on 2007-04-25
same problem here with the freezing

can move the mouse but the buttons wont do anything except within a web page i can use left button to highlight text but thats it, it varies in its frequency, rebooting about once an hour roughly but can be just a few minutes and i cant replicate it but can kind of guess when its happened because my mouse pointer seems to jump to the other side of the screen.

ati 9200se open source drivers
                     (tried the official drivers too, no effect)
i don't use desktop effects

i had the beta version via dist upgrade
this final release installed via iso image
both would freeze

not sure if this is related or normal but by just moving a window my cpu% jumps right up to about 90%-100%, is this normal anyone?
and also i doubt its a temperature thing, iam at 39-40 degrees most of the time

i've just done the noapic thing, i'll post back if any good but iam not holding my breath

**EDIT**: noapic didnt do the job although it did last 3 hours without freezing, which is much more bearable

---

### Post by iopo on 2007-04-25
Hi everybody!

Same problem here, but I'm not using any restricted driver and I have a fresh installation of the final feisty release! I'm on ati and I have 'desktop effects' enabled.

Here what happen: for no apparent reason (although it is somehow correlated with firefox) the CPU usage goes to 90% for about 20 sec. If during this period I open menus if I do something in a fast sequence the computer freezes: I can move the mouse but nothing responds, no <ctrl><alt><Bckspace> or <ctr><alt><del>. The only thing I can do is <alt><prnt scrn><b>.

I also notice one thing. When the CPU usage peaks (90% or so), if I open the system monitor there are just 4-5 active processes using around 5% each. Weird!

I tried the 'noapic' option. Nothing change. I also disabled 'hdparm'. It happen somehow less frequently but still happen.

I'm just waiting for this problem to be solved to show off my new OS with my friends!

Thanks



Edit: as tmg4883 pointed out, here are my specs: Dell inspiron 6000, intel pentium M (no dual core!),  ATI Mobility Radeon X300
[http://reviews.cnet.com/Dell_Inspiron_6000/4507-3121_7-31257675.html](http://reviews.cnet.com/Dell_Inspiron_6000/4507-3121_7-31257675.html)

---

### Post by Vashu on 2007-04-25
> **mills said:**
> same problem here with the freezing

can move the mouse but the buttons wont do anything except within a web page i can use left button to highlight text but thats it, it varies in its frequency, rebooting about once an hour roughly but can be just a few minutes and i cant replicate it but can kind of guess when its happened because my mouse pointer seems to jump to the other side of the screen.

ati 9200se open source drivers
                     (tried the official drivers too, no effect)
i don't use desktop effects

i had the beta version via dist upgrade
this final release installed via iso image
both would freeze

not sure if this is related or normal but by just moving a window my cpu% jumps right up to about 90%-100%, is this normal anyone?
and also i doubt its a temperature thing, iam at 39-40 degrees most of the time

i've just done the noapic thing, i'll post back if any good but iam not holding my breath

**EDIT**: noapic didnt do the job although it did last 3 hours without freezing, which is much more bearable

The 100% processor thing is the same for me. Using noapic seems to delay the freezing but doesn't stop it. Also when it does the cursor becomes distorted into a rectangle (kind of like what people call artifacts). Without noapic it remains normal.

---

### Post by tgm4883 on 2007-04-25
Since not everybody has posted there system specs it makes it really hard to pinpoint what we all have in common (besides the freezing)

I wonder if this is related
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by iopo on 2007-04-25
Right! I edited my previous post with my system specs.
By the way, I don't have a dual core!

---

### Post by 13013kid on 2007-04-25
Also have the same problem with freezing...installed feisty with nvidia restricted drivers yesterday and all went well, however, today it froze up.  The cursor would not move and the keyboard was useless.  I did a hard reboot and it froze again within minutes of logging on.  I had modified my fstab and thought that might be an issue (side note: automatix2 has an option to add fat partitions to fstab...not a good idea).  I was not able to get to the fstab so I did a clean re-install.  Five minutes after logging in the computer once again froze, while using FF to find solutions.  Tried a third install with my second sata disconnected thinking maybe there was a heat issue.  This install also failed after five minutes.  Unfortunately I didn't have time to use a monitoring device to check the CPU or memory.  I also never had the opportunity to changed to restricted nvidia on either reinstall.
My computer is a Biostar 754 with a 3000 Athalon64 processor, nvidia GF5500/256mb,  WD 80gb sata, and 1gb of ddr400 and Feisty i386.
I reinstalled winders to see if it was a hardware issue...it's not.  I don't want to run winders,

---

### Post by vievie on 2007-04-25
Same here.  Firefox freeze about several seconds every few minutes.  Also mplayer.

Everyday, it freeze completely once, I can move cursor, do nothing else but reset.  then spend rest of my night in WinXP ....

Specs:
AMD 3600+ X2
ASUS M2NPV-VM N430 + 6150 integrated 
Maxtor PATA 200G 
1GB DDR2 667
Feisty i386 alternate (LVM )+ beryl

---

### Post by jessegillies on 2007-04-25
I'm also having the freezing problem. I'm able to move the mouse, but I can't click anything and there's no keyboard input. It probably happens four or five times a day.

Dell Inspiron 6000
Pentium M 1.6
2 GB ram
ATI x300 video card using radeon driver
Feisty installed from ISO (I had the same problem after I did dist-upgrade from Edgy)

---

### Post by benner on 2007-04-25
just to make sure that i've got it, the problem happens with 

32 and 64 bit systems
dual core and not
at least 3 different brands of video cards
restricted and open-source drivers
beta upgrades and final release installs
ubuntu and kubuntu (don't know about xubuntu or fluxbuntu)
a few people using edgy as well
with and without desktop effects
with or without virtual machines running
old and new machines (so heat is not likely an issue)
tons and tons of people and has been going on for a while and no official word on how to fix it or if it's a bug in the system or what

has anyone had a freeze without being connected to the internet?  (mine often freezes when i start downloading something)

anything i missed?  i was planning to do a fresh install until i read 13013kid's post about a fresh install and it still happens.  i have windows running in a virtual machine but the host freezes.  another day of this and i may have to actually switch back to windows.  i rarely get more than 10 minutes work in before it freezes on me.

---

### Post by Xyhthyx on 2007-04-25
I've had two freezes as described in this thread since I installed Feisty 3 days ago. Using a HP Pavillion ze5700 laptop. It's a weird freeze, the clock keeps ticking, gaim windows I have open I keep recieving messages in them, I can minimize and maximize windows. I just can't open menus, type anything, launch any new programs, etc. 

If it helps anyone, when this happens I do the following:
Left Alt + Print Screen + R (this sets the keyboard to RAW mode or something, which allows me to do the next command)
Left Alt + Left Ctrl + F1 (this brings up a full screen terminal)

After logging in the terminal session I type the following to restart X:
sudo /etc/init.d/gdm restart

Edit: Also, during my six months with Edgy, this exact type of freeze happened around a total of 3 times.

---

### Post by mills on 2007-04-26
_update on previous post_

using the noapic nolapic boot seems to have sorted the freezes
i had a freeze about 3 hours after i 1st entered the command but it was a different kind of freeze (Everything locked) since then i,ve left feisty running non stop and tried desperately to cause a freeze ie; opening loads of programs while downloading and countless windows open, but no freezes

its been 24 hours now, i should have had about 24 freezes at least

i think my problems fixed guys

EDIT; desktop effects are good to go as well, alas i can enjoy ubuntu again :)

---

### Post by KrazyPenguin on 2007-04-26
Freeze only happens when u least expect it!!!

:twisted:

---

### Post by austaph on 2007-04-26
Driving me crazy, too.  Sometimes everything freezes once every few hours, sometimes once every 10 minutes.  Only happens during activities like opening/closing windows or menus.  I can leave my laptop powered on overnight and come back to it in the morning with no problems.

Thought it was Gimp, then Amarok caused about 5 crashes in a row.  When they persisted, I thought it might be Beryl, then desktop effects.  I'm not willing to sacrifice much more, and I don't know where to begin searching for the cause, unfortunately.

Keeping this thread bookmarked in the meantime.

---

### Post by knuno on 2007-04-26
In addition to random freeze my system always freeze at shutdown. My screen is shutdown and then nothing happens. I have to turn power off on my computer to reboot. I am runnumg kubuntu on an ordinary PC. ATI Radeon 9800 XT card.

Knut

---

### Post by Digitallysick on 2007-04-26
In my var/log/messages, i get this ,does it have anything to do with my problem? i get it all the way down

Apr 26 21:29:35 adam-desktop kernel: [  206.627278] NVRM: os_map_kernel_space: can't map 0xe0008000, invalid context!
Apr 26 21:29:35 adam-desktop kernel: [  206.627283] NVRM: os_map_kernel_space: can't map 0xe0008000, invalid context!
Apr 26 21:29:35 adam-desktop kernel: [  206.627286] NVRM: os_map_kernel_space: can't map 0xe0008000, invalid context!
Apr 26 21:29:35 adam-desktop kernel: [  206.627289] NVRM: os_map_kernel_space: can't map 0xe0008000, invalid context!
Apr 26 21:29:35 adam-desktop kernel: [  206.627291] NVRM: os_map_kernel_space: can't map 0xe0008000, invalid context!

---

### Post by benner on 2007-04-26
got through the whole night without a freeze yesterday.  and i had a million windows open and a virtual machine that also had a million windows open.  before that was every 10 minutes.  and no updates since then.  weird.  i found this thying about a possible network card connection but don't know what to make of it.

[https://answers.launchpad.net/ubuntu/+question/5157](https://answers.launchpad.net/ubuntu/+question/5157)

---

### Post by Ubuntiac on 2007-04-27
Hmmm..

Well I'm getting the "cursor frozen, too" version. I have two computers, both running Kubuntu feisty 7.04 i386 (fresh install). One freezes, one doesn't:

**Computer A (freezes)**
[LIST]
[*]ASRock (cheapie) motherboard
[*]ATI Radeon 9600 (w fglrx)
[*]Beryl (installed, but not turned on)
[*]Single core intel P-IV
[*]1 gig ram
[*]single Samsung lcd screen
[*]Desktop
[/LIST]

**Computer B (never freezes)**
[LIST]
[*]Generic Motherboard
[*]Onboard Intel video (using OpenChrome)
[*]Beryl (installed, but not turned on)
[*]Single core intel P-IV
[*]512mb ram
[*]CRT monitor
[*]Desktop
[/LIST]

So it's obviously not a lack of ram (my non freezing computer has 50% less), it's not solely feisty (I used the same disk to install on both). I don't have any errors like the ones a couple of posts ago in my /var/logs/messages.

**Note:** One other wierd thing... when my computer hangs, the caps lock light on my M$ Multimedia 1.0A keyboard starts instantly blinking slowly on and off... Superwierd. Has M$ secretly sabbotaged my linux with a trojan keyboard? ;)

---

### Post by ksamvel on 2007-04-27
I used noapic option in Kernel and it seems to solve the problem. At least I am working on my laptop for another 30 minutes and no freezes took place.

---

### Post by Bealer on 2007-04-28
I too get this problem. The "noapic" solution hasn't worked for me.

I've got a standard, fresh install of Feisty.
I'm using the restricted drivers for my ATI X1950. 

It freezes randomly, I've not been able to determine when. Usually it'll just be all the windows, and I can still move the mouse, but nothing else responds. I didn't have any such problem with Edgy.


Spec:
E6300 Core 2 Duo
Gigabyte DS3
ATI X1950

---

### Post by wacky_ninjas on 2007-04-28
> **tgm4883 said:**
> Since not everybody has posted there system specs it makes it really hard to pinpoint what we all have in common (besides the freezing)

Ok, then:

Desktop
AMD Athlon 1300+
Asus A7V266-E
768 Mb RAM
NVIDIA GeForce2 MX400, CRT monitor
Ubuntu Edgy (maybe moving to Fiesty this weekend)
using NVIDIA restricted drivers from the repos

Until I disabled some options for the nvidia drivers in xorg.conf (see my earlier posts in this thread), my computer would freeze up several times per day. The mouse pointer would move, but nothing else responded, including sequences like Alt-Ctrl-F1 or Alt-Ctrl-Delete.

This mostly (but not exclusively) seemed to happen in Firefox, especially when using the scroll-wheel on my mouse. It once happened while nothing was open except Mines, I think. So I don't think my problem had much to do with having too many apps open. As this was on Edgy, there were no desktop effects to enable.

Disabling those driver options worked well for me, but then I don't demand much in terms of graphics. (As my HW specs surely attest.)

---

### Post by benner on 2007-04-29
i haven't had a single freeze since my last post.  days.  no idea what happened.  keeping my fingers crossed.  there were a couple of updates but i didn't see anything that looked significant.  good luck everybody.  hopefully i won't have to return to this thread...

-just had 2 freezes in the last 2 days.  damn!

---

### Post by dliberal on 2007-04-29
Greetings

I have a Toshiba A75 P4, ATI mobility radeon 9000. I had the same issue and it was solved with the noapic flag.

Thank you very much!

---

### Post by ozee on 2007-04-29
Hi

Most probably problem is not in configuration but in linux kernel. When you look in to /var/log/kernel.log you should find information like this:

```
Apr 29 09:49:33 lz-laptop kernel: [ 1587.764000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Apr 29 09:50:04 lz-laptop kernel: [ 1587.764000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
Apr 29 09:50:04 lz-laptop kernel: [ 1587.764000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr 29 09:50:04 lz-laptop kernel: [ 1594.805000] ata1: port is slow to respond, please be patient (Status 0xd0)
Apr 29 09:50:04 lz-laptop kernel: [ 1617.806000] ata1: port failed to respond (30 secs, Status 0xd0)
Apr 29 09:50:04 lz-laptop kernel: [ 1617.806000] ata1: soft resetting port
Apr 29 09:50:04 lz-laptop kernel: [ 1618.207000] ata1.00: configured for UDMA/100
Apr 29 09:50:04 lz-laptop kernel: [ 1618.397000] ata1.01: configured for MWDMA2
Apr 29 09:50:04 lz-laptop kernel: [ 1618.397000] ata1: EH complete
Apr 29 09:50:04 lz-laptop kernel: [ 1618.404000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
```

If you got earlier versin of ubuntu (6.06) you could notice that your hard drivers is now recognized as /dev/sdx insted of /dev/hdx. This heppend when ubuntu migrate to new ata drivers (libata?).

Kernel developers don't fix this bug yet but it is possible to stop system freezing. You should put cd-rom into your cd-driver. I known it is quit strange but it helps me and few other persons. 

Ozee

PS. Apologize for my English :(

---

### Post by frodon on 2007-04-30
BTW, just for the few of you who use skype 1.3, read this :
[https://bugs.launchpad.net/ubuntu/+bug/71037](https://bugs.launchpad.net/ubuntu/+bug/71037)
[https://bugs.launchpad.net/ubuntu/+source/alsa-modules-i386/+bug/73933](https://bugs.launchpad.net/ubuntu/+source/alsa-modules-i386/+bug/73933)


If i use skype 1.3 i got a 30s or 1min freeze each time someone call me or start a chat, it's the same if it's me who start the communication and this when i did used skype for more than 30 min. So i use skype 1.2 and have no problem with this anymore.

---

### Post by ajelliot on 2007-04-30
> **dliberal said:**
> Greetings

I have a Toshiba A75 P4, ATI mobility radeon 9000. I had the same issue and it was solved with the noapic flag.

Thank you very much!

Can somebody elaborate on this "noapic" fix? I need to know what text goes into what file at what point and why, if you have that info.

Thanks, I'm a newb.

---

### Post by se2131 on 2007-04-30
ajelliot: see post #29 in this thread

the noapic flag does something with interrupt routing, I'm not quite sure what though.

---

### Post by ajelliot on 2007-04-30
Oop, I'm blind. my_points--

I too have a Toshiba Satellite A75 and was getting the same 8254 timer error. Freezes were occuring once every 10 or 15 minutes. Now, not one freeze in just over an hour and a half. Knock on wood.

---

### Post by Bealer on 2007-05-01
I think I'm gonna give up and go back to Edgy. 

I've been watching the logs, but can't see anything wrong. My only slight suspicion is that the graphics card is overheating.

I know ATI cards run hot (I've got an X1900), but mine does seem quite hot. I was wondering if it could be the drivers causing the card to run hot as it runs fine in Edgy and Vista/XP. I really need to find some monitoring software so I can watch the temps.

I'll switch back to Edgy and just make sure it's ok. If it is, then I definitely know something isn't right with Feisty.

As much as I like Feisty, an unstable computer is possibly the worst thing I could have (would rather go back to Windows). Just as a side note, I tried most of the possible fixes I could find.

The noapic (there was another one named similar, can't remember its name) to the Grub boot entry.
Not having a cd in the drive.
Running from a minimal, fresh install of Feisty.

The problems always seem to occur for me once I've installed the restricted fglrx drivers. If I use the default vesa drivers, its runs perfectly. So I can only assume it's a driver problem, or the graphics card is overheating, or the drivers are relating to the graphics card overheating.

---

### Post by suoko on 2007-05-02
I experience the freeze as well although it's just a question of seconds (sometime a minute)
The system randomly stop responding but after a random time it continues working without any problem.

I have an asus notebook with intel dual core, intel GPU and intel wireless Chipset.

Are intel drivers so buggy??
I have also problems with 3d app when compiz is enabled...

---

### Post by Bealer on 2007-05-02
Ok, I've got mine working and stable!

I've done numerous possible fixes, so not sure which one worked, or if it's a combination of them all. Anyway, I've done:

```

sudo gedit /boot/grub/menu.lst

```

```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d441d241-9fbd-4462-9168-095709ff2619 ro quiet splash **noapic nolapic acpi=off  apm=power_off**
**pci=assign-busses**
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

I added "noapic", "nolapic" "acpi=off" to the boot option for Ubuntu (at the bottom of the file). I also added "apm=power_off" as my machine wouldn't turn off with the latter additions.
And on a separate line "pci=assign busses" (yes two S's)

```

sudo gedit /etc/X11/xorg.conf

```

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	[b]Option      "HorizSync" "30.0 - 93.0"
	Option      "VertRefresh" "56.0 - 85.0"[/b]
EndSection

```

Under the monitor section in my xorg.conf I added the Horizontal and Vertical refresh rates. I've actually had quite big problems with these in Feisty. Upon installing, by default my graphics won't work. With Edgy I just needed to reconfigure the xorg.conf, and remove and resolutions above 1024x768. 

With Feisty however, this wasn't enough. I had to drop the colour depth to 16-bit and also set the refresh rates just to get some form of graphical output. From there I could then install fglrx.


My system is now fine. Running XGL and Beryl too without a single problem. Was very frustrating early on, but now a huge relief to have fixed it.

---

### Post by mishranurag on 2007-05-02
I started having this issue today. I use NVIDIA drivers.  
The system randomly freezes anytime. I cannot even move mouse when it does that.

I am not sure what can I do except updating by going through recovery mode. The system is pretty much unusable right now. I have to come to Windows partition to be able to post this.

Anurag

---

### Post by pbhill on 2007-05-02
I freeze when trying to download through Update Manager. The updates are not completely installed, and I have to reboot. Now I get the error message:

    "E: dpkg was interruped, you must manually run 'dpkg --configure -a' to correct the problem.
     E:_cache->open()failed, please report."

However, when I try to run this in a terminal I get:

    dpkg: error processing caplets-data (--configure).
    Package is in a very bad inconsistent state - you should reinstall it before attempting configuration.
    Errors were encountered while processing.

How do I get the update completed and installed without freezing the machine?

---

### Post by headcronie on 2007-05-02
Didn't notice any of you using Xubuntu Feisty Fawn.  It's happening there as well on my desktop.

I've got a much older system - specs in my sig.  The freezes aren't nearly as frequent, but I've encountered 3 within the past week and a half now.

---

### Post by g02h31l on 2007-05-03
I'm having a problem that seems to be several degrees worse than most of the posts in here.  When I log into Feisty, everything seems to be normal, but upon opening firefox, things go wrong.        The machine freezes, but I still have control of the mouse.  Whats weird is that the system freezes, but the open application doesn't.  Right now I'm using firefox in Ubuntu.  None of the menu buttons work, but I have mouse gestures installed, and for some reason, they work.  I can browse anywhere if I can do it without needing to use the menubar.  I can't move the web browser window or even select an object on my desktop,  Occasionally the computer will snap out of it and I will regain full control.  But after another 30 seconds, it goes right back into the same sort of freeze.  I know that the problem isn't temperature because i have a thermometer in the case which reads 30 C.

System Specs:
Intel Pentium D (64 bit) processor
Gigabyte i-DNA Motherboards with and nVidia chipset
GeForce 6600 Graphics card (nVidia) 
1 GB RAM

---

### Post by dvrraju on 2007-05-03
I too am having random freezes with Fiesty. Here are the details:

0. Fresh install (32bit install)
1. ASUS NV570SLI motherboard.
2. CPU: Athlon X2 4600
3. 2 GB RAM
4. GeForce 8500GT (with latest beta drivers)
5. SATA hard drives (2x seagate 500GB)
6. Pioneer SATA DVD RW drive
7. Qiet & Cool enabled (enabled both S states and C states in BIOS)

I have desktop effects enabled. Freezes happen randomly, and don't seem to be related to any activity. For example, I left the computer running for a while and when I checked back, it is frozen (can move mouse, but that's about it).

I haven't tried any of the suggested fixes in this thread yet. Will report back once I try them out.

Edit: Added motherboard info

---

### Post by greghill on 2007-05-03
I was having the same issue after a clean install of Feisty just last week. After enabling restricted drivers (NVidia-glx) and then Beryl the problems started. Thought it might be a video issue, as there are known bugs when using these drivers with graphics acceleration enabled, so I tried turning off Beryl. No luck - the freezing continued until I uninstalled Beryl *COMPLETELY*. Unfortunately when I did this it also hosed my x-server. Had to boot into terminal and do apt-get install to reinstall nvidia-glx. Once I did this and rebooted I was OK. It's been several days now and the problem seems to have gone away - forever I hope. Beryl is pretty to look at, and a pure joy to use (when it doesn't freeze), but it's not mature enough to use on my system just yet.I've gone back to "plain" old Gnome, and couldn't be happier.

---

### Post by PinkBullets9 on 2007-05-05
This thing keeps happening to me too. It usually happens when I'm on youtube watching a video thats more than 5 minutes or when im playing a game. But the weird thing is it only happens if I have desktop effects from Compiz or Beryl running otherwise the machine runs fine. I thought it was my graphics card which is a winfast geforce 6200 but since everyone seems to having this problem i am guessing its not. I'm a noob to Ubuntu, just started using it around a month ago and don't really no what to do.

---

### Post by KrazyPenguin on 2007-05-05
> **PinkBullets9 said:**
> This thing keeps happening to me too. It usually happens when I'm on youtube watching a video thats more than 5 minutes or when im playing a game. But the weird thing is it only happens if I have desktop effects from Compiz or Beryl running otherwise the machine runs fine. I thought it was my graphics card which is a winfast geforce 6200 but since everyone seems to having this problem i am guessing its not. I'm a noob to Ubuntu, just started using it around a month ago and don't really no what to do.

**Solution: Works on some computers - worth a shot !!!**

Orginally posted here:
[http://ubuntuforums.org/showthread.php?t=424068&page=3&highlight=root%3DUUID%3D70d0a61f-7453-46d4-85ad-1373ef99813a](http://ubuntuforums.org/showthread.php?t=424068&page=3&highlight=root%3DUUID%3D70d0a61f-7453-46d4-85ad-1373ef99813a)

> Did you try turning 3d effects OFF and then editing your /boot/grun/menu.lst file as mentioned in the other posts about this subject. Just add noapic nolapic at the end as mentioned here:
[http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)
Go half way down page and try each of those options one at a time.

Do you get the pci=assign-busses error in /var/log/messages???
(do a search, it is long)

Also see if you can crash it without connecting to the internet.

2 hours with Beryl today and I am still trying to Freeze my system.


Here is my stanza:
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=70d0a61f-7453-46d4-85ad-1373ef99813a ro quiet splash noapic nolapic pci=assign-busses
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Notice the 3 things added to the end of the kernel:
Seems noapic and nolapic are important here for some reason.

Good luck!!!



**Update (05/05/07):** And I have been up for over a week now with no crashes using Beryl.
I've tried to crash it. But with over a dozen things open on my desktop at the same time, the damn thing won't crash anymore !!! :shock:

Hint: Add [COLOR="DarkRed"]**noapic nolapic **[/COLOR] to the end of your kernel boot file.

---

### Post by greghill on 2007-05-05
Hi Krazy Penguin:

Thanks for your post. I have just followed your advice above and am trying it out after a reboot. Will let you know after an hour or two how it's working!

---

### Post by greghill on 2007-05-05
OK- Update time people......and I'm prepared to say that maybe I was a bit hasty when I said that Beryl wasn't mature enough yet for my system. It appears that, thanks to Krazy Penguin's post, I may just have fixed the problem. It's been over an hour now (closer to two) and I haven't had a single freeze-up since adding that line to  the kernel section of the boot.lst file. Boy, this list is the best! Can't wait to give back some of the help I've received from here. Fantastic!

---

### Post by KrazyPenguin on 2007-05-05
> **greghill said:**
> OK- Update time people......and I'm prepared to say that maybe I was a bit hasty when I said that Beryl wasn't mature enough yet for my system. It appears that, thanks to Krazy Penguin's post, I may just have fixed the problem. It's been over an hour now (closer to two) and I haven't had a single freeze-up since adding that line to  the kernel section of the boot.lst file. Boy, this list is the best! Can't wait to give back some of the help I've received from here. Fantastic!

Your welcome greghill !!!

Always a pleasure to help a fellow Canadian Ubuntu User !!!!

;-)

---

### Post by PinkBullets9 on 2007-05-06
Thanks for the tip but noapic nolapic just seems to make it a longer time before my computer freezes up. Should I try the other phrases from that site that you gave Krazy or is noapic nolapic the only one that is supposed to work?

---

### Post by headcronie on 2007-05-06
Here is the best list and summary of the noapic alternatives.  It solved my double clock error, and one of these options will probably solve the freeze problem as well.

[http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)

Best wishes.  :)

---

### Post by coolcalt on 2007-05-06
I'm having the same problem seems to happen once a week at the moment.

I did a fresh install of Fiesty Fawn 64.
I have an NVidea 9600GT 
I have the NVidea drivers installed
I have Beryl installed and working, the decorations randomly disappear on restarts, reloading cntl, alt backspace restores them.

Nothing but a Print Save button push fixes it.  (Power/Reset button)

Next time it happens I'll check the logs and file a bug.

---

### Post by verevi on 2007-05-06
Just to add the the thread:  I've had 6 crashes on my Desktop running Fiesty.  It freezes up completely.  I run Fiesty on my Laptop without any problems. I don't use Compiz/Beryl and everything is pretty much out-of-the-box.  I'm going to try the APIC fix described in this thread.  I really hope it works.  

I've used Linux for about 2 years now and I've *never* had it crash..... which makes this soooo strange.  

Whatever the root cause is, I hope someone gets it resolved because this will not make Linux / Ubuntu look good.

---

### Post by PinkBullets9 on 2007-05-06
Scratch the it takes longer for it to freeze. Whenever I type noapic nolapic into the boot menu it does NOT save and my computer keeps freezing. Am I doing something wrong when trying to boot. After I write in noapic nolapic I press enter to leave the text field and then press "b" to boot ubuntu. When i check the menu.lst after boot the noapic nolapic seems to have disappeared. I am probably doing something wrong since I just started using Ubuntu any help is appreciated.

---

### Post by greghill on 2007-05-06
You must edit the grub menu using a terminal, then "save" your changes, then reboot... in that order.
Evidently you are still having the freeze problem because you have not really "saved" your changes/modifications.
In a terminal....

sudo gedit /boot/grub/menu.lst

Make the changes described in the previous post

THEN ***_SAVE_*** THE FILE. This will close gedit and return you to the  terminal. "Exit" the terminal and reboot. Your changes should now be saved, and will be invoked by the system on restart.

This worked on my particular machine. No guarantee it will work for all, though, but it's worth a shot. My system still seems to be OK a day later.

---

### Post by archiesteel on 2007-05-07
I'm posting this just in case it might help someone...I had similar freeze problems, often with Firefox and OpenGL applications, and I suspected it might have been the nvidia drivers, but even with the nv driver it kep happening...I even reinstalled Edgy because I thought it was a Feisty bug I couldn't put my finger on.

Eventually, it turned out to be a memory slot problem. Moving the memory chips to use other slots solved it...and everything was working perfectly. No freezes. 3D acceleration. The funny thing was that memtest didn't spot the problem, and the BIOS showed the correct amount of RAM (768MB)...but I quickly identified the offending slot (putting only one 512MB chip in that slot resulted in kernel panics!!)

Obviously, for many people here that won't be the problem, but if you're banging your head against the wall trying every solution suggested on the forums, and nothing works, just remember that sometimes you need to check the actual gear.

Good luck to all!

---

### Post by greghill on 2007-05-07
You know, it's really strange... I have been an avid user of Ubuntu since it came out, and have upgraded with each new release, (skipping over  Edgy Eft ) and this is the first issue I have had with Ubuntu that I consider serious. Dapper was by far the most stable system I have ever used. All of a sudden it seems a great many users are having this freezing problem. The common denominator is Feisty. So....... is it the gear? Or is it Feisty? I really think this needs to be fixed quickly. Ubuntu has too good a reputation to have it ruined by this release.

---

### Post by archiesteel on 2007-05-08
> **greghill said:**
> You must edit the grub menu using a terminal, then "save" your changes, then reboot... in that order.
Evidently you are still having the freeze problem because you have not really "saved" your changes/modifications.
In a terminal....

sudo gedit /boot/grub/menu.lst

Make the changes described in the previous post

THEN ***_SAVE_*** THE FILE. This will close gedit and return you to the  terminal. "Exit" the terminal and reboot. Your changes should now be saved, and will be invoked by the system on restart.

Er, not quite. You aslo need to run update-grub once the changes have been made to menu.lst:

sudo /sbin/update-grub

Otherwise the changes are kept in the file, but not written to the actual bootloader. So, to recapitulate: edit file, save, run update-grub, reboot.

---

### Post by verevi on 2007-05-08
Well, it seems to be hardware-related.  I have Fiesty installed identically on two of my PCs.  The laptop NEVER crashes, and th desktop is freezing up ALL OF THE TIME.  

Is it the Soundblaster Audigy card?  Nvidia driver? Twin view display? Those are the only semi-non-standard things I have.  Does everyone else use an Audigy perhaps?

---

### Post by suoko on 2007-05-08
> **verevi said:**
> Well, it seems to be hardware-related.  I have Fiesty installed identically on two of my PCs.  The laptop NEVER crashes, and th desktop is freezing up ALL OF THE TIME.  

Is it the Soundblaster Audigy card?  Nvidia driver? Twin view display? Those are the only semi-non-standard things I have.  Does everyone else use an Audigy perhaps?

I'm experiencing the same thing:
feisty is ok on my pentium 4 desktop (with no wirless nics) while it keeps temporary freezing on my intel dual core notebook with integrated intel wireless nic.

**I bet it's a kernel issue with dual cores or with wireless nics ...**

---

### Post by blaz86 on 2007-05-08
i have neither dual core or wireless and i have freezes :(

---

### Post by devilears on 2007-05-08
mmm, ALSO did an upgrade to feisty and ALSO experiencing "freezes", especially when running FF and/or Synaptic....Mine just stops responding completely & I have to wait untill all disk activity has stopped before trying to do anything else. NOT GOOD!

---

### Post by verevi on 2007-05-08
Same here.  I have AMD. Surely there is something we all have in common to get these freezes.  Not everyone who uses Fiesty is getting them.  



> **blaz86 said:**
> i have neither dual core or wireless and i have freezes :(

---

### Post by sparky64 on 2007-05-08
Been having same problem.
screen locks up (can move mouse but no response), can sometimes use ctrl/alt/back but half the time it kills my x server.
Did memtest which did pick up a couple of faults (8 in 24 hours of to get some new) but for now have gone back to edgy, No probs in last 24 hours.

---

### Post by iopo on 2007-05-08
> **blaz86 said:**
> i have neither dual core or wireless and i have freezes :(

You should try to downgrade to the 386 kernel. Check this for more info:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243)

My computer hasn't froze in three days now!

---

### Post by suoko on 2007-05-08
> **devilears said:**
> mmm, ALSO did an upgrade to feisty and ALSO experiencing "freezes", especially when running FF and/or Synaptic....Mine just stops responding completely & I have to wait untill all disk activity has stopped before trying to do anything else. NOT GOOD!

my freeze could also be related to synaptic and FF.
I have watched a 2 1/2 hours long movie with no freeze at all while it usually occurs twice per hour while using FF and sometimes it occurs while using synaptic.
my thought goes to network then ...

---

### Post by dvrraju on 2007-05-08
With noapic and nolapic options, my Ubuntu box did not freeze for the last 2 days and is still going strong. So that does it for me. Thanks for everyone who helped.

---

### Post by kelvin spratt on 2007-05-08
well lucky my i don't have any problems with fiesty but my wife does with her laptop duel core on xp

---

### Post by ghostofcain on 2007-05-08
acpi=off noacip etc etc all tried with no success, finally bit the bullet and did a frsh install, carrying over my /home partition, and lo it works! just wish I knew what had gone wrong in the first place

---

### Post by bootsbradford on 2007-05-09
> **Bealer said:**
> Ok, I've got mine working and stable!

I've done numerous possible fixes, so not sure which one worked, or if it's a combination of them all. Anyway, I've done:

```

sudo gedit /boot/grub/menu.lst

```

```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d441d241-9fbd-4462-9168-095709ff2619 ro quiet splash **noapic nolapic acpi=off  apm=power_off**
**pci=assign-busses**
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

I added "noapic", "nolapic" "acpi=off" to the boot option for Ubuntu (at the bottom of the file). I also added "apm=power_off" as my machine wouldn't turn off with the latter additions.
And on a separate line "pci=assign busses" (yes two S's)


I am running Feisty and have been experiencing exactly the same problems as others here. Random lock-ups for no particular reason. I was even running Feisty for a few weeks happily before the problems began!!

I have followed the advice above and added it to my menu.lst. Do I just save it, or do I need to do anything like 'sudo update-grub'? Whenever I've done the latter as well, I've gone back to the menu.lst and the added details have disappeared...

P.S. Is there any reason why my kernel is listed as 'Debian GNU/Linux, kernel 2.6.20-15-generic'? (as opposed to 'Ubuntu, kernel 2.6.20-15-generic')

---

### Post by ghostofcain on 2007-05-09
oh dear, sourced my problem and do I feel an idiot! Yes it was the bloody NVIDIA DRIVERS after all, only realised after my clean install was rock stable that the NVIDIA drivers where off, activated them via the restricted drivers menu and lo my system was as stable as Windoze again!

The moral of this story RTFM and make sure the Restricted drivers are deactivated before anything else  

**No the real story is wait and make sure the problem has gone,total up time over the last 24 hours without a freeze was about 18 hours and then back to square one! this morning in five boot attempts approx up time without freezing about 2 minutes **

---

### Post by defishguy on 2007-05-09
Just out of curiosity, what bios manufacturers are represented here?

On the Acer 5100 I'm using Phoenix.

---

### Post by crazedgremlin on 2007-05-09
> **ghostofcain said:**
> oh dear, sourced my problem and do I feel an idiot! Yes it was the bloody NVIDIA DRIVERS after all, only realised after my clean install was rock stable that the NVIDIA drivers where off, activated them via the restricted drivers menu and lo my system was as stable as Windoze again!

The moral of this story RTFM and make sure the Restricted drivers are deactivated before anything else

As stable as windows???

Oh GOD!  What happened?!

---

### Post by chicoicho on 2007-05-10
In my PC Feisty Fawn freezee too , Ubuntu 6.10   - the Edgy Eft  work great. 4 time i install ,reinstall,install Feisty buth freeze randomize when screensaver is aktive,when i firefox runing,when movie work just randomize.The Edgy Elf work   wonderfully.

---

### Post by ghostofcain on 2007-05-10
> **defishguy said:**
> Just out of curiosity, what bios manufacturers are represented here?

On the Acer 5100 I'm using Phoenix. Ami bios here

---

### Post by bootsbradford on 2007-05-10
Sorry to ask again, but if I've done the 'noapic' and 'nolapic' thing, do I need to just save or do 'sudo update-grub' as well? 

Whenever I've done 'sudo update-grub' as well, I go back into my menu.lst and the 'noapic' etc additions have disappeared.

---

### Post by Digitallysick on 2007-05-10
I tried the noapic nolapic it seems i couldnt even boot into ubuntu, who knows maybe i didnt do it right *will try again * but mostly if i keep beryl off, then i have no freezes.

---

### Post by Bealer on 2007-05-10
I got mine running okish.

It still crashes. I posted all the changes I made a few pages back, but it's still not perfect. I've done a fresh install and applied every attempted fix I've seen, but it's never truly stable. I'm sure it revolves around the restricted drivers too, but I have to run them, as my X1900 and 20" monitor can only achieve 1024x768 maximum otherwise.

I've yet been able to notice a pattern, but it mostly occurs when I've just booted up. If I start working on something straight away (like open Firefox, Rhythmbox etc...) it will crash within a few minutes.

If however I leave it for 5-10 mins, then start using it then it doesn't happen. Anyone else get similar?

---

### Post by Adenildo on 2007-05-10
> **se2131 said:**
> I have also been having lots of random freezes after upgrading to Feisty Fawn.

The thing is, this happened to me a month ago as well, when i downloaded the Beta.  I was forced to downgrade to Edgy, and I was hoping that it would be fixed by now.  The Beta was a fresh install, this was an upgrade, so I don't think changing the method of installation would do anything.

From [http://ubuntuforums.org/showthread.php?t=392690](http://ubuntuforums.org/showthread.php?t=392690)

"I have been using Edgy, and yesterday I wiped it out and replaced it with the feisty beta installation. Under Edgy, my computer would freeze every once in a while (about once every day or two), but then I found that if I cooled it down w/ an external fan, then the freezing happened much less frequently. I attributed it to heat problems, and forgot about it.

Now after installing Feisty, it's freezing on me very often (about every hour or two), even with the cooling fan. What's more worrisome is that it seems to happen more or less randomly, I can't duplicate it at will.

So my question is: is there a way I can figure out why my computer freezes, after the fact (a log file or something of some sort)? I've done very little configuring since the installation, so I'm not sure if it's something that I've done. Should I go back to edgy until the feisty release comes out?

Additionally, when it freezes, I can still move the mouse, but I can't go to a virtual terminal, Ctrl-Alt-Backspace or anything. Only way to reboot it is to do a hard shut down or the Alt-PrtSc-S,Alt-PrtSc-U,Alt-PrtSc-B thing (which usually is successful at rebooting)

Btw, I have a Toshiba Satellite A75 computer, with a pentium 4 chip (probably why it's heating up too much)."

My graphics card is an ATI Radeon 9100

Hi,
I also have a Toshiba Satellite A75 and it used to freeze randomly too. I had installed Kubuntu and was about to try Ubuntu when I saw the same problem posted in Ubuntu forums. I gave up and installed Fedora, and the problem didn't happend anymore. But Fedora installs too many softwares I don't use and I was looking for any other distribution and was about to try OpenSUSE. When I looked at the hardware compatibility list I discover that OpenSUSE woul freeze if the option "noapic" wasn't added to kernel boot options for my laptop model.
Well, I tried this with Kubuntu and the problem disappeared. Maybe you should try this. Just add noapic to the kernel as an option in /boot/grub/menu.lst (or something similar - I'm not at home now, but I can verify the correct file name and the correct line to place the option).

---

### Post by mills on 2007-05-10
this is absolute insanity!!!

i thought i'd got rid of this problem but 2-3 days ago had to a reinstall and the boot command that sorted the freezes just doesn't work this time and its even more unstable than b4. ive reinstalled 3 times in the last 3 days with 2 different cd's both were checked for defects, tried 8 different boot commands on each install applications work only when they feel like it including terminal!!! 

i get an hour at the very most the freeze kicks in, i know exactly when its happened because the cursor jumps just prior to the freeze, can sometimes still use firefox to certain degree though which i find completely baffling, the mouse wheel scrolls the page the icons to the left of the url bar are clickable but not the menu options above the url bar, links in the pages are clickable sometimes, but  everything else is just no go like everyone else posting in this thread.

---

### Post by se2131 on 2007-05-10
Adinildo

Thanks for the reply, I've already solved the problem using the noapic option (see posts #20-something).

---

### Post by Digitallysick on 2007-05-10
```
I froze again, sorry for the long post maybe someone can see what might be causing a problem?

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux adam-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 10 22:41:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Logitech MX1000"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2584 card 147b,103e rev 0e class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2585 card 0000,0000 rev 0e class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,2668 card 147b,103e rev 04 class 04,03,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,2658 card 147b,103e rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 147b,103e rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 147b,103e rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 147b,103e rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 147b,103e rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d4 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 8086,2640 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2652 card 8086,2652 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 147b,103e rev 04 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,00c3 card 1682,2177 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 8086,1076 card 147b,103e rev 05 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 104c,8024 card 147b,103e rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:08:0: chip 8086,1065 card 147b,103e rev 04 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV42 [Geforce 6800 XT] rev 162, Mem @ 0xfa000000/24, 0xc0000000/29, 0xfb000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[1] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[2] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[3] -1	0	0xfddc0000 - 0xfdddffff (0x20000) MX[B]
	[4] -1	0	0xfdda0000 - 0xfddbffff (0x20000) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[6] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[7] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B](B)
	[9] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ee00 - 0x0000ee3f (0x40) IX[B]
	[11] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[12] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[13] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[19] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[20] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[21] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[1] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[2] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[3] -1	0	0xfddc0000 - 0xfdddffff (0x20000) MX[B]
	[4] -1	0	0xfdda0000 - 0xfddbffff (0x20000) MX[B]
	[5] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[6] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[7] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B](B)
	[9] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ee00 - 0x0000ee3f (0x40) IX[B]
	[11] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[12] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[13] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[19] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[20] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[21] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[5] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[6] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[7] -1	0	0xfddc0000 - 0xfdddffff (0x20000) MX[B]
	[8] -1	0	0xfdda0000 - 0xfddbffff (0x20000) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[10] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B](B)
	[13] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000ee00 - 0x0000ee3f (0x40) IX[B]
	[17] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[18] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[19] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[25] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[5] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[6] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[7] -1	0	0xfddc0000 - 0xfdddffff (0x20000) MX[B]
	[8] -1	0	0xfdda0000 - 0xfddbffff (0x20000) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[10] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B](B)
	[13] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000ee00 - 0x0000ee3f (0x40) IX[B]
	[17] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[18] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[19] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[25] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[5] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[6] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[7] -1	0	0xfddc0000 - 0xfdddffff (0x20000) MX[B]
	[8] -1	0	0xfdda0000 - 0xfddbffff (0x20000) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[10] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B](B)
	[13] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000ee3f (0x40) IX[B]
	[20] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[28] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[30] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 XT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.41.02.48.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 XT at PCI:1:0:0:
(--) NVIDIA(0):     HSD HW192D (DFP-0)
(--) NVIDIA(0): HSD HW192D (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HW192D (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1440"; removing.
(WW) NVIDIA(0): No valid modes for "1920x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1856x1392"; removing.
(WW) NVIDIA(0): No valid modes for "1792x1344"; removing.
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1400x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1280x960"; removing.
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0):     "1280x768"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1152x768"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[8] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]
	[9] -1	0	0xfddff000 - 0xfddff7ff (0x800) MX[B]
	[10] -1	0	0xfddc0000 - 0xfdddffff (0x20000) MX[B]
	[11] -1	0	0xfdda0000 - 0xfddbffff (0x20000) MX[B]
	[12] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
	[13] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000ee3f (0x40) IX[B]
	[23] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[24] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[25] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[31] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]
	[32] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]
	[33] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1440x900"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Logitech MX1000-isa0060/serio1/input0: Core Pointer
(II) Logitech MX1000-isa0060/serio1/input0: Found 4 relative axes.
(II) Logitech MX1000-isa0060/serio1/input0: Configuring as pointer.
(**) Option "HWHEELRelativeAxisButtons" "7 6"
(**) Logitech MX1000-isa0060/serio1/input0: HWHEELRelativeAxisButtons: 7 6.
(**) Logitech MX1000-isa0060/serio1/input0: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MX1000-isa0060/serio1/input0: Found 8 mouse buttons
(**) Logitech MX1000-isa0060/serio1/input0: Configuring 4 relative axes.
(II) Logitech MX1000-isa0060/serio1/input0: Configured 12 mouse buttons
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Logitech MX1000-isa0060/serio1/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Logitech MX1000-isa0060/serio1/input0: 4 valuators.
(**) ../../src/evdev_btn.c (166): Registering 12 buttons.
(II) Logitech MX1000-isa0060/serio1/input0: Init
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) evdev brain: Rescanning devices (2).
(II) Logitech MX1000-isa0060/serio1/input0: On
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) NVIDIA(0): Setting mode "1024x768_70"
ProcXCloseDevice to close or not ?
```

---

### Post by Bealer on 2007-05-11
As mentioned I tried all the possible solutions I could find. Completely modified my grub menu (with about 4 or 5 additions) and made a few other changes. It would still crash.

I've now reverted back to Edgy. Not a single problem or crash. I can only guess that the bug in Feisty was around the kernel and restricted drivers. 

I'll wait for a fix, or 7.10 to come out.

---

### Post by mills on 2007-05-11
ok, pretty sure iam sorted again and this time iam certain what causes it for me.
found this [link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243") on this thread and [this thread ]("http://ubuntuforums.org/showthread.php?t=416532")on these forums

iam convinced its the rt61 drivers causing alot or at least some of these lockups experienced on this thread which can be solved by installing  **linux-image-2.6.20-15-386**

i vaguely remember installing the 386 image around the last time i solved my freeze problem last time but for some reason i thought it was  the kernel parameter i put in to the boot command as thats what most ppl seemed to be doing

also when i went wireless a couple of weeks later i had to install the rt61 drivers which made my system unstable again so took out wireless and drivers,  (without seeing the link between the rt61 drivers and the freezes :oops: ) ,back to stability again

and recently as can be seen in my  previous post above i had to reinstall, when i did the freezes were back none of the boot parameters did the job, found the threads in the above links, installed the 386 image and back to stability again

---

### Post by chek2fire on 2007-05-11
i have same problem with random freeze.i cant use and the ctrl-alt-backspace.i dont know what happen but it seem to happen very often.

---

### Post by ghostofcain on 2007-05-12
AARRRGGGHHH just as it seems everything is working it all falls apart again.

findings so far.. 
1. it doesn't appear to be restricted drivers , as removing them seems to make no real difference
2. If system is stable for more than 30 minutes it will generally stay up all day
3. no acpi etc changes have no beneficial effect on my system
4. possibly rt61 drivers??

anyway trying the 386 kernel to see if that helps? so far so good but wont give a definitive thumbs up for a couple of days, as sods law it'll soon go belly up

---

### Post by donmiguel on 2007-05-13
**maybe helpful for a bunch of people**

well, i had the problem that my pc freezed when reactivating after the screen saver was active for a few minutes. i followed the hints and deactivated the "network manager" under System/preferences/sessions/startup programs. It was of no use anyway for me..

now, after two checks (letting screen saver do his saving for about 20 minutes each time) the problem was gone! I'm quite positive that this is definiteve :)

btw: i have also nvidia cards and their drivers running... good luck to the rest!!!

---

### Post by bootsbradford on 2007-05-13
> **mills said:**
> ok, pretty sure iam sorted again and this time iam certain what causes it for me.
found this [link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243") on this thread and [this thread ]("http://ubuntuforums.org/showthread.php?t=416532")on these forums

iam convinced its the rt61 drivers causing alot or at least some of these lockups experienced on this thread which can be solved by installing  **linux-image-2.6.20-15-386**

AT LAST!!!

I've tried many of the solutions suggested in this thread but the one that finally seems to have done the trick is this one. Went to synaptic, installed **linux-image-2.6.20-15-386** and we're finally stable again.

Feels good to have my computer back again!! :) Thanks mills for the tip!

---

### Post by jaims on 2007-05-13
hi!

just tried the noapic thing and, it works fine I think!
I've rebooted several times and everything worked fine.

The problem I was having was that one out of every 2 times the boot process got frozen, even in recovery mode. Kernel panik, something not syncing, soft problem with my cpu (amd64 dual core although I installed a 386 kubuntu feisty)

Thanks

---

### Post by joe.turion64x2 on 2007-05-13
I had problems once with my Edgy Eft installation in my laptop, however I found later it was a hard drive issue (I had to replace it later), could that be your case? I don't think all of you have faulty hard drives, mostly because most of you will have desktops (i.e. stable hard drives).

I am sorry to dissapoint you but my machine is the exception to the rule which tried to bound the stability issues with ATI restricted drivers. Right now I am running Ubuntu 7.04 (32 bits) in an AMD Turion 62 X2 box, with ATI Radeon Xpress 1100 graphics card (128MB) which is running with the restricted drivers. Furthermore I followed a how to posted in this forum to enable Beryl and it is running like a charm.

The result: I have a rock solid system until this moment and since I locked the versions of Beryl & related packages, that is not likely to fail anytime soon.

Joe.

---

### Post by DBO on 2007-05-13
The only way I was able to resolve this issue was to revert to the 2.6.17 kernel that came with edgy...  Nothing else mentioned here worked.

---

### Post by mills on 2007-05-14
> **bootsbradford said:**
> AT LAST!!!

I've tried many of the solutions suggested in this thread but the one that finally seems to have done the trick is this one. Went to synaptic, installed **linux-image-2.6.20-15-386** and we're finally stable again.

Feels good to have my computer back again!! :) Thanks mills for the tip!

glad i could help someone :)

---

### Post by iopo on 2007-05-14
Hi guys,
I installed 386 kernel image about 10 days ago. The system is now way more stable than before but still, once every few days, I experience the same kind of random freeze.
So be careful!

---

### Post by Bealer on 2007-05-14
> **mills said:**
> glad i could help someone :)

You absolute legend. 

I'd tried all the other fixes but not managed to get it stable. Just didn't occur to me to switch kernel. I ended up going back to Edgy. I have just reinstalled Feisty with the 386 kernel. So far so good. It's been stable for 6 hours. 

Hopefully this is the solution!

---

### Post by joe.turion64x2 on 2007-05-15
Today I experienced my 'first' unstability issue in Ubuntu 7.04. I don't know what caused it but I am pretty sure it does not like to work without AC power in my laptop. I'll try it tonight.

Joe.

---

### Post by fabertawe on 2007-05-15
I've been getting complete system freeze with Feisty but only for about a week. I've had two today and it's incredibly frustrating. I can find nothing in the logs to give any hint as to the cause and can see no pattern to it. I'm using 2.6.20-15-generic (x86_64) with an AMD64 3000+, Asus K8V-X, 1.5 Gb RAM (3x512, tested!), nVidia 6800 (nvidia-glx 9756). Edgy, despite it's name, was wonderful for me, I don't want to downgrade now though!

Paul

---

### Post by joe.turion64x2 on 2007-05-15
> **fabertawe said:**
> I've been getting complete system freeze with Feisty but only for about a week. I've had two today and it's incredibly frustrating. I can find nothing in the logs to give any hint as to the cause and can see no pattern to it. I'm using 2.6.20-15-generic (x86_64) with an AMD64 3000+, Asus K8V-X, 1.5 Gb RAM (3x512, tested!), nVidia 6800 (nvidia-glx 9756). Edgy, despite it's name, was wonderful for me, I don't want to downgrade now though!

Paul
This is why I don't trust Ubuntu, even though everything seems to be al right. Fedora is gonna prevail in my system.

Joe.

---

### Post by Bealer on 2007-05-15
Switching kernel image (to the 386 version in my case, instead of using the generic one) as mentioned earlier seems to have worked for me. I've yet to have a single freeze. It's not too hard to do.

---

### Post by tgm4883 on 2007-05-15
I have notice a couple things regarding my freezes and would like others input on my thoughts.

System Info:
Gigabyte 965P-DS3 motherboard
Core 2 Duo E6300
1Gb RAM
Geforce 7300GS (3d enabled)

Since this is my primary desktop it rarely gets turned off.  I have noticed that it doesn't freeze often, but when it does it is usually in the first 10 minutes of use.  I am wondering if it is possible that something is loading differently/not loading during boot and that is causing the system freezes.  I ask because I have noticed that my computer will not freeze up, no matter how hard I try to get it to.  But if I reboot, there is a chance that it will freeze.  I reboot again and it either freezes or not.  After I reboot, if I am able to use the computer for more than 10 minutes then it most likely will not freeze up until the next reboot (or perhaps even after that).

This seems to be something to look at and would explain why my earlier post about my experiences was working.

---

### Post by crazedgremlin on 2007-05-15
One little tidbit, I seem to get the most freezes when I'm listening to music in amarok.  When it freezes, a little bit of the music repeats and repeats.

---

### Post by Nordicnurse on 2007-05-15
Hmm, 
so i'm not only getting Feisty freeze. I haven't had the time to troubleshoot this but feisty is giving me a headache on my old desktop. It freezes on screensaver (yes, nvidia...) and freezes while trying to connect to my wireless (ralink rt61). I'll have to see what else it freezes on, but it smells like the restricted drivers are messing this up #-o

---

### Post by joe.turion64x2 on 2007-05-16
> **tgm4883 said:**
> I have notice a couple things regarding my freezes and would like others input on my thoughts.

System Info:
Gigabyte 965P-DS3 motherboard
Core 2 Duo E6300
1Gb RAM
Geforce 7300GS (3d enabled)

Since this is my primary desktop it rarely gets turned off.  I have noticed that it doesn't freeze often, but when it does it is usually in the first 10 minutes of use.  I am wondering if it is possible that something is loading differently/not loading during boot and that is causing the system freezes.  I ask because I have noticed that my computer will not freeze up, no matter how hard I try to get it to.  But if I reboot, there is a chance that it will freeze.  I reboot again and it either freezes or not.  After I reboot, if I am able to use the computer for more than 10 minutes then it most likely will not freeze up until the next reboot (or perhaps even after that).

This seems to be something to look at and would explain why my earlier post about my experiences was working.
Perhaps you have problems with your hard drive. My laptop behaved in a way very similar to your computer and at the end I was forced to replace the hard drive, and after that I ended with a rock solid system.

Joe.

---

### Post by benner on 2007-05-16
i had 2 network cards in my machine.  i was messing about with thin clients.  i was getting freezes all the time.  when i disabled the second one, i rarely had them.  it would still hang on boot sometimes.  then i reinstalled for other reasons.  the freezes came back.  every few minutes.  i disabled the card.  they didn't happen as often.  i removed the card 2 days ago.  haven't had a freeze since then.  the card was a gigabyte something or other.  i can't guarantee that this is the problem.  they have been so unpredictable.  but the network card is my best guess so far.  and earlier in this thread you will see that i tacked on a launchpad bug that mentioned this as a possible problem.  i didn't understand it very well but i (cross my fingers) haven't had a freeze in almost 3 days.

---

### Post by dannyboy79 on 2007-05-16
i have been having these same type of freezes with all different stuff. FF, gogle earth, just copying files from ext3 internal drive to external ntfs drive using drag-n-drop in Nautilus. Everytime the active window will all of a sudden not respond (this is with FF, it will kind of turn a shaded color), I can minimize it but not get it back, when this happens I can sometimes use a terminal but eventually the windows start losing the window decorations (close, minimize, maximize), and my desktop's icons go away sometimes and everything freezes except for the mouse? I have tried to turn off Desktop Effects and I am still having this issue but less frequently. This is with the Nvidia Driver 9755 installed using Envy. 

Specs:
ASRock 775Dual-VSTA
E4300 Core 2 Duo
1.5gb RAM DDR
AGP GeForce 6200 128mb
600 watt Power Supply (Brand New)
1.52TB HDD's (300gb FAT32-ide, 300gb EXT3-ide, 400gb EXT3-sata, 500gb-EXT3-Esata, 20gb EXT3-ide)
HP PVR-350 tv card
3 port Firewire card (not sure of chipset as I haven't ever attempted to hook anything up to it so I can maybe try to remove it but I was hoping that when I get MythTV working that I am going to use that to change my channels instead of IR Blaster because the cable box doesn't have a serial port)

I'll definitely try out some of the suggestions that I have read here and hopefully I can get this resolved, otherwise I love Fiesty! Another weird thing is that right after I try to remove the nvidia driver using Envy and I clean it out, then reinstall it, I can't chose 1280x1024 in the resolution option within System, Admin, I have to chose it thru the Nvidia-Settings dialog box, is this normal? I even restarted and the resolution went back to 1024x768, can anyone comment on this?

---

### Post by tgm4883 on 2007-05-16
> **joe.turion64x2 said:**
> Perhaps you have problems with your hard drive. My laptop behaved in a way very similar to your computer and at the end I was forced to replace the hard drive, and after that I ended with a rock solid system.

Joe.

Nope, had this problem with feisty beta, switched back to edgy.  Thought they would have fixed the problem for release so I switched back.

---

### Post by Visceral Monkey on 2007-05-16
I'm seriously wondering if it's not related to this issue as well.

[http://ubuntuforums.org/showthread.php?t=443799](http://ubuntuforums.org/showthread.php?t=443799)

---

### Post by dannyboy79 on 2007-05-16
> **Visceral Monkey said:**
> I'm seriously wondering if it's not related to this issue as well.

[http://ubuntuforums.org/showthread.php?t=443799](http://ubuntuforums.org/showthread.php?t=443799)

well since I haven't seen anyone in this thread mention anything about a dual head I don't see how it's related unless I missed reading that in any of the posts? i am just guessing that something was changed in xorg. you know they went from 7.0 or was it 7.1 to 7.2 right. There could be a major change in there. did you try to downgrade your xserver version? just a thought. i may try that if all else fails. or try using an older version of the nvidia driver.

---

### Post by vendetta red on 2007-05-16
I too am finding myself in the middle of this mess. I was experiencing freezes after periods of about 5-10 mins of letting my PC idle (using the generic kernel). After reading this thread, I went ahead and downloaded the 386 kernel, uninstalled nvidia-glx-new & updated my xorg.conf, booted into the new kernel and got my nvidia drivers set up again. I am going to let the PC idle for a bit and see what results I get.

Other than the freezes, I am now having trouble with the built-in desktop effects (the title bar disappears when I enable the effects) - I'll scrounge on the forums, should be something related to that, I'm sure.
**EDIT: Resolved the missing title-bar issue, just had to edit my xorg.conf**

My Hardware:

700W OCZ GameXtreme PSU
Asus Crosshair motherboard
AMD 64 X2 4200+
2GB Corsair PC26400 RAM
2x eVGA Nvidia 7950 GT KO (still trying to figure out SLi in ubuntu)
2x 150GB WD Raptor X 10,000 RPM Sata HDD's

---

### Post by crazedgremlin on 2007-05-16
Any luck with that hal update? I just did it a few minutes ago. I think I need to reboot before it takes effect.

---

### Post by vendetta red on 2007-05-16
Changing the kernel to the 386 one seems to have fixed the problem for me, everything has been running smoothly for the last couple of hours.

---

### Post by bootsbradford on 2007-05-17
> **bootsbradford said:**
> AT LAST!!!

I've tried many of the solutions suggested in this thread but the one that finally seems to have done the trick is this one. Went to synaptic, installed **linux-image-2.6.20-15-386** and we're finally stable again.

Feels good to have my computer back again!! :) Thanks mills for the tip!

Seems like I spoke too early... system has definitely been more stable with 386 image, but still I've had 3 lock-ups since the weekend. That's 3 too many.

Ubuntu for me was meant to provide a more stable platform than Windows. Since this freezing has begun, it's been anything but that. In fact, it's made Windows look rock solid!

Sadly, I'm switching back to Windows until this gets sorted. I'm fed up with spending hours trawling the web to find solutions to a problem which seems to be affecting so many people, but to which no permanent fix looks like being released for now.

Edgy worked great for me, even Feisty did at first. I've no idea why the freezes started but until I know for definite, that's my Ubuntu-experience on hold for now!!

---

### Post by dannyboy79 on 2007-05-17
> **vendetta red said:**
> 
**EDIT: Resolved the missing title-bar issue, just had to edit my xorg.conf**
 
whenever you report back and inform people that you fixed it, can you please inform us HOW instead of just saying you fixed it. that way people don't have to send you a PM or ask within the thread etc etc. It's just a good habit to get into and will be very helpful for many to come. Thank you if you can provide us the solution.

---

### Post by kelvin spratt on 2007-05-17
I think a lot of these problems is caused by Beryl crashing and damaging drivers, and using the wrong drivers for beryl and comix i'm lucky as my ati card runs on default drivers from set up. 
but with other distros i get all sorts of problems. Pclinux sets up Ati drivers for the card, touch Beryl instant freeze Compix works ok. so just be aware i fit works don't change things and be carefull with Beryl you need loads of ram to use Beryl,

---

### Post by fabertawe on 2007-05-17
Being unable (and unwilling, I've always used x86_64) to install the 386 kernel I installed the low latency kernel a couple of days ago and have not had another lock up (yet!). I shall report back in another few days [-o<

Paul

---

### Post by cheleb on 2007-05-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi everyone!

I also have the same issues posted in this thread. So far, no suggestion posted here worked for me.
Today i had some time to investigate a bit and managed to get some debug logs. So i opened a new bug in Launchpad to post some info about the crash. If anyone has some more logs or info, please have a look at the bug and post as much info as you can. It's about time to see this bug go down! :)

Cheers,
Ralf

---

### Post by rplantz on 2007-05-18
I sometimes go for days with no problems, then freezes every few minutes. I'm running 64-bit on:

* amd64 3200+ CPU
* abit NF8 motherboard
* nvidia fx5200, 128 MB with 1.0-9755 driver from the repositories.

It got so bad with feisty (that I had been updating through beta to final release), I installed debian etch. Ran fine for a while, then the same freezing problem.

So I replaced edgy with a fresh feisty (release) install. Again, it was fine for a while, then the freezes came back.

I was playing with compiz and beryl on my previous feisty, but not with this fresh install.

Seems like there might be a problem that is common to ubuntu feisty and debian etch.

---

### Post by Vashu on 2007-05-18
I'm thinking hardware issues might be the real problem here. None of the solutions stated before worked for me so i decided to install edgy again completely formatting my disk and doing a fresh install. I've always used ubuntu but since it seemed like a good chance I installed Kubuntu Edgy instead so I could see what the diff. between gnome and kde was. 

Oddly enough kubuntu froze on me too, same symptoms. I'm thinking about maybe installing ubuntu edgy to see if the problem persists.

---

### Post by dannyboy79 on 2007-05-18
> **fabertawe said:**
> Being unable (and unwilling, I've always used x86_64) to install the 386 kernel I installed the low latency kernel a couple of days ago and have not had another lock up (yet!). I shall report back in another few days [-o<

Paul

could you be more specifuc about your kernel choice etc etc? are you using the default 2.6.20.15-generic kernel? are you using the x86 32bit Fiesty or the x86 64bit Fiesty? thanks

---

### Post by fabertawe on 2007-05-18
> **dannyboy79 said:**
> could you be more specifuc about your kernel choice etc etc? are you using the default 2.6.20.15-generic kernel? are you using the x86 32bit Fiesty or the x86 64bit Fiesty? thanks

No problem... I did say I've always used x86_64 ;) In fact I've never even tried the 32bit version! I'm currently using 'linux-image-2.6.20-15-lowlatency' (Feisty 64bit). I was using 'generic'. Still no feezes but I'm not feeling totally confident just yet!

Paul

---

### Post by rplantz on 2007-05-18
> **Vashu said:**
> I'm thinking hardware issues might be the real problem here. 

That's what I thought. The first thing I tried -- several weeks ago -- was to open the case (desktop machine). The CPU heatsink fins were clogged with dust. Cleaning that seemed to fix things -- for just a few days.

Some people in this thread say they have new hardware. And most say they don't have the same problem with Windows. It would be odd if some many people were having hardware problems that coincided with the release of feisty.

It sounds like some sort of interrupt problem to me. Hardware interrupts are unpredictable, hence the random nature of the problem, which makes them extremely difficult to debug. I don't know the internals of how interrupts are handled in ubuntu. About the only clue I have is, as I stated in a previous post, I get the same behavior with my debian etch installation. This implies that there is something that is common to the two releases that isn't quite right.

---

### Post by dannyboy79 on 2007-05-18
before we say that it's interupts, we need to know if these freezes are occuring within xserver only or do these freezes occur on a fiesty machine that doesn't have a gui (gui meaning desktop environment like KDE, Gnome, XFCE or the like running in the xserver) cuase I believe it's a problem with xorg 7.2, I didn't think edgy had 7.2 and that's really the only major change that I can think of but please don't misunderstand me here, I don't know that much about what changed from edgy to fiesty but I know that in Dapper I never had these issues!

---

### Post by nlunpu on 2007-05-18
I am running Fiesty w/ i386-generic kernel on a P3 w/ 256MB RAM.  I have been experiencing the freezes due to what appears to be sudden overloading of ram. As I watch gkrellm while I do just about anything other than use xterm I see my ram go from an idle level of ~30% to ~60% immediately after starting any gui program (ie Firefox, Synaptic, PCManFM) then if I do anyting else such as install something w/ synaptic it jumps to over 80% and often all I have to do is try to close the app at that point and it will freeze solid.  I had no such problems when running Edgy.  I thought you guys might be able to use my observations.
PS Yes, I have a crap system.:)

---

### Post by Talon2 on 2007-05-18
Last year a friend and I built new systems.  They are almost identical.  My system runs rock solid.  Sometimes I don't reboot or shutdown for days or weeks.  On the other hand my firend's system has had periodic lock ups.  Neither of us have had the time to troubleshoot to any degree.

There are 3 basic small differences in the systems:

- Different brand of memory (2x512 ddr in both).  Memory has tested good.

- I use a 1280x1024 res LCD monitor while he uses a 1024x768 res tube monitor.  Doubtful this would cause lockups.

- His system has a ATI 9250 128mb agp video card while mine has a ATI 9600 128 mb agp video card.

We both run Fiesty now but ran Edgy with the same situation...my system is rock solid and his had shown periodic lock ups.

If I had to guess at this point I'd guess there is a problem with the driver for the ATI 9250 (using the open source radeon driver).

Anyone else that runs a ATI 92xx card seeing lock ups?

---

### Post by dannyboy79 on 2007-05-19
nope, I have the Nvidia 6200 128mb AGP card. Using the nvida driver  9755 I get these freeezes but when I try to use Envy unstable to install the beta nvidia driver 100.xx.xx, I get the stupid API mismatch error because the system trys to load the 9755 nvidia kernel module. and YES, I have added nvidia-new to the blacklist and also added "nv" to teh ...........modules-common located within /etc/defaults/. 

Any suggestions?

---

### Post by rplantz on 2007-05-19
Some additional observations.

There are times when I have to shut off the power to the case and wait for a minute or so before I can turn it back on and boot up my system. I get the sense that a driver has placed a hardware component in a bad state.

Yesterday I opened the case and reseated all the cards --- two memory cards and the video card. The system has run well since. On the other hand, I've seen periods of several days that it ran well, then a period of freezes every few minutes.

Perhaps feisty has been given some human characteristics? :)

---

### Post by dannyboy79 on 2007-05-19
well, I just finally got the 100.xx.xx nvidia driver working with psyke83's help. and I am hoping that this and flashing my bios with the latest will hopefully make these freezes go away. I have just used gogleearth for a while, am running FF, ran glxgears and what not and no freeze yet. I am about to transfer some stuff to a ntfs drive cause that has made it freeze as well. i'll keep everyone posted.

---

### Post by FuturePilot on 2007-05-19
I started getting these freezes with Feisty on my laptop. It only seems to happen when I play around with the wallpaper or themes or if I play around with the size of the panels. And I wasn't using any compositing. I'm was using the 9631 Nvidia driver. 

The weird thing is I never had this problem with Dapper while using the same 9631 driver. So I went back to Dapper. Still this is odd because every release since Dapper has done this. What changed? I'm kind of disappointed:(

However Feisty works fine on my desktop PC.

---

### Post by dagrump on 2007-05-20
This issue isn't limited to feisty, it affects edgy too! 
I have been fighting this lock-up issue for some time & have not pinned it down yet, seems wide spread & wide assortment of hardware. I think it's the generic kernel. 
I'm backing stuff up & will try some of the so called obsolete kernels, what can it hurt? This box is pretty limited w/o nvidia drivers. If load I them from the repositories or using envy this box locks up all the time. Firefox open & screensaver tries to load, just push the reset as it's toast.  !0/17/06 edgy alt install disk used i386 kernel, which I most likely changed to i686 smp. I can't pin this issue down as everyone has different hardware so it has to be something software related.
Must be nice to not be hampered by this issue! It sure seems to be being ignored. 
It also seems to effect other disros, so that seems to point to a kernel issue.
But, I'm not the brightest bulb in the box, so what the heck do I know?

---

### Post by crazedgremlin on 2007-05-20
Now that I have updated the hal package, I don't need any of the kernel parameters or any other fixes.  My advice is to do your updates.

---

### Post by suoko on 2007-05-20
> **dagrump said:**
> 
Must be nice to not be hampered by this issue![COLOR="Red"] It sure seems to be being ignored. 
It also seems to effect other disros, so that seems to point to a kernel issue.[/COLOR]
But, I'm not the brightest bulb in the box, so what the heck do I know?

The greatest problem of this  bug is: "do I install feisty on my friend's PC? or I'd better install dapper?" if the pc hangs my friend  could say: "hey, linux is buggy too! and what a bug!"

---

### Post by bristleburger on 2007-05-20
I've also been having trouble with the kernel freezing one one of my machines.

The problematic host is an old SMP machine based on a VP6 motherboard fitted with a pair of PIIIs. I wouldn't be surprised if the VP6 has a rather buggy BIOS, but nevertheless the machine was very reliable when running Dapper Drake.

The freeze isn't quite a hard-lock because whilst it isn't possible to log in using an X terminal or using ssh, it is still possible to ping the frozen host.

I would always find an APIC warning like this in syslog after a freeze:
[INDENT]steve@starbug:~$ cat /var/log/syslog | grep APIC 
May 18 07:51:58 starbug kernel: [  791.519088] APIC error on CPU0: 00(04) [/INDENT]

In my case adding “irqpoll” to the list of kernel boot options fixed this and my machine now seems to be stable.

The kopt line in /boot/grub/menu.lst now looks like this:
[INDENT]# kopt=root=UUID=e7e15e37-c33f-4105-9fbf-0602abbadd2a ro irqpoll[/INDENT]

Hope this helps someone.

---

### Post by dagrump on 2007-05-20
I'm totally lost on this deal, 2 boxes running feisty & don't lock up. Then this one freakin' beast that doesn't want even install feisty (yeah updated w/ update manager turned it into a paperweight).  My laptop has feisty & dapper on it only issue I've noticed is it won't unmount usb drives, & a test box I haven't switched to gutsey or whatever as it seems to be the solidest of the lot.
The stupid box that freezes is the more robust of the group, this is the hardware, maybe some one has some insight to a hardware issue I've overlooked.
abit ab9 mobo
e6600 core 2 duo proc
2 gig of ram (4 512 sticks of ddr2)
geforce 7950 gtoc (512 gddr3)
2 250 gig sata drives
a dvd rom & dvd burner
oh & a sound blaster audigy2 zs
I'd say it works with winblows, but I couldn't tolerate all the jumping thru hoops to get windows set up. Edgy works other than these freeze issues, no desktop effects just running the "nv" drivers, it still locks up every so often, most of the time just takes the screensaver to turn it to a lump. 
Well, I've backed up everything of value, so I guess if it bricks it's not that big of a deal, ain't usb drives great?

---

### Post by Death_Sargent on 2007-05-20
> **Invius said:**
> Might you all be using ati restricted drivers? if so I believe that is the cause, I was rock solid till I enabled those drivers (more specifically, enabled those, then compiz, and later beryl) you all crash with things as simple as screensavers, I am guessing these are opengl related, either way, it is video related, I am currently downloading sabayon to play with it, if anyone is interested, you may wish to read this as it suggests a workaround for ati users.

[http://beranger.org/index.php?article=354](http://beranger.org/index.php?article=354)

awe you had my hopes up but that artical is for AGP users not PCI users which sucks for me

---

### Post by dannyboy79 on 2007-05-20
to make another note, I can ssh into the frozen box as well. I am pretty sure it has something to do with the nvidia binary drivers and or xorg 7.2. i have already stated this once but I have installed both the 9755 and the latest beta 100.xx.xx and they both have the same stupid freezing of very simple progream like gedit or even editing my menu thru system, prefs, or even when I tried to open up the network dialog box. then I can force quit the frozen apps, and still can use FF and terminal for a small amount of time, then nothing but moving the mouse works, can't even do ctrl-alt-f1 but I can still ssh into the box. it's very weird that I can't even go to another tty using ctrl-alt-f1 or even shutdown xserver trying crtl-alt-backspace. I sure hope this doesn't happen with the nv driver as I at least want better graphics than vesa. i didn't think trying to get openGL or Direct rendering would be that hard to get to work with a GeForce 6200 128mb. this is getting insane. I was using the 9755 in Dapper and I had no problems which is why I think it may be related to Xorg 7.2. Hope this gets resolved very soon. 


I am going to be updating my bios today which hopefully will update something do with the AGP port and hopefully will fix this. I can also try other settings in the bios regarding agp but I am no expect so hopefully some1 has a gaurentee fix for tyhis soon with Fiesty. I may also just try ouyt Gutsy as my machine doesn't really have to be working all the time as I still have a winbloz machine around for these exact situations. I most definitely want Ubuntu to work however and would love to NOT have to be ripped off by Billy anymore in the future!!!!! Hell, If I knew I could buy a new graphics card and it would wortk for sure, I might even do that.

UPDATE: this is what happens after I open a simple gedit: [[IMG]http://img511.imageshack.us/img511/7139/geditfrozenle2.th.png[/IMG]](http://img511.imageshack.us/my.php?image=geditfrozenle2.png)

---

### Post by FuturePilot on 2007-05-20
That makes sense that it might be related to Xorg 7.2 but Edgy would do this too. So maybe it's with both 7.2 and 7.1. I've never had this problem with Dapper. Using the 9631 driver. Nvidia had to stick me on the Legacy driver#-o

Or could it be a kernel issue. On Dapper I'm using the i386 kernel. I'm not quite sure what the difference is between the i386 and generic kernels.

Someone else said it's also happening with the nv drivers too.

---

### Post by dagrump on 2007-05-20
It freezes on edgy too, & w/ the "nv" drivers w/ something  as simple as a screensaver. It is not as often as when I was using "nvidia" drivers, it still freezes.

---

### Post by iopo on 2007-05-21
Hi everybody!

because of these random freezes my computer became completely useless. So I decided to try out some other distro. I installed linux mint 3 days ago. It is mostly based on Ubuntu, so I wasn't really hoping to get rid of the freezes and instead I had no problem what so ever anymore!

Since the two systems are 99% identical, it would be useful to figure out what are the differences. For example booting up in "verbose" mode I noticed that the ipv6 module is blacklisted by default.

Can this be the cause? Can anyone suggests some other tests?

---

### Post by FuturePilot on 2007-05-21
OMG Feisty just randomly froze on my desktop. Nothing would respond. But I could still move the mouse around. But the keyboard wouldn't do anything and I couldn't click anything either. I couldn't restart X server or anything. My only option was to do a hard reboot. But after that my BIOS got borked and nothing would boot at all. Not even Windows. That was scary:eek: I thought it was bricked. Had to remove the little battery and put it back. Now I'm back up and running, but this is rather unsettling as if this can happen at any time, well not good if you're in the middle of something.

It's running a Pentium 4 HT @ 3.4GHz
2 GB RAM
Nvidia GeForce 6600

---

### Post by rplantz on 2007-05-21
> **FuturePilot said:**
> Had to remove the little battery and put it back.

I had to do this once. The next time your system freezes, try just turning off the power to the box. Let it set for a couple of minutes or so. Then turn on the power and boot the system. The power off sequence usually works for me.

---

### Post by FuturePilot on 2007-05-21
Oh no!! It just did it again! What is going on here? It worked perfectly since I installed it shortly after it was released. Now all of a sudden it's freezing? I love all the new features in Feisty but I miss the stability of Dapper. Something is going to need to be done here. 
Shuold we make a bug report?

---

### Post by tgm4883 on 2007-05-21
> **FuturePilot said:**
> Oh no!! It just did it again! What is going on here? It worked perfectly since I installed it shortly after it was released. Now all of a sudden it's freezing? I love all the new features in Feisty but I miss the stability of Dapper. Something is going to need to be done here. 
Shuold we make a bug report?

If you have a second computer try to ssh into your frozen box and restart it that way.

---

### Post by FuturePilot on 2007-05-22
> **tgm4883 said:**
> If you have a second computer try to ssh into your frozen box and restart it that way.

Well it's too late now. It totally borked my BIOS and now my computer is a brick and won't boot anything because I can't reflash it since they're all in Windows .exe format. I'm in a huge mess now:cry:

---

### Post by joe.turion64x2 on 2007-05-22
> **FuturePilot said:**
> Well it's too late now. It totally borked my BIOS and now my computer is a brick and won't boot anything because I can't reflash it since they're all in Windows .exe format. I'm in a huge mess now:cry:
Who borked your BIOS? Ubuntu?
Perhaps you can open a motherboard's jumper to reset it. Wouldn't it work?

---

### Post by FuturePilot on 2007-05-22
> **joe.turion64x2 said:**
> Who borked your BIOS? Ubuntu?
Perhaps you can open a motherboard's jumper to reset it. Wouldn't it work?

Maybe it was me. I don't know. I had to do a hard reboot and then it wouldn't boot anything. I tried fooling with the jumper but it didn't do anything.:(

---

### Post by rplantz on 2007-05-22
> **FuturePilot said:**
> Maybe it was me. I don't know. I had to do a hard reboot and then it wouldn't boot anything. I tried fooling with the jumper but it didn't do anything.:(

Do you have the manual for your motherboard? Mine has instructions for resetting the bios. I have to move a jumper to another position and leave it there for some time. Then you move it back. I had to do it once during this mess.

(I'm a little afraid to say this, but my system is behaving right now.)

---

### Post by FuturePilot on 2007-05-22
Yeah I also had to move the jumper over to another position for a few seconds then move it back. It seemed to have done something because I got a screen asking me if I want to keep the default setting or go into the setup, but it still won't boot anything. And all the images have these ugly lines running through them. Windows starts to boot but then gives me a BSOD. Ubuntu will boot fine until it tries to start X. Then I get random colors on the screen and then if just freezes at a blank screen. Same with any live CD too.

---

### Post by krypto_wizard on 2007-05-22
I have the same issue. Toshiba Satellite A70-S249 Laptop...freezing with Feisty.

---

### Post by rplantz on 2007-05-22
> **FuturePilot said:**
> Yeah I also had to move the jumper over to another position for a few seconds then move it back. It seemed to have done something because I got a screen asking me if I want to keep the default setting or go into the setup, but it still won't boot anything. And all the images have these ugly lines running through them. Windows starts to boot but then gives me a BSOD. Ubuntu will boot fine until it tries to start X. Then I get random colors on the screen and then if just freezes at a blank screen. Same with any live CD too.

Have you tried (carefully!) removing all the boards and putting them back in again? Something might be loose or slightly corroded. Sometimes just reseating everything will make a good contact again. As always, if you do this, make sure you are well grounded so you don't zap anything with static electricity.

---

### Post by dannyboy79 on 2007-05-22
if you tried to flash your bios and borked it, then ever trying to reset the bios will not work, all the reseting of the bios by placing a jumper on 2 pins for a certain amount of time does is simply return the currently installed bios back to factory defaults and if you erased the previous bios with whatver bios you tried installing then there's no way that by placing a jumper on 2 pins is going to magically reflash your bios with the original bios that came shipped on the board. if you have any kind of decent motherboard, there are always bios's and dos flash programs on your motherboards website. Yes, there are noramally windows .exe verisons as well but I can almost guarentee that there is a dos version as well. so to do that you simply create a dos boot disk and put the flash program and the new bios on the same dos boot disk and boot to that, and then from the command line, you enter the flashing program's name like FLASH, then you put 1 space and enter the name of the new bios. So for my ASRock mb, my command is, FLASH 715VSTA2.70, and away it goes a flashing. always make sure that your power source is for sure not going to cut out on ya because if you bork a flashing of a bios, your computer is normally then turned into a little chair you can sit on when rotating your tires. You'd have to check on your MB website about the exact verison of the bios you need and what the flash program is that you should use. Also, you can always call the MB company to see what if anything you can about the borked flash attempt. Maybe you can get a new flash rom from them and solder it onto your board instead of throwing it away. Regardless, this is WAY off topic so please start a different thread about bios flashing if you desire to. Thanks and good luck!

---

### Post by Vashu on 2007-05-22
> **dagrump said:**
> This issue isn't limited to feisty, it affects edgy too! 
I have been fighting this lock-up issue for some time & have not pinned it down yet, seems wide spread & wide assortment of hardware. I think it's the generic kernel. 
I'm backing stuff up & will try some of the so called obsolete kernels, what can it hurt? This box is pretty limited w/o nvidia drivers. If load I them from the repositories or using envy this box locks up all the time. Firefox open & screensaver tries to load, just push the reset as it's toast.  !0/17/06 edgy alt install disk used i386 kernel, which I most likely changed to i686 smp. I can't pin this issue down as everyone has different hardware so it has to be something software related.
Must be nice to not be hampered by this issue! It sure seems to be being ignored. 
It also seems to effect other disros, so that seems to point to a kernel issue.
But, I'm not the brightest bulb in the box, so what the heck do I know?

I can vouch for it affecting edgy too. but once I fully upgraded to the latest edgy the issue was solved. I don't know how feisty could have this issue since edgy already seemed to have fixed it. I still get some 2-8 second lock ups once in a while but nothing like it used to be.

---

### Post by dannyboy79 on 2007-05-22
> **Vashu said:**
> I can vouch for it affecting edgy too. but once I fully upgraded to the latest edgy the issue was solved. I don't know feisty could have this issue since edgy already seemed to have fixed it. I still get some 2-8 second lock ups once in a while but nothing like it used to be.
what happens if you add a command to your accessories pull down menu, and the command added is "gksudo gedit", then close the menu editor and go to accessories and click on the newly added command, which is gksudo gedit for modifying files that are owned by root. does it lock up???? Also, when you say the latest edgy, you just mean that you installed the released edgy version and hten performed a update and upgrade over and over until there were no more updates and upgrades correct? well this is just rediculious because I thought since I had a nvidia card, adn semi-decent hardware that this wouldn't happen to me. I mean I have a new Core 2 Duo cpu, an ASRock 775dual-VSTA MB, 1.5gb of value ram, stock Heat Sink Fan, and a brand new 600WAT PSU. I sure wish this wasn't happening to me!!!! I can't even use the nv driver, the vesa driver or the 9755 or 100.xx.xx drivers without these screen lockups. I have to go to a tty, and perform a shutdown -r now. So I can't even use Fiesty basically. The last thing I am about to try is a bios update but I have tried jsut about everything else!!!!!

---

### Post by FuturePilot on 2007-05-22
> **dannyboy79 said:**
> what happens if you add a command to your accessories pull down menu, and the command added is "gksudo gedit", then close the menu editor and go to accessories and click on the newly added command, which is gksudo gedit for modifying files that are owned by root. does it lock up???? Also, when you say the latest edgy, you just mean that you installed the released edgy version and hten performed a update and upgrade over and over until there were no more updates and upgrades correct? well this is just rediculious because I thought since I had a nvidia card, adn semi-decent hardware that this wouldn't happen to me. I mean I have a new Core 2 Duo cpu, an ASRock 775dual-VSTA MB, 1.5gb of value ram, stock Heat Sink Fan, and a brand new 600WAT PSU. I sure wish this wasn't happening to me!!!! I can't even use the nv driver, the vesa driver or the 9755 or 100.xx.xx drivers without these screen lockups. I have to go to a tty, and perform a shutdown -r now. So I can't even use Fiesty basically. The last thing I am about to try is a bios update but I have tried jsut about everything else!!!!!
I can feel your pain. I've got some pretty decent hardware. I can't understand why this is happening. You'd think if it was an issue with Xorg you would at least be able to restart X, but for me everything freezes, even the keyboard so I can't do anything.

---

### Post by Bealer on 2007-05-22
> **dannyboy79 said:**
> what happens if you add a command to your accessories pull down menu, and the command added is "gksudo gedit", then close the menu editor and go to accessories and click on the newly added command, which is gksudo gedit for modifying files that are owned by root. does it lock up???? Also, when you say the latest edgy, you just mean that you installed the released edgy version and hten performed a update and upgrade over and over until there were no more updates and upgrades correct? well this is just rediculious because I thought since I had a nvidia card, adn semi-decent hardware that this wouldn't happen to me. I mean I have a new Core 2 Duo cpu, an ASRock 775dual-VSTA MB, 1.5gb of value ram, stock Heat Sink Fan, and a brand new 600WAT PSU. I sure wish this wasn't happening to me!!!! I can't even use the nv driver, the vesa driver or the 9755 or 100.xx.xx drivers without these screen lockups. I have to go to a tty, and perform a shutdown -r now. So I can't even use Fiesty basically. The last thing I am about to try is a bios update but I have tried jsut about everything else!!!!!

Have you tried switching Linux image as mentioned in the previous posts. I had the exact same problem, switch to the 386 image, and have been fine since.

---

### Post by dannyboy79 on 2007-05-22
really??? wow, that sucks even more than my issue. recently I have been having another weird freeze that I forgot to put in my last post. If i have several windows open, FF, terminal, etc, etc and I want to get to the desktop, normally I can hit the little icon in the lower left corner, well as soon as I hit that, both the upper and lower panels freeze and I can't chose anything in relation to either of them, meaning I can't open ANY of the pull down menus. also, I notice that the graphics of the lower panel, like gets all shitty, hor and vert lines appear like there's some sort of graphics issue with only the panels?. I have tried to add irqpoll, noapic, nolapic, I have tried the -386 kernel versus the -generic kernel. I have played with my AGP settings in the bios, i have played with other settings in the bios (I am not overclocking that's for sure, I just want Ubuntu to work.) I was so happy with Dapper, I never went to Edgy because I was afraid of this exact problem but after reading plenty of threads that Fiesty was more stable than Edgy or what have you, I decided to leave Dapper and come to Fiesty using a fresh install because I wanted to ensure the best outsome. HA HA HA, guesss I was wrong! I am not mad at Ubuntu, don't get me wrong, it's just disappointing as I want Ubuntu to work for everyone. as i said before, 2 things left to try, compile brand spanking streamlined kernel and or bios flash then it's back to Edgy and or Dapper if need be until Gutsy comes out or until they update anything related to xorg as that's what I believe it's related to.

---

### Post by dannyboy79 on 2007-05-22
> **Bealer said:**
> Have you tried switching Linux image as mentioned in the previous posts. I had the exact same problem, switch to the 386 image, and have been fine since.


what hardware? any boot options like noapic or whatever? what nvidia driver??? these things would help. and yes, I did try it as I have stated just as you were asking the question I presume.

---

### Post by dastuma on 2007-05-22
Those of you using the Backport-Repository, could try downgrading this files:

hal to 0.5.8.1-4ubuntu12
hal-device-manager to 0.5.8.1-4ubuntu12
libhal-storage1 to 0.5.8.1-4ubuntu12
libhal1 to 0.5.8.1-4ubuntu12

Since I did this the system didn't freeze.

Daniel

---

### Post by oomingmak on 2007-05-22
I've been having the freezes since early this year when I was using the Feisty beta. I was hoping that the problem would be sorted with the final release of 7.04 but it wasn't. I have done countless clean installs using the release version and I've downloaded all updates, bit the problem remains.

The symptoms my system exhibits are similar to many other people (i.e. completely unresponsive system, mouse can move freely around the screen, but you can't click or type anything on anything).

However, in my case I don't need to reboot to fix it, I just wait for about 2½ and it unfreezes itself and everything works again (meaning no lost work etc). The only problem is that these freezes can occur as much as once every 10 minutes, so the constant waiting for the system to become responsive again gets old very quickly.

Thank goodness I don't have to use Ubuntu for any real work, cos this would drive me insane.

---

### Post by Bealer on 2007-05-23
> **dannyboy79 said:**
> what hardware? any boot options like noapic or whatever? what nvidia driver??? these things would help. and yes, I did try it as I have stated just as you were asking the question I presume.

My spec is back on around page 10 along with all the comments and things I've tried.

Did you try the -386 image from a fresh install (without any of the "noapic" etc... settings)? It's just the linux-image you need to change (or at least from what I got to work). Once you've got it installed then setup the rest of your system and see how it runs.

---

### Post by Necreia on 2007-05-23
I went through and didn't see this posted, but I have a Core 2 Duo and had the same problem.  I see that others here have Core 2 Duo getting the 'random freeze' problem, and below was the fix that worked for me:

[Source]("http://ubuntuforums.org/showthread.php?t=285683&page=8")

> 
Ambrosa

If you want to see how is scaling your cpu, add to panel the "CPU frequency scaling monitor" applet.
An E6600 cpu can have two freq: 1.60 GHz and 2.40 GHz
"ondemand" governor set cpu at lower speed (1.60 GHz). When the system is under heavy load, "ondemand" increases cpu freq (2.40 Ghz) and there is an high probability that the system crash (due to SMP code).

For disabling "ondemand" governor there are 2 mandatory steps:

1)
After installation I've disable (using menù SYSTEM / ADMINISTRATION / SERVICES) "powernowd" service, but this is NOT ENOUGH !
Without powernowd the default scaling_governor is "ondemand" (switch cpu freq. up and down), and this is the problem.
It's better to leave service "powernowd" enabled and then to modify /etc/init.d/powernowd as described in my previous post.

With a text editor open (as root with "sudo") /etc/init.d/powernowd and change "ondemand" woth "performance" (CPU always at max freq).

------------ original ---------------------
use_ondemand() {
for x in /sys/devices/system/cpu/*; do
echo -n ondemand >$x/cpufreq/scaling_governor;
---------------------------------------------

------------- modified ------------------
use_ondemand() {
for x in /sys/devices/system/cpu/*; do
echo -n performance > $x/cpufreq/scaling_governor;
-----------------------------------------------


2)
Gnome-power-manager also sets "ondemand" governor.
Launch a terminal, run "gconf-editor" (as normal user), go in APPS -> GNOME-POWER-MANAGER and change the key "cpufreq_ac_policy" from ondemand to perfomance


The cpu now is always at 2.40 Ghz (max freq.) and system is very stable, without crash.

The only thing I did different, which was a matter of preference, was to uninstall powernowd instead of tweak it (sudo apt-get remove powernowd).

I hope this fixes your problem as it did for me and Ambrosa.

---

### Post by FuturePilot on 2007-05-23
I've been doing some thinking about this, and I'm almost convinced this is an Xserver-xorg issue. When my computer froze and I did a hard reboot, when it came back it did a fsck. When it was done it said it corrected errors on the drive. This must mean that when I shut it down, the system was still reading and writing to the drive. Therefore it was functioning perfectly normal. X had just froze. And the reason it seems that everything else freezes like the keyboard and everything is because when X starts it takes control of all those input devices. And if X freezes so do the input devices. But underneath the base system is still fine.

---

### Post by rplantz on 2007-05-23
> **FuturePilot said:**
> I've been doing some thinking about this, and I'm almost convinced this is an Xserver-xorg issue....Therefore it was functioning perfectly normal. X had just froze....]. But underneath the base system is still fine.

Adding to this, I have noticed that applications running at the time of my hard reboot, e.g., Evolution, Firefox, will recover the session for me.

My system has been running fine since I reseated the two memory cards and the video card several days ago. (Touch wood.) I suspect that there is some code that is running on the ragged edge of the hardware capabilities. It has problems with hardware that is too near the edge of acceptable tolerances. Any very minor glitch in the hardware is not handled correctly by this code.

I once worked on a CT scanner design that had this sort of problem. We ended up sending two start commands to the motor drive board every time to ensure reliability. Missing a sweep in a CT scan is not acceptable.

---

### Post by dannyboy79 on 2007-05-23
well these last few posts are great suggestions. I have one question regardin the cpu scaling or whatever was mentioend about uninstalling powernd or whatnot. I have a E4300, which is the 1.83 or is it 1.80 and I am not sure if it can do what the E6600 which I think is the Extreme. Should I still give this a try???

I am going to reseat everthing on my board as well as try out 1 memory stick, this is getting obsurd that the issue can't be nailed down however I do understand why, it's because there is just so many different systems (hardware and variables) for each person with the freeze. It also be because the kernel is so generic and is suppose to work for so much hardware that it's having trouble with the new Core 2 Duo (not sure on the last note of course)

---

### Post by HoMe_CaNiBaL on 2007-05-23
i there.

i have freezes on my

p4 2.8 HT
p4c800 dlx
aopen 6600gt 128mb agp
audigy 1
1.5gb ram kingston
1 hdd 160gb seagate
1 hdd 120gb seagate

since dapper drake i have freezes, with and without beryl running. system freeze at each 3/4 days...

i dont know what the problem is.

[[]]

---

### Post by cheleb on 2007-05-23
Hey everyone,

i just got an answer from one of the devs in my bugreport on launchpad. He thinks it might have something to do with powernowd. 
For me, on the first start after disabling powernowd, my system immediately came up without a crash and ran stable.
I cant say  for sure that this is the solution, but this is the first time my system ran stable so quick for a long time. Kind of promising.

In case you want to try, here's how:

1) Open /etc/init.d/powernowd with your favourite text editor
2) In the second line, directly under "#! /bin/sh", add "exit 0"
3) Save, close and reboot

Here's the URL of the original bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275)

Good luck!
Ralf

---

### Post by dannyboy79 on 2007-05-23
Ralf, that's WITHOUT the quotes correct? Just like the end of the file? So what we are doing is basically leaving this command still being called upon but what happens when it's called is nothing since the first command is exit, is that the basics of it? ALso, I would like to ask, what are the implications with this? The Ubuntu Developers put powernd within the default Ubuntu Package for a reason so I am only curious as to what this may cause by virtaully disabling it? Also, my question may be answered if you answer the previous one but what is powernd suppose to do? Thanks for any input.

---

### Post by dannyboy79 on 2007-05-23
> **Necreia said:**
> I went through and didn't see this posted, but I have a Core 2 Duo and had the same problem.  I see that others here have Core 2 Duo getting the 'random freeze' problem, and below was the fix that worked for me:

[Source]("http://ubuntuforums.org/showthread.php?t=285683&page=8")



The only thing I did different, which was a matter of preference, was to uninstall powernowd instead of tweak it (sudo apt-get remove powernowd).

I hope this fixes your problem as it did for me and Ambrosa.

you state that you only removed it but what of the persons specific comments that the "default" cpu_scaling feature will still be ondemand? Are you still stable? ALso, you may have already listed your hardware but could you list it again please. I am very very sick of this issue.  I basically can't even use my Fiesty install in gui mode. It takes all of  5 to 10 mins before FF or whatever becomes frozen using both the nv and the nvidia driver. So any more comments would be much appreciated.

---

### Post by grantjohnston on 2007-05-23
Alright, it's good to see that other people are having this issue, and not just me. The way that mine seems to be freezing is after I'll go to bed at night, if I don't turn my monitor off, when I wake up in the morning, the entire thing will be frozen on the screen saver (doesn't seem to matter which one). I've tried using SSH to get into the computer and kill X, but it times out and won't log in. I have to do a hard shutdown, and boot back up. This time it's managed to stay up for 19 hours 56 minutes! There are even times when I will go to bed with the monitor off, come back and it's frozen. This is really starting to get on my nerves. It never did it with Edgy, it was right after the upgrade to Feisty. It's even happened if I go out and run some errands and come back in an hour or two, and the same thing happens. 

Right around the time I upgraded to Feisty, I switched monitors from a Sony HS95/P to an HP w2207. I've made all the changes to Xorg.conf. However, I don't see how a monitor could be affecting lock-ups on this, though.


Hopefully someone will have some insight on this, it's really starting to piss me off.


thanks

-grant

---

### Post by Scotty562 on 2007-05-23
I can't wait till this gets fixed... I've been using XP for the last 3 weeks or so because of it :(.

---

### Post by Cows on 2007-05-23
My feisty use to freeze completely ( even the mouse didn't move ). The problem was solve by me removing my rt61 wireless card from my desktop computer. If you have a laptop with a rt61 chipset consider running it on recovery mode and reinstalling the rt61 drivers.

---

### Post by dagrump on 2007-05-23
Well, I might of botched editing the file, so tried the exit 0 trick & reinstall nvidia drivers. At this point I'll give it a shot, it's not like it's real useful as it stands, I'll report what happens.
good luck all.

---

### Post by rplantz on 2007-05-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/116456](https://bugs.launchpad.net/ubuntu/+bug/116456) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Somebody finally posted a bug report. We should add our experiences to it and hope that it can be fixed soon.

Unfortunately, our experiences remind me of reading "reasons" why the stock market goes up or down. :)

---

### Post by dagrump on 2007-05-23
While I knock on that lump of wood that I call my head, the disabling of powernowd seems to help, & I assure you this thing would have normally locked up since my last post, but so far so good. 
Wow I sure hope I didn't jinx myself.

---

### Post by dannyboy79 on 2007-05-23
i have removed it instead of disabling it and I still have gksudo gedit freeze me. and I am sure this will freeze now any second. it all starts with something very small and then the whole system (meaning X freezes!!!) I can still ssh into it and I can still use tty's. i still haven't flashed bios, waiting till last resort.

Anyone of you who feel that you MAY have solved it please tell me what happens when you issue gksudo gedit from the terminal? PLEASE.

YEP, it only took anther minute and had to tty out. I can see that even though I force quit that gedit it's still there in ps aux. but even if I kill it it still is frozen. I can move the mouse but not interact with anything. I tried going to that bugreport and post the files one of the mods are asking for but FF froze on me, well you know the whole system is froze EXCEPT for mouse movement, tty's are ok and ssh is ok. I am using the 9755 driver.deb that TSELIOT uploaded within another bug for owners of the 8800gt cards and thought it may help. I am not in my windows box adding this but still have the box open and up thru the tty. I am going to reinstall the powernowd package and try to modify it as suggested and try the other fix associated to that after I restart the gui since I have to edit it thru a gui. Hope this gets resolved very soon otherwise I may just try out Linux Mint as some1 said they don't have the problem with that although I do understand everyones hardware is different.

BACk AGAIN and this time with vesa driver and no nvidia loading. no dri or glx in xorg and I am still getting freeze on gksudo gedit so I don't know WTF is going on. I even tried changing the powernowd things as suggested a few posts back. I changed it both in the /etc/init.d/powernowd as well as the gconf-editor app blah blah BUT it still freezes gedit when I open it using gksudo. How am I suppose to be able to edit files that are owned by root? I know I can nano and it'll work I am sure but that's WAY besides the point. I am going to post the requested files now on the bug report.

---

### Post by dagrump on 2007-05-23
As I stated earlier the first fix didn't work for me so I used the exit 0 fix. I may not understand the use of gksudo?, if I try that in a terminal I get some weird error message, but no slow down or freeze. 
I have not had any freezes since disabling powernowd, I open a terminal & sudo gedit /path/to/file to edit or sudo su to move lots of files or change permissions, etc... & exit, enter or reboot. Of course I am not the sharpest knife in the drawer & may do things the hard way.  Of course this issue seems to span alot of different hardware so what fixing one machine may not do another any good, or not change anything.

---

### Post by dagrump on 2007-05-24
Nasty beasty hasn't froze in over 6 hours w/ nvidia drivers, I think it may of fixed this old monster. I did the exit 0 fix earlier in this post. I'll leave it alone but it sure seems to of helped my assorted hardware.

---

### Post by mtwin2 on 2007-05-24
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/5537](https://answers.launchpad.net/ubuntu/+question/5537) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am encountering random freezes as well. At first I thought it might have been firefox or Beryl + XGL (ATI Radeon X1600) but after disabling both and using the default vesa driver the freezes still occur. When I first installed Feisty a few weeks ago the freezes were occurring within an hour of first boot. I added noapic to my grub configuration which made things better (would only freeze every few days), here's my grub config file:

```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=ef8e4547-dcdd-4551-a7f4-fbc0162af1a8 ro quiet splash noapic
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

Here is relevant information from my xorg.conf file:

```
Section "Device"
 Identifier "ATI X1600"
 Driver "fglrx"
 BusID "PCI:1:0:0"
 Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
 Option "Composite" "0"
EndSection

Section "Monitor"
 Identifier "Samsung 941BW"
 Option "DPMS"
 HorizSync 30-100
 VertRefresh 50-160
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "ATI X1600"
 Monitor "Samsung 941BW"
 DefaultDepth 24
 SubSection "Display"
  Depth 1
  Modes "1440x900" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 4
  Modes "1440x900" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1440x900" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 15
  Modes "1440x900" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 16
  Modes "1440x900" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1440x900" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "stylus" "SendCoreEvents"
 InputDevice "cursor" "SendCoreEvents"
 InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
 Mode 0666
EndSection

Section "ServerFlags"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection
```

I also disabled /etc/init.d/powernowd after reading through this forum and haven't encountered a freeze, but sometimes the freezes may take a day or two to occur.

Here is the output from my lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 02)
00:1e.0 ISA bridge: ALi Corporation Unknown device 1575
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8)
00:1f.1 IDE interface: ALi Corporation ULi M5288 SATA (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:11.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:13.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:14.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

Also I just booted feisty without the quiet and splash boot parameters to see if anything was going wrong at boot.  Here are a few things that caught my attention:

```
BUG: Soft lockup detected on CPU #0

/dev/hdb1 mounted 39 times without being checked
```

I never experienced any freezes in Ubuntu Edgy on my system.  Also I did a fresh install of Feisty on this machine on it's own hard drive.

Hopefully I won't encounter any more freezes, but if I do I'll post back.  If what I've done so far doesn't work does any have any other ideas?  If you need any other information about my setup let me know, thanks.

---

### Post by DjBeck on 2007-05-24
> **rplantz said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/116456](https://bugs.launchpad.net/ubuntu/+bug/116456) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Somebody finally posted a bug report. We should add our experiences to it and hope that it can be fixed soon.

Unfortunately, our experiences remind me of reading "reasons" why the stock market goes up or down. :)

I also have this annoying problem, described in that bug report. Suddenly all input devices freezes, and the screen gets white with a lot of horizontal stripes. Only a hard reboot will get the system up and running again. 
I get this like twice or thrice a week, so it's kind of hard to trouble shoot.

Another noticeable thing, is that I also experienced this issue a couple of times in the earlier version Edgy.

---

### Post by dannyboy79 on 2007-05-24
> **dagrump said:**
> As I stated earlier the first fix didn't work for me so I used the exit 0 fix. I may not understand the use of gksudo?, if I try that in a terminal I get some weird error message, but no slow down or freeze. 
I have not had any freezes since disabling powernowd, I open a terminal & sudo gedit /path/to/file to edit or sudo su to move lots of files or change permissions, etc... & exit, enter or reboot. Of course I am not the sharpest knife in the drawer & may do things the hard way.  Of course this issue seems to span alot of different hardware so what fixing one machine may not do another any good, or not change anything.
OK, well i doesn't appear to be the same bug at all then because no matter what, eiher with the powernowd fix or not, exit 0 or not, my sudo and gksudo commands entered from a terminal in which I want a GUI app to open with root privalages is causing that app to freeze at which point akes down X on my machine.

Here's the difference of gksudo and sudo and when to use which. It can have bad results if you don't use gksudo just so you are aware.
[http://ubuntuforums.org/showthread.php?t=287563&highlight=gksudo+versus+sudo](http://ubuntuforums.org/showthread.php?t=287563&highlight=gksudo+versus+sudo)

---

### Post by johanPO on 2007-05-24
I am also having these complete freezes. On my system not even the mouse works. To me it seems to be a network issue. My machine has gone through 6.0.6 and 6.10 and was rock solid. I first did an upgrade, but later a fresh installation of Feisty.

I can see a clear correaltion to network usage. 
First the network sometimes gets dropped, and I have to do sudo ifdown wlan0 followed by sudo ifup wlan0. This was never the case with earlier releases. (I had some problems with WPA, but that I have not even dared to try out yet on Feisty)
Secondly I can provoke a crach by starting any sort of filesharing program. That is guaranteed to crash the system within 30 minutes. The craches also can occure while using firefox. ( I also have a strange effect, and that is when I start the PC, open evolution for emails. It complains that it can not find the servers. I have to click cancel a few times, and then it works. I know the network is up and running, so I don't understand this)

I have tried
-removing IPv6
-using the vesa driver ( I am not at all usign Beryl)
-noapic 
-disabling power stepping 

I also filed a bug [report ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111033")

---

### Post by cheleb on 2007-05-24
> **dannyboy79 said:**
> Ralf, that's WITHOUT the quotes correct? 
Correct!
> Just like the end of the file? So what we are doing is basically leaving this command still being called upon but what happens when it's called is nothing since the first command is exit, is that the basics of it? 
Yup, that's right.
> ALso, I would like to ask, what are the implications with this? The Ubuntu Developers put powernd within the default Ubuntu Package for a reason so I am only curious as to what this may cause by virtaully disabling it? Also, my question may be answered if you answer the previous one but what is powernd suppose to do? 
As far as i know powernowd regulates the speed stepping of the processor. If you have a desktop machine as i do, you basically don't need powernowd.
You should not not pay too much attention on that for now, because it is only a temporary workaround to confirm the bug. I am sure that the devs will take care of the rest.
If you have any other questions about this workaround, you should ask the dev that gave me the tip.
Here's the URL again:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275)

Having said that, on my system the workaround, well, worked! Everything is back in a stable state. :)
I suggest anybody with an similar issue to check it out.

Cheers,
Ralf

---

### Post by dannyboy79 on 2007-05-24
> **cheleb said:**
> Correct!
 
Yup, that's right.
 
As far as i know powernowd regulates the speed stepping of the processor. If you have a desktop machine as i do, you basically don't need powernowd.
You should not not pay too much attention on that for now, because it is only a temporary workaround to confirm the bug. I am sure that the devs will take care of the rest.
If you have any other questions about this workaround, you should ask the dev that gave me the tip.
Here's the URL again:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275)

Having said that, on my system the workaround, well, worked! Everything is back in a stable state. :)
I suggest anybody with an similar issue to check it out.

Cheers,
Ralf
Well as I stated this solution does NOT work for me and I have edited both the powernowd file within /etc/init.d/ as well the gconf-editor. I tried changing it to performace as well as adding the exit 0 to no avail. Can you please tell what happens when you go to a terminal and enter, gksudo gedit? Does gedit open? Is it usable? Can you open a file owned by root and edit it and save it? Can you close gedit it withoiut haveing to force quit? Thank you if you can answer these questions.

---

### Post by bristleburger on 2007-05-24
> **johanPO said:**
> I am also having these complete freezes. On my system not even the mouse works. To me it seems to be a network issue. My machine has gone through 6.0.6 and 6.10 and was rock solid. I first did an upgrade, but later a fresh installation of Feisty.

I can see a clear correaltion to network usage. 
First the network sometimes gets dropped, and I have to do sudo ifdown wlan0 followed by sudo ifup wlan0. This was never the case with earlier releases. (I had some problems with WPA, but that I have not even dared to try out yet on Feisty)
Secondly I can provoke a crach by starting any sort of filesharing program. That is guaranteed to crash the system within 30 minutes. The craches also can occure while using firefox. ( I also have a strange effect, and that is when I start the PC, open evolution for emails. It complains that it can not find the servers. I have to click cancel a few times, and then it works. I know the network is up and running, so I don't understand this)

I have tried
-removing IPv6
-using the vesa driver ( I am not at all usign Beryl)
-noapic 
-disabling power stepping 

I also filed a bug [report ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111033")

JohanPO, if noapic doesn't work, try using irqpoll instead, regards BB

---

### Post by dannyboy79 on 2007-05-24
can PLEASE anyone who thinks they solved the issue PLEASE tell me if their gksudo gedit causes gedit to freeze. Does gedit open? Is it usable? Can you open a file owned by root and edit it and save it? Can you close gedit it withoiut haveing to force quit? PLEASE. People keep posting but not answering this very simply question. It would help me troubleshoot whether or not I have the same bug and if I should submit a different bugreport.

---

### Post by bristleburger on 2007-05-24
> **dannyboy79 said:**
> can PLEASE anyone who thinks they solved the issue PLEASE tell me if their gksudo gedit causes gedit to freeze. Does gedit open? Is it usable? Can you open a file owned by root and edit it and save it? Can you close gedit it withoiut haveing to force quit? PLEASE. People keep posting but not answering this very simply question. It would help me troubleshoot whether or not I have the same bug and if I should submit a different bugreport.

Dannyboy79, happy to report that gksudo gedit works just fine.

BB

---

### Post by johanPO on 2007-05-24
Thanks for the suggestion bristleburger. 
My PC did not want to boot with irqpoll, so that was also not the solution.

---

### Post by dannyboy79 on 2007-05-24
> **bristleburger said:**
> Dannyboy79, happy to report that gksudo gedit works just fine.

BB

hardware? graphics driver version? kernel?

---

### Post by Necreia on 2007-05-25
> **dannyboy79 said:**
> you state that you only removed it but what of the persons specific comments that the "default" cpu_scaling feature will still be ondemand? Are you still stable? ALso, you may have already listed your hardware but could you list it again please. I am very very sick of this issue.  I basically can't even use my Fiesty install in gui mode. It takes all of  5 to 10 mins before FF or whatever becomes frozen using both the nv and the nvidia driver. So any more comments would be much appreciated.

Intel Core 2 Duo E6600 Conroe 2.4GHz LGA 775
DFI INFINITY 975X Socket T
eVGA 512-P2-N573-AR GeForce 7900GTO
pqi TURBO 240-Pin DDR2 SDRAM 667 (4 gig -- 4 x 1 gig chips)

I removed it AND changed the scaling in the gnome control panel thing as well.  I had to do both, but I'm rock-solid stable now.

---

### Post by Bushwack on 2007-05-25
> **dastuma said:**
> Those of you using the Backport-Repository, could try downgrading this files:

hal to 0.5.8.1-4ubuntu12
hal-device-manager to 0.5.8.1-4ubuntu12
libhal-storage1 to 0.5.8.1-4ubuntu12
libhal1 to 0.5.8.1-4ubuntu12

Since I did this the system didn't freeze.

Daniel

This seems to have solved my freezing issues as well.  Thanks for the tip.

---

### Post by bristleburger on 2007-05-25
dannyboy79 ,

Please see the attached extract from "hardinfo" for details of hardware, graphics, kernel etc...

Like johanPO, I found that I mysteriously lost my network connection on a couple of occasions.
I also had numerous kernel freezes, usually after plugging a USB device into the system. After a freeze, I would always find an APIC warning like this in syslog:
[INDENT]steve@starbug:~$ cat /var/log/syslog | grep APIC 
May 18 07:51:58 starbug kernel: [  791.519088] APIC error on CPU0: 00(04) [/INDENT]

In my case adding “irqpoll” to the list of kernel boot options fixed this and my machine now seems to be stable.

If you don't find APIC errors in your syslog then I guess you have a different problem.

Regards

BB

---

### Post by dannyboy79 on 2007-05-25
thanks but I have already tried adding irqpoll. I have also tried noapic and nolapic, heck I even added acpi=off to see if that would do it. I have a post related more towards my situation here if you could maybe provide some troubleshooting tips. I am totally at a loss here and am almost disappointed I came to Fiesty when my Dapper was perfectly stable.
[http://ubuntuforums.org/showthread.php?t=454394](http://ubuntuforums.org/showthread.php?t=454394)

---

### Post by bristleburger on 2007-05-25
> **johanPO said:**
> Thanks for the suggestion bristleburger. 
My PC did not want to boot with irqpoll, so that was also not the solution.

Sorry it didn't work JohanPO,

Maybe it would be worth checking your BIOS settings. I found this "I believe the bios settings for the HDD itself needs to allow 32 bit data transfers. If this is not allowed in the bios, and the kernel tries setting this value on the drive at boot, you get this, and it won't boot. Also, there should be a bios setting for 'Plug And Play OS' 'Yes'. Set that to 'Yes' so the drive settings aren't locked by the bios. Finally, to get rid of buggy ACPI, 'acpi=off' passed to the kernel on boot."

here:
[http://www.debianhelp.org/node/5931](http://www.debianhelp.org/node/5931)

BB

---

### Post by dannyboy79 on 2007-05-25
UPDATE FROM ME.
I am happy to inform everyone that a fresh install of Fiesty (no other hardware changes) has fixed the issue of the frozen commands when using gksu or gksudo which would eventually bring gnome-session and or X-server and or gnome-panel to it's knees. Meaning I could only exit to a tty or ssh into the box to restart it. So it obviously had something to do with something I installed along the way. Apps include pretty much everything in Automatix2, rkhunter, chkrootkit, tripwire, Exim4 and then sendmail, samba as a local master browser, and ssh. I can't think of much else I installed. Obviously the nvidia from the restricted modules manager, then the 100.xx.xx which both had this freeze. Then the freeze even occured in nv and vesa so who knows what the cause of it was I am just glad it's gone and I'll be sure to check it before and after every single I install!!!

There are 2 errors I am getting now that I am not applying any boot options like noapic or nolapic, they are:

[    2.937741] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df85989c), AE_BAD_HEADER
[    2.937854] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df8597fc), AE_BAD_HEADER

We'll see how it goes from here.

---

### Post by bristleburger on 2007-05-26
dannyboy79,

Glad you got it working :-)

I still see APIC errors in the system logs but my system remains stable as long as I boot with irqpoll. I have never seen the ACPI errors that your getting so I'm not sure how serious these are; hopefully you will be OK.

Regards

BB

---

### Post by fabertawe on 2007-05-26
It seems we've all been getting freezes with a diverse range of fixes! Just to update on my own problem, I've not had a single freeze since moving to the low latency kernel.

Paul

---

### Post by johanPO on 2007-05-26
> **bristleburger said:**
> Sorry it didn't work JohanPO,

Maybe it would be worth checking your BIOS settings. I found this "I believe the bios settings for the HDD itself needs to allow 32 bit data transfers. If this is not allowed in the bios, and the kernel tries setting this value on the drive at boot, you get this, and it won't boot. Also, there should be a bios setting for 'Plug And Play OS' 'Yes'. Set that to 'Yes' so the drive settings aren't locked by the bios. Finally, to get rid of buggy ACPI, 'acpi=off' passed to the kernel on boot."

here:
[http://www.debianhelp.org/node/5931](http://www.debianhelp.org/node/5931)

BB

Thanks for the input. I tried with the apci=off and Ubuntu wont start. I checked my BIOS. I have an ASUS P5NSLI MB. I do not find any settings for either the 32 bit transfer (I am using a SATA disk) nor for the Plug and Play OS.  I assume that these are not longer necessary...  I remember seeing those settings in older PCs.

Somehow I am still convinced that this has something to do with the changes that has been done in the (W)LAN configurations/settings. When I tried with the different boot parameters, all of a sudden the network did not come up automatically... I had to do a sudo ifup wlan0 to get it starting... I can not remember having disabled this anywhere.

Looking in the var/log/messages I find the following.
May 26 13:04:51 johans kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
May 26 13:04:51 johans kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override

could this be an issue? Not finding much useful with google..

Just tried the low latency kernel, did not work any better. After the restart I had issues again my WLAN... Trying with 2.6.20-16-generic,  and then we will see how that goes

---

### Post by sparky64 on 2007-05-26
Still having same problem.
this time with 64bit version and have not yet loaded nvidia drivers (basic install and upgrades) when i came back after upgrades finished and tried to open terminal system was locked.
Been running edgy for last couple of weeks with no problems.
Looks like it,s back to edgy until Mr gibbon arrives.

---

### Post by QwUo173Hy on 2007-05-26
> **tgm4883 said:**
> Nope, freezes on mine all the time.  Never had desktop effects enabled

Core 2 Duo E6300
Nvidia GeForce 7300GS
Gigabyte 965P-DS3 Motherboard
Feisty 64-bit Fresh install from release

I also have that Gigabyte DS3 board and GeForce 7600GT graphics card.
Core 2 Duo E6600.
250GB SATA drive X 2
SATA DVD/CD drive
2GB RAM (2 X 1GB)

I have had the freezes with Feisty, but also Edgy. This is a newly built machine. Edgy and Feisty fine on laptop. (Laptop was a fresh install of Edgy, updated and upgraded to Feisty. New machine is Feisty fresh install).

Mandriva also gave me these problems, but not Knoppix 5.1.1.

I got the freezes without desktop effects enabled, but the funny thing is that when I disabled my LAN, everything has been fine since (1 hour).

I'm sorry, I haven't read the entire thread, but maybe the LAN is a factor in this.

For info, my laptop (running fine) specs are

P3 850Mhz Dell Inspiron Laptop
512MB RAM

It seems we all have modern systems. As I've said, the on board lan seems to have helped, but maybe I will get the freeze again. I'm going to try a PCI ethernet card in two weeks and see if that is a workaround.

---

### Post by johanPO on 2007-05-27
I also belive that this has to do with the network. Somehow it does not seem to be very simple though. I can normally crash my PC by running a bit of file sharing. In less then 30 minutes I will have a complete freeze. Yesterday I got tiered of fiddling around, and thought that I should try another distribution. So I downloaded Sabayon over night from an ftp server 3.7 GB, withouth problems. 

I can not say that I understand this, but I guess that there are more connections to handle with some filesharing then with a ftp connection

---

### Post by QwUo173Hy on 2007-05-27
johanPO, can you run any of these file share applications from the command line? If you could boot Ubuntu, kill X from the first terminal and run a file sharing app - you could cut the possible causes in half.

I think mldonkey has a terminal only version. I only have intermittent access to a wire connection.
Anyway, I think it's worth a try.

---

### Post by yannlieb on 2007-05-27
On my side, I have upgraded kernel to 2.6.20-16, but still suffering from freezes. The only thing that keeps freezes away (else, life expectancy is around 10 minutes) is having amaroK playing music (this way, computer can spend a full day without freezing). Last combination of options I've used for kernel was noapic, nolapic and noacpi. Next reboot, I'll also test irqpoll.

Regarding someone who suggested to downgrade hal to 5.8.1, that didn't change anything....

Hope this annoying bug will be resolved soon !

---

### Post by QwUo173Hy on 2007-05-27
Well I bought myself an ethernet card (Belkin E Wired Desktop PCI card) and now I'm networking again with no problems whatsoever. So for me, it was my onboard ethernet with the Marvell controller causing the problem.

I've downloaded nearly 2 hours (download time) worth of updates / software, enabled desktop effects, played music (with exaile) used Epiphany and pretty much pushed things all day long. Initially the problem occurred a few minutes into my session.

One thing that did scare me though was when I was playing a 3D game and pressed F during the game to make it full screen. The computer hung except for mouse for about two minutes. then it responded to a CTRL ALT BACKSPC

Anyway, there seem to be may ways to lock up Feisty. Good luck to everyone finding out their way.

---

### Post by bigdavesr on 2007-05-27
I have had the same problem. It did it on daper drake and now on fiesty fawn. It only happens to me when I am serefing the web. Thought it was firefox so I tired other browsers with the same results One time I got a message when cont. alt. backspace that memory was maxed out. Its like the hard drive is locked up. I dont know the answer. I sure hope someone comes up with it.

---

### Post by Digitallysick on 2007-05-28
must be separate issues, for me, with beryl off, i don't have any freezes at all, with beryl on, i lock up  anywhere between a few min, or hours.

---

### Post by johanPO on 2007-05-28
jaralth, I never got any useful infomration. PC just instantly freezes and there is never any information in consoles or similar. As of today I hope this is history, I have just wiped out Feisty and installed Sabayon. Apart from the usual problems with the wireless settings, it is up and running and seems to be pretty smooth.


> **jarlath said:**
> johanPO, can you run any of these file share applications from the command line? If you could boot Ubuntu, kill X from the first terminal and run a file sharing app - you could cut the possible causes in half.

I think mldonkey has a terminal only version. I only have intermittent access to a wire connection.
Anyway, I think it's worth a try.

---

### Post by HotShot on 2007-05-28
I have the same problem as the most of you. My kernellog says this:

```
May 28 13:48:55 SilverServer kernel: [ 4438.311308] irq 16: nobody cared (try booting with the "irqpoll" option)
May 28 13:48:55 SilverServer kernel: [ 4438.311330]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
May 28 13:48:55 SilverServer kernel: [ 4438.311345]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
May 28 13:48:55 SilverServer kernel: [ 4438.311351]  [<f95cd0fa>] nv_kern_isr+0x2f/0x62 [nvidia]
May 28 13:48:55 SilverServer kernel: [ 4438.311512]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
May 28 13:48:55 SilverServer kernel: [ 4438.311520]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
May 28 13:48:55 SilverServer kernel: [ 4438.311527]  [do_IRQ+64/128] do_IRQ+0x40/0x80
May 28 13:48:55 SilverServer kernel: [ 4438.311534]  [common_interrupt+35/48] common_interrupt+0x23/0x30
May 28 13:48:55 SilverServer kernel: [ 4438.311545]  [mwait_idle_with_hints+70/96] mwait_idle_with_hints+0x46/0x60
May 28 13:48:55 SilverServer kernel: [ 4438.311552]  [cpu_idle+73/208] cpu_idle+0x49/0xd0
May 28 13:48:55 SilverServer kernel: [ 4438.311558]  [start_kernel+869/1056] start_kernel+0x365/0x420
May 28 13:48:55 SilverServer kernel: [ 4438.311564]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
May 28 13:48:55 SilverServer kernel: [ 4438.311574]  =======================
May 28 13:48:55 SilverServer kernel: [ 4438.311576] handlers:
May 28 13:48:55 SilverServer kernel: [ 4438.311578] [<f8881f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
May 28 13:48:55 SilverServer kernel: [ 4438.311595] [<f88f7770>] (ata_interrupt+0x0/0x200 [libata])
May 28 13:48:55 SilverServer kernel: [ 4438.311618] [<f89e8390>] (sky2_intr+0x0/0x40 [sky2])
May 28 13:48:55 SilverServer kernel: [ 4438.311629] [<f95cd0cb>] (nv_kern_isr+0x0/0x62 [nvidia])
May 28 13:48:55 SilverServer kernel: [ 4438.311768] Disabling IRQ #16
May 28 13:49:03 SilverServer kernel: [ 4446.953401] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1b9
May 28 13:49:08 SilverServer kernel: [ 4451.948674] NVRM: Xid (0001:00): 8, Channel 00000002
May 28 13:49:08 SilverServer kernel: [ 4451.949151] NVRM: Xid (0001:00): 30,  L1 -> L0
May 28 13:49:11 SilverServer kernel: [ 4454.948488] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1ba
May 28 13:49:19 SilverServer kernel: [ 4462.940914] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1bb
May 28 13:49:25 SilverServer kernel: [ 4468.968093] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
May 28 13:49:25 SilverServer kernel: [ 4468.968101] ata7.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x0 data 0
May 28 13:49:25 SilverServer kernel: [ 4468.968103]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
May 28 13:49:25 SilverServer kernel: [ 4468.968117] ata7: soft resetting port
May 28 13:49:27 SilverServer kernel: [ 4470.930234] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1bc
May 28 13:49:35 SilverServer kernel: [ 4478.922660] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1bd
May 28 13:49:43 SilverServer kernel: [ 4486.915085] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1be
May 28 13:49:51 SilverServer kernel: [ 4494.907512] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1bf
May 28 13:49:56 SilverServer kernel: [ 4499.423235] ata7.00: qc timeout (cmd 0xef)
May 28 13:49:56 SilverServer kernel: [ 4499.423245] ata7.00: failed to set xfermode (err_mask=0x4)
May 28 13:49:56 SilverServer kernel: [ 4499.423249] ata7: failed to recover some devices, retrying in 5 secs
May 28 13:49:59 SilverServer kernel: [ 4502.899938] NVRM: Xid (0001:00): 16, Head 00000000 Count 0007f1c0
May 28 13:50:01 SilverServer kernel: [ 4504.422485] ata7: soft resetting port

```
This is the part from the freeze to manual reset. If someone needs more information, please ask.

System:
Gigabyte 965P-DS3 motherboard
Core 2 Duo E6300
2Gb RAM
Geforce 7300GT

I will try irqpoll now.

HS

---

### Post by yannlieb on 2007-05-29
I have tested also with irqpoll, which is also unsuccessfull. My boot options are : noapic nolapic noacpi irqpoll, and the system is still freezing. I have also tested in recovery mode, still freezing in less than 10 minutes.

I'm going to install a debug kernel to see if I can get extra-information on why it is crashing. As previously, the only thing that keeps the computer from freezing is to have amaroK play music all day long. Therefore this freezes might have something related to audio or disk access, I don't know....

System :
Athlon XP3000+
Asus A7N8X-X
2x512Mb Kingston RAM
160+250 Maxline III Hard disks
1 pioneer DVD burner
1 7600GS AGP Nvidia Card

---

### Post by QwUo173Hy on 2007-05-29
johanPO, that's a pity.

Has anyone tried disabling hardware from their BIOS? I did this one device at a time and foud that when I disabled my intergrated LAN (Marvell chipset), I was able to boot up and didn't get freezes. So basically, it solved my problem.

Now I have found another trigger for the freeze. When I put a game such as L-breakout or Frozen Bubble into fullscreen - when I exit fullscreen, the computer freezes (except for the mouse).

As I've said, I think there are different categories of freezing going on here, but for this particular situation, I have found a tutorial on how to prevent conflicts between onboard Intel graphics and your AGP graphics card (Nvidia / ATI). [here]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated") it is if anyone is interested.

As far as Amarok is concerned. It does access the internet to update album covers and connectts to Magnatunes or whatever service it uses these days. So it would fall into the same category as a web-browser for this activity. Since people are having trouble with web-browsers, I'd imagine this is the same thing.

Would users of Amarok consider trying Banshee, Exaile! or something non-network to see if that solves the problem?

---

### Post by dannyboy79 on 2007-05-29
I would like to repost to see if I can help anyone. I have posted many times about my freezing issue and as I stated earlier I did solve it and am not entirely sure why other than it must have something to do with software as I didn't chaange anything related to the hardware!!! So, when I was getting the freezes, I had used Automatix2 to install pretty much everything it had, after my reinstall of Feisty I have installed things only from Synaptic, and downloaded Source files (Bittornado) and then the super cool feature from Fiesty when you click on a .avi file that requires another codec (that was awesome, it just downloaded what it needed!!!) Anyway, I would just suggest that if you did use Automatix2 to install anything, I would do a fresh install and then install stuff slowly as you go and see what ends up freezing it IF it doesn't freeze from the get go OR you didn't use Automatix2 to begin with, than I am not sure what to sugget. I don't even have to use any boot options either! I do still have 4 weird errors in dmesg but since I haven't any issues they must not be serious.
The errors are as follows:
[    2.857782] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.C                                               PU1._PDC] (Node df81689c), AE_BAD_HEADER
[    2.857899] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.C                                               PU2._PDC] (Node df8167fc), AE_BAD_HEADER
[    2.857936] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Dev                                               ice is not present [20060707]
[    2.857943] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Dev                                               ice is not present [20060707]

And they DO go away when I issue noapic nolapic BUT I want to continue with NO boot options to see what's up and maybe I can help the kernel developers by providing this info to them in a bugreport.

---

### Post by badman3k on 2007-05-29
I've been experiencing this problem with my other machine (ASUS Z35Fm) and before the recent kernel update, the way I stopped the freezing was by making sure that there was a cd always in the drive.

I've now got the problem that a random length of time after booting the computer just starts freezing, and the logs go crazy with a new entry every 5 seconds. The entries are always:
hdb: status timeout: status=0xd0 { Busy }
ide: failed opcode was: unknown
hdb: drive not ready for command

I read a post about flashing the DVD drive, as I'm using a TSST Corp TS-632D DVD-RW, but am reluctant to do this as it would require formatting and installing windows on the machine, flashing the drive and then adding ubunut as a fresh install.

Does anyone know of a method for solving this problem, with or without flashing the drive, and if it requires flashing the drive, is there a way to do it, without installing windows?

Any help would be appreciated.

Rich

---

### Post by yannlieb on 2007-05-29
> **jarlath said:**
> 
As far as Amarok is concerned. It does access the internet to update album covers and connectts to Magnatunes or whatever service it uses these days. So it would fall into the same category as a web-browser for this activity. Since people are having trouble with web-browsers, I'd imagine this is the same thing.

Would users of Amarok consider trying Banshee, Exaile! or something non-network to see if that solves the problem?

Hi Jarlath,

It is the opposite for me, amaroK is _avoiding_ my computer to freeze. Without amaroK running, I can expect computer to work for 5-10minutes. With amaroK running, I can avoid crashes during more than a day.

That would make me suspect that amaroK is activating things as keeping Pata disks running, having some IRQ beeing activated for the music, some periodic network access or another thing I don't know about, but which keeps those freeze away (complete freezes for me, black screen, no mouse, no keyboard, no magig SysRescue keys).

---

### Post by FuturePilot on 2007-05-29
I'm thinking this might be something in the Linux Restricted Modules. I cannot reproduce these freezes while using the nv driver. It only happens with the Nvidia driver. 9631. That same driver works fine on Dapper, so it's not a bug with the driver.

---

### Post by QwUo173Hy on 2007-05-29
Strange. There are obviously different triggers for the freeze, and everyone on this thread has at least one of these triggers on their systems. There are two ways you can find out what your trigger(s) are (is);

**1) - Hardware**
I would suggest to everyone to try disabling their hardware via the BIOS  first (or else remove it from the machine) These include Audio, LAN, graphics card, extra hard-drives, extra sticks of memory and extra CD / DVD drives. 

Run your machine for a day first. If this runs well then great. We know that the offender is in the group we have disabled or removed, whether it be the device itself or the drivers / software for it.

After this, every day re-enable a piece of hardware again and see if that introduces the problem. The trigger for the freeze is obviously different for everyone and this is how I found out it was network related for me.

**2) User Software**
For software, especially elaborate software like Amarok - try using a lightweight alternative and see what happens. If things look good, start using the offending application and see if the problem comes back. If it does, we just need to find out the difference between the two apps to hone in on the problem. If there is no difference this time, then the offender is most likely a piece of hardware you removed from your system (or the driver that uses it).

This isn't perfect, but it worked for me. I don't know a whole lot about under the hood so this is the next best thing. If none of the above works, then there is an underlying piece of software / hardware that is always running (eg. kernel) that is causing the problem in your case.

It seems everyone here also has an independent graphics card too. I'm going to try blacklisting the onboard intel graphcs chip (as per the link I posted earlier) when I get time and see if it helps.

---

### Post by badman3k on 2007-05-29
@Jarlath: I'm having difficulty disabling the devices via the BIOS; probably because I haven't really got much of a clue when it comes to the BIOS. I've checked my BIOS screens, but there doesn't appear to be a method for disabling the device. Any hints on how to disable them via the BIOS?

---

### Post by tgm4883 on 2007-05-29
> **jarlath said:**
> Strange. There are obviously different triggers for the freeze, and everyone on this thread has at least one of these triggers on their systems. There are two ways you can find out what your trigger(s) are (is);

**1) - Hardware**
I would suggest to everyone to try disabling their hardware via the BIOS  first (or else remove it from the machine) These include Audio, LAN, graphics card, extra hard-drives, extra sticks of memory and extra CD / DVD drives. 

Run your machine for a day first. If this runs well then great. We know that the offender is in the group we have disabled or removed, whether it be the device itself or the drivers / software for it.

After this, every day re-enable a piece of hardware again and see if that introduces the problem. The trigger for the freeze is obviously different for everyone and this is how I found out it was network related for me.

**2) User Software**
For software, especially elaborate software like Amarok - try using a lightweight alternative and see what happens. If things look good, start using the offending application and see if the problem comes back. If it does, we just need to find out the difference between the two apps to hone in on the problem. If there is no difference this time, then the offender is most likely a piece of hardware you removed from your system (or the driver that uses it).

This isn't perfect, but it worked for me. I don't know a whole lot about under the hood so this is the next best thing. If none of the above works, then there is an underlying piece of software / hardware that is always running (eg. kernel) that is causing the problem in your case.

It seems everyone here also has an independent graphics card too. I'm going to try blacklisting the onboard intel graphcs chip (as per the link I posted earlier) when I get time and see if it helps.


Interesting, while it may help some, I don't think it will help my particular case (note edgy works fine so hardware is good)

Running feisty I do get freezes (in the first 5 minutes of booting up).  In which I must hit the reset button on my computer.  If my system doesn't freeze up in the first 5 minutes, then it won't freeze up at all (running for weeks now without a freeze).  But if I reboot again, I run into this same problem that it may freeze in the first 5 minutes.  (does any of that make sense !?!).  My best guess is that something isn't loading right during boot (or out of order?).  How would I go about diagnosing this problem?

---

### Post by QwUo173Hy on 2007-05-29
Hi badman3k,

First of all, since you're not familiar with the BIOS, I would say to make a note of all settings before making changes. I did this by literally taking a photograph of each screen (about 9 in total) - save a lot of writing.

If you have more questions about the BIOS specifically. Post a new thread because this one is getting long enough. I'll keep an eye out for your thread and you'll get more attention in general with a new thread instead of buried 25 pages into one about a different topic ;)

Good luck!

---

### Post by QwUo173Hy on 2007-05-29
> **tgm4883 said:**
> (note edgy works fine so hardware is good)

It's not just about hardware. When certain hardware is connected, kernel modules get loaded at boot time. Drivers get loaded and certain applications become usable. For example, if you remove your wireless card, those modules and drivers won't be loaded, the PCI slot won't be addressed by the system and you won't be running Firefox!

This is about trouble shooting. My network device was actually okay, but the drivers weren't. It was by disabling hardware and re-enabling one at a time that I detected it.

By the way, I'm accepting NO responsibility if something goes wrong. I'm just trying to put down some troubleshooting logic that we could follow to isolate the problem. It's obvious that there is a different cause for everyone so I think for this thread to be relevant, we should do a bit of troubleshooting.

---

### Post by tgm4883 on 2007-05-29
> **jarlath said:**
> It's not just about hardware. When certain hardware is connected, kernel modules get loaded at boot time. Drivers get loaded and certain applications become usable. For example, if you remove your wireless card, those modules and drivers won't be loaded, the PCI slot won't be addressed by the system and you won't be running Firefox!

This is about trouble shooting. My network device was actually okay, but the drivers weren't. It was by disabling hardware and re-enabling one at a time that I detected it.

By the way, I'm accepting NO responsibility if something goes wrong. I'm just trying to put down some troubleshooting logic that we could follow to isolate the problem. It's obvious that there is a different cause for everyone so I think for this thread to be relevant, we should do a bit of troubleshooting.

I agree that it isn't just about hardware, and I am very interested in getting a fix for this.  My problem is that I don't know where my problem is.  I have all my hardware installed and activated in my BIOS and my computer will run fine, but sometimes, just sometimes, it decides to freeze right after booting.  This is what I would like to troubleshoot.  If I hadn't already checked these things (and run a different OS on it) I would think that it was bad hardware.  But since edgy worked fine (still does actually) then I am thinking the problem is elsewhere.  I think that the problem with this thread is that there are different things causing feisty to freeze, which leads to the different remedies to fix the problem (and also leads to mass confusion).

---

### Post by QwUo173Hy on 2007-05-29
Hi tgm4883,

I think we're at cross purposes. We're essentially saying the same thing. We don't know what the problem is - it's obviously either hardware or software.

But as I said before, removing the hardware helps you debug the software (kernel modules / drivers) by not having them running. Just like you, all my hardware is good. And by disabling it, I discovered that the driver was causing the problem.

> I have all my hardware installed and activated in my BIOS and my computer will run fine, but sometimes, just sometimes, it decides to freeze right after booting.  This is what I would like to troubleshoot. 
That's the point I was trying to make.

> I think that the problem with this thread is that there are different things causing feisty to freeze, which leads to the different remedies to fix the problem (and also leads to mass confusion).
That's why I suggest this approach. It's something everyone can do regardless of what is causing their problem. 

Troubleshooting isn't where you know what the problem is and try to fix it. It's where you don't know what the problem is and you build up from scratch again, keeping a watchful eye to see what's triggering the behaviour you want to eliminate.

Whatever route you choose, best of luck. Feisty is an amazing OS and I hope you get to experience it without the glitches!

Regards,
Jarlath

---

### Post by tgm4883 on 2007-05-29
> **jarlath said:**
> Hi tgm4883,
Troubleshooting isn't where you know what the problem is and try to fix it. It's where you don't know what the problem is and you build up from scratch again, keeping a watchful eye to see what's triggering the behaviour you want to eliminate.


Totally agreed.  I don't know what the problem is and would like to find it.  I agree that the method you posted is a great way to find the problem.  My post though is concerning my problem, and I don't think that your method would work.  (as I cannot guarentee that the system will freeze at any given time).  What I am trying to indicate (and not doing a very good job of it) is that I think that there is a difference between two different boot ups.  

For instance, lets say that on one boot up everything boots fine and the system doesn't freeze at all.  However, on the next boot up, something doesn't boot right (ie, NIC gets loaded before the Vid Driver) and that causes the system to hang.  I am looking for a method to perhaps log everything that happens during boot (and the times and order they happen in), that way I can compare two different boots and perhaps see a difference in what is happening.

I believe that your method is valid, but would show a hardware device/software driver that is causing the system to freeze (which would happen on every single boot), while my method would show if there was a difference between the two boots for things such as when things start, what gets loaded when, what is causing it to hang, etc

Perhaps im just talking crazy talk.

---

### Post by dannyboy79 on 2007-05-29
> **badman3k said:**
> I've been experiencing this problem with my other machine (ASUS Z35Fm) and before the recent kernel update, the way I stopped the freezing was by making sure that there was a cd always in the drive.

I've now got the problem that a random length of time after booting the computer just starts freezing, and the logs go crazy with a new entry every 5 seconds. The entries are always:
hdb: status timeout: status=0xd0 { Busy }
ide: failed opcode was: unknown
hdb: drive not ready for command

I read a post about flashing the DVD drive, as I'm using a TSST Corp TS-632D DVD-RW, but am reluctant to do this as it would require formatting and installing windows on the machine, flashing the drive and then adding ubunut as a fresh install.

Does anyone know of a method for solving this problem, with or without flashing the drive, and if it requires flashing the drive, is there a way to do it, without installing windows?

Any help would be appreciated.

Rich
this is a bug in the kernel already documented here: well after 10 minutes I can't find it now I am sorry. I do know it's there and I think it's a confirmed bug., I found it when I was trying to locate why my machine kept freezing when I would try  to use any app which required gksudo in front of it. It turned out that I did a fresh install and HAVEN'T used Automatix2 yet and I don't have the freezing anymore. Hope you figure out what to do.

---

### Post by dannyboy79 on 2007-05-29
> **tgm4883 said:**
> Totally agreed.  I don't know what the problem is and would like to find it.  I agree that the method you posted is a great way to find the problem.  My post though is concerning my problem, and I don't think that your method would work.  (as I cannot guarentee that the system will freeze at any given time).  What I am trying to indicate (and not doing a very good job of it) is that I think that there is a difference between two different boot ups.  

For instance, lets say that on one boot up everything boots fine and the system doesn't freeze at all.  However, on the next boot up, something doesn't boot right (ie, NIC gets loaded before the Vid Driver) and that causes the system to hang.  I am looking for a method to perhaps log everything that happens during boot (and the times and order they happen in), that way I can compare two different boots and perhaps see a difference in what is happening.

I believe that your method is valid, but would show a hardware device/software driver that is causing the system to freeze (which would happen on every single boot), while my method would show if there was a difference between the two boots for things such as when things start, what gets loaded when, what is causing it to hang, etc

Perhaps im just talking crazy talk.
It's pretty much impossible for something to load differently from each time to time because of init. you should research it and you'll see hoow it works. Also, you want a log to show you the major things occuring, it would be dmesg. or look at the /var/log/kern.log I believe it is. I think it'd be a good idea to do what he suggests.

---

### Post by QwUo173Hy on 2007-05-29
tgm4883, I understand you now :) Luckily,  dannyboy79 is right and everything loads up the same at boot.

The only way things might behave differently once you're up and running would be for example a cron job that runs on the hour every hour. If you booted up at 15:45 you wait 15 minutes for that program to do it's stuff whereas if you booted at 16:01, you'd be waiting an hour.

The CPU speed stepper only takes action when it sees that your battery is low for example. These all happen in the background.

Whatever is causing the problem is present at every boot. Just may be dormant until a certain condition is met.

---

### Post by tgm4883 on 2007-05-29
> **jarlath said:**
> tgm4883, I understand you now :) Luckily,  dannyboy79 is right and everything loads up the same at boot.

The only way things might behave differently once you're up and running would be for example a cron job that runs on the hour every hour. If you booted up at 15:45 you wait 15 minutes for that program to do it's stuff whereas if you booted at 16:01, you'd be waiting an hour.

The CPU speed stepper only takes action when it sees that your battery is low for example. These all happen in the background.

Whatever is causing the problem is present at every boot. Just may be dormant until a certain condition is met.

That makes sense, things booting will always happen in the same order.  Thats how it works right?  As long as your telling me that there is not 1 possible way for that to change (perhaps a reboot is different than a cold boot?) then i'll agree with you.  I'll try turning off things in my bios and see if i can recreate the freeze.

I don't really want to talk about external components, but I do notice that on my mythtv box, if I coldboot my STB is at node 1, while if I reboot, it will always be at node 0.  Not sure if that helps to see why im thinking the way I am

---

### Post by dannyboy79 on 2007-05-30
well if you don't want to take my word for it than read up on the boot process and init which manages it. BUT yes, there is no possible way that things can boot differently from each boot UNLESS YOU changed something within /etc/init.d/ or anywhere which affects the boot process.

i haven't hooked my STB to my mythtv box yet so I am unaware of what you mean by node 0 and node 1. maybe you could explain more. Is it hooked up via firewire or ir or serial?

---

### Post by rplantz on 2007-05-30
> **dannyboy79 said:**
> well if you don't want to take my word for it than read up on the boot process and init which manages it. BUT yes, there is no possible way that things can boot differently from each boot UNLESS YOU changed something within /etc/init.d/ or anywhere which affects the boot process.

Where does upstart fit into the picture? See
```

bob@ubuntu:~$ less /usr/share/doc/upstart/README.Debian.gz 

```

I can see that init is pid 1, which is what I expect, and I don't see upstart running. I thought that upstart was intended to replace init. :confused:

---

### Post by tgm4883 on 2007-05-30
> **dannyboy79 said:**
> well if you don't want to take my word for it than read up on the boot process and init which manages it. BUT yes, there is no possible way that things can boot differently from each boot UNLESS YOU changed something within /etc/init.d/ or anywhere which affects the boot process.

i haven't hooked my STB to my mythtv box yet so I am unaware of what you mean by node 0 and node 1. maybe you could explain more. Is it hooked up via firewire or ir or serial?

You can daisychain things together on firewire, and each device is a node, so when you setup your STB on mythtv at node 1, then after a reboot it changes to node 0, then mythtv can't find the STB and thats a problem.  The STB streams the data over the firewire.  no ir or serial needed as it also gets its channel changed over that too.

---

### Post by buba on 2007-05-31
For users who have Gigabyte ga-965p-ds3 motherboard there is a solution to fix the freezing which is triggered by bad driver (sky2) for the marvell on board NIC. You need to use the new driver (sk98lin) as stated in post #9 in this thread:
_[http://ubuntuforums.org/showthread.php?p=2370287#post2370287]("http://ubuntuforums.org/showthread.php?p=2370287#post2370287")_

---

### Post by dannyboy79 on 2007-05-31
SORRY OFF TOPIC, last question regarding mythtv and channel changing of STB.

i have read that you can't record channels that are protected (HBO and I am sure other premium stations) thru the firewire connection though so I will probably have time warner only activate the firewire port for me so that I can use it to change the channels since the STB's don't have a serial port and I have read that IR isn't the easiest to configure expecially if no channel change.conf exits for my STB already? I have read that I just need to ask time warner to activate the firewire port for tivo (no need to confuse then with mythtv) i wil be getting the cable box very soon, it's the SA3250HD or the SA4200HD.
What cable service do you have? What STB do you have? I want to be able to get HBO and other channels that my PVR-350 has not found by it's own tv-tuner.

---

### Post by FuturePilot on 2007-05-31
Hmmm. This is very interesting. The latest version of Linux Mint which is based on Feisty does not freeze on me! What could be different?

---

### Post by tgm4883 on 2007-05-31
> **dannyboy79 said:**
> SORRY OFF TOPIC, last question regarding mythtv and channel changing of STB.

i have read that you can't record channels that are protected (HBO and I am sure other premium stations) thru the firewire connection though so I will probably have time warner only activate the firewire port for me so that I can use it to change the channels since the STB's don't have a serial port and I have read that IR isn't the easiest to configure expecially if no channel change.conf exits for my STB already? I have read that I just need to ask time warner to activate the firewire port for tivo (no need to confuse then with mythtv) i wil be getting the cable box very soon, it's the SA3250HD or the SA4200HD.
What cable service do you have? What STB do you have? I want to be able to get HBO and other channels that my PVR-350 has not found by it's own tv-tuner.

Last post on this topic, if you want to talk about it further then we should start a new thread.  Just let me know via PM.

There are two things that you have to worry about when streaming via firewire.  Those two things are the Copy Control Flag, and the 5c implementation.  Either of those and you aren't recording via firewire.  Those are supposed to be turned on or off by the broadcasting company, but sometimes the cable company turns them on (they are not supposed to, and I believe that it is illegal for them to do so), also, they may be turned on by accident in which a simple call to the cable company may fix the problem.  The firewire port has to be activated by law (if your in the US).  

If you plan on changing the channel via firewire, and going from the STB to the PVR-350 via RG6, then you should set the PVR-350 on channel 3 (or 4).  You will also need an external channel changing setup with mythtv, but im not sure on the setup for that.  You will be able to record anything that is output via the RG6 and it will not have any copy control or 5c implementation.  You won't however, be able to get high definition over RG6, firewire you can.

As for the premium movie channels (HBO, Showtime, etc).  Those follow the same guidelines.  If they have no Copy Control or 5c implemented then you should be able to record them fine over firewire.

One thing that could be a problem though is the signal.  Sometimes the signal from the cable company will throw a hiccup into the situation, and cause the mythtv box to not get any signal from the STB until a reboot (actually I think it is until the firewire is reprimed, but I haven't tested this yet).  Hopefully this will improve as the firewire drivers mature.  This is only a problem when recording via firewire.

I have comcast digital cable and a motorola 6200.  When I first got the service I didn't have either copy control or 5c on any channel.   I haven't checked since.

---

### Post by loathsome on 2007-05-31
> **malegria said:**
> I've been using the ati restricted drivers via the Restricted Drivers Manager, and yes that's when my problems started. Ay caramba!:guitar:
 
I'm also experiencing this bloody freeze!! It happened **right after** I grabbed the «nvidia-glx» drivers-
I've got an nVIDIA GeForce 7900GT card together with an C2D E6600 CPU.
This doesn't happen to my laptop which is running Intel-something + C2D. I'm going to try the «noapic-fix» now and see how it goes.
I'm way too lazy to read thirty pages, so; Are there any "good" solutions out there? Thanks!

---

### Post by loathsome on 2007-05-31
Exactly **what does adding apic** to the kernel boot do?

I'm up and running, and so far I've had zero crashes. Seems like this is working.

---

### Post by loathsome on 2007-05-31
Also, what's really weird is that I had Feisty up and running stable for two days, until I decided to reinstall due to some messing up with system files. I've reinstalled FOUR times today due to this fuc&#312;ing bug, and now going strong for my fifth.

DAMNIT! I had it STABLE FOR TWO DAYS, why does it happen like .. now? I didn't to anything out of the ordinary.

**EDIT**
Ok, it's not the damned drivers - IT JUST FROZE DURING MY **FIFTH** INSTALL.

What the heck should I do?

---

### Post by loathsome on 2007-05-31
Ok, that's IT!

I can't even install ubuntu on my freaking desktop. IT FREEZES INSTANTLY FOR GOD SAKE. I'm going back to Vista, no matter how bad it is!!!!11:(:evil::evil:

Something is VERY VERY wrong, it now freezes when LOADING the LiveCD.

---

### Post by tgm4883 on 2007-05-31
> **buba said:**
> For users who have Gigabyte ga-965p-ds3 motherboard there is a solution to fix the freezing which is triggered by bad driver (sky2) for the marvell on board NIC. You need to use the new driver (sk98lin) as stated in post #9 in this thread:
_[http://ubuntuforums.org/showthread.php?p=2370287#post2370287]("http://ubuntuforums.org/showthread.php?p=2370287#post2370287")_

As much as I would have liked that to work.  It now Freezes every single time I boot the computer, within 10 minutes of starting up.

---

### Post by loathsome on 2007-05-31
I can't even install this fuc&#312;ing ****.

Full specs:
- Asus P5B
- Intel C2D E6600
- NVIDIA GeForce 7900GT
- 2048GB OCZ RAM

ARGH!!!!!!! Me and my gf was going to watch a movie, but no .. this stupid thing had to ruin everything. It worked perfectly two days ago.

I AM SO FREAKING ANNOYED BY THIS I COULD SMASH MY COMPUTER.

...

Btw, I've tried with two different CDs; Both pass that check.

:( :(

---

### Post by dannyboy79 on 2007-05-31
> **loathsome said:**
> I can't even install this fuc&#312;ing ****.

Full specs:
- Asus P5B
- Intel C2D E6600
- NVIDIA GeForce 7900GT
- 2048GB OCZ RAM

ARGH!!!!!!! Me and my gf was going to watch a movie, but no .. this stupid thing had to ruin everything. It worked perfectly two days ago.

I AM SO FREAKING ANNOYED BY THIS I COULD SMASH MY COMPUTER.

...

Btw, I've tried with two different CDs; Both pass that check.

:( :(
OK, you need to stop swearing and settle down!!! If it's freezing, than please hit ctrl-alt-f1 and see ahwat it says if anything. Try to hit enter and it may continue to boot. Have you looked thru the thread at the solutions instead of just posting over and over and swearing??

---

### Post by loathsome on 2007-05-31
> **dannyboy79 said:**
> OK, you need to stop swearing and settle down!!! If it's freezing, than please hit ctrl-alt-f1 and see ahwat it says if anything. Try to hit enter and it may continue to boot. Have you looked thru the thread at the solutions instead of just posting over and over and swearing??

When it freezes it **freezes** - I can't do anything.

Sometimes it freezes when loading the LiveCD, sometimes it freezes in the middle of the installation etc.

I've tried «everything», reset my CMOS, default BIOS settings, three CDs, re-partitioning my HDD EVERYTHING!

You wouldn't understand how extremely annoying this is, just decided to drop Windows totally and RIGHT after I let XP go, this stupid damned thing happens - out of nowhere. It's weird .. really, really weird.

Please help, thanks a lot. I'm very frustrated, as you guys have already noticed:p

:(

---

### Post by loathsome on 2007-05-31
Yes!

I managed to install Feisty using *another* CD. I'm starting to believe that it's the CDs that are bad. Hmmm. We'll see how long this lasts. It havent crashed the past 15 minutes - yet :)

I also think it might be something to do with the updates I get through apt-det update, I don't know. I'll investigate it further.

---

### Post by loathsome on 2007-05-31
Aaaand THERE we go, crashed like 10 mins after I booted up. YES! Way to go.
My entire day is now wasted, ruined by this unstable system.

Bye bye, Linux and Ubuntu - XP, here I come.



._.

---

### Post by tgm4883 on 2007-05-31
> **loathsome said:**
> Aaaand THERE we go, crashed like 10 mins after I booted up. YES! Way to go.
My entire day is now wasted, ruined by this unstable system.

Bye bye, Linux and Ubuntu - XP, here I come.



._.

Bye

---

### Post by dannyboy79 on 2007-05-31
> **loathsome said:**
> Aaaand THERE we go, crashed like 10 mins after I booted up. YES! Way to go.
My entire day is now wasted, ruined by this unstable system.

Bye bye, Linux and Ubuntu - XP, here I come.



._.

if you haven't tried any of the solutions than goodbye.
(PS, do you have a marvel ethernet chip on your motherboard? oh, well, that's fixable as well as all the other freezing but goodbye)

---

### Post by tgm4883 on 2007-05-31
> **dannyboy79 said:**
> if you haven't tried any of the solutions than goodbye.
(PS, do you have a marvel ethernet chip on your motherboard? oh, well, that's fixable as well as all the other freezing but goodbye)

My gues is that he hasn't

> **loathsome said:**
> I'm also experiencing this bloody freeze!! It happened **right after** I grabbed the «nvidia-glx» drivers-
I've got an nVIDIA GeForce 7900GT card together with an C2D E6600 CPU.
This doesn't happen to my laptop which is running Intel-something + C2D. I'm going to try the «noapic-fix» now and see how it goes.
**I'm way too lazy to read thirty pages, so; Are there any "good" solutions out there? **Thanks!

Yea there are so many good solutions that we have fixed all the problems.  We are just here now complaining about fake problems in order to increase this thread's posts in hope of it getting more attention.  Attention that it deserves seeing as we have fixed all the problems.  In fact, we fixed it back on page one, and are now bug bashing Windows now, almost got that licked too.

---

### Post by loathsome on 2007-05-31
FYI I read the whole thread, and not one solution actually works.
As I said, this problem is very weird and extremely annoying - my computer is supposed to *work*, and I am not going to use hours after hours trying to fix it.
I am keeping Ubuntu on my laptop, though - it works flawlessly there.

*edited;*
Actually I am going to give Ubuntu one more chance - I'm downloading a fresh image, will burn it at the slowest speed possible, delete my partition, reinstall and then again try to apply the fixes. I really like Ubuntu, but if it's going to crash every 10 minutes, I can't keep it - and I'm sure everybody understands that.

Yeah, I might have gone a bit too enthusiastic about my problems later, sorry about that. I just haven't been this annoyed since my Windows 95 days. And the whole thing that me and my girlfriend couldn't watch that stupid movie just made things worse.

Best,
loathsome

---

### Post by tgm4883 on 2007-05-31
I hope your trying perhaps edgy or dapper.  Cause if your try Feisty again I can only draw that you have no faith in your burning skills, or you buy seriously crap cd's

---

### Post by loathsome on 2007-05-31
> **tgm4883 said:**
> I hope your trying perhaps edgy or dapper.  Cause if your try Feisty again I can only draw that you have no faith in your burning skills, or you buy seriously crap cd's

Haha, I've tried with multiple CDs - only through Nero though - I'll burn them with k3b or something this time.

As for the Edgy/Dapper thing; I don't feel like using an old and 'unsupported' version - plus I really enjoy Feisty's features.

My desktop has btw been up and running for about 1½ hours now. I just watched two King of Queens episodes, and left it idle. It still hasn't crashed .. I'll leave it on for the night (3:30 in the morning here in Norway), and check if it's still alive in the morning.

I have a lot to try tomorrow - I really hope I'll solve this out!

---

### Post by tgm4883 on 2007-05-31
> **loathsome said:**
> Haha, I've tried with multiple CDs - only through Nero though - I'll burn them with k3b or something this time.

As for the Edgy/Dapper thing; I don't feel like using an old and 'unsupported' version - plus I really enjoy Feisty's features.

My desktop has btw been up and running for about 1½ hours now. I just watched two King of Queens episodes, and left it idle. It still hasn't crashed .. I'll leave it on for the night (3:30 in the morning here in Norway), and check if it's still alive in the morning.

I have a lot to try tomorrow - I really hope I'll solve this out!

Unsupported, ha thats funny.  I didn't think i recommend hoary.  Seems like someone that loves the features of feisty, would love the features of edgy or dapper if it didn't freeze on them all the time.  Sounds like someone doesn't know how to install codecs

---

### Post by jimcooncat on 2007-06-01
I've been lurking this thread for a while.  My Feisty has been freezing only once in a while, compared to every ten minutes. And it seems that people reporting problems in this thread are in one of two different camps. 

I'm using the proprietary Nvidia driver. My crashes seem to happen using Firefox with either Ajax laden web pages or YouTube videos. I don't have enough swap. a situation I'll fix this weekend; but don't seem to fill up my 512 memory often. I tried "Desktop Effects" for a few minutes then disabled it. I haven't had a crash in two days after running "sudo nvidia-xconfig --no-composite", but I haven't pushed it too hard either since then. I've been running computers since 1986 and still can't figure out problems from looking at log files. :(

---

### Post by Pulle on 2007-06-01
Hi,

i've also had the problems with random lockups, but I found a solution for me and maybe it's worth trying it out for you too. 

I have a prism54 based wlan-card. Ubuntu uses the p54 drivers based on the new wireless stack and I think they are the reason for the lockups. So if you also have network devices with drivers based on the new stack, try using ndiswrapper with the windows drivers for your card.

Using the p54 drivers I had at least one lockup a day and playing ut2004 over internet crashed the computer reliably after a maximum of 5 minutes. I'm now using ndiswrapper for 3 days and haven't had a single crash. Even playing ut2004 is possible without problems.

---

### Post by loathsome on 2007-06-01
Ok, I THINK I have solved the problem now - Too early to say really.

I have a n RT61 chipset, and got recommended to install 'linux-image-386' for some reason - anybody knows why? 
I also added theese flags: **noapic nolapic pci=asign-busses** to the kernel boot.

I'm starting to get some hope back :D

Thanks.

---

### Post by QwUo173Hy on 2007-06-01
I had problems with my PCI wireless card too. To save hassle, I ordered one of [these]("http://www.elara.ie/products/detailsfull.asp?productcode=ECE1145047").

You connect it to your wired ethernet socket and let it do the wireless work. Doesn't need any drivers and my system is running great. Not really a solution for laptops but I'm on a desktop so I'm very happy with this. 

For those of you outside of Ireland, here's an [amazon link]("http://www.amazon.com/Technology-AirStation-Wireless-Converter-WLI-TX4-G54HP/dp/B000BNDEZY")

---

### Post by loathsome on 2007-06-01
> **jarlath said:**
> I had problems with my PCI wireless card too. To save hassle, I ordered one of [these]("http://www.elara.ie/products/detailsfull.asp?productcode=ECE1145047").

You connect it to your wired ethernet socket and let it do the wireless work. Doesn't need any drivers and my system is running great. Not really a solution for laptops but I'm on a desktop so I'm very happy with this. 

For those of you outside of Ireland, here's an [amazon link]("http://www.amazon.com/Technology-AirStation-Wireless-Converter-WLI-TX4-G54HP/dp/B000BNDEZY")
Hi,

I might consider another wifi card, because I'm sure my freezes are related to the **RT61** chipset. I'm going to try the following first: > Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. and hope that works. I'm currently reinstalling with my wifi card unplugged :lolflag:

---

### Post by soundray on 2007-06-01
I put feisty on a laptop with a rt61 mini PCI module. I got it to work by compiling the legacy CVS version of the serialmonkey driver ([http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz) from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)). I also had to disable roaming, NetworkManager and nm-applet, because they appear to be incompatible with the driver.

---

### Post by loathsome on 2007-06-01
I've just finished my fresh installation (alternate), and the first thing I did was blacklisting the «rt61pci» module. By my dearest God it looks like this is working. I haven't had a freeze yet - I'll try to put load on my system soon, just got to update my repositories etc first.


Please, don't ever freeze on me again [-o<

(lol, my box name is now **Freezey-Fawn**)

---

### Post by loathsome on 2007-06-01
.. and back to the crash we go.

---

### Post by Pulle on 2007-06-01
Hm,

maybe it helps if you blacklist the following modules too (if they are used for your setup):

rc80211_simple
mac80211
cfg80211

---

### Post by dannyboy79 on 2007-06-01
> **loathsome said:**
> .. and back to the crash we go.

post the output from
lsmod
so we can see the modules that are being loaded. Also, since you blacklisted the rt61pc driver, how in the world are you using your wireless card? DId you compile your own using the serialmonkey source? Can we see teh output from
dmesg
as well as 
lspci
then we can maybe help you.

---

### Post by loathsome on 2007-06-01
> **dannyboy79 said:**
> post the output from
lsmod
so we can see the modules that are being loaded. Also, since you blacklisted the rt61pc driver, how in the world are you using your wireless card? DId you compile your own using the serialmonkey source? Can we see teh output from
dmesg
as well as 
lspci
then we can maybe help you.

There was another driver, «rt61», and not «rt61pci». But whatever, that didn't help.

What DOES work, is using the 386 kernel. Should I just use that? I've been up and running forever with that, not a single crash. My PC seems a bit slower with it, though.

I'll post the output later. Thanks a lot for trying to help, really appreciate it :)

---

### Post by dannyboy79 on 2007-06-01
> **loathsome said:**
> There was another driver, «rt61», and not «rt61pci». But whatever, that didn't help.

What DOES work, is using the 386 kernel. Should I just use that? I've been up and running forever with that, not a single crash. My PC seems a bit slower with it, though.

I'll post the output later. Thanks a lot for trying to help, really appreciate it :)

your PC will be slightly slower as it's not taking advantage of SMP which is multithreading and multicore processing that the CPU does. So if you have a Dual Core, Core 2 Duo, a Hyperthreading or similar machine you want to use the -generic kernel as that has the SMP support built into the kernel (Simultanious Multiple Processing) I think that's what it means but don't quote me on that. Also, we I can't help you if you don't answer my questions.
What wireless driver are you using for your wireless card? If you're not using it then take it out of your computer. 
If you do want to use it, than follow this guide ([http://ubuntuforums.org/showthread.php?t=400236)for](http://ubuntuforums.org/showthread.php?t=400236)for) compiling your own serialmonkey drivers ([http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads))  be sure to blacklist all the modules that ubuntu provides by default relating to this chipset.

---

### Post by loathsome on 2007-06-01
Here's the output (running the graphical LiveCD)

---

### Post by loathsome on 2007-06-01
> **dannyboy79 said:**
> your PC will be slightly slower as it's not taking advantage of SMP which is multithreading and multicore processing that the CPU does. So if you have a Dual Core, Core 2 Duo, a Hyperthreading or similar machine you want to use the -generic kernel as that has the SMP support built into the kernel (Simultanious Multiple Processing) I think that's what it means but don't quote me on that. Also, we I can't help you if you don't answer my questions.
What wireless driver are you using for your wireless card? If you're not using it then take it out of your computer. 
If you do want to use it, than follow this guide ([http://ubuntuforums.org/showthread.php?t=400236)for](http://ubuntuforums.org/showthread.php?t=400236)for) compiling your own serialmonkey drivers ([http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads))  be sure to blacklist all the modules that ubuntu provides by default relating to this chipset.

I'm using the ones that ships with Feisty. Yes, I do use the card - it's essential to me. I'll try the serialmonkey drivers - but as far as I can see that guide wants me to download the 386 kernel. Hmm.

Thanks a lot **dannyboy79**!

---

### Post by dannyboy79 on 2007-06-01
> **loathsome said:**
> I'm using the ones that ships with Feisty. Yes, I do use the card - it's essential to me. I'll try the serialmonkey drivers - but as far as I can see that guide wants me to download the 386 kernel. Hmm.

Thanks a lot **dannyboy79**!

OK, did you give me the dmesg from the livecd booting? or did you give me the dmesg from YOUR install booting. I'll need it from YOUR system booting, not the livecd. I am not entirely sure if they are different but it's possible that something is loading on YOUR system and NOT on the live cd which is what dmesg shows. Also, if you read on, there was a person that chimed in that stated that he got it to work using the latest source and still used the -generic kernel. The -386 kernel will not take advantage of your dual cores or hyperthreading if you have a CPU that does that. and according to the guide, he states that you really won't notice it unless your crunching number to figure out more prime numbers. he he he

according to the dmesg, it's loading these 2 modules:
r8169
rt61
and this is your problem according to a previous poster. you stated that you REMOVED your wirless card,booted the machine up, it shouldn't call for rt61 anymore because your card is removed,  then you blacklisted the rt61 driver along with anything similar to it, then you shut down, then you plugged in the wireless card again, tehn you booted up. I know the wireless card won't work, but your freezes should stop according to a previous poster, than just follow the link I provided about compiling new wireless drivers.
NOTE: cautious about kernel upgrades, everytime you update to a new kernel, you'll haev to reinstall any modules that you compiled.

---

### Post by loathsome on 2007-06-01
Hi there,

Thanks for your help. I have read a lot, and now I think I've got it! (REALLY REALLY HOPE SO DAMNIT :D)

I compiled the serialmonkey drivers and installed them (I think). I rebooted my PC, loaded the module and ran stable until I manually rebooted again. How can I verify which drivers my card are using?

Again, thank you! If it weren't for this thread, I'd so be on ugly XP now.

Best,
loathsome

---

### Post by dannyboy79 on 2007-06-01
check this command
lsmod
and also, please post back the results of the dmesg AFTER you feel as though the module being loaded is the NEW compiled one.

---

### Post by loathsome on 2007-06-01
> **dannyboy79 said:**
> check this command
lsmod
and also, please post back the results of the dmesg AFTER you feel as though the module being loaded is the NEW compiled one.

Yarr, seems like the drivers are up and running! > [  105.262566] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[  105.263023] RT61: Vendor = 0x1814, Product = 0x0301 
[  105.319068] RT61: RfIcType= 3


ANYYYHOW, It's stable enough now - until I install the nvidia-glx drivers. Then it becomes unstable again. I've tried both 'new' and 'legacy', both keeps my pc crashing and I couldn't even select my resolution (1440x900)

So, basically; I've solved the problem with my wireless card - now my damn GPU drivers crash :lolflag:

---

### Post by dannyboy79 on 2007-06-01
well I am not sure about that, was the dmesg that you provided when you still had the original rt61 drivers that ubuntu's provides? If so, your NEW dmesg states that same thing as your OLD dmesg, which was this:
rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[  143.448851] RT61: Vendor = 0x1814, Product = 0x0301
So I don't know how this works as I pointed out before. I don't understand how both the ubuntu rt61 driver and the new compiled driver are both the CVS version 1.1.0 UNLESS the dmesg you uploaded before was after you already installed the new driver OR there was never a need to compile a new driver OR the name of the driver doesn't change and somehow when you install the new driver, it removes the old one and the name stays the same. 
Hope it's working for ya!!!
As far as the nvidia issue, are you certain it's related to the nvidia card? it could just be a coicidence (i hate spelling!!) that it's freezing after you install it but may be related to somehting else. You haev a motherboard that has been plagued with issues, you have the Jmicron chipset, do you have any hard drives hooked to that controller? Here's a link to some common issues with core2duo cpu's and motherboards. [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)
also, what EXACT method did you use to install the nvidia driver. Also, you can't just use the legacy to give it a try, it's not even compatible with the card you have, you need to either use the 9755 or the latest and greatest from nvidia site or from envy, that's the 100.xx.xx driver. You'll figure it out, just don't give up. You'll be way wiser and will be able to troubleshoot other stuff with all this stuff you're learning.

---

### Post by loathsome on 2007-06-01
Hi,

Hmmm. I just booted up the LiveCD, and what the heck? It says I'm using the serialmonkey driver???!

No, I'm not certain on anything :-P I THINK it's the nvidia card, because I had the pc running an hour or so (stable as hell), and then when I grabbed the drivers from the «restricted drivers manager» it immediately started freezing and whatnot.

I've got a S-ATA harddrive connected directly to my P5B.

My hear has turned gray and I've almost smashed my keyboard in a million pieces :D But I'm not giving up..




.. not yet.

---

### Post by dannyboy79 on 2007-06-01
> **loathsome said:**
> Hi,

Hmmm. I just booted up the LiveCD, and what the heck? It says I'm using the serialmonkey driver???!

No, I'm not certain on anything :-P I THINK it's the nvidia card, because I had the pc running an hour or so (stable as hell), and then when I grabbed the drivers from the «restricted drivers manager» it immediately started freezing and whatnot.

I've got a S-ATA harddrive connected directly to my P5B.

My hear has turned gray and I've almost smashed my keyboard in a million pieces :D But I'm not giving up..




.. not yet.
that's what I figured, Ubuntu Feisty IS using the serialmonkey driver to begin with, it was some1's sggestion to blacklist the rt61pc module so that it didn't cause conflicts with the rt61 driver. So I apologize since I suggested that you try the latest rt61 drivers from serialmonkey which you didn't need to only because it appears that feisty already IS using them. I would strongly suggest reading thru each of the freeze's and solutions on the page I linked you to for the core2duo support as I don't think you have this fixed yet.

As for the nvidia drivers, try this link 
[http://ubuntuforums.org/showthread.php?t=432056&page=8](http://ubuntuforums.org/showthread.php?t=432056&page=8)
and follow post number 78 bit for bit, and if you have a question, it's probably been answered within that same link, just on the next pages.

---

### Post by loathsome on 2007-06-01
Ok, I'm back from another fresh install (#5315640640 :lolflag:), and when I grab the "nvidia-glx", I always get the "no screens found". I tried everything you said, and have reconfigured, reinstalled (purge etc etc) multiple times. I just can't seem to get them to work. Again, I've got a **7900 GT** card.

The «nv» drivers works fine, but .. I can nearly do anything in them :-P (they work with my resolution, though)

I got the freeze until I manually compiled the serialmonkey driver and overwrote the default driver.  :) So I've solved that problem.

What do I do about the drivers?

---

### Post by loathsome on 2007-06-01
Here's what dmesg outputs;

> [  634.557106] NVRM: API mismatch: the client has the version 1.0-9631, but
[  634.557108] NVRM: this kernel module has the version 1.0-9755.  Please
[  634.557110] NVRM: make sure that this kernel module and all NVIDIA driver
[  634.557111] NVRM: components have the same version.
[  638.601506] NVRM: API mismatch: the client has the version 1.0-9631, but
[  638.601508] NVRM: this kernel module has the version 1.0-9755.  Please
[  638.601510] NVRM: make sure that this kernel module and all NVIDIA driver
[  638.601511] NVRM: components have the same version.
[  642.648739] NVRM: API mismatch: the client has the version 1.0-9631, but
[  642.648741] NVRM: this kernel module has the version 1.0-9755.  Please
[  642.648743] NVRM: make sure that this kernel module and all NVIDIA driver
[  642.648744] NVRM: components have the same version.

I feel like my goal is getting closer and closer :D

---

### Post by loathsome on 2007-06-01
I just watched three episodes of King of Queens, and idled the computer for a while without a single freeze :D

---

### Post by dannyboy79 on 2007-06-01
> **loathsome said:**
> I just watched three episodes of King of Queens, and idled the computer for a while without a single freeze :D

ok, well if you're still after the nvidia driver than you keep installing the wrong one. If you have a 7900gt than you need the 9755 driver and that driver is located wihtin the repo's under the name of nvidia-glx-new. I haev already informed you how to install it.
It states here: [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
that this card is supported by the driver I am terlling you to install. GeForce 7900 GT/GTO 	0x0291
and the guide I got my instructions which i have already gaven you are here: [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
under method 1

By your post above (you installed the nvidia-glx????) you didn't read what I stated to do if you wanted my help so I can't help you anymore if you chose to use my help.
Good luck.

---

### Post by loathsome on 2007-06-01
> **dannyboy79 said:**
> ok, well if you're still after the nvidia driver than you keep installing the wrong one. If you have a 7900gt than you need the 9755 driver and that driver is located wihtin the repo's under the name of nvidia-glx-new. I haev already informed you how to install it.
It states here: [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
that this card is supported by the driver I am terlling you to install. GeForce 7900 GT/GTO 	0x0291
and the guide I got my instructions which i have already gaven you are here: [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
under method 1

By your post above (you installed the nvidia-glx????) you didn't read what I stated to do if you wanted my help so I can't help you anymore if you chose to use my help.
Good luck.
The restricted drivers manager told me to get «nvidia-glx», so .. 

I'll try out everything you've said right now! :D I'll report back in a small while.

PS: 
```
loathsome@hornydawg:~$ uptime
 16:07:31 up  3:46,  5 users,  load average: 0.40, 0.41, 0.30

```

:D :D I couldn't leave it on for 10 mins before. Thanks a LOT!

---

### Post by loathsome on 2007-06-01
> **dannyboy79 said:**
> ok, well if you're still after the nvidia driver than you keep installing the wrong one. If you have a 7900gt than you need the 9755 driver and that driver is located wihtin the repo's under the name of nvidia-glx-new. I haev already informed you how to install it.
It states here: [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
that this card is supported by the driver I am terlling you to install. GeForce 7900 GT/GTO 	0x0291
and the guide I got my instructions which i have already gaven you are here: [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
under method 1

By your post above (you installed the nvidia-glx????) you didn't read what I stated to do if you wanted my help so I can't help you anymore if you chose to use my help.
Good luck.

I have only one thing to show you:
[**CLICK**]("http://i139.photobucket.com/albums/q316/loathsome_/Miscellaneous/2007-06-02-162148_1440x900_scrot.png")
:KS:KS:KS:KS:KS:KS:KS

The magic command I had to do after nvidia-glx-new was ```
sudo nvidia-xconfig --no-composite
```

FREAKING FREAKING **GREAT!** Seriously, I am forever grateful! Thank you ever so much. I AM SO GLAD I DON'T HAVE TO GO BACK TO VISTA!!!!!

Though, I have ONE small problem yet - the max refresh rate I can set is 56hz, and things looks kinda groggy with it. How do I set it to 60, which is what my monitor is supposed to show? I've tried 1440x900_60 in xorg.conf, and when I do that things gets kind of pixelated

---

### Post by rplantz on 2007-06-02
My system runs fine for several days (I turn it off each night), then gets into a bad state. I'm running an amd64 in 64-bit mode on an abit nf8 motherboard with nvidia fx5200 (128 MB) video. I use the 9755 driver from ubuntu repositories.

I have Ubuntu Feisty and Debian Etch on my 160GB SATA disk. I recently installed FreeBSD 6.2 on my 80GB PATA disk.

When it got into its bad state two days ago, Ubuntu would run for a few minutes, same for Debian, and I could not even boot into FreeBSD.

Now this part will sound crazy, but I've had this same experience several times. Mine is a desktop box. I disconnected it and opened it up. I reseated the disk cables and looked around for loose connections. Put it all back together, and now it's working fine. In previous "fixes" I have (1) cleaned the dust out of the CPU heatsink, (2) cleaned the dust out of the video card heatsink, (3) reseated the memory and video cards, and (4) just sort of poked around and looked for loose wires, etc. Each of these has been a separate "fix." I'm not joking, and I don't do drugs (not even alcohol). It seems like simply disconnecting the box from the monitor, etc. and looking inside "fixes" the system for several days. (Perhaps it's lonely. :))

I also noticed today from my /etc/X11/xorg.conf file that Feisty did not identify my video card and monitor. In the past it has done that. Debian Etch did that. For example, from Feisty,
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

```
and in Debian,
```

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Daewoo 19 PnP-CRT"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

```
Previous versions of Ubuntu generated an xorg.conf similar to Debian's.

Notice that the horizontal sync and vertical refresh are incorrect in Feisty's xorg.conf. I have to go in and modify them by hand to match my monitor.

Also, I can only set the refresh rate with Applications->System Tools-> NVIDIA Settings. System->Preferences->Screen Resolution does not work. And when I set the refresh rate to 85 Hz, System->Preferences->Screen Resolution shows it to be 120 Hz!

I think that there is something weird with xorg and that it puts my video card in a weird state every once in a while. The next time my system goes into its bad state, I will try simply disconnecting my monitor for a few minutes, not open the case, and see if that works.

---

### Post by loathsome on 2007-06-02
Hey **dannyboy79**!

I just did a fresh reinstall (this is most likely my last ever :D), and compared the default drivers to my new ones. Look at this; These are the old ones:
> [  281.282708] rt61 1.1.0 CVS CVS [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[  281.347111] RT61: RfIcType= 3

And here's my self-compiled ones:> [   48.043235] rt61 1.1.0 CVS 2007060212 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[   48.124610] RT61: RfIcType= 3

They are not the same! And ALL my freezes are gone! I haven't had a single freeze since I did this. Thank you ever so much - again!

(had to unplug my wireless card to be able to install :lolflag:)

Kindest,
loathsome

---

### Post by skywarp04 on 2007-06-02
I have been having a lot of freezes too.  It only happens if Firefox is running.  Doesn't matter if it's minimized or not.  If I'm using another program while Firefox is minimized it's almost guaranteed to lock up in about 10 minutes or less.  It hard locks like everyone in this forum is talking about.  I can move the mouse cursor, but that is it.  Nothing else works, can't reset X server, can't switch to a terminal, nothing.  I agree with one other post I read.  People need to start giving their hardware configurations instead of just writing in saying that they have the same problem.  I have a MB with an intel 875 chipset, P4 2.4 ghz w/ hyper threading enabled, 512 Mb of ram, serial ata harddrive and cdrom, and a radeon 9700 pro video card.  I originally suspected my radeon card as being the problem until I read this thread.  I am using the fglrx driver from Ubuntu's restricted repository.  Yes, I have tried different drivers.  They actually made my system more unstable.  I have tried disabling hyper threading, removing flash, and several things that I have read in posts which I can't remember.  I installed Epiphany today and am going to try using it for awhile.  I have three different programs open.  One of them being Epiphany which I'm using to surf the internet and so far I haven't had a single lock up.  Keeping my fingers crossed.  I'll post again to let everyone know how if it fixes my problem.

---

### Post by loathsome on 2007-06-02
> **skywarp04 said:**
> I have been having a lot of freezes too.  It only happens if Firefox is running.  Doesn't matter if it's minimized or not.  If I'm using another program while Firefox is minimized it's almost guaranteed to lock up in about 10 minutes or less.  It hard locks like everyone in this forum is talking about.  I can move the mouse cursor, but that is it.  Nothing else works, can't reset X server, can't switch to a terminal, nothing.  I agree with one other post I read.  People need to start giving their hardware configurations instead of just writing in saying that they have the same problem.  I have a MB with an intel 875 chipset, P4 2.4 ghz w/ hyper threading enabled, 512 Mb of ram, serial ata harddrive and cdrom, and a radeon 9700 pro video card.  I originally suspected my radeon card as being the problem until I read this thread.  I am using the fglrx driver from Ubuntu's restricted repository.  Yes, I have tried different drivers.  They actually made my system more unstable.  I have tried disabling hyper threading, removing flash, and several things that I have read in posts which I can't remember.  I installed Epiphany today and am going to try using it for awhile.  I have three different programs open.  One of them being Epiphany which I'm using to surf the internet and so far I haven't had a single lock up.  Keeping my fingers crossed.  I'll post again to let everyone know how if it fixes my problem.
Did you apply the firefox update(s) that was released today?

---

### Post by thewall on 2007-06-02
Hi everybody! :D I'm a Ubuntu Feisty Fawn user from Italy and I'm having this problem of freezes...

I tried everything suggested in this topic: kernel options, rt61 drivers (I checked it, but I don't use it), CPU clock always set on maximum frequency,etc etc...
But I didn't solved the problem!

My hardware configuration?
AMD Athlon 64 3200+
ATI Radeon X800GTO
RAM 1024 MB
Motherboard: Gigabyte k8 triton nforce4 SLI

I attach my dmesg and my lspci... I hope that someone has time to read them... [-o<

BYE!!! ;)

---

### Post by Digitallysick on 2007-06-02
Ok i think i have made some changes, and now my beryl and nvidia driver havent froze in days. I dont know for sure if this corrected the problem but i will follow up In a few weeks. 

My fawn worked fine, but beryl would cause it to freeze at random. As long as beryl was off, i didnt have a problem I think i fixed the issue, Here is what i did. 

1. Open the beryl settings manager, and disable beryl "blur" click the warning tab  where it says "nividia users should disable blur" i just unchecked it and disabled blur.

2. Turn off water effects, splash, snow (whatever) in my extras i only have dbus and window previews checked.

3. Go to advanced options, rendering platform and select  force nvidia!

4. Dont use a open GL screen saver, i kept useing "hufos tunnel" That screen saver freezes the pc, i think all the gl ones do. So i just selected "gnome feet" but you get the idea, just a basic screen saver. 



After doing these steps i havent had a freeze in about 5 days and counting! *crosses fingers*

---

### Post by loathsome on 2007-06-03
> **Digitallysick said:**
> Ok i think i have made some changes, and now my beryl and nvidia driver havent froze in days. I dont know for sure if this corrected the problem but i will follow up In a few weeks. 

My fawn worked fine, but beryl would cause it to freeze at random. As long as beryl was off, i didnt have a problem I think i fixed the issue, Here is what i did. 

1. Open the beryl settings manager, and disable beryl "blur" click the warning tab  where it says "nividia users should disable blur" i just unchecked it and disabled blur.

2. Turn off water effects, splash, snow (whatever) in my extras i only have dbus and window previews checked.

3. Go to advanced options, rendering platform and select  force nvidia!

4. Dont use a open GL screen saver, i kept useing "hufos tunnel" That screen saver freezes the pc, i think all the gl ones do. So i just selected "gnome feet" but you get the idea, just a basic screen saver. 



After doing these steps i havent had a freeze in about 5 days and counting! *crosses fingers*

I don't think this is the case for my NVIDIA - I use the tunnel one all the time, plus I haven't unchecked anything particular in beryl. But I'm glad to hear that you might have solved your problem! :)

---

### Post by Digitallysick on 2007-06-03
i was wrong, i froze again, so its back to the drawing board

---

### Post by joe.turion64x2 on 2007-06-03
> **Digitallysick said:**
> i was wrong, i froze again, so its back to the drawing board
Have you considered a hard drive issue? My machine used to freeze some time ago, I blamed the ATI drivers and tried everything. My problems stopped when I replaced the hard drive.

Joe.

---

### Post by loathsome on 2007-06-03
loathsome@globalcasting:~$ uptime
 20:05:02 up **3 day, 38 mi**n,  3 users,  load average: 0.67, 0.30, 0.17

If that's not *stable*, I don't care. I'm sure I'll never have to turn my PC off again! I'm so damn happy I solved my problem!!:KS

> **Digitallysick said:**
> i was wrong, i froze again, so its back to the drawing board

How many RAM bricks do you have? You might want to try setting them into «single channel» instead of dual, if you have more than one.

---

### Post by johanPO on 2007-06-03
One thing that one can do is to put another distribution on. I installed sabayon, and have not had a single freeze since then, so there is something in feisty that need to be fixed. It is not my HW. I will keep following this thread but right now I have a solution to the problem I had.

---

### Post by rplantz on 2007-06-03
> **johanPO said:**
> One thing that one can do is to put another distribution on. I installed sabayon, and have not had a single freeze since then, so there is something in feisty that need to be fixed. It is not my HW. I will keep following this thread but right now I have a solution to the problem I had.

As I have mentioned above, when my system is in its "freeze mode," my Debian Etch also freezes and I cannot boot into my FreeBSD. Both of them boot through my grub that got installed with Ubuntu.

---

### Post by cuplex on 2007-06-03
Hi there! I had alot of system freezes too and i tried all suggestions in the forums starting with this [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)
and working me through others.

Well none of them satisfied me completely and i had to find out why! Well before i talk to much. I tried to install Windows just to test if its hard or software. Install BSOD!!!

**So what i did is reseting my BIOS defaults! BTW i use an DFI Lanparty Ultra NF4, and rised my RAM Voltage from Default 2,5 to 2,7! Made some manual timing adjustments 3-4-4-8 and voila my box runs like a charm!**

Before i made that i changed nearly everything, Power Supply, RAM, removed every additional card. none helped! Oh and you should use an ATX Adapter if you maybe using some new MoBo and some "old" Power Supply 20pin to 24pin! 

Well after thinking on how that could work before i remembered that i overclocked my box a few months ago and after some testing and checking how far i can go i reseted those values! (that was maybe 6 Months ago) well and there was some mistake... and i also remebered that my windows had alot of BSOD after "resetting" my overclocking stuff, but that was kind o normal these days i thought!

So maybe this helps some ppl out there! And yes that can happend to you without overclocking! especially when you are using DFI Lanparty boards! They seem to be very "selfish" when it comes to RAM choosing! Anyway just some thoughts!

regards and thx to the community!

PS: i forgott to mention that i'm using <>noapic acpi=off<> option from above mentioned topic

---

### Post by dannyboy79 on 2007-06-04
> **cuplex said:**
> Oh and you should use an ATX Adapter if you maybe using some new MoBo and some "old" Power Supply 20pin to 24pin! 
If you were hooking an old PSU that only had a 20 pin and tried hooking it to a 24 pin motherboard than that's a huge mistake in itself! It's a good point for people coming from Winbloz to make sure they reset their previous overclocked machines to default, at least until Feisty is stable, than they can play with overclocking as you have found out. 

Glad you got it working. As we have seen, there are many many solutions as everyone's problem is most likely just hardware combiination and has nothing to do with ubuntu or nvidia drivers to be honest!!!! OR they installed somehting that is comflicting the libraries etc etc as that's what my problem was. I used Automatix2 immediately after installing Feisty and then I keep getting freezing on gksudo commands, that was all, nothing else. I had reinstalled and now my machine runs like a champ!!! I use compiz however not Beryl, I don't need the rain drops and other similar. I only need wobbly windows, snaping windows when minimizing and maximiaing, the 3d cube for workspaces (that's PIMP) and that's it so compiz does the triick for me. ALso, opengl stuff should work if you have direct rendering yes from glxinfo just so you you know. (at least mine does using nvidia proprietaty 9755 or nvidia-glx-new if they aren't one in the sme!) I can even use compiz along with my mythtv and opengl theme!

forgot to mention something huge. I use NO boot options!!!! As I stated earlier, there's 4 things within dmesg that are ussual but I'm running strong since I reinstalled, it's only shut off once due to power outage (damn, i really need the UPS)
[ 2.857782] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.C PU1._PDC] (Node df81689c), AE_BAD_HEADER
[ 2.857899] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.C PU2._PDC] (Node df8167fc), AE_BAD_HEADER
[ 2.857936] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Dev ice is not present [20060707]
[ 2.857943] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Dev ice is not present [20060707]

---

### Post by bootsbradford on 2007-06-04
IS THERE ANYONE WHO CAN HELP?

I am so frustrated with Ubuntu. My PC is set up as a dual boot between XP and Ubuntu. It worked fine with Edgy for a number of months. It worked fine for a few weeks with Feisty. Then one day, for no particular reason, it started freezing and it's been freezing ever since.

I've read this thread but its confused me more than helped - everyone is suggesting so many reasons, has no-one in Ubuntu got to the bottom of this issue with a clear and definite solution? It seems to be affecting so many people.

Here are some basic specs about my PC: 
Desktop
Wired internet connection
Intel(R) Pentium(R) 4 CPU 3.40GHz
RADEON X600/X550 Series
What other info can I give people to enable them to help me? 

I've loved Ubuntu so much but I'm so frustrated that I can't stop it freezing, even though it works fine with XP...

PLEASE HELP IF YOU CAN!

---

### Post by candtalan on 2007-06-04
> **suoko said:**
> I'm experiencing the same thing:
feisty is ok on my pentium 4 desktop (with no wirless nics) while it keeps temporary freezing on my intel dual core notebook with integrated intel wireless nic.

**I bet it's a kernel issue with dual cores or with wireless nics ...**

I do not have wireless.

I have just today upgraded one of my machines to 7.04 Kubuntu and it is freezing a lot. It is a straight new install, and then with firefox installed (not being run yet). No fancy graphics no wireless. Wired ethernet only. 
Mainboard is asrock (mentioned earlier in thread I think). 
Happens to have onboard NIC and a PCI board too. I notice that IRQ is 11 for one NIC and also something else, fwiw.

I have a number of machines and 7.04 kubuntu is now on a several of them an dhas been fro some time, all ok., but only this one PC is freezing. 

I will persist with this PC and install xubuntu-desktop on it, use it, and watch.

Good luck to they who may find the solution!

Edit:
I have now installed xubuntu-desktop and attempted to log out  (not reboot) to allow a windows manager change at login again. The display remains blank and I cannot at this stage login. I now recall that today when I first used the kubuntu 7.04 live CD, it did not give a display, so I restarted and used Safe graphics mode.

---

### Post by loathsome on 2007-06-04
> **bootsbradford said:**
> IS THERE ANYONE WHO CAN HELP?

I am so frustrated with Ubuntu. My PC is set up as a dual boot between XP and Ubuntu. It worked fine with Edgy for a number of months. It worked fine for a few weeks with Feisty. Then one day, for no particular reason, it started freezing and it's been freezing ever since.

I've read this thread but its confused me more than helped - everyone is suggesting so many reasons, has no-one in Ubuntu got to the bottom of this issue with a clear and definite solution? It seems to be affecting so many people.

Here are some basic specs about my PC: 
Desktop
Wired internet connection
Intel(R) Pentium(R) 4 CPU 3.40GHz
RADEON X600/X550 Series
What other info can I give people to enable them to help me? 

I've loved Ubuntu so much but I'm so frustrated that I can't stop it freezing, even though it works fine with XP...

PLEASE HELP IF YOU CAN!
There's no such thing as "clear and definite solution", because everybody has different hardware, and there's a different solution for everybody.

Do you have all the latest updates?
Does this happen if you try kernel 2.6.20-15 instead of 16?
Which ATI drivers do you use?
Have you tried all the numerous solutions posted in this thread?
Do you have any wifi cards in your computer?
Did you try reseting your bios?

It's impossible to give you a "definite" solution; Such thing doesn't (unfortunately) exist.

Best,
loathsome

---

### Post by dannyboy79 on 2007-06-04
> **bootsbradford said:**
> IS THERE ANYONE WHO CAN HELP?

I am so frustrated with Ubuntu. My PC is set up as a dual boot between XP and Ubuntu. It worked fine with Edgy for a number of months. It worked fine for a few weeks with Feisty. Then one day, for no particular reason, it started freezing and it's been freezing ever since.

I've read this thread but its confused me more than helped - everyone is suggesting so many reasons, has no-one in Ubuntu got to the bottom of this issue with a clear and definite solution? It seems to be affecting so many people.

Here are some basic specs about my PC: 
Desktop
Wired internet connection
Intel(R) Pentium(R) 4 CPU 3.40GHz
RADEON X600/X550 Series
What other info can I give people to enable them to help me? 

I've loved Ubuntu so much but I'm so frustrated that I can't stop it freezing, even though it works fine with XP...

PLEASE HELP IF YOU CAN!
show us output from 
lsmod
it has appeared to be comflicting modules many times. Let's start there and NO, no one has nailed this down as MANY MANY people don't have any issues. Did you check out lanuchpad? I myself had freezes when using gksudo but after a reinstall and no Automatix2 or any of the apps installed by automatix2, I have no more problems. have you checked out log files, checked out TOP after ssh'ing into the frozen box? can you go to tty1 (ctrl-alt-f1) when it freezes? so there are many many questions you need to answer to narrow this down to hardware of software!!!

---

### Post by dannyboy79 on 2007-06-04
> **candtalan said:**
> I do not have wireless.

I have just today upgraded one of my machines to 7.04 Kubuntu and it is freezing a lot. It is a straight new install, and then with firefox installed (not being run yet). No fancy graphics no wireless. Wired ethernet only. 
Mainboard is asrock (mentioned earlier in thread I think). 
Happens to have onboard NIC and a PCI board too. I notice that IRQ is 11 for one NIC and also something else, fwiw.

I have a number of machines and 7.04 kubuntu is now on a several of them an dhas been fro some time, all ok., but only this one PC is freezing. 

I will persist with this PC and install xubuntu-desktop on it, use it, and watch.

Good luck to they who may find the solution!


show us output from 
lsmod
it has appeared to be comflicting modules many times. Let's start there and NO, no one has nailed this down as MANY MANY people don't have any issues. Did you check out lanuchpad? I myself had freezes when using gksudo but after a reinstall and no Automatix2 or any of the apps installed by automatix2, I have no more problems. have you checked out log files, checked out TOP after ssh'ing into the frozen box? can you go to tty1 (ctrl-alt-f1) when it freezes? so there are many many questions you need to answer to narrow this down to hardware of software!!!

---

### Post by rplantz on 2007-06-04
> **bootsbradford said:**
> IS THERE ANYONE WHO CAN HELP?

I am so frustrated with Ubuntu. My PC is set up as a dual boot between XP and Ubuntu. It worked fine with Edgy for a number of months. It worked fine for a few weeks with Feisty. Then one day, for no particular reason, it started freezing and it's been freezing ever since.

I've read this thread but its confused me more than helped - everyone is suggesting so many reasons, has no-one in Ubuntu got to the bottom of this issue with a clear and definite solution? It seems to be affecting so many people.

Here are some basic specs about my PC: 
Desktop
Wired internet connection
Intel(R) Pentium(R) 4 CPU 3.40GHz
RADEON X600/X550 Series
What other info can I give people to enable them to help me? 

I've loved Ubuntu so much but I'm so frustrated that I can't stop it freezing, even though it works fine with XP...

PLEASE HELP IF YOU CAN!

Your situation sounds a little similar to mine, although my hardware differs. The next time mine goes into its "freezy" mode, I plan to shut it down, unplug the power cord, and let it set for 15 - 30 minutes. Then I will plug it back in and start everything up again.

You can read my reasons in post #307 in this thread.

---

### Post by dannyboy79 on 2007-06-04
> **rplantz said:**
> Your situation sounds a little similar to mine, although my hardware differs. The next time mine goes into its "freezy" mode, I plan to shut it down, unplug the power cord, and let it set for 15 - 30 minutes. Then I will plug it back in and start everything up again.

You can read my reasons in post #307 in this thread.

Have you checked the temp in which your cpu runs at? what about the voltages? I am guessing  if it runs fine for a period of time, then it freezes, this is definitely hardware issue UNLESS you can tell me specifically you that you were doing the same thing exactly every time, then I'd tell you that it's possibly libraries conflicting and or similar. Did you use Automatix2 to isntall stuff, that's one of best looking suspects for me which caused my freezing of any app that required gksudo to have root privalages of it.

ALso, just so you are aware, unplugging a monitor will not unfreeze anything to the best of my knowledge as the video output is sent to the nvidia out port whether you have a monitor hooked to it or not, if it does unfreeze, I can almost 99% guarantee it was not because you unplgugged the monitor for a little bit. Think about, how would that unfreeze what's  frozen? You need to answer the few questions that I asked above to help troubleshoot this if you're interested that is. do you have hddtemp installed? That's a huge known freeze app with Feisty.

---

### Post by candtalan on 2007-06-04
> **dannyboy79 said:**
> show us output from 
lsmod
it has appeared to be comflicting modules many times. Let's start there and NO, no one has nailed this down as MANY MANY people don't have any issues. Did you check out lanuchpad? I myself had freezes when using gksudo but after a reinstall and no Automatix2 or any of the apps installed by automatix2, I have no more problems. have you checked out log files, checked out TOP after ssh'ing into the frozen box? can you go to tty1 (ctrl-alt-f1) when it freezes? so there are many many questions you need to answer to narrow this down to hardware of software!!!

(still using kubuntu here, although xubuntu-desktop has now been installed)

lsmod:

user@dabs1:~$ lsmod
Module                  Size  Used by
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_stats           7360  0
cpufreq_userspace       5408  0
cpufreq_conservative     8200  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
tc1100_wmi              8068  0
dev_acpi               12292  0
pcc_acpi               13184  0
sony_acpi               6284  0
battery                10756  0
ac                      6020  0
button                  8720  0
video                  16388  0
sbs                    15652  0
container               5248  0
dock                   10268  0
asus_acpi              17308  0
i2c_ec                  6016  1 sbs
backlight               7040  1 asus_acpi
ext2                   66824  1
reiserfs              247680  3
ipv6                  268960  8
lp                     12452  0
fuse                   46612  0
snd_intel8x0           34332  4
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m
idi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi
di,snd_seq
serio_raw               7940  0
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_i810                6276  0
pcspkr                  4224  0
psmouse                38920  0
i2c_algo_bit            8712  1 i2c_i810
snd                    54020  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mix
er_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
intel_agp              25244  1
agpgart                35400  1 intel_agp
i2c_core               22656  3 i2c_ec,i2c_i810,i2c_algo_bit
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
af_packet              23816  4
tsdev                   8768  0
evdev                  11008  3
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  2 ext2,ext3
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
ide_disk               17024  9
ata_generic             9092  0
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
generic                 5124  0 [permanent]
usbhid                 26592  0
hid                    27392  1 usbhid
8139cp                 25088  0
floppy                 59524  0
piix                   11140  0 [permanent]
8139too                27648  0
e100                   36232  0
mii                     6528  3 8139cp,8139too,e100
ehci_hcd               34188  0
uhci_hcd               25360  0
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability
user@dabs1:~$

---

### Post by candtalan on 2007-06-04
> **dannyboy79 said:**
> show us output from 
lsmod
it has appeared to be comflicting modules many times. Let's start there and NO, no one has nailed this down as MANY MANY people don't have any issues. Did you check out lanuchpad? I myself had freezes when using gksudo but after a reinstall and no Automatix2 or any of the apps installed by automatix2, I have no more problems. have you checked out log files, checked out TOP after ssh'ing into the frozen box? can you go to tty1 (ctrl-alt-f1) when it freezes? so there are many many questions you need to answer to narrow this down to hardware of software!!!

My output from lsmod in another post from me.

This machine has run 6.06 kubuntu for a year, no problem.

It has been reinstalled from clean to kubuntu 7.04 today, updated fully, then used, and then freezes happened. It has no multimedia, standard graphics only, is used for backing up directories of approximately 50 GB, including use of digikam  and camera with 1GB of photos. Wired internet only. No automatix. The only installed extra app is firefox, but this has not been used except a single test of firefox.

Launchpad - I will look in time.

Log files - I have no idea which ones or how - I would be glad of guidance.

TOP and ssh'ing into frozen box - sorry I do not know what to do there - The frozen box has had to be mains reset (!!) I have no way I know to manage it when frozen. Guidance (and experience) would be useful.

At freezing, ctrl f1 has no effect, keyboard lights are flashing (??), mouse cursor frozen, 
ctrl alt backspace also no effect, nothing seems available, display is frozen, no disk activity seen.

I note that when originally today using the 7.04 kubuntu live CD I got no display after the initial boot menu options, so I restarted and used the live CD with safe graphics mode, and continued into the gui install (using manual) - all went ok then. Including full updates immediately after install.

hth

---

### Post by rplantz on 2007-06-04
> **dannyboy79 said:**
> Have you checked the temp in which your cpu runs at? what about the voltages?
What's a good way to check my CPU temperature?

The voltages are "stock." I have not changed them from my standard installation two years ago -- long before freezing began. The freezing behavior began when I installed a pre-beta version of feisty and continues through my current feisty install, which I did from a release CD.

> 
 I am guessing  if it runs fine for a period of time, then it freezes, this is definitely hardware issue UNLESS you can tell me specifically you that you were doing the same thing exactly every time, then I'd tell you that it's possibly libraries conflicting and or similar.

I generally agree with you, but I also realize that it's impossible to do exactly the same thing repeatedly. For example, I have little control over the timing of events when browsing the web.
> 
Did you use Automatix2 to isntall stuff, that's one of best looking suspects for me which caused my freezing of any app that required gksudo to have root privalages of it.

No.
> 
ALso, just so you are aware, unplugging a monitor will not unfreeze anything to the best of my knowledge as the video output is sent to the nvidia out port whether you have a monitor hooked to it or not, if it does unfreeze, I can almost 99% guarantee it was not because you unplgugged the monitor for a little bit. Think about, how would that unfreeze what's  frozen?

I have worked with smart monitors in the past, but mine is pretty dumb. So I agree that unplugging it should have no effect. On the other hand, I know that it is possible for software to read from the monitor. How else would the installer know its sync frequencies, model number, etc.? I would like to assume that this does not occur once installation has completed, but I have seen a lot of pretty weird code. (I worked as a programmer and CS professor, so I've read **lots** of code.)
> 
You need to answer the few questions that I asked above to help troubleshoot this if you're interested that is. do you have hddtemp installed? That's a huge known freeze app with Feisty.
I do not have hddtemp installed.

Thank you for your comments and questions.

---

### Post by candtalan on 2007-06-05
> **Digitallysick said:**
> feisty fawn keeps freezing on me, at first i thought it was FF causeing the issue. But now i have tried opera and it still happens, at random. Mostly when it freezes i can still move the mouse, but thats it. Today it froze with the screen saver (gnome feet). How can i tell what is causing this? would it be in the system logs? i can't take it much longer

Can someone please say which logs (to be examined after the event presumably) would help to get information on this?
tia

---

### Post by TyphoidHippo on 2007-06-05
I just thought I would drop a line in here that might help.

I, too, had horrible freezing problems with Feisty on one of my computers.

The only thing that helped was adding a line to my grub list that disabled apic and acpi when booting Ubuntu.  The tradeoff is that I can't monitor my temps and some other stuff that some people will deem as necessary....but the computer runs *forever without freezing up*, at least.

I will check what the line is (it's pretty long - it disables apic and acpi for sure....maybe some other similar things, too) and get back to this thread with the line that I added, if somebody doesn't fill it in before I get a chance to.

Sorry if this has already been mentioned here - I didn't read through all 34 pages.

---

### Post by candtalan on 2007-06-05
> **TyphoidHippo said:**
> I just thought I would drop a line in here that might help.

I, too, had horrible freezing problems with Feisty on one of my computers.

The only thing that helped was adding a line to my grub list that disabled apic and acpi when booting Ubuntu.  The tradeoff is that I can't monitor my temps and some other stuff that some people will deem as necessary....but the computer runs *forever without freezing up*, at least. 

Thanks, I think I saw it and can refer.
I did install (from kubuntu) the xubuntu-desktop as I suggested earlier in the thread, and ran it once, then went back to kubuntu to see if more could be found about the freezing in this brand new install. I left the PC on overnight, with a number of (kde) directory Properties (200,000 files or so) to display which maybe would have kept things warm and moving. PC is still on today, though not much used, but no freezing at all.

Wierd thought:
Could a library or something from xubuntu-desktop, even though not currently in action - be giving lack of freezes?

---

### Post by skywarp04 on 2007-06-05
Feisty has been driving me crazy for a few weeks now too.  I was having freezes like what most people in the thread are describing.  You could move the mouse cursor, but nothing else.  Updating Firefox or using Epiphany neither one solved my problem.  I decided to check my BIOS settings one more time.  I have an aBit IC7 motherboard and the memory settings in the BIOS have always been flaky, even after updating to the most recent BIOS.  You could manually set the timings and sometimes they wouldn't take and the motherboard is extremely sensitive to how you have the timings set.  Usually if you relax the timings it makes your computer more stable, but slightly slower right?  No, not mine, it won't even make it past the BIOS post screen with most slower settings.  And SPD does not work correctly either.  

    I did some research on my memory modules to find what SPD should be detecting.  I have Kingston HyperX memory and according to their website the timings should be set way different than what SPD is detecting on my motherboard.  So I manually set the timings to what Kingston says they should be.  So far my computer has been running for a day straight with no lock ups!!  Before I could force it to lock up in under 10 minutes just by running Firefox and another program together.  It has been running for awhile now with four programs including Firefox running.

    Hopefully this information will help some one else solve their problem too.  I have been using this computer ,set up the way it previously was, with Win XP for 3 years now.  I would occasionally (once every three or four months)  have a blue screen error which I just attributed as being normal Windows behavior :biggrin:, but it may have been my memory timings  not being set correctly causing the problem.  Moral of the story is, if you are having freezing problems take a step back and double check your hardware.  I had previously checked my BIOS settings, but refused to believe that might be the cause because I have been using the system with Win XP for years with almost no problems, just the occasional hic up.

---

### Post by benner on 2007-06-05
i haven't been on this thread for a while.  my freezes inexplicably went away.  then came back with a vengeance.  They were frequent enough that i did a fresh install with a 32bit just to see if that would help even though others have stated it wouldn't.  i installed and had freezes right away, before i installed anything at all.  the first happened when i opened movie player.  then i rebooted and it froze on the login screen.  i couldn't even type in my login name.  i rebooted and it was all fine.  i installed vmware server and let it run while i was out for a couple hours.  came back and it had frozen while i was away.  i rebooted and here i am.

i have an amd 4200+
asus video card with ati x550 chipset
some sort of nvidia chipset on the motherboard but don't know how to check
an 80gig IDE disk with 32bit ubuntu feisty on one partition and /home on another
a 250gig SATA disk with 3 partitions, ubuntu feisty 64 is on one of them
benq ide cd-rom
samsung SATA dvd burner
an extra usb card 

i thought it was a network card issue after reading some bugs on launchpad so i took out my extra network card.  problem went away for a month.  now it is back again.

i don't know what lsmod is/does but here's my output...

ben@ramen32:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
agpgart                35400  1 drm
powernow_k8            16064  1 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
button                  8720  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
battery                10756  0 
asus_acpi              17308  0 
video                  16388  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
ipv6                  268960  10 
lp                     12452  0 
fuse                   46612  0 
xpad                    9988  0 
yealink                12800  0 
snd_usb_audio          79744  0 
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
usbhid                 26592  0 
hid                    27392  1 usbhid
snd_pcm                79876  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              23684  2 snd_seq,snd_pcm
snd                    54020  14 snd_usb_audio,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               8672  1 snd
pcspkr                  4224  0 
k8temp                  6656  0 
af_packet              23816  2 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
serio_raw               7940  0 
i2c_nforce2             6784  0 
psmouse                38920  0 
i2c_core               22656  2 i2c_ec,i2c_nforce2
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  5 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
ide_cd                 32672  0 
ide_disk               17024  3 
sr_mod                 17060  0 
cdrom                  37664  2 ide_cd,sr_mod
sd_mod                 23428  7 
ata_generic             9092  0 
floppy                 59524  0 
ohci_hcd               22532  0 
uhci_hcd               25360  0 
ehci_hcd               34188  0 
forcedeth              46728  0 
usbcore               134280  9 xpad,yealink,snd_usb_audio,snd_usb_lib,usbhid,ohci_hcd,uhci_hcd,ehci_hcd
amd74xx                15260  0 [permanent]
sata_nv                20868  6 
libata                125720  2 ata_generic,sata_nv
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


i'm seeing some folks have been on this thread for a long time.   i'm impressed that you haven't given up yet.

---

### Post by idealist61 on 2007-06-05
I am having the same problem on a Toshiba A75-S206 laptop with ATI Radeon 9000 video. On booting I get BIOS error message 8254, relating to timing. Is this helpful?

---

### Post by DBStevens on 2007-06-05
Have any of you tried turning off hyperthreading  (SMP) in your bios?

Or adding nosmp  option in your grub configuration?

Just a thought from what I'm reading you all seem to have that in common.

---

### Post by tgm4883 on 2007-06-05
> **DBStevens said:**
> Have any of you tried turning off hyperthreading  (SMP) in your bios?

Or adding nosmp  option in your grub configuration?

Just a thought from what I'm reading you all seem to have that in common.

Not everyone has that in common, and not everyone that has SMP enabled has a problem.  Although I would agree that there are multiple different problems in this thread and that is a solution to some people problem (although not the underlying problem)

---

### Post by yannlieb on 2007-06-05
> root@yann-desktop:~# uptime
 22:36:16 up 4 days, 23:14,  1 user,  load average: 1.22, 2.66, 2.47


I have removed bunch of modules that I wasn't considering important, and I managed to get a stable system, without lockups for nearly 5 days.

Here is what I've removed (manually with rmmod, seems like modprobe.d/blacklist isn't working) :

### Yann removal
blacklist asus_acpi
blacklist backlight
blacklist linear
blacklist multipath
blacklist raid0
blacklist raid1
blacklist raid10
blacklist raid456
blacklist md_mod
blacklist fbcon
blacklist bitblit
blacklist tileblit
blacklist font
blacklist dm_mod
blacklist sony_acpi
blacklist ipv6
blacklist amd74xx

---

### Post by TyphoidHippo on 2007-06-05
Ok.  

I finally got around to checking what the menu.lst line was on that machine.

noapic nolapic pci=noacpi acpi=off

I had to add that to the end of the kernel flags in /boot/grub/menu.lst
(If you can't even get your OS running long enough to do that, you can add it to the boot line in Grub by pressing e in the loader).

The menu.lst for that machine looks (mostly) like this:

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,2)
kernel /vmlinuz-2.6.20-15-generic root=/dev/hda3 ro quiet splash noapic nolapic pci=noacpi acpi=off
initrd /initrd.img-2.6.20-15-generic
quiet
savedefault

That machine was a serious pain because of the freezing issues - and adding all of those flags is the only thing that finally made the freezing completely stop.

I have had several other machines that only required the much simpler 'pci=noacpi' flag (to run Feisty without freezing up randomly).

I hope that helps, and I'm sorry if I'm way off base on what the problem is here. Like I said earlier, I didn't read through all 34 pages...

---

### Post by DBStevens on 2007-06-05
> **tgm4883 said:**
> Not everyone has that in common, and not everyone that has SMP enabled has a problem.  Although I would agree that there are multiple different problems in this thread and that is a solution to some people problem (although not the underlying problem)

That is probably true, however it looks like a driver issue, one that is probably not exactly unaffected by having SMP ( or hyperthreading)  turned on, hence my mention. 

I'm not saying I have the exact solution here just another thing to check.

I haven't been running Unbuntu long enough to form an opinion on its stability.  However, I haven't run into any freezes on my home system which is running Fiesty. 

I do however have several remote servers running various versions of Redhat that haven't been rebooted in over two and a half years. 

I would like to see some system boot logs.

---

### Post by Electricboots on 2007-06-05
My Ubuntu Feisty AMD64 installation has been freezing too.  The computer just hangs, keyboard/mouse won't respond, the only solution is the Reset button.

I tried different booting options (noapic nolapic, etc), but it doesn't help.

Also, after I reboot, if I don't use Firefox 32 bit, it never freezes.  I can use the 64bit Firefox and everything will be ok for many days.

Once I start using Firefox 32 bit, then there's about 50% chance that my computer will freeze within the next hour or so.

If only I didn't need Firefox 32bit for flash/java...... :-/

---

### Post by dannyboy79 on 2007-06-05
> **candtalan said:**
> Can someone please say which logs (to be examined after the event presumably) would help to get information on this?
tia
all log files for all suff is located within /var/log/
you could check out
syslog
kern.log
maybe dmesg | tail
if you can ssh into the box or if you can go to tty1 you will be able to check the last command
hell, it's not like there's hundreds of log files, just read the ones you think may be applicable.

---

### Post by bootsbradford on 2007-06-06
> **dannyboy79 said:**
> show us output from 
lsmod
it has appeared to be comflicting modules many times. Let's start there and NO, no one has nailed this down as MANY MANY people don't have any issues. Did you check out lanuchpad? I myself had freezes when using gksudo but after a reinstall and no Automatix2 or any of the apps installed by automatix2, I have no more problems. have you checked out log files, checked out TOP after ssh'ing into the frozen box? can you go to tty1 (ctrl-alt-f1) when it freezes? so there are many many questions you need to answer to narrow this down to hardware of software!!!

I've attached a file with the output from lsmod. PLEASE let me know if there's anything which can be concluded from this, I'm at my wits end with this Ubuntu issue at the moment!

---

### Post by dannyboy79 on 2007-06-06
your lsmod looks ok, it's all about modules conflicting with 1 another. can you ssh into the box or go to tty1? if so than it's related to a xorg freeze I would think. have you used automatix2 to install anything? that was the cause of my gksudo freezing problem. I did a reinstall and didn't use automatix2 and that fixed it. I even use compiz with nvidia 9755 driver.

---

### Post by bootsbradford on 2007-06-06
> **dannyboy79 said:**
> your lsmod looks ok, it's all about modules conflicting with 1 another. can you ssh into the box or go to tty1? if so than it's related to a xorg freeze I would think. have you used automatix2 to install anything? that was the cause of my gksudo freezing problem. I did a reinstall and didn't use automatix2 and that fixed it. I even use compiz with nvidia 9755 driver.

Thanks for your help (and that of anyone else who would be able to offer it!). Could you explain what 'ssh' and 'tty1' are?!!

I do use automatix2. Used it without problem with edgy and certainly for a while without trouble with feisty. Hadn't considered that might be the problem, though maybe it could...

---

### Post by loathsome on 2007-06-06
Press CTRL+ALT+F1

There you have tty1 ;)

---

### Post by Peter76 on 2007-06-06
@loathsome:That doesn't work. Only thing that works is sshing to your box. BTW, having the same issues here on an iBook ( with ati ) and on a amd 900 dektop with a nvidia card. DOes anybody know what's going on exactly yet??? ( Hope someone answers quicker than I can read this whole thread :-)

---

### Post by Digitallysick on 2007-06-06
Ok im ready to break this thread into different issues. Beryl is causing my feisty fawn to freeze, so maybe i should start the thread "Beryl Feisty Fawn Freeze" because with beryl off im 100% ok. Where as Others i read, are not.  We should break this problem into known sections

---

### Post by dannyboy79 on 2007-06-07
> **Peter76 said:**
> @loathsome:That doesn't work. Only thing that works is sshing to your box. BTW, having the same issues here on an iBook ( with ati ) and on a amd 900 dektop with a nvidia card. DOes anybody know what's going on exactly yet??? ( Hope someone answers quicker than I can read this whole thread :-)
Are you trying to say that it doesn't work to people who haven't even tried it yet???? That's not a good idea, when I had my freezes, I could move the mouse but not interact with anything and I could go to tty1. So maybe you're just informing us what does and doesn't work for YOU only. So apparently for you, you have a keyboard freeze but not a system freeze since you can still SSH into you box. Sounds like it may be an Xorg issue. Have you tried to downgrade your xorg version? Might be a thought.

---

### Post by bootsbradford on 2007-06-07
> **dannyboy79 said:**
> your lsmod looks ok, it's all about modules conflicting with 1 another. can you ssh into the box or go to tty1? if so than it's related to a xorg freeze I would think. have you used automatix2 to install anything? that was the cause of my gksudo freezing problem. I did a reinstall and didn't use automatix2 and that fixed it. I even use compiz with nvidia 9755 driver.

I definitely cannot 'tty1' (now that I understand what that is!) when the system freezes. Still hoping that someone can explain what 'ssh into the box' means??!!

---

### Post by QwUo173Hy on 2007-06-07
You should probably start a seperate thread asking about SSH, as it would be going off topic here to do so. But while I'm here...

You need to run 
```
sshd
```

On the machine that freezes. Then, when it freezes, go to a machine on your network and type (in  my case)

```
ssh jarlath@ja-desktop
```

I got the jarlath@ja-desktop bit from the terminal. If you open your terminal you'll find your hostname there.

After you run this command (if memory serves me correct) you will actually be in a terminal for the frozen machine, as opposed to the machine you are working from. Cool huh?!

---

### Post by Chaoticwhizz on 2007-06-07
I solved this problem on my PC. Any of you who are running SuperKaramba, try turning off all of your applets on the desktop. Doing this after trying countless other things fixed it for me. There is a confirmed bug on launchpad on this issue. 

[https://bugs.launchpad.net/kdeutils/+bug/109507](https://bugs.launchpad.net/kdeutils/+bug/109507)

This solution obviously wont apply to all of you but it may help some.  I apologize if this has already been mentioned. I haven't read all 30-something pages.

---

### Post by gridsleep on 2007-06-09
My laptop has completely locked up once, so far.  And using SSH in remote terminal mode is completely useless on a totally locked up machine.  By locked up, in this case, I mean no response whatsoever.  All I could do is turn it off and back on.  The only applications running were Azureus, in which I was retrieving one file, and Firefox, in which I was viewing a video on YouTube.  When the video started playing, the machine locked up completely.  This is on a Toshiba Satellite M45-S165 laptop using Atheros wireless as the only network connection to my home wireless access point.  The lockup damaged the Azureus or the Java somehow, I haven't determined which.  I had to dump the download which was over 90% done, reinstall Azureus several times, and it still did not work right.  Azureus would drop out on startup because the file was still listed in its download list.  I had to delete the .azureus directory.  After reinstallation and restarting the torrent, the best I got was about five minutes of download before it dropped out again, this time without even having gone to YouTube or even having started Firefox.  Limewire was still running perfectly so I don't think the Java is damaged, but I still don't know that for sure.  I have stopped using any file sharing on the laptop.  If this rates a bug report, I'll do it.

---

### Post by johanPO on 2007-06-10
gridsleep

Your problem is similar to mine, but it does not look like we have much HW in common. I have a E6300+ AUS P5NSLI MB and a ALLNET PCI wireless card (using the prism54 driver). I have the same problem as you do, with the exception that it also craches with ktorrent, gwget so I do not think that this is something that has anything to do with a particular service. 

I have tried Ubuntu 7.04, crashes
Linux Mint, crashes
Mepis (that is where I am today) crashes
Fedora 7, does not crash but I could not install the ATI drivers so I dropped that (also they did nothave the prism54 drivers as a standard part, had to install that separately)
Sabayon, does not crash. Everything installed from the beginning. However to updates took 2 days of hard compiling and somehow I did not like that... it is the fall back solution 

To me it looks like this is something that comes with every Ubuntu flavor and other distros does not have this. Contemplating on what to try next PClinuxOS or openSUSE are the candidates

---

### Post by rplantz on 2007-06-10
> **johanPO said:**
> 
To me it looks like this is something that comes with every Ubuntu flavor and other distros does not have this. Contemplating on what to try next PClinuxOS or openSUSE are the candidates

When my system gets into its bad state, my Debian installation also freezes and I cannot boot into my FreeBSD installation. (I have provided more details in my earlier posts in this thread.)

My "fix" is weird. It seems like simply opening up my box and poking around inside for a few minutes "fixes" the problem. (Again, details are provided earlier.)

My system has been running fine for over a week now. The only thing I have done differently is that I have *not* used either **beryl** or **compiz**. In the past I have been using them, trying to determine which I like better. This time I decided that the standard ubuntu gnome desktop (without desktop effects enabled) provides enough eye candy for me, and that seems to be paying off in stability.

---

### Post by Antto on 2007-06-10
Hi, 
I have this same problem with Ubuntu feisty using Acer aspire 5021wlmi with ati X700 and amd turion ml-28. I had the computer freeze on random times but the mouse still worked allthough I cant do anything with it, also I can't kill the xserver with ctrl+alt+backspace or any other combination I've tried.
At first I was using the open source r300 driver which worked fine with aiglx etc but I had the crashes with it, So I decided to use the fglrx+xgl approach and since then I have not had any crashes or freezes, I also tried the opensource driver without beryl but not without aiglx and composite extension so maybe all the problems are because of either the composite extension or aiglx.
 At least that would explain the fact that I have seen most people having nvidia drivers with this problem. For me the solution was fglrx but I'd prefer the opensource drivers because of the quirks with xgl.

---

### Post by Digitallysick on 2007-06-11
If you know for a fact that beryl is causeing the freeze, try this command

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

then run it for a week or 2 and see if you get the freeze, if not, add this to your session startup! Im trying it, gues i will know in some days

---

### Post by rplantz on 2007-06-11
> **Digitallysick said:**
> If you know for a fact that beryl is causeing the freeze, try this command

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

then run it for a week or 2 and see if you get the freeze, if not, add this to your session startup! Im trying it, gues i will know in some days

I assume those of us who have nvidia cards should do
```

LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa beryl

```
What does this do?

---

### Post by dannyboy79 on 2007-06-12
> **rplantz said:**
> I assume those of us who have nvidia cards should do
```

LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa beryl

```
What does this do?

i notice that you're using the 64bit version, have you thought to test out the normal 32bit version to see if that's the issue? You could always try it out on a older hard drive temporarily within the same hardware.

---

### Post by rplantz on 2007-06-12
> **dannyboy79 said:**
> i notice that you're using the 64bit version, have you thought to test out the normal 32bit version to see if that's the issue? You could always try it out on a older hard drive temporarily within the same hardware.

Yes, I have thought of that. But I assume that most of the people in this thread are running 32-bit, so 64-bit seems pretty low on the list of suspects. Of course, it could be the interaction of 64-bit with my particular hardware/software.

One of the things I was asking for in my previous post is an explanation of the suggested fixes. (Dannyboy79, this is not aimed at your comment; I do understand your suggestion of 32-bit.) I see several suggestions, like ```
 noapic nolapic pci=noacpi acpi=off
``` but no explanation of what these are supposed to do. It sort of reminds me of Bill Cosby's "The Regular Way." :)

---

### Post by dannyboy79 on 2007-06-12
to tell you the truth, the best way to get the correct answer is to gogle them and find out on your own otherwise people will tell you different answers and you may be given some bad info. All I can tell is that this is a great sire for almost all kernel boot option explainations.

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/ch-bootopts.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/ch-bootopts.html)

it is for redhat but since the kernel is the heart of linux I believe that they should all be very similar.  I understand that kernels can be compiled differently with different .configs but I believe the boot options affect all kernels the same way, they tell it to do something or not to do it (someone correct me if I am wrong please)

---

### Post by loumsmith on 2007-06-12
I recently started having the same problem.  Sometimes the screen freezes at the login screen.  Other times it freezes the desktop.  No pattern to it.  I had 7.04 installed for weeks and there was no problem.  Could some update have created the problem?  Is there a log of updates somewhere on the system?
Thanks,
Lou

---

### Post by jimcooncat on 2007-06-12
> **jimcooncat said:**
> ... I tried "Desktop Effects" for a few minutes then disabled it. I haven't had a crash in two days after running "sudo nvidia-xconfig --no-composite", but I haven't pushed it too hard either since then. 

I've gone back to my normal heavy usage ... *and increased the size of my swap to 2 times my RAM* ... and haven't had a freeze for more than a week now.  :D

My freezes were the type that the mouse would be unenabled. I didn't bother to try to SSH in during those times as I suspected it would be too slow (the computer being busy trying to purge its toxins) for my patience. I suspect it was the swap more than the *no-composite* setting, but I've no means to test which did the trick.

I've found out too, that if you run Firefox, ajax-laden web pages (like Zimbra, gmail), and flash (esp. YouTube) -- you really need adequate swap no matter how much RAM you have.

---

### Post by grumpymole on 2007-06-13
I read the whole thread and tried all the advice offered - nothing really worked.  Until I upgraded to Gutsy and a new kernel.

Now my machine has stopped freezing.

---

### Post by loumsmith on 2007-06-13
I was trouble free with fiesty.  This past week it started to freeze.  It will freeze at the login screen.  It will freeze when I am logged in.  Sometimes things are fine for a few minutes.  Sometimes it won't crash for hours.  I have used Ubuntu for 6 months without any problems and no hardware changes.  I am wondering if any of the updates have caused the problems.
Louis

---

### Post by weirdguille on 2007-06-13
[COLOR="DarkGreen"]Hi.  I'm having the same problem.

On Saturday I decided to move from Slack to Ubuntu, so I did it.  I installed my old Dapper CD, and then upgraded it all the way to Feisty.  Then I got my first freeze, while installing stuff from synaptic (after installing my graphics restricted driver from the system/restricted drivers menu, and then by the .run at the ati website, an ATI Radeon Xpress 200).  Given that I did not know that I had to wait, I restarted my computer, which caused my GDM to crash (more info here: [http://ubuntuforums.org/showthread.php?t=471228](http://ubuntuforums.org/showthread.php?t=471228)).

So, I downloaded the Feisty iso, and installed it today.  I've been having freezes for hours now (and they have occupied even 5 minutes), both in the login as while using the OS.  It does not matter if I'm connected to the network or not.  I've also had those while being only on the desktop.  And, what seems even more... weird, lets call it, is that I've even had that error while running the Feisty LiveCD (while installing, actually).

I used Dapper for about 6 months (at college, with my LiveCD)... until they found out and prohibited me to use it XD, and it never froze.  I've also been using Puppy Linux these few days, along with SysRescCD for the NTFS tools, and have not had that problem.

I have not installed the ATI driver yet, and still have the freezes.

I just red the entire tread (hell, it took me about 3 hours and about 3 or 4 freezes), and have already applied the Kernel downgrade (to the 15-386 one)... and when I rebooted it did not wait even 10 seconds to freeze.  Right now I've applied the noapic solution, but have not restarted yet.  Lets hope it fixes my pc.  If it does not... I'll either go back to Slack or Dapper... T_T.

When the system is not pwnd, it works well with heavy processes (I'm running VideoLAN, and reading both music and videos from NTFS partitions).

**My PC specs are:**
Intel Pentium D (2.2 GHz, I think).
512 RAM
SATA HDD (160 GB, several partitions).
Dual boot from Windows (who died from that virus that automatically closes your session when you open it)
ATI Xpress 200 Motherboard (that is, ATI Radeon Xpress 200, 128 MB, integrated graphic card).
LG DVD RW (ATA)
Caviar ATA HDD (80 GB, 3 partitions, not used as bootable).

I hope the problem gets fixed soon, and that my post helped someone... I mean, at least to document what's going on.

EDIT: Oh, yeah, I forgot... even if I have a CD or DVD in the rom, it still freezes.[/COLOR]

---

### Post by gregfulkerson on 2007-06-14
I started running into this problem as well. I scanned the internet for answers and nothing gave me this idea, but it worked. I had two hard drives installed and the freeze occurred during the partition scan. To get around this, I removed one of the hard disks and the installation went smoothly. Just 2 cents worth of experience that may or may not be of use. 

Peace

---

### Post by dannyboy79 on 2007-06-14
> **weirdguille said:**
> [COLOR="DarkGreen"]Hi.  I'm having the same problem.

On Saturday I decided to move from Slack to Ubuntu, so I did it.  I installed my old Dapper CD, and then upgraded it all the way to Feisty.  Then I got my first freeze, while installing stuff from synaptic (after installing my graphics restricted driver from the system/restricted drivers menu, and then by the .run at the ati website, an ATI Radeon Xpress 200).  Given that I did not know that I had to wait, I restarted my computer, which caused my GDM to crash (more info here: [http://ubuntuforums.org/showthread.php?t=471228](http://ubuntuforums.org/showthread.php?t=471228)).

So, I downloaded the Feisty iso, and installed it today.  I've been having freezes for hours now (and they have occupied even 5 minutes), both in the login as while using the OS.  It does not matter if I'm connected to the network or not.  I've also had those while being only on the desktop.  And, what seems even more... weird, lets call it, is that I've even had that error while running the Feisty LiveCD (while installing, actually).

I used Dapper for about 6 months (at college, with my LiveCD)... until they found out and prohibited me to use it XD, and it never froze.  I've also been using Puppy Linux these few days, along with SysRescCD for the NTFS tools, and have not had that problem.

I have not installed the ATI driver yet, and still have the freezes.

I just red the entire tread (hell, it took me about 3 hours and about 3 or 4 freezes), and have already applied the Kernel downgrade (to the 15-386 one)... and when I rebooted it did not wait even 10 seconds to freeze.  Right now I've applied the noapic solution, but have not restarted yet.  Lets hope it fixes my pc.  If it does not... I'll either go back to Slack or Dapper... T_T.

When the system is not pwnd, it works well with heavy processes (I'm running VideoLAN, and reading both music and videos from NTFS partitions).

**My PC specs are:**
Intel Pentium D (2.2 GHz, I think).
512 RAM
SATA HDD (160 GB, several partitions).
Dual boot from Windows (who died from that virus that automatically closes your session when you open it)
ATI Xpress 200 Motherboard (that is, ATI Radeon Xpress 200, 128 MB, integrated graphic card).
LG DVD RW (ATA)
Caviar ATA HDD (80 GB, 3 partitions, not used as bootable).

I hope the problem gets fixed soon, and that my post helped someone... I mean, at least to document what's going on.

EDIT: Oh, yeah, I forgot... even if I have a CD or DVD in the rom, it still freezes.[/COLOR]

if you have a laptop and have more than 1 wirleess card, maybe 1 built in and the other a usb or pcmcia, make sure your blacklist the modules that are being loaded for the card you;re not using, or disable it in bios, or remove it. Also, do you have latest bios? do you see any error's in your dmesg? /var/log/syslog? /var/log/kern.log? gutsy has been a saviour for some, if you have a dual boot and cvan always count on getting required stuff done in windows, give Gutsy Tribe 1 a run for it's money!!
here's the link for iso's and torrent's: [http://cdimage.ubuntu.com/releases/gutsy/tribe-1/?C=N;O=D](http://cdimage.ubuntu.com/releases/gutsy/tribe-1/?C=N;O=D)

---

### Post by weirdguille on 2007-06-14
> **dannyboy79 said:**
> if you have a laptop and have more than 1 wirleess card, maybe 1 built in and the other a usb or pcmcia, make sure your blacklist the modules that are being loaded for the card you;re not using, or disable it in bios, or remove it. Also, do you have latest bios? do you see any error's in your dmesg? /var/log/syslog? /var/log/kern.log? gutsy has been a saviour for some, if you have a dual boot and cvan always count on getting required stuff done in windows, give Gutsy Tribe 1 a run for it's money!!
here's the link for iso's and torrent's: [http://cdimage.ubuntu.com/releases/gutsy/tribe-1/?C=N;O=D](http://cdimage.ubuntu.com/releases/gutsy/tribe-1/?C=N;O=D)
[COLOR="DarkGreen"]I do have a laptop... but it is not the one giving me the problem (XD).  I'm talking about my desktop.

I've have not had a problem since I changed the kernel, so I don't think the log would give me errors.

As well... wasn't Gutsy the next release?  The one scheduled for September?  So... upgrading to Gutsy wouldn't be installing a beta, or something like that?... I'm  just not sure.  Would you explain it to me?

Oh, yeah, and I'm going to install the .run for my graphic card (because I use my computer for playing Ragnarok, browsing, programming (python, MySQL and blender) and watching animé... and its lack does not let me play, use blender, and my animé looks all pixelated...

So I'll install it and get back to you.[/COLOR]

---

### Post by dannyboy79 on 2007-06-14
yes, Gutsy is the next release and is currently in Development and SHOULD NOT BE USED FOR PRODUCTION MACHINES. I was merely suggesting you try it if your machine is just for whatever and if it breaks during Gutsy updates or whatnot, that it wouldn't be a big deal.

For your graphic issues, I am guessing that you need to use Proprietary drivers so that you get accelerated graphics, openGL, or whatever if you want to use Blender. Not sure how ATI drivers are as I use Nvidia. If you're kind of new and not sure about the whole graphics card thing and linux drivers, maybe check out Envy. IT's a program that will download the driver for you and install based on the card you have.

---

### Post by weirdguille on 2007-06-14
[COLOR="DarkGreen"]No, no.  You see... I have the driver (downloaded from the ati website), and have already installed it (it gives me even more resolution than Windows... I'm at 800x600 now Y_Y), but last time I installed it, my computer broke, XD, and given that a lot of the messages in the tread have been about the proprietary... but I'm going to try installing it and get back here if a problem arises.[/COLOR]

---

### Post by dannyboy79 on 2007-06-14
> **weirdguille said:**
> [COLOR="DarkGreen"]No, no.  You see... I have the driver (downloaded from the ati website), and have already installed it (it gives me even more resolution than Windows... I'm at 800x600 now Y_Y), but last time I installed it, my computer broke, XD, and given that a lot of the messages in the tread have been about the proprietary... but I'm going to try installing it and get back here if a problem arises.[/COLOR]

i am not sure whay you keep mentioning XD, are we suppose to know what that means? good luck with whatever you're trying to do.....

---

### Post by rplantz on 2007-06-14
> **dannyboy79 said:**
> i am not sure whay you keep mentioning XD, are we suppose to know what that means? good luck with whatever you're trying to do.....

Yeah, I was wondering about that myself. So I did some searching and came up with> XD (used to represent laughing) supposedly became popular on the internet shortly after it was used in the television show, South Park, usually explained to the unknowing as the emoticon being akin to the animation method used when a character was laughing so hard they had their eyes closed (a sideways X for their eyes).
from [http://en.wikipedia.org/wiki/Emoticon](http://en.wikipedia.org/wiki/Emoticon). This is the first time I've seen it.

---

### Post by weirdguille on 2007-06-14
[COLOR="DarkGreen"]Indeed, XD means laugh, or "I laugh right in this spot".  It's pretty used over the internets.
And... well, sadly, after several hours of peace, now I've had 2 freezes (one while having only the "add wallpaper" and a nautilus window open) and one right now, while having only FF open.  And they have not been benevolent ones.  They've taken about 10 minutes each to snap out.
Too bad... I guess I'll go back to Dapper until the problem is solved...
EDIT: Ignore what I just said.  Now it's been 3 times (third while looking at a youtube video).  So I'm writing from my sister's computer while loading the Dapper CD on mine T_T[/COLOR]

---

### Post by Jack H on 2007-06-14
Just a note -- I did not read all the posts on this subject, but was glad to see it is not just me with the problem  My solution?  I have both Gnome and KDE installed with 7.04 and the KDE has been running for at least a day and a half with no problems.  I will lie low on Gnome usage until the problem is resolved.     Jack  H

---

### Post by dannyboy79 on 2007-06-15
> **Jack H said:**
> Just a note -- I did not read all the posts on this subject, but was glad to see it is not just me with the problem  My solution?  I have both Gnome and KDE installed with 7.04 and the KDE has been running for at least a day and a half with no problems.  I will lie low on Gnome usage until the problem is resolved.     Jack  H

I am sure the community would appreciate it if you DID run gnome, than maybe we can nail this issue down to a cause. it sounds like, IF what you say is true, it may be gnome libraries confliction issue causing the freezes for YOU at least. I wonder how you would debug this then if you get freezes in gnome but not imn kde?

---

### Post by dawdler on 2007-06-15
Just wanted to point out something that may be interesting...

On my home machine where I am running ubuntu feisty as my OS, I also sporadically get the freezes people have been describing.  At work, I am running ubuntu feisty as a virtual machine and have not run into the freeze up problem.

My home machine is using the ATI x700 card with the flgrx driver and a netgear wireless card.  I can get more details if necessary.  This issue is a pain in my bun-tu and wish to get to the bottom of it!

---

### Post by Jack H on 2007-06-15
> **dannyboy79 said:**
> I am sure the community would appreciate it if you DID run gnome, than maybe we can nail this issue down to a cause. it sounds like, IF what you say is true, it may be gnome libraries confliction issue causing the freezes for YOU at least. I wonder how you would debug this then if you get freezes in gnome but not imn kde?
     Well . . . All I know is the kDE is still up and running with NO problem.  The Gnome was quickly becoming unusable here.  I do not know the source of the problem but it appears isolated to the Gnome desktop in this machine.  There are 5 recent updates I downloaded a few hours ago but will not have the time to see if there is a fix in them for the problem until tomorrow some time.   Jack H

---

### Post by Digitallysick on 2007-06-15
I can run sabayon from the live dvd, with beryl and xgl and it doesnt freeze, i can run it for days. so this tells me it cant be a hardware problem, *points finger at beryl/ubuntu conflict* ubuntu runs fine with beryl off, so it has to be some type of conflict

---

### Post by cmost on 2007-06-16
> **dawdler said:**
> Just wanted to point out something that may be interesting...

On my home machine where I am running ubuntu feisty as my OS, I also sporadically get the freezes people have been describing.  At work, I am running ubuntu feisty as a virtual machine and have not run into the freeze up problem.

My home machine is using the ATI x700 card with the flgrx driver and a netgear wireless card.  I can get more details if necessary.  This issue is a pain in my bun-tu and wish to get to the bottom of it!

My Feisty x86-64 bit OS randomly freezes on a regular basis and it's driving me insane.  In my case, it's definitely related to disk usage.  If I have a disk intensive process running (i.e., a virtual machine running in VMware, or decompressing a large tarball,) or if I have several processes accessing the disk at the same time then the machine simply freezes up.  I have to hit the reset button to reboot.  My hardware is fairly new and I didn't have this problem until I upgraded to Feisty.  By the way, I have a nVidia graphics board and no wireless card.  That should shoot down the theory that the ATI driver is causing the problems, or the wireless.  If Canonical and Ubuntu devs think people are willing to put up with something like this they're nuts.  We might as well run Windows!  I'd be interested in knowing the percentage of Ubuntu users running Feisty who are having this random freezing problem.  In the meantime, I'm searching for a new distribution.

---

### Post by johanPO on 2007-06-16
Cmost, you are right. There is no reason to put up with this. You can easily go for another distribution. I worked my way through a few. The ones that are not Ubuntu based, did not cause any crashes.

Strangely enough, I did have a complete crash of my system using SUSE. I could not even make it into the BIOS: In the process of figuring out what went wrong, I replaced both MB and CPU. I used to have a ASUS P5NSLI with the Nvidia NForce 570 chip set. On the new one I have a Intel 965 chipset. Just as a test I decided to go back and try Ubuntu again, and to my surprise it is now stable. I have the same graphics card, and the same WLAN card etc. For me that looks like it has something to do with the MB or more likely with the drivers for the MB:

Maybe I should add that after a while my system started to freeze again. It took longer then before but it sill did on some occasions. So I installed PCLinuxOS2007 and now it is stabile

---

### Post by rplantz on 2007-06-16
> **cmost said:**
> My Feisty x86-64 bit OS randomly freezes on a regular basis and it's driving me insane.  In my case, it's definitely related to disk usage.  If I have a disk intensive process running (i.e., a virtual machine running in VMware, or decompressing a large tarball,) or if I have several processes accessing the disk at the same time then the machine simply freezes up.  I have to hit the reset button to reboot.  My hardware is fairly new and I didn't have this problem until I upgraded to Feisty.  By the way, I have a nVidia graphics board and no wireless card.  That should shoot down the theory that the ATI driver is causing the problems, or the wireless.  If Canonical and Ubuntu devs think people are willing to put up with something like this they're nuts.  We might as well run Windows!  I'd be interested in knowing the percentage of Ubuntu users running Feisty who are having this random freezing problem.  In the meantime, I'm searching for a new distribution.

As you can see from my signature, my hardware is similar, but a notch older. I have deleted all the "fixes" suggested in this thread. I have a "standard" menu.lst. My system has been stable since I stopped playing around with beryl and compiz. Since the last time I "fixed" my machine (search this thread for my weird technique) I have simply stayed away from them and my system has been stable. I'm running the 1.0-9755 nvidia driver from the repositories.

I know what you mean about other distributions. One person in this thread reports having good luck with Gutsy. It seems that the developers should know what has changed from Feisty to Gutsy, and that should help them find a solution for Feisty. On the other hand, perhaps very few of us are affected by this rather maddening problem.

Meanwhile, I have installed FreeBSD and downloaded Solaris.

---

### Post by MrShmoo on 2007-06-17
Just wanted to reply to say that this seems to be the exact bug that is plaguing me. Unfortunately none of the solutions in this thread have seemed to help (changing kernels, noapic/nolapic, etc.).

My hardware:

-ABIT IS-7 Motherboard
-P4 2.6 Ghz (tried hyperthreading on and off)
-1024 MB RAM (memtest checks out...)
-ATI Radeon 9700 Pro (strangely with the fglrx drivers I can move the mouse, nothing responds. with the default 'ati' drivers I can't even do that)
-Soundblaster Audigy 2

For my network I am using the onboard wired ethernet of my motherboard.

I am running a dual-boot with Win XP on the same partition and have xorg.conf setup for my two monitors.

---

### Post by Digitallysick on 2007-06-17
I also have an abit fatal1ty lga775 motherboard, humm

---

### Post by suoko on 2007-06-17
I'm quite fed up of random pauses of feisty too.
I'm going to upgrade to gutsy and see if it's got the same problem and if it's stable enough.
Otherwise I'll say bye bye ubuntu and welcome back debian.

---

### Post by t.rei on 2007-06-18
Now this is a long long thread, and I've worked through about every hint there was in here.

The only thing getting my System to be so stable I cannot remember a lockup (been fokussing on work, when not toying around with the system) is, when I **do not use beryl**. Not using composite extensions to be exact. 

Since this is actually a feature I enjoy having (eyecandy! wheee) because the Userinterface is the part of the system I am continually confronted with, I would like to see it working. Stable that is. 

Since it locks using Beryl and else it doesn't - I guess the Problem lies somewhere within the usage of those extensions?

Anyone have a clue about what exactly it might be? Maybe we all just need to disable a part of the functionality. ;)

---

### Post by thomasaaron on 2007-06-18
Check to see if there is a more recent BIOS version for your motherboard. If so, flash it and see if that helps.

---

### Post by dannyboy79 on 2007-06-18
> **Digitallysick said:**
> I can run sabayon from the live dvd, with beryl and xgl and it doesnt freeze, i can run it for days. so this tells me it cant be a hardware problem, *points finger at beryl/ubuntu conflict* ubuntu runs fine with beryl off, so it has to be some type of conflict

this statement is not true. when running from the livecd you're not accessing the disk like you would be when it's installed to the hard drive. Many people have problems with jmicron controller built onto many motherboards. Also, i can't say for sure but since it's strickly running from memory and the livecd, I don't know if all the neccessary libraries are loaded like they would when you install to hard disk.

---

### Post by dannyboy79 on 2007-06-18
> **t.rei said:**
> Now this is a long long thread, and I've worked through about every hint there was in here.

The only thing getting my System to be so stable I cannot remember a lockup (been fokussing on work, when not toying around with the system) is, when I **do not use beryl**. Not using composite extensions to be exact. 

Since this is actually a feature I enjoy having (eyecandy! wheee) because the Userinterface is the part of the system I am continually confronted with, I would like to see it working. Stable that is. 

Since it locks using Beryl and else it doesn't - I guess the Problem lies somewhere within the usage of those extensions?

Anyone have a clue about what exactly it might be? Maybe we all just need to disable a part of the functionality. ;)

beryl is still VERY buggy, I would suggest if you want composition, you should try out Desktop Effects, it's way more stable hence the reason Ubuntu included by default over Beryl. I use it when I am not using my Dual Display setup and it's stable as a rock! I have the nvidia 9755 and a Nvidia GeForce 6200 128mb ram AGP8x card.

---

### Post by t.rei on 2007-06-20
So, I'm going to give compiz a run. See if it's stable. Although many of the nice features included in beryl are missing, it's still has at least transparency, wich I am really fond of right now.

---

### Post by dannyboy79 on 2007-06-20
> **t.rei said:**
> So, I'm going to give compiz a run. See if it's stable. Although many of the nice features included in beryl are missing, it's still has at least transparency, wich I am really fond of right now.

you can install gnome-compiz-manager for extra modifications to compiz settings.

---

### Post by HoMe_CaNiBaL on 2007-06-20
hi there.

in ubuntu if i'm running beryl + firefox + thunderbird + gaim + second life + etc the computer freezes..

yesterday, i install kubuntu, and with everything working, i havent 1 freeze... i think that maybe a problem with gnome...but i dont like kde... how can install gnome package? from gnome to kde i have to install kde-base, and to gnome?to test if i have problems...

i say that because, i test (when i have ubuntu) i install kde base package, and the computer freezes, but now my computer is stable, if i install gnome maybe can be stable, because i dont like kde, but its stable for now...

[[]]

---

### Post by dannyboy79 on 2007-06-20
sudo aptitude install gnome-desktop
should grab all the dependencies and install them. then when you restart, just make sure you chose your desktop manager you want to use.

---

### Post by t.rei on 2007-06-20
Ok, now I've had only a single lockup on gnome running compiz after a complete day of work. Strangly the crash came on a dropdown-box when I wanted to zip my work-of-the-day. Now, this seems somehow familiar. It's quite often something like a dropdown-box, isn't it.

Ok, one lockup a day is still one too many for my taste but a nice change from 1 lockup every 15 Minutes or so. 

So, compiz crashed less then beryl. It probably really is some nasty code Problem in one of those extensions or maybe in some part between the Driver, the X and the UI?

I shure hope this HUGE thread gets noticed by someone with alot more clue about this than me. :)

I tried KDE btw, didn't like it too much although its really a sharp desktop. Crashes too, as soon as composites come into play, though.

Anyone an Idea? Wobbly is turned off on my machine... just Cube and transparency and those are such basic and old old extensions... Would be weird if they case the error. Maybe its something about blending in stuff? Like dropdown-Menu's. Hmmm...

Could someone point me to the source packages of the extensions? Might want to take a look (although... whats up with this compiz/beryl merger?)

---

### Post by HoMe_CaNiBaL on 2007-06-20
well, i think i find a way to pass freezes..

with kubuntu i dont have any freeze, with beryl on,playing secondlife, windows xp running virtually, thunderbird etc etc, and i install gnome package, and still no freezes... so i think i solve my problem.

[[]]

---

### Post by Digitallysick on 2007-06-20
even just useing desktop effects in feisty fawn freezes me up, grr, *gives up* for now.

---

### Post by mayamaniac on 2007-06-22
I recently experienced this freezing after a system update. I narrowed it down to the nvidia driver that's affecting it. I uninstalled the the nvidia driver and it no longer freezes, but then I don' t have the benefits of the nvidia features such as 3D acceleration. To make matters worse, now I can't get the the nvidia driver using Envy to work. I always get an X server failed to load error, something about nvidiaact1 failing. I think something in the recent linux kernal updates is the culprit here. I have a backup of feisty when everything was working, I may have to restore the backtup unless this problem is fixed by some other means.

Didn't read through 40 pages of posts, but is there a solution to fix this freezing?

---

### Post by Digitallysick on 2007-06-22
got the new nvidia driver today and installed it, i have beryl on, the count down to freezing begins, *crosses fingers* 

[http://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)

Lets see how long i make it

---

### Post by jrev on 2007-06-23
I just installed ubuntu feisty fawn on my wife's computer :
She has had no problem with thunderbird getting & sending her mail but the game freecell has already frozen solid twice and there is only the reset button to restart the computer !

Is there config magic working on that bug ?

---

### Post by aristotlewilde on 2007-06-23
I installed Feisty on an older Thinkpad (T22) on Thursday.  I have experienced several freezes as well (to the point where there isn't even any mouse movement and a power down is required.

I too thought it was Firefox related, so I switched to Epiphany.  I handed it to my wife to surf the web tonight and thought I was out of the woods, but after about 90 minutes, it froze.  

This is an older machine, so I am going to try downgrading to Edgy or Dapper.

---

### Post by vinnn on 2007-06-25
I have suffered from this problem, seems that there could be a problem in relation to the proprietory Nvidia driver (which I installed from the package manager), I have a 7600 GS PCIe 512MB card.
Once I disabled the Nvidia driver and used the open source nv graphics driver with the original stock xorg.conf, all is rock solid. Only problem is that I have to switch back to play games or run Google Earth, neither of which I spent a great deal of time doing.

The 'lock up' doesn't lock the system though, just X (the keyboard, mouse & display). I'm still able to ssh into the system from my laptop and look at the syslogs which when the problem occurs goes something like this...
```
[ 3930.482518] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba3
[ 3938.466056] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba4
[ 3939.464008] NVRM: Xid (0001:00): 8, Channel 00000000
[ 3946.453560] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba5
[ 3947.451507] NVRM: Xid (0001:00): 8, Channel 0000001e
[ 3954.441077] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba6
[ 3955.439031] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3962.424600] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba7
[ 3963.422547] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3970.408134] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba8
[ 3971.406081] NVRM: Xid (0001:00): 8, Channel 0000001e
[ 3978.395657] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071ba9
[ 3979.393604] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3986.379148] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071baa
[ 3987.377112] NVRM: Xid (0001:00): 8, Channel 00000020
[ 3994.362701] NVRM: Xid (0001:00): 16, Head 00000000 Count 00071bab
```

I haven't got any further than that with the problem so far due to lack of time but this issue only cropped up since going from Edgy to Feisty.

Those of you who have this problem, do you have Nvidia GPUs by any chance?

---

### Post by DjBeck on 2007-06-25
I also have these irritating problems in Feisty ... what really annoys me is that it freezes randomly, and it's different every time;

Sometimes everything hangs, just like someone had taken a screenshot and zoomed it to full screen, and I can still move the mouse around. The system wont react to any i/o though.

The other version is kind of the same as above, with the difference of not being able to move the mouse.

The third one is similar to both the others, but with this one there're a lot of vertical white lines all over the screen.

I've tried loads of different theories from this thread, but nothing has solved my problem ...

The previous version of the kernel - same problem.
Running Kde / Xfce / Fluxbox instead of Gnome - same problem.
Adding the additional options to the boot menu - same problem.
Removed Beryl - no difference.

and so on ...

The only possible explanation I can see that's left, would be if it had something to do with my wireless network card ... 

Well, it looks like there are quite many with the same problem (same symptoms anyway) so hopefully there'll be a solution to it in the near future.

---

### Post by Digitallysick on 2007-06-25
The latest nvidia driver, i can almost safely say has corrected my beryl freeze! I Started this thread wayyyy long ago, it seems whatever they fixed corrected the problem finally. I have ran it for many days now without a freeze.

---

### Post by Darkhack on 2007-06-25
The two main reasons fiesty freezes are because of graphics cards as you guys have talked about and powernowd.  In powernowd there is a bug in it that will lock up some machines but it wasn't caught until after it was released and to my knowledge there still isn't a patch for it.  Most of the time, both the ATI and Nvidia proprietary graphics drivers can be fixed by altering certain settings in xorg.conf.  The only solution to the powernowd bug is to simply uninstall it.

---

### Post by dawdler on 2007-06-26
I installed the kubuntu desktop on my ubuntu image and ran a session using kdm.  My machine still froze.  I will try updating my fglrx ati driver to the latest and see what happens.  Has anyone tried Darkhack's proposed thought and solution?

In the meantime here is some info on my P4 machine:

```

00:00.0 Host bridge: Intel Corporation E7220/E7221 Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation E7220/E7221 PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] Secondary
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
04:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
04:01.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

---

### Post by krishna_ggk on 2007-06-26
> **Darkhack said:**
> The two main reasons fiesty freezes are because of graphics cards as you guys have talked about and powernowd.  In powernowd there is a bug in it that will lock up some machines but it wasn't caught until after it was released and to my knowledge there still isn't a patch for it.  Most of the time, both the ATI and Nvidia proprietary graphics drivers can be fixed by altering certain settings in xorg.conf.  The only solution to the powernowd bug is to simply uninstall it.

Hey , looks like my problem is solved. No lockups till now after random logins for random time intervals. Hope this continues.
BTW do i need that package. I am using kubuntu-feisty on a desktop pc (3GHz, 1GB ram, ATI-xpress 200M video card)

Thanks a lot Darkhack :)

---

### Post by dawdler on 2007-06-26
how did you fix the issue, krishna_ggk?

did you uninstall the powernowd package, tweak the xorg.conf file, or updated your graphics driver?

---

### Post by krishna_ggk on 2007-06-26
> **dawdler said:**
> how did you fix the issue, krishna_ggk?

did you uninstall the powernowd package, tweak the xorg.conf file, or updated your graphics driver?

I uninstalled powernowd which fortunately hasn't locked my systemyet.
BTW i had added noacpi and other kernel parameters specified here but they didn't work. Even now i haven't reverted menu.lst file. I'll do that and test.

---

### Post by DjBeck on 2007-06-26
Yey, disabling powernowd (adding "exit 0" to the config) seems to have solved my problem too ... my system's been stable for like 7 straight hours now. Thanks for the suggestion Darkhack!

---

### Post by sdouble on 2007-06-26
ComputerA = running Ubuntu 7.04
ComputerB = freezing up during the livecd

ComputerA has been running for nearly a week with no problems.   

ComputerA Specs:
 Athlon XP 1900+
 ECS N2U400 motherboard using onboard sound and ethernet
 32 MB Nvidia GeForce 2 MX 400
 1 GB DDR
 40 GB ATA

I was attempting to install Kubuntu on ComputerB but it was freezing up.  I decided to just install from the same disc I used on the other computer.  Wrong.  Also freezes during the livecd.  Sometimes while it's loading, sometimes during the install.

ComputerB specs:
Athlon 64 3000+
2 GB DDR
128 MB ATI 9800 Pro
Soundblaster 5.1
160 GB SATA

I have enjoyed the use of ComputerA as a trial run and decided to toss Windows entirely.  Went through and made a bunch of backups and got all ready to go just to find I couldn't get it installed.  Is there something in my hardware that might be causing this?  Or is this just the same issue everyone else seems to be having?

Thanks!

---

### Post by siddthekidd on 2007-06-27
I had the same problem until I installed Dapper, then upgraded it to Edgy and then Feisty. Feisty does not freeze anymore.

---

### Post by DjBeck on 2007-06-27
> **DjBeck said:**
> Yey, disabling powernowd (adding "exit 0" to the config) seems to have solved my problem too ... my system's been stable for like 7 straight hours now. Thanks for the suggestion Darkhack!

Crap. My system just froze when attempting to burn a dvd ... well, at least the powernowd option has increased the time gaps between the freezes ... Guess the only explanation left then is the Nvidia driver ...

---

### Post by rplantz on 2007-06-27
My system ran fine for two weeks. Then I got adventurous and enabled desktop effects, thus turning on compiz. The freezing began. I disabled desktop effects. Still got freezing. I booted into my gutsy installation. While trying to update, it froze. Finally, I went back to my usual method of "fixing" things. I shut down, opened the case and poked around for a while, moving wires, etc. Now all seems to be okay (1/2 day).

Sigh.

---

### Post by buckmaster60 on 2007-06-27
Wanted to shed another angle - I am also locking up.  I have a IBM T43 with a ATI x300 card.  When I locked up - mouse freeze, could not access alternate terminal to perform a graceful reboot, the only way out was to power cycle the laptop.  I tried something on the next lockup just to see if it helped - I ejected my wireless card from the laptop "Ubiquiti SRC 300" and I got my computer to respond!  I've tried the following to fix the card using madwifi-ng drivers.

1.  Found on [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
       Find the following section: IconExample48.png
        include memory 0xc0000-0xfffff
        include memory 0xa0000000-0xa0ffffff
        include memory 0x60000000-0x60ffffff
        Change it to look like this:
    *
        include memory 0xd0000-0xdffff
        include memory 0xc0000-0xcffff
        include memory 0xc8000-0xcffff
        include memory 0xd8000-0xdffff

DID NOT HELP

2.  Tried loading the madwifi drivers with information from another post "http://ubuntuforums.org/showthread.php?t=480778&highlight=ar5212"  like so:        

Turn the minipci device ON via the bios.
Unistall ndiswrapper via Synaptic (choose remove completely).
Uninstall network-manager via Synaptic. (choose remove completely)
Uninstall restricted-modules madwifi.
Verify the ath is not blacklisted.
Remove the pcmcia card.
Connect by wire.
Open a root terminal and do:
Code:

ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
cd /usr/src
apt-get install build-essential
apt-get install linux-headers-`uname -r`
apt-get install subversion
svn checkout [http://svn.madwifi.org/trunk/](http://svn.madwifi.org/trunk/) madwifi-ng
wget [http://patches.aircrack-ng.org/madwifi-ng-r2277.patch](http://patches.aircrack-ng.org/madwifi-ng-r2277.patch)
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci

Stick in the pcmcia card & do:
iwconfig
You should see ath0 & ath1

DID NOT HELP!

By the way if I just use my wired connection I never freeze.

At this point I have no clue how to fix the issue.

Any help is appreciated.

---

### Post by t.rei on 2007-06-28
> **DjBeck said:**
>  Guess the only explanation left then is the Nvidia driver ...


Well, I'm having the same lockups but using the radeon driver and AIGLX. Actually I'm rather positive that there is some flaw in some effect or some extension...

---

### Post by jrev on 2007-06-28
HI all,
I installed the official feisty release a couple of weeks ago on one of my PC which was working OK since the start of the Dapper (more than a year ago)

This PC is now freezing solid, (keyboard & mouse) roughly once every other day  usually when my wife is playing card :freecell, aunt mary or majong.

The screen stays on unaltered...

After I switch off the power, on the next boot I have a long stop at :
grub loading, please wait.

then I got a black screen for a long time before the PC starts its proper booting 

I can see some info : file system not clean ...

Can you give me a hint  to trace the defect on this new version ? Or is it a bug that will be corrected in the near future ?

I would prefer not to go back to the excellent Dapper Drake

---

### Post by krishna_ggk on 2007-06-28
Well i dont know how but _uninstalling powenowd hasn't froze my systime till now_ :).
I'd like to inform that i use my computer for about 4-5 hours a day, **shut it down** and my sister again boots sometime of day, uses for couple of hours and **shutdown**(ofcourse both boot to linux). So i havent really tested my system with more than 6hrs uptime.

BTW i use kubuntu, may be this also is one of the reason for that powernowd suggestion to work for me.

---

### Post by DjBeck on 2007-06-29
> **krishna_ggk said:**
> Well i dont know how but _uninstalling powenowd hasn't froze my systime till now_ :).
I'd like to inform that i use my computer for about 4-5 hours a day, **shut it down** and my sister again boots sometime of day, uses for couple of hours and **shutdown**(ofcourse both boot to linux). So i havent really tested my system with more than 6hrs uptime.

BTW i use kubuntu, may be this also is one of the reason for that powernowd suggestion to work for me.

That sounds like a logical explanation ... My computer's on  24/7 (is supposed to anyway), and now usually freezes every 24-36 hours.

It'd be interesting to see how long your system would actually run ... just for comparison :)

---

### Post by dawdler on 2007-06-29
I uninstalled the powernowd package, and I still get the random freezes.

I have a new issue now where on top of random freezes, one of two montiors will at random times lose signal from the machine.  (I am running dual screen mode)

---

### Post by DjBeck on 2007-06-29
Update. I'm gettin' ******* tired of this ... ****, windows's more stable than this ... I'll seriously consider what OS to run, but as for now Feisty is way to unstable ....I think I'm going back to Debian until this is solved ... 

this is not cool

---

### Post by joe.turion64x2 on 2007-06-30
> **DjBeck said:**
> Update. I'm gettin' ******* tired of this ... ****, windows's more stable than this ... I'll seriously consider what OS to run, but as for now Feisty is way to unstable ....I think I'm going back to Debian until this is solved ... 

this is not cool
Have you tried other Linux distributions? Perhaps Ubuntu is not the one for your PC. By the way Fedora 7 is really cool, provided you don't have an ATI card (ATI support is delayed because of a very latest Xorg version).

---

### Post by jrev on 2007-06-30
Yes I tried Ubuntu Dapper Drake 6.06 and It works perfectly on my three computers.

The version to replace it is not yet born ...:D

---

### Post by sparky64 on 2007-06-30
So far so good.
Have uninstalled powenowd and used nvidias latest driver(man install) and so far have had no freeze.
Ran for 6 hours last night with no probs, Touch wood for the rest of the day.
Oh even beryl (on kde) is running perfect.=D>

---

### Post by OutCell on 2007-06-30
The only thing that stopped Ubuntu Feisty freezes for me was disabling desktop effects :( i really loved the desktop effects

---

### Post by MaDRaY on 2007-06-30
Its crashing like hell on me. My mouse freezes and I cant even move anything. I have to do a hardware restart. 

My Specs are: 250Gb Maxtor SATA HD, GeForce 6600GT (Nvidia Drivers Installed), Asus A8N-Sli Deluxe (Latest Bios installed), Athlon 64 3200 and 1Gb of RAM (1x Corsair module). Using Feisty 32bits.

Sometimes it crashes like in 2 minutes, sometimes 10 minutes, max that I had it without a single crash on me was 50 minutes. Will try OpenSUSE now. I really really wanna to get in the Linux world!:(

---

### Post by krishna_ggk on 2007-06-30
I ran my system for about 30 hours and it never crashed. Uninstalling powernodwd seems to have solved my problem. 
Probably the problem with others(with ati/nvidia) has to do with ubuntu since i use kubuntu.
Why don't you try kubuntu and then install gnome desktop?

---

### Post by joe.turion64x2 on 2007-07-01
> **krishna_ggk said:**
> I ran my system for about 30 hours and it never crashed. Uninstalling powernodwd seems to have solved my problem. 
Probably the problem with others(with ati/nvidia) has to do with ubuntu since i use kubuntu.
Why don't you try kubuntu and then install gnome desktop?
Or try a different distro altogether. Once installed through Synaptic, GNOME is darn fast (even faster the Feisty's), in PCLinuxOS 2007, and almost everything is supported out of the box.

---

### Post by johanPO on 2007-07-03
I can confirm that PCLinuxOS2007 is a very stable and good distribution. I am going to stick with it for a while. If it has one drawback then it is that there are less packages available. For most users I am sure this is not going to be a problem though.

I have tried a few others

1. Sabayon. Everything is there, but once you start upgrading your system (compiling for a few days) you are likely to get into problems. With Sabayon, everything was set up correctly. I had Berryl set up and working. Very stabile
2. Fedora 7. Good but if you have an ATI graphics card, I did not manage that. Also the drivers for my WLAN card was not included (PRISM54). Very Stabile
3. SUSE. Somehow I did not like it............ and the PRISM54 driver was not available on the installation. Very Stabile
4. Mepis and LinuxMint, same stability issues as Ubuntu..

---

### Post by joe.turion64x2 on 2007-07-03
> **johanPO said:**
> I can confirm that PCLinuxOS2007 is a very stable and good distribution. I am going to stick with it for a while. If it has one drawback then it is that there are less packages available. For most users I am sure this is not going to be a problem though.

I have tried a few others

1. Sabayon. Everything is there, but once you start upgrading your system (compiling for a few days) you are likely to get into problems. With Sabayon, everything was set up correctly. I had Berryl set up and working. Very stabile
2. Fedora 7. Good but if you have an ATI graphics card, I did not manage that. Also the drivers for my WLAN card was not included (PRISM54). Very Stabile
3. SUSE. Somehow I did not like it............ and the PRISM54 driver was not available on the installation. Very Stabile
4. Mepis and LinuxMint, same stability issues as Ubuntu..
I'll add to this that in my experience Sabayon 3.3 is somewhat bloated. Yes, it has MOST of the packages you will ever install, however it uses lots of RAM. It was not happy with the GB my laptop has!
It reminded my Windows Vista.

Joe.

---

### Post by dawdler on 2007-07-04
Installed the kubuntu and used the kubuntu desktop...Still freezes
Uninstalled the powernowd package...Still freezes
Compiled and installed the latest ATI propreitary fglrx driver v. 8.36.6...Still freezes

What's next?

---

### Post by joe.turion64x2 on 2007-07-04
> **dawdler said:**
> Installed the kubuntu and used the kubuntu desktop...Still freezes
Uninstalled the powernowd package...Still freezes
Compiled and installed the latest ATI propreitary fglrx driver v. 8.36.6...Still freezes

What's next?
Install another Linux distro, if it still freezes the problem does not lie in Ubuntu itself.

---

### Post by dawdler on 2007-07-05
> Install another Linux distro, if it still freezes the problem does not lie in Ubuntu itself.

I will try another distro...soon...
The thing is when I was running edgy, I didn't get these intermittent lock ups.  Then again, there has been a lot of changes since then e.g. gnome, restricted drivers, kernel, etc.

I think the culprit is my stupid ati video card.  When I run the application "fgl_glxgears", my machine freezes in seconds after the app starts running.  However, "glxgears" runs fine.

---

### Post by orb9220 on 2007-07-05
> I think the culprit is my stupid ati video card.

Don't be to sure I have a nvidia FX5900xt and a FX5200 which I get a Lockup during the night. I have firefox,ktorrent,nautilus open using Beryl and nvidia 100.?? driver 

For Me I know it is either the Video driver,Beryl,Firefox,java,Network connections,or Kernel?

No matter what I try I can count on getting a total lockup once every 24hr period.

---

### Post by sparky64 on 2007-07-05
> **sparky64 said:**
> So far so good.
Have uninstalled powenowd and used nvidias latest driver(man install) and so far have had no freeze.
Ran for 6 hours last night with no probs, Touch wood for the rest of the day.
Oh even beryl (on kde) is running perfect.=D>


Spoke to soon.
After a week of faultless operation It,s started locking up again:(
There has been no other software added since original, Don,t think theres been any upgrades.
weired.
Just d/load dreamlinux am going to give it a try.

---

### Post by soxs on 2007-07-05
What I#ve done so far, trying to fix it:
1. Added to the xorg.conf following, which was supposed to help for edgy:
Section "Extensions"
	Option		"Composite"	"0"
EndSection
2. 2x fresh Installation still freezing randomly, even running live cd randomly freezes
3. using legacy/restricted graphic drivers, no matter freezing stays
4. playing around with xorg.conf, enabling disabling stuff does not really matter

-> nothing fixed it so far

Some think it may be caused by firefox+flashplugin.. but even when NOT running Firefox at all, it freezes from time to time.

I'm waiting for kernel updates and the next gen. x-server

Note: Windows is running fine :-(

---

### Post by Jack H on 2007-07-05
Just a note For What It's Worth --
I posted earlier that my system is more stable with KDE than Gnome.  Still true.  The recent update, about 27 to 29 June, seemed to clear the problem with Gnome.  Then it crashed after 2 plus days.  KDE has been running for several days now.
I think . . . I run a fairly plain Jane setup with no action games, just word processing and Internet plus a special soundcard app. and some WINE, plus burning CDs and DVDs.. It looks as though the folks with problems are doing more zippy stuff such as action games.
I am so ingrained into Ubuntu for everyday use that I have no intention to switch as some are ready to do.  I started with Dapper which was exceptionally stable.  Now 7.04 has greater versatility.  want to keep using it.
    What I am saying is, I agree there is a problem, and I hope it can be cured soon.  This is so far ahead of Windows it is not a contest.  XP is good though a tad slow.  I saw Vista --  What a dud.  Couldn't pay me . . . 
    Jack  H

---

### Post by seul on 2007-07-06
I had the "everything freezes" variation of the disease. After 5 to 10 minutes after booting (logging on or not) screen froze, I could not move the mouse, clock wasn't counting, and the only way out was to pull the plug (or press power switch for 5 secs).

Strangely it only happened in the mornings. I had a couple of messages that I thought were related to it:
[LIST]
[*]dev/hda2: Superblock last write time is in the future. FIXED
[*]Error receiving uevent message: no buffer space available
[*]bogl init failed
[*]screeen ini failed
[/LIST]
I can't make head or tail of any of them. Googled a lot, tried this and that, nothing really helped, so I guess they are not related to the freezing problem.

I think I read it in this thread (or maybe in one of the zillion other places I went to), that someone had problems with the wifi card. Then I remembered that I once spotted a network manager error on shutdown. 

**Solving the Problem:**
I removed the wifi card and voilà. No freezer ever since. Yesterday afternoon I switched system time to next morning and did not encounter any freezers. Switched time back to present and still alright. Hope it stays that way.

I use (or rather: don't use) a Belkin Wireless G Notebook card, model F5D7010 version 6000uk on a ~4 year old ASUS L3500D Notebook running ubuntu 7.04.

Hope this helps some of you, good luck to all.

---

### Post by Mark Phelps on 2007-07-06
Just to add my 2-cents ...

I have the freezing problem but in a different way -- gnome is somewhat stable, KDE is flaky. I've read ALL the threads on shutdown and lockup problems, tried everything I've read -- nothing works, at least not for long.   I've uninstalled stuffed, modified /boot/grub/menu.lst until I can do it in my sleep, turned ACPI on and off in my BIOS, even gone back to using kernel 20.15 -- again, nothing works.  I've run memtest several times and it never shows any errors.

Using gnome, I can get an hour or more without seizures; using KDE I sometimes can't even run long enough to open a terminal and run a command.  Plus, with gnome, when I do get a seizure, I can control-key to the console and back, wait a few minutes, gnome will reset -- and I'm back working.  With KDE, when it seizes, nothing works.  Have to reboot using the power button -- and that trashes my file systems, forcing FSCKs when I reboot.  Haven't had this much "fun" since I was beta testing THAT OTHER OS.

So, it's not just a gnome issue or a KDE issue -- there's more to it than that.

---

### Post by joe.turion64x2 on 2007-07-06
> **Mark Phelps said:**
> Just to add my 2-cents ...

I have the freezing problem but in a different way -- gnome is somewhat stable, KDE is flaky. I've read ALL the threads on shutdown and lockup problems, tried everything I've read -- nothing works, at least not for long.   I've uninstalled stuffed, modified /boot/grub/menu.lst until I can do it in my sleep, turned ACPI on and off in my BIOS, even gone back to using kernel 20.15 -- again, nothing works.  I've run memtest several times and it never shows any errors.

Using gnome, I can get an hour or more without seizures; using KDE I sometimes can't even run long enough to open a terminal and run a command.  Plus, with gnome, when I do get a seizure, I can control-key to the console and back, wait a few minutes, gnome will reset -- and I'm back working.  With KDE, when it seizes, nothing works.  Have to reboot using the power button -- and that trashes my file systems, forcing FSCKs when I reboot.  Haven't had this much "fun" since I was beta testing THAT OTHER OS.

So, it's not just a gnome issue or a KDE issue -- there's more to it than that.
Have you experienced this KDE problem since the beginning?

I have experienced problems with KDE (and much less frequently with GNOME) in several Linux distros after prolonged usage periods (I mean, after several months for example). Creating another user and moving the data there solves the problem. Creating a new user is easier that reinstall.

Joe.

---

### Post by orb9220 on 2007-07-06
> **orb9220 said:**
> Don't be to sure I have a nvidia FX5900xt and a FX5200 which I get a Lockup during the night. I have firefox,ktorrent,nautilus open using Beryl and nvidia 100.?? driver 

For Me I know it is either the Video driver,Beryl,Firefox,java,Network connections,or Kernel?

No matter what I try I can count on getting a total lockup once every 24hr period.

Well just an update about an hour after posting this I had just shutdown ktorrent in gnome because I lost wireless connection. Then I went to nm-applet to reselect ssid and Bingo!,Bango! the system hard locked when I tried to use nm-applet.

Could this be a Network layers in kernel issue? that is causing all this?

I say this because It doesn't seem to matter if you are KDE or Gnome,Ati or Nvidia,Firefox or not.

So is this a Kernel thing? specifically network layers?

---

### Post by Vashu on 2007-07-06
> **orb9220 said:**
> Well just an update about an hour after posting this I had just shutdown ktorrent in gnome because I lost wireless connection. Then I went to nm-applet to reselect ssid and Bingo!,Bango! the system hard locked when I tried to use nm-applet.

Could this be a Network layers in kernel issue? that is causing all this?

I say this because It doesn't seem to matter if you are KDE or Gnome,Ati or Nvidia,Firefox or not.

So is this a Kernel thing? specifically network layers?

I agree, I think it might be network related, since its usually network activity that seems to trigger it. At first I thought it was a wireless issue, but it also happened while using LAN. When I turn networking off Hardly experience issues but i have no internet which pretty much makes things a lot harder.

---

### Post by johanPO on 2007-07-06
I am not sure that there is one issue. For me this is/was a network issue. I could leave my PC on for hours and it would work without problems. Once I generate network traffic. Azureus and so on, it would freeze within 15-30 minutes. 
I do not believe this is a kernel issue. I have tried several distributions, and only the Ubuntu based ones (Mint&Mepis) shows the same behavior. Other distributions does not... I must admit I have not tried any other debian distros. Contemplating about trying either 4.0 or sidux...

---

### Post by orb9220 on 2007-07-06
> I do not believe this is a kernel issue. I have tried several distributions

Yes but the different distro's were they all using the same kernel versions?

As this poblem for me started in edgy at the end just before feisty release I would get 1 or 2 lockups a week just before I did a clean install of feisty. 

Now I get Lockups when I leave ktorrent running while I sleep. The other thing I notice if I loose my wireless connection while I am sleeping and it does not reconnect on it's own then I do not have any lockups.

Also with ktorrent downing 3 or less torrents there is alot less chance of lockup than when I am downing 5 or more torrents.

---

### Post by oomingmak on 2007-07-06
> **orb9220 said:**
> Could this be a Network layers in kernel issue? that is causing all this?

** I say this because It doesn't seem to matter if you are KDE or Gnome,Ati or Nvidia,Firefox or not.**
That's what I've noticed. It seems to be affecting all sorts of users with entirely different setups (which make me wonder how on earth this problem would ever be tracked down).

At the moment I am still getting lock ups about once every 4 to 6 minutes (on a totally clean install) and it's really irritating.

However, your comment gives me one more avenue to explore (to see if it makes any difference).

---

### Post by orb9220 on 2007-07-07
> That's what I've noticed. It seems to be affecting all sorts of users with entirely different setups (which make me wonder how on earth this problem would ever be tracked down).

Simply by knowing the kernel and/or xorg are the culprit. I would be suprised if the kernel developers by now are not aware of this issue and are busy trying to track it down.

What I can remember tho all this started with nm-applet as default. And they did an upgrade from 0.6.3 to the 0.6.4 sometime during that period.  But I remember disabling it and using knetwork instead and it still happened.

So my feeling that it is the network layers in kernel. And people having other network problems such as "says I'm not connected but I am" sort of thing to "My wireless always worked but since feisty it doesn't sort of thing."

I am holding off till I see a stable alpha to move to gutsy. Maybe by the end of the month.

---

### Post by johanPO on 2007-07-08
> **orb9220 said:**
> Yes but the different distro's were they all using the same kernel versions?

As this poblem for me started in edgy at the end just before feisty release I would get 1 or 2 lockups a week just before I did a clean install of feisty. 

Now I get Lockups when I leave ktorrent running while I sleep. The other thing I notice if I loose my wireless connection while I am sleeping and it does not reconnect on it's own then I do not have any lockups.

Also with ktorrent downing 3 or less torrents there is alot less chance of lockup than when I am downing 5 or more torrents.

No they are not and I that was the reason for my statement. I tried Mepis and Mint, which are both Ubuntu based but I belive Mepis is 2.6.15 and mint is 2.6.20 and they frooze.  I am now running PCLinuxOS with 2.6.18  and that is stabile.

---

### Post by soxs on 2007-07-08
> **johanPO said:**
> No they are not .... which question does this refer to?

If it's really a kernel dependand thing, we can actually not influence its cure *at all*, except of bug reports or opening tickets. So what to do now? Wait, till gutsy alpha gets stabel? Search for other reasons, which in fact can not be excluded at the moment.

---

### Post by orb9220 on 2007-07-09
> No they are not and I that was the reason for my statement. I tried Mepis and Mint, which are both Ubuntu based but I belive Mepis is 2.6.15 and mint is 2.6.20 and they frooze. I am now running PCLinuxOS with 2.6.18 and that is stabile.

Well color me Ubuntu then cuz I just can't seem to nail down whether it is the Kernel,xorg,Beryl or networking. Will keep trying tho cuz it is starting to really piss me off.

---

### Post by Vashu on 2007-07-09
Ok Guys. I have good news and bad news. 

First the good news: 
**I solved my problem and have been completely stable and lock free on fiesty.**

The bad news: 
**It was a hardware issue. **

Here's my story:
As some of you may have noticed i've been posting on this thread since some time having gone from multiple re-installings, to trying out other ubuntu flavors and versions. Oddly enough, the problem started just after updating to fiesty, but after that every installation after that had the same issues. Even worst, after the second installation **every time the computer locked up, i had to hard reboot and every time i got a disk check complaining about some non-contiguous files.** I dismissed it as rutine checks from the system after hard reboot.

Since i knew i would be re-installing many times i never formatted my home partition in order to keep my settings and stuff, but the non-contiguous complain always returned and so did the locking up. After reading in this forum this seemed like a **debian/debian-based **issue i decided to go and install open-suse, assured that i would be safe from the locking up.

Boy was i wrong, the same locking, the same non-contiguous files. So, i decided to check more carefully. It seemed to be my home partition was corrupted maybe due to a** non-compliant partitioning** i did while trying to loose my windows installation. 

[B]So, I removed all my partitions, created them all from scratch and reinstalled windows and ubuntu fiesty. They are all as stable as they could be.

It seems to be that the disk issue was causing this and it seems consistent with a previous user who solved the issue in a similar way.[/B]

I recommend you all to check your partitioning and disk health because that might be your problem here.

I think on my case this rules out this being a network driver/xorg/kernel issue. but before taking is a such, i would recommend more people check out first.

---

### Post by joe.turion64x2 on 2007-07-09
> **Vashu said:**
> Ok Guys. I have good news and bad news. 

First the good news: 
**I solved my problem and have been completely stable and lock free on fiesty.**

The bad news: 
**It was a hardware issue. **

Here's my story:
As some of you may have noticed i've been posting on this thread since some time having gone from multiple re-installings, to trying out other ubuntu flavors and versions. Oddly enough, the problem started just after updating to fiesty, but after that every installation after that had the same issues. Even worst, after the second installation **every time the computer locked up, i had to hard reboot and every time i got a disk check complaining about some non-contiguous files.** I dismissed it as rutine checks from the system after hard reboot.

Since i knew i would be re-installing many times i never formatted my home partition in order to keep my settings and stuff, but the non-contiguous complain always returned and so did the locking up. After reading in this forum this seemed like a **debian/debian-based **issue i decided to go and install open-suse, assured that i would be safe from the locking up.

Boy was i wrong, the same locking, the same non-contiguous files. So, i decided to check more carefully. It seemed to be my home partition was corrupted maybe due to a** non-compliant partitioning** i did while trying to loose my windows installation. 

[B]So, I removed all my partitions, created them all from scratch and reinstalled windows and ubuntu fiesty. They are all as stable as they could be.

It seems to be that the disk issue was causing this and it seems consistent with a previous user who solved the issue in a similar way.[/B]

I recommend you all to check your partitioning and disk health because that might be your problem here.

I think on my case this rules out this being a network driver/xorg/kernel issue. but before taking is a such, i would recommend more people check out first.
Good to see you sorted it out. You were lucky to don't have bad sectors in your hard drive.
Several months ago I ended my lock up problems in a similar way: disabling the comprised partition solved everything, however the disk ended with damage. If I want to use it now, I have to set it to far smaller size ~40GB instead of 120GB, or at least two partitions avoiding the middle of the drive.

Joe.

---

### Post by grumpymole on 2007-07-10
I also experienced lockups and tried everything without success.  Eventually, it came down to a hardware problem, as [described here]("http://grumpymole.blogspot.com/2007/07/freeze-issue-resolved-after-removing.html").

Regards

---

### Post by johanPO on 2007-07-10
> **soxs said:**
> which question does this refer to?

If it's really a kernel dependand thing, we can actually not influence its cure *at all*, except of bug reports or opening tickets. So what to do now? Wait, till gutsy alpha gets stabel? Search for other reasons, which in fact can not be excluded at the moment.

I was answering the question with a question mark. "Were all the distros having the same kernerl?" and for me the answer is no.  I can not say that I have had stabile "non-ubuntus" with the same kernels, but I have had every other "non ubuntu" being stabile, and the ubunts being unstabile. So for me this is not a kernel issue. It may be for others though.. I am a bit tempted to try Debian 4.0, as it is supposed to be rock solid

---

### Post by El Viejo Lobo on 2007-07-10
> **derrekito said:**
> This might sound like a dumb question but:  Feisty Fawn is not beta anymore, so have you tried installing the official release from scratch?

I would look for fresh download and fresh install, this way it is easier to know from where the problem come or....get rid of it and be happy.:guitar:

---

### Post by Digitallysick on 2007-07-10
Mine isnt a hardware problem, i can run beryl with full effects in sabayon fine. Just not in ubuntu, i cant run open gl screen savers without freezing the system sometimes, but they are ok in sabayon. I think i should try the new kernel? although i don't really know what im doing enough to try it

---

### Post by joe.turion64x2 on 2007-07-10
> **Digitallysick said:**
> Mine isnt a hardware problem, i can run beryl with full effects in sabayon fine. Just not in ubuntu, i cant run open gl screen savers without freezing the system sometimes, but they are ok in sabayon. I think i should try the new kernel? although i don't really know what im doing enough to try it
I don't know what are you using, but in my ATI Radeon Xpress 1100 the new kernel did not work very well. I'll explain: I managed to configure Beryl using XGL and it looks really cool (the coolest thing I have seen in this machine), however after updating and booting to the new kernel things get screwed and I can not see anything. As a result of that I have locked the kernel version and just remain with the previous one.

I believe there is something weird with this new kernel, it does not like my machine because even sound becomes lost.

Although I managed to make work Beryl + XGL in Fedora Core 6 too, it still looks nicer in Ubuntu 7.04.

Thanks.
Joe.

---

### Post by Supremacy on 2007-07-11
Hi,

I've been following this problem for about a month now. I too have felt its impacts.

I have installed numerous times and even tried 2 different hard drives (both same size). I only notice this prob with Desktop Effects or Beryl (sometimes even both, though it happens more frequently).

I have tried many fixes but none have worked so far. Its a great OS and it would be nice to have these effects but I do hope they are being worked on.

When my system freezes, both the keyboard and mouse are completely unresponsive. Only once or twice has it responded to Alt-SysRq commands. I cannot get to the command line (Ctrl-F1).

However, if i leave Desktop Effects and Beryl off I can run all day or longer (no freezing in other terms).

Here are my specs for comparison. It may help others too:

M/B: Gigabyte K8NXP-SLi
CPU: AMD Athlon64 3700+ 939 Socket
RAM: 2gb (1gb Corsair, 1gb Kingston). DDR 400
HDD: Windows has a 250gb (in removable rack), Linux I have a low 15gb HDD for (also in rack)
GFX Card: Gigabyte 7900GS 256mb PCI-e
Disc Drives: LG D/L DVD Burner 16x, Sony CD-R/DVD Combo Drive

For those of you wondering, I have a removable rack system as to keep linux and windows separate and safe form any damage to windows. So i remove the windows HDD and put the linux one in when I want to run linux and vice versa.

All the NVidia drivers are installed. I used the **nvidia-glx-new** and not the **nvidia-glx** ones the Restricted Driver dialog downloads.

Hope this assists in the fixing of this problem.

[B]EDIT: OK i have just installed Compiz Fusion. It seems to be running fine. No lockup after 30mins so far. I suggest other attempt to use it instead of Beryl. I'm still using Emerald as the theme manager but Compiz fusion seems to be running perfectly fine.

[Installing Compiz FUsion In Ubuntu Feisty Fawn (7.04)]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion+no+window+decorations")

[/B]
**EDIT 2: I just had a freeze. My PC was idling with me away for a few minutes. I was lucky enough to get MythTV installed before it did. I believe it would have been stable if I had not downloaded about 130mb of data. I still think (as others have stated), that it is a network related problem within the kernel or dirvers?? I do have a Marvell LAN port onboard my Motherboard along wiht an NVidia Network port too (yes I have dual LAN Ports on my motherboard). I did as what was said in this thread to update those. Dunno, if it really worked.**

**EDIT 3: OK, Final edit for today. Just crashed again as soon as Compiz Fusion was enabled (started). I think its a fault somewhere in there. I'm rather disappointed cause it was stable for quite a long time earlier today (when I first installed it).**

Regards,
Supremacy

---

### Post by oomingmak on 2007-07-11
I'm not running any kind of composite desktop (because I've never been able to get *any* of them to work, despite months of trying).

As I said in an earlier post, I get system freezes every few minutes, even on a totally clean install (i.e. immediately after the reboot on completion of installation from the Live CD). This is with no extra software installed at all, no extra drivers and no configuration changes (apart from a couple of innocuous changes to menu.lst and xorg.conf - which I have to perform, otherwise my system won't work). 

Within minutes of the reboot after install, the system will lock (although the mouse can move freely). I only started having the problem when I switched from 6.10 to Feisty (about a month before the release of 7.04). Prior to that there was no such problems (for me at least). I've used both 6.10 and 6.06 and they were fine.

I hoped that it was just a beta related issue, so about a week after the offical release of 7.04 I downloaded another iso (rather than try to update), but that didn't make any difference. I even downloaded a fresh ISO only last week (as a desperate long shot) just in case there was something wrong with my previous 7.04 iso that I downloaded in April. 

But unfortunately exactly the same problem persists.

---

### Post by Vashu on 2007-07-11
> **oomingmak said:**
> I'm not running any kind of composite desktop (because I've never been able to get *any* of them to work, despite months of trying).

As I said in an earlier post, I get system freezes every few minutes, even on a totally clean install (i.e. immediately after the reboot on completion of installation from the Live CD). This is with no extra software installed at all, no extra drivers and no configuration changes (apart from a couple of innocuous changes to menu.lst and xorg.conf - which I have to perform, otherwise my system won't work). 

Within minutes of the reboot after install, the system will lock (although the mouse can move freely). I only started having the problem when I switched from 6.10 to Feisty (about a month before the release of 7.04). Prior to that there was no such problems (for me at least). I've used both 6.10 and 6.06 and they were fine.

I hoped that it was just a beta related issue, so about a week after the offical release of 7.04 I downloaded another iso (rather than try to update), but that didn't make any difference. I even downloaded a fresh ISO only last week (as a desperate long shot) just in case there was something wrong with my previous 7.04 iso that I downloaded in April. 

But unfortunately exactly the same problem persists.

When you did the fresh installs did you keep your same partitions or did you try erasing them and creating them again.

---

### Post by oomingmak on 2007-07-11
> **Supremacy said:**
> I've been following this problem for about a month now. I too have felt its impacts.

I have installed numerous times and even tried 2 different hard drives (both same size). **I only notice this prob with Desktop Effects or Beryl **(sometimes even both, though it happens more frequently).

When my system freezes, **both the keyboard and mouse are completely unresponsive.**
Your problem does not sound anything like the one described by the originator of this thread. Throwing composite desktops into the equation will undoubtedly muddy the waters (as such software is hardly stable, even in its own right). 

I suspect that this 'Freeze' issue is being complicated by people who are assuming that any lockup that they have (regardless of the symptoms or what they have installed) must be due to the same problem as described in this thread. But of course there are loads of different things that can cause a lock up (especially a hard lock where nothing at all is responsive). 

However, my particular situation is exactly as the OP describes. The clock continues, mouse can move freely, but no menus will work, no icons can be moved or clicked to open anything. The symptoms are exactly as described on page 1 of this thread.

---

### Post by oomingmak on 2007-07-11
> **Vashu said:**
> When you did the fresh installs did you keep your same partitions or did you try erasing them and creating them again.
Complete format and re-create partitions. 

I was going to do this anyway, because I wanted to have a separate data partition from my home partition and I couldn't find a way to consolidate disparate free space in Gparted. So I just wiped the disk and started again.

I also tried installing it onto another hard disk (albeit within the same machine) but that didn't work either. 

I'm pretty sure it's not a hardware issue, because my PC is a fairly new build and I spent ages testing the hardware before I installed my main Windows set-up on it (because I can't afford to have that be unreliable). I ran extensive RAM tests, low level disk test as well as getting my system 12 hours Orthos stable with good TAT / Core Temp scores.

---

### Post by Zannax on 2007-07-11
I had similar locks (always on switch-user/logout) and I wasn't running any desktop-effects as well.
Explicitly *disabling* the "composite extension", i.e. editing the xorg.conf file and adding the relevant line finally solved the problem.
Turning off desktop-effects wasn't enough...

---

### Post by orb9220 on 2007-07-11
Well for me I had a Hard-Lock is when I went to nm-applet and tried to switch networks have had this happen 3 times so far.

I believe for me anyway it is something network since this started at the end of edgy where I was getting 1 or 2 lockups a week to Feisty when I did a clean install and now am getting 1 or 2 a day.

My bet is 1) nm-applet or network layers in kernel 2) Kernel itself in regards to networking whether using wireless or wired.

Just did an update which I put off for about 2-3 weeks and have been going straight for 13hrs now with no lockups 8 of that was torrenting with ktorrent while I slept.

And I do use Beryl with the nvidia 100 series driver and have not totally ruled them out.

---

### Post by Supremacy on 2007-07-11
> **oomingmak said:**
> Your problem does not sound anything like the one described by the originator of this thread. Throwing composite desktops into the equation will undoubtedly muddy the waters (as such software is hardly stable, even in its own right). 

I suspect that this 'Freeze' issue is being complicated by people who are assuming that any lockup that they have (regardless of the symptoms or what they have installed) must be due to the same problem as described in this thread. But of course there are loads of different things that can cause a lock up (especially a hard lock where nothing at all is responsive). 

However, my particular situation is exactly as the OP describes. The clock continues, mouse can move freely, but no menus will work, no icons can be moved or clicked to open anything. The symptoms are exactly as described on page 1 of this thread.

I have read this thread from page 1  to now. There are plenty of examples where I have the same as other people. It also happened a few hours after I had updated my pc (downloading the updates) using Synaptic. THis was without anything else being installed.

---

### Post by joe.turion64x2 on 2007-07-11
> **Supremacy said:**
> **I have read this thread from page 1  to now**. There are plenty of examples where I have the same as other people. It also happened a few hours after I had updated my pc (downloading the updates) using Synaptic. THis was without anything else being installed.
Man!!! 47 pages!!

OK, right now I am happily using my Linux system again, this morning it refused to boot altogether (even GRUB hid itself). However booting with a live CD and deleting Windows NTFS partition at the beginning of the drive worked a miracle.

This could solve the problem I had, maybe not yours...

Joe.

---

### Post by Supremacy on 2007-07-11
> **joe.turion64x2 said:**
> Man!!! 47 pages!!

OK, right now I am happily using my Linux system again, this morning it refused to boot altogether (even GRUB hid itself). However booting with a live CD and deleting Windows NTFS partition at the beginning of the drive worked a miracle.

This could solve the problem I had, maybe not yours...

Joe.

Yes, 47 pages was a good 3-4hours of reading.

Mine is not related to HDD as its completely separate from my windows drive (1hdd for linux and 1 for windows) .

I just did an update and there were updates for Beryl in there. I wonder whether they fix any of the probs here?

**EDIT: Uptime of about 30mins now. Runing Beryl. Berly was recently updated so I wonder whether there was a bug fixed. I dunno. I also changed Beryl to "Force NVidia" Rendering. It was stated earier.**

---

### Post by matthewboh on 2007-07-12
I just had the same problem and I was wondering if it could be tied to the automatic update.  It happens during the first few minutes that the machine is running and that's one of the very few cron jobs that I have.  I noticed that there's entry in the syslogs during the time that the machine was locked (for 10 minutes) that just stated that the weekly cron job finished.  Is it possible that it's waiting for a web site that's down?

---

### Post by kpox on 2007-07-12
I don't powerd daemon  installed, and I still get a total freeze. How can I install the nvidia latest drivers? what package do I need to apt-get?

---

### Post by Supremacy on 2007-07-12
> **kpox said:**
> I don't powerd daemon  installed, and I still get a total freeze. How can I install the nvidia latest drivers? what package do I need to apt-get?

use the following command to get the latest NVidia drivers:

```
sudo apt-get install nvidia-glx
```

OR:

```
sudo apt-get install nvidia-glx-new
```

Depending on what card you have. Otherwise you can install them using the Restricted Drivers Manager.

Mine crashed after about 35mins of uptime with Beryl enabled. And i thought forcing Nvidia rendering would help.

Regards,
Supremacy

---

### Post by skullmunky on 2007-07-13
hi, 

i have, i think,  the same problem as OP:

- kubuntu feisty, athlon 64 X2 on an abit kn8 ultra. 

- system freeze, except for mouse movement.  ctrl-alt-del, ctrl-alt-f1, etc. don't respond.  can't ping or ssh into it.

- usually after a day or so; hasn't happened yet while i'm actually doing anything, always after hours of just sitting idly, like overnight.  i 

- no beryl or compiz, but i do have the nvidia-glx installed by way of restricted drivers manager, with twinview.  card is a quadro fx 1400.  as far as i can tell everything works fine there.

not sure if there's a good solution already posted, but the thread's gotten kinda long and i might have missed something.  

the only thing that stands out in the kernel log is hours and hours worth of this:

eth0: Interrupt posted but not delivered -- IRQ blocked by another device?
Flags; bus-master 1, dirty 3302(6) current 3302(6)

and this:

eth0: Resetting the Tx ring pointer.
NETDEV WATCHDOG: eth0: transmit timed out

every 10 seconds.

i'm not using the onboard ethernet - i'm using another old, dusty ethernet card because the onboard nvidia chipset has a known bug with producing invalid MAC addresses, which in turn causes random MAC addresses to be assigned at boot, which in turn confuses the flexlm license manager.  (ugh).  

does this seem relevant?  

think it could be fixed by NOAPIC?  

i can just try it and test, but the freeze is so sporadic it's hard to know when i've got it beat.

---

### Post by Bealer on 2007-07-14
I've been using the 386 (not the Generic) version of the kernel/image and it works fine for me. I've never had a lockup.

When using the Generic kernel I did try all of the suggested fixes. Changing xorg.conf, my boot parameters in GRUB, running off a fresh install etc...

I think it relates to my ATI card and the restricted drivers. I can't be certain, but from what I can remember when running my machine on the "vesa" driver it was fine (although I'd be stuck in 1024x768 on my 20"tft :().

I've tried other distro's (PC Linux OS 2007 for example) and they've been fine, so it looks like something in the Ubuntu build. And Edgy 6.10 worked fine, it's just something in Feisty 7.04. Having said that it works on my laptop perfectly, just not on my desktop. 

It's frustrating as I'd preferably like to use the Generic image, but every time I go back to it I get freezes, whereby nothing responds, but I can still move the mouse around. I couldn't see anything from the logs that might suggest what it is.

---

### Post by oomingmak on 2007-07-14
> **Bealer said:**
> ... every time I go back to it I get freezes, whereby nothing responds, but I can still move the mouse around. I couldn't see anything from the logs that might suggest what it is.
Did your system "unfreeze" itself again if you left it for long enough? or or did you have to restart?

---

### Post by emid on 2007-07-15
I have the same issue on 64bit Feisty where I can move the mouse but not click anything.  It unfreezes itself after a couple seconds.  It seems the longer the computer has been sitting idle, the longer it takes to unfreeze.  I'm using Compiz and have the Nvidia drivers installed.  I uninstalled powernowd, but I still have the same issue.

---

### Post by crazedgremlin on 2007-07-15
emid, could your problem possibly be your mouse?  Try using a different mouse for a while.

---

### Post by oomingmak on 2007-07-15
> **emid said:**
> I have the same issue on 64bit Feisty where I can move the mouse but not click anything.  It unfreezes itself after a couple seconds.  It seems the longer the computer has been sitting idle, the longer it takes to unfreeze.
Interesting.

On my system it "unfreezes" itself after a pause too. However mine can last from 10 seconds up to about one minute maximum. But invariably, if you wait long enough, it will unfreeze in the end.

If I have tried to click menus (or perform other tasks) while the system is frozen, and all of my attempted actions get played back at high speed immediately after the system is unfrozen. So it's as if the system is still able to recognise and record my actions in its frozen state, but it just can't execute them until the 'blockage' (for want of a better word) that's causing the freeze is out of the way to let the new commands through.

I have to say that Ubuntu is pretty unusable for me in this state, because the freezes are about every 5 - 10 minutes non stop.

---

### Post by soxs on 2007-07-15
> **Bealer said:**
> And Edgy 6.10 worked fine, it's just something in Feisty 7.04. Having said that it works on my laptop perfectly, just not on my desktop. 

This statement is simply wrong, I had the same problems on edgy.
Now I can say with a *high* propability that it's either the FireFox OR a Kernel bug which affects the network stuff.

I am currently testing opera, as I was told it would help, to make it happen more rarely (well maybe operas network accessing sys is diffrent).

---

### Post by emid on 2007-07-16
> **crazedgremlin said:**
> emid, could your problem possibly be your mouse?  Try using a different mouse for a while.

I really don't think it's my mouse.  I can move the mouse around perfectly, it's the rest of the system which appears to temporarily freeze.

---

### Post by Phayder92889 on 2007-07-17
God... I've followed all the advice that's helped people in this thread, and all it does is delay the freezing. What's really screwy is that I can log in as root and it works just peachy for me, staying up for about 2 days now.

---

### Post by soxs on 2007-07-17
> **soxs said:**
> This statement is simply wrong, I had the same problems on edgy.
Now I can say with a *high* propability that it's either the FireFox OR a Kernel bug which affects the network stuff.

I am currently testing opera, as I was told it would help, to make it happen more rarely (well maybe operas network accessing sys is diffrent).

So i am using opera since 2 days now and my PC appeared to be 100% (real 100%) stable!!

So, folk,.. go and dl opera and test it yourself! For me, it's the fix (and confirms that it's either a FireFox Bug or a Kernel bug)

[COLOR="DarkRed"]***_EDIT_***
opera does not fix the freezes.. they just seem to happen a lot more rare[/COLOR]

---

### Post by henkstubbe on 2007-07-18
Yes, my freeze seems to be gone! For several weeks I tried all tips in this thread, like
- Disabling Cool & Quiet
- Disabling powernod
- Using all suggested kernel options like noapic, pci=noapci etc.
- Installing new ATI drivers
- Installing gconf 

Finally I thought, hey, let's check how Windows performs. It froze too! Yes! It's hardware :-)

So what the heck could be wrong with my brand new computer (M2A-VM HDMI, AMD X2 3400+, 2GB)? Let's do the memory test.. I remembered changing some settings a couple of weeks ago. That did the trick! 

I had to downscale the DDR2 frequency (or whatever it is called) from 800Mhz to 667Mhz.  Solid as a rock from that moment on!

---

### Post by Bealer on 2007-07-19
> **oomingmak said:**
> Did your system "unfreeze" itself again if you left it for long enough? or or did you have to restart?

Hmmm, well I'd left it for about an hour maybe two once and it still hadn't unfronzen so I assume it never was going to unfreezen. Actually frozen is wrong terminology. I could still move the mouse and spin the Beryl cube etc... but nothing would respond (no menu's, apps etc...)

> **soxs said:**
> This statement is simply wrong, I had the same problems on edgy.
Now I can say with a *high* propability that it's either the FireFox OR a Kernel bug which affects the network stuff.

How can it be wrong? Are you saying you have the exact same system as me and you had the same problems in 6.10, yet I didn't hence it being wrong? 

It's a fact 6.10 worked on my system without this problem, and 7.04 doesn't (using the Generic kernel). Whether it's kernel related or due to restricted drivers I don't know. That's why we're all here, to post our experiences, setups etc... in order to find a fix.

---

### Post by FenrirVII on 2007-07-19
Hey guys, im new here, havent checked much of the forums except the announcement parts haha just searched and found this trhead- and no not just for the little problem.. ive been using Linux for a while and have been meaning to use it in better ways :P And coincidentally  just got a pretty O-K crappy graphics card thats just enough to work well with the Ubuntu compix or beryl.  

Fiesty 7.04
NVidia MX 4000 128mb
P4 1.6ghz
512mb Ram


The program ran fine for a few minutes after enabling it, But ive also experienced this freezing.  I think its just to do with overloading the graphics card, not letting things load or interrupting the processes?.  When i start it up for instance right after it logs in and click the system profile, ive had it freeze on me.  Or when i use firefox and watch a youtube video, it freezes BUT the audio of the video is still running after the desktop has frozen.  Mouse is still moveable and all.  And no it never comes to- and yes without running the desktop effects ive also had that screensaver freeze that does this same thing.  Its kinda wierd.. Cant be just to do with the graphics card devs though becuase i see people with ATI having problems Exactly like mine too.. Maybe the problems would go away if we just installed an earlier version of Ubuntu and manually downloaded and configure up beryl/compiz?

Edit- Im using Beryl and have like 25 apps spread across the 4 sides (desktops), Its been working nonstop, no freezing for the last 2 hours.  None are Firefox related apps, so im lead to believe it definately is a firefox compatability issue like originally mentioned.

---

### Post by crouger92 on 2007-07-20
hi,

i have an acer aspire 3000WLMi laptop (1.86ghz, 512 ram), totally stock. From the first time i installed feisty (i must have done it 3 or 4 times) it would freeze on me. i tried installing the 386 image but that doesn't work. 

this is what comes up in the terminal a few minutes before freezing:

[B]Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] ------------[ cut here ]------------

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] invalid opcode: 0000 [#2]

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] CPU:    0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EIP:    0060:[kfree+115/128]    Not tainted VLI

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EFLAGS: 00010046   (2.6.20-16-386 #2)

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EIP is at kfree+0x73/0x80

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] eax: 00000000   ebx: da441f60   ecx: cc60e7a0   edx: c1800000

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] esi: 00000001   edi: 00000202   ebp: 00000400   esp: da441f30

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Process hald (pid: 4534, ti=da440000 task=dbe61550 task.ti=da440000)

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Stack: da441f60 cb824180 00000001 c017b8ce 00000400 080860e0 ce3656c0 cb8241a0 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]        00000000 00000000 dba95040 00000000 00000000 00000000 ce3656c0 080860e0 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]        da441fa0 00000400 c016369c da441fa0 dba95074 c017b840 ce3656c0 fffffff7 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Call Trace:

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [seq_read+142/672] seq_read+0x8e/0x2a0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [vfs_read+188/400] vfs_read+0xbc/0x190

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [seq_read+0/672] seq_read+0x0/0x2a0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [sys_read+65/112] sys_read+0x41/0x70

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  =======================

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Code: 89 74 83 10 83 c0 01 89 03 89 f8 50 9d 66 66 66 90 66 66 66 90 5b 5e 5f c3 8b 52 0c eb d0 89 c8 89 da e8 d1 fe ff ff 8b 03 eb d5 <0f> 0b eb fe 89 f6 8d bc 27 00 00 00 00 57 89 d7 8d 92 00 00 00 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EIP: [kfree+115/128] kfree+0x73/0x80 SS:ESP 0068:da441f30

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] invalid opcode: 0000 [#3]

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] CPU:    0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EIP:    0060:[kfree+115/128]    Not tainted VLI

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EFLAGS: 00010046   (2.6.20-16-386 #2)

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EIP is at kfree+0x73/0x80

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] eax: 00000000   ebx: cb824180   ecx: cb824180   edx: c1800000

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] esi: 00000001   edi: 00000202   ebp: d0a8a804   esp: da441d58

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Process hald (pid: 4534, ti=da440000 task=dbe61550 task.ti=da440000)

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Stack: cb824180 cc60e7a0 cf314414 c017b18b 00000010 c017b1f5 00000010 ce3656c0 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]        c0163ef7 00000000 00000000 cf314414 dbee41c0 d0a8a804 ce3656c0 dbe76600 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]        00000000 dbe76600 c0161337 00000000 00007fff dbe76608 00000000 c011d0af 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Call Trace:

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
vfred kernel: [ 1526.876000]  [seq_release+11/32] seq_release+0xb/0x20

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [single_release+21/48] single_release+0x15/0x30

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [__fput+167/400] __fput+0xa7/0x190

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [filp_close+71/128] filp_close+0x47/0x80

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [put_files_struct+143/176] put_files_struct+0x8f/0xb0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [do_exit+277/1920] do_exit+0x115/0x780

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [printk+27/32] printk+0x1b/0x20

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [die+551/560] die+0x227/0x230

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [do_invalid_op+0/176] do_invalid_op+0x0/0xb0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [do_invalid_op+162/176] do_invalid_op+0xa2/0xb0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [kfree+115/128] kfree+0x73/0x80

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [printk+27/32] printk+0x1b/0x20

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [acpi_os_vprintf+37/40] acpi_os_vprintf+0x25/0x28

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [error_code+116/128] error_code+0x74/0x80

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [kfree+115/128] kfree+0x73/0x80

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [seq_read+142/672] seq_read+0x8e/0x2a0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [vfs_read+188/400] vfs_read+0xbc/0x190

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [seq_read+0/672] seq_read+0x0/0x2a0

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [sys_read+65/112] sys_read+0x41/0x70

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000]  =======================

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] Code: 89 74 83 10 83 c0 01 89 03 89 f8 50 9d 66 66 66 90 66 66 66 90 5b 5e 5f c3 8b 52 0c eb d0 89 c8 89 da e8 d1 fe ff ff 8b 03 eb d5 <0f> 0b eb fe 89 f6 8d bc 27 00 00 00 00 57 89 d7 8d 92 00 00 00 

Message from syslogd@fred at Sat Jul 21 18:44:23 2007 ...
fred kernel: [ 1526.876000] EIP: [kfree+115/128] kfree+0x73/0x80 SS:ESP 0068:da441d58[/B]


i haven't read most of these posts as they all seem the same, and feisty would probably freeze before i got halfway through.
it sometimes occurs at random, or when its doing something semi-strenuous.

help?? please? [http://ubuntuforums.org/images/smilies/confused.gif:mad:](http://ubuntuforums.org/images/smilies/confused.gif:mad:)

ps i had none of these problems with dapper.

---

### Post by soxs on 2007-07-20
> **Bealer said:**
> 


How can it be wrong? Are you saying you have the exact same system as me and you had the same problems in 6.10, yet I didn't hence it being wrong? 

It's a fact 6.10 worked on my system without this problem, and 7.04 doesn't (using the Generic kernel). Whether it's kernel related or due to restricted drivers I don't know. That's why we're all here, to post our experiences, setups etc... in order to find a fix.

Sorry, I did not want to flame on you.. I do obviously not have the same sys specs as you,.. but I at least, I expired this one same bug (freezing and having to hard reboot, mouse is movable, no response to keyboard, never unfreezing, music goes on playing) allready on edgy & now on feisty. Somebody mentioned that gutsy will have implemented a new x-server... so it's likely that, if the problem is related to the x-erver it 'll be fixed (if not driver related), otherwise we must wait for kernel-updates

---

### Post by crazedgremlin on 2007-07-20
> **FenrirVII said:**
> Hey guys, im new here, havent checked much of the forums except the announcement parts haha just searched and found this trhead- and no not just for the little problem.. ive been using Linux for a while and have been meaning to use it in better ways :P And coincidentally  just got a pretty O-K crappy graphics card thats just enough to work well with the Ubuntu compix or beryl.  

Fiesty 7.04
NVidia MX 4000 128mb
P4 1.6ghz
512mb Ram


The program ran fine for a few minutes after enabling it, But ive also experienced this freezing.  I think its just to do with overloading the graphics card, not letting things load or interrupting the processes?.  When i start it up for instance right after it logs in and click the system profile, ive had it freeze on me.  Or when i use firefox and watch a youtube video, it freezes BUT the audio of the video is still running after the desktop has frozen.  Mouse is still moveable and all.  And no it never comes to- and yes without running the desktop effects ive also had that screensaver freeze that does this same thing.  Its kinda wierd.. Cant be just to do with the graphics card devs though becuase i see people with ATI having problems Exactly like mine too.. Maybe the problems would go away if we just installed an earlier version of Ubuntu and manually downloaded and configure up beryl/compiz?

Edit- Im using Beryl and have like 25 apps spread across the 4 sides (desktops), Its been working nonstop, no freezing for the last 2 hours.  None are Firefox related apps, so im lead to believe it definately is a firefox compatability issue like originally mentioned.

That's strange that firefox would freeze your entire system.  I use an nVidia GeForce MX 4000 in a mythtv box and wanted to tell you that it's not your graphics card causing the problems.

---

### Post by FenrirVII on 2007-07-20
Yeah hehe its strange alright, I knew my grahpics card works and everything- beryl loads up and works fine.  Basically Ive now installed Fedora 7 and am running desktop effects with more stability it feels like.. but it still freezes.. maybe theres something that Mozilla Firefox does after a certain time constrait that somehow glitches/freezes up X or beryl? 

One Very Key difference between Ubuntu and Fedora's Desktop Effects settings is though when I disable it in ubuntu.. i cant get it back again, not even manually.   Fedora 7 seemlessly switches without hitch, yet they both freeze so it must be something either universal to the desktop effects.. Or maybe how the drivers for the 4000 are installed to each system?  I basically used the standard enabling on ubuntu, but on Fedora i installed them through yum and livn.

Im just going to restore everything and remove it all and install beryl or compiz directly with the drivers and see what turns out from it.

---

### Post by fredj on 2007-07-21
On one PC I had the same freeze i.e could move the cursor but not click on anything. I solved it by updating
the firmware on my DVD drive. I imagine that it was caused by Ubuntu interrogating the drive and not 
receiving a suitable reply and waiting for a timeout.

---

### Post by tjnugent on 2007-07-21
Hi Folks, 

This is my first post the to the forum.  

i have been using Ubuntu Feisty and have had the same system freezes.  I think I may have found the answer for my machine.  I am using a nVidia GeForce 7300 graphics card and using the "Restricted Drivers" for the card.  I would get freezes after a short time, or sometimes when surfing the web. 

I saw a thread that talked about getting the right nVidia drivers for your card so I went did. 

sudo apt-get install nvidia-glx-new

That was 24 hours ago, and not one freeze since.  

The other driver mentioned in the earlier thread:

sudo apt-get install nvidia-glx

You may want to try changing your current nVidia driver to see if it helps.  It did for me.  

PS.  I downloaded firefox 2.0.0.5 and it was still freezing before I changed the driver to the "New" nVidia driver.  

Ted :)

---

### Post by Bealer on 2007-07-21
> **soxs said:**
> Sorry, I did not want to flame on you.. I do obviously not have the same sys specs as you,.. but I at least, I expired this one same bug (freezing and having to hard reboot, mouse is movable, no response to keyboard, never unfreezing, music goes on playing) allready on edgy & now on feisty. Somebody mentioned that gutsy will have implemented a new x-server... so it's likely that, if the problem is related to the x-erver it 'll be fixed (if not driver related), otherwise we must wait for kernel-updates

That's ok, I didn't mean to come across rude either. I was lucky enough not to have the bug in Edgy. I'm gonna try Gutsy Tribe 3. See how things are with it, see if I can help with any bug finding.

---

### Post by Bealer on 2007-07-21
Gutsy Tribe 3 seems to be working ok for me. I've been running it for half a day and it's fine. No freezes. Hopefully whatever the bug was it'll be fixed in the final release.

---

### Post by highd1 on 2007-07-21
How would I update my firmware for my DVD-ROM in terminal?  I did what TJNUGENT suggested and I hope it works but just in case it doesn't I'd like to try updating the firmware.

---

### Post by Antto on 2007-07-22
I'm still having this problem and today I decided to test whether a new kernel helps at all.
I downloaded and compiled the newest stable vanilla kernel from kernel.org (2.6.22.1) and compiled it, the freezes are still happening at least when the composite extension and aiglx are enabled.
At the moment I'm downloading nexuiz to test the stability with those two disabled. Also another thing I noticed is that when the computer froze I decided to press pretty much all the buttons and removed usb devices and my audigy2zs notebook pcmcia card, all those events can be seen in the kern.log so it seems at least some of the underlying system is still functioning it just doesn't seem to respond to mouse or keyboard input at all and the only way to restart is by doing a hard reset.
I can also see the screen and move the cursor but nothing will respond. I guess the next step is to try to install newer xorg server but I don't think I'm yet up to it.

Well after installing nexuiz and playing with it as long as I wanted I couldn't crash the computer once, so for me atleast disabling aiglx and composite extension fixes this, but because of that I can't use compiz/beryl which I really like so it's not really a solution.

---

### Post by crouger92 on 2007-07-22
the same thing happens to me; the system still works and registers things, but there's no prompt and if it does respond to input (alt + prtsc etc...) for a while it soon stops. I don't think it can be a graphics thing for me because the only graphics card i've got is the one that comes stock. I tried to dillo browser to see if it was FF and it still froze. I hope Gutsy is ok too. Something like this could ruin Ubuntu's reputation.

---

### Post by QwUo173Hy on 2007-07-22
> **crouger92 said:**
> Something like this could ruin Ubuntu's reputation.

If it was only Ubuntu with this problem that would be true but luckily (or unluckily) that's not the case.

Antto, great work you're doing there. Any light that can be shed on this is great and that's the most constructive effort any of us have put forward yet.

---

### Post by Ocxic on 2007-07-22
I've heard that disabling the intell speedstep, in your bios, may stop your freezing, certian cpus apperntly lockup, when switching modes, had to do it fo r my buddie

---

### Post by highd1 on 2007-07-22
Okay, I updated the nvidia driver and it solved nothing.  I am pulling out my hair here!  I have noticed that if I lock the screen when I walk away instead of letting it hibernate by itself that it thwarts the problem while inactive.

---

### Post by sunshine12 on 2007-07-22
Ubuntu freezes when I kept it overnight or long time for some download/upload things.. it generally freezes after 1-2hours,
don't know what is the problem but it was working well before.. having this problem since last week..

---

### Post by BA53 on 2007-07-22
Same problem here. 

The problem started suddenly using Edgy. So I decided to make the switch to Feisty, but the problem continues. Once it also froze during the install from the live cd.

Turning off ACPI makes GDM to stop right after the login screen. It has to be a software problem since so many people report it even in the German forum. 

I'm also using the "nv" driver, but that doesn't help.

---

### Post by FenrirVII on 2007-07-23
Ubuntu 7.04 -Enabled Restricted Drivers- Desktop Effects: Freezes after use of Firefox
Fedora 7-Installed Nvidia drivers- Desktop Effects: Freezes after extended use (15+mins)
Kubuntu 7.10-Installed Nvidia miraculously- beryl would never load??
Linux Mint- I have to say its By far the extremely most stable so far, yet its still freezing after some time (30+mins?)

Ive used Envy, manually installed drivers, and just enabled restricted drives on many of these Linux.  And im still not closer to knowing why it keeps freezing?  Ive had someone with my exact MX 4000 say its not the card.. In my logs many of last actions before it froze revolved around Gconf on Fiesty Fawn.. I dont know.  Getting a bit lost here.  I thought Linux Mint had worked and yet it still freezes like this.. Ill keep trying though.

The By far largest and obvious freezing occurs when im watching a Video on Youtube using FireFox

---

### Post by Antto on 2007-07-23
Well I decided to bite the bullet and compiled newest xorg from git plus also new mesa and drm so my graphics system is pretty much as bleeding edge as it can be.
I can finally use EXA and the acceleration is working fine but as soon as I enable aiglx and composite extension I still have the freezes So now im running latest stable kernel and latest xorg+other stuff connected to it and it still freezes.
I'm out of ideas about what to try next, only difference the new xserver made was that now when the xorg freezes there is error "tossed event which came in late" repeated many times in the Xorg log so maybe this can give some idea to somebody who knows more about these things.

---

### Post by FenrirVII on 2007-07-23
Ok, ive redone my LinuxMint and Beryl was Extremely stable.. and what do i do to test out?  Youtube videos- Crashed my whole computer that time :/ , Rock solid no mouse movement or anything.. Other than that My experience with LinuxMint was very good.  Just a few hiccups (instead of entire beryl Freezing).. still though, i'd say it was more stable than any other linux beryl :/ Im going to try and install compiz fusion now and see what that gives me

- And for the Record, Im using my laptop to browse the forums though, it has Kubuntu KDE  7.04 :P too bad it only has a Rage 8mb graphics card haha.  Though I remember installing Beryl on this (attempting to) until i discovered it was only an 8mb.. (Beryl installed perfectly- it just got me the white Cube of Death. and that thing never froze up or anything.. so Im guessing if i run out to an electronics store and buy another/newer Nvidia card it would work better? 

-i know alot say its not the video card, and my Above example where a Youtube video is the sole cause for a crash.. which would maybe say its the beryl itself.. But seeing as how Beryl worked (in a sorta broken white screen way), without any freezing at all.. maybe it is possibly my NVidia MX 4000.... 

I tried installing Kubuntu 7.10 Gutsy Gibbon on my desktop, but i couldnt find the Beryl installer, and the websites are all changed around along with repositories for everything so i gave up on the Gutsy.  Just too gutsy for me.. If i install 7.04 KDE on my desktop would it be different than on my 7.04 Ubuntu in any ways?  Like with the Adept manager somehow making Beryl install better?  Or some sorta better manual install? 

-Im going to go back to LinuxMint and give it another test again- basically i browse online/forums/other random sites for an hour.. Decree Minor stability (hiccups and general problems, but nothing to do with freezing the entire computer where it needs a manual hold down power button restart- Reloading beryl is a simple fix to many times where the beryl desktop just crashes so its not a problem and Is minor stable in my eyes :P ) .. and then go to youtube.. where it crashes.. letsee how it works out again


Edit- Update-  Linux Mint Betrayed me :( removed the compiz and beryl cores and installed Compiz fusion.. ontop of the no title bar.. It freezes on me .. while watching a youtube video..So Im going to go buy some other graphics card and see how that might work out..

---

### Post by crouger92 on 2007-07-24
does anyone else get this sort of error while booting? It might be connected:

error: microcode '<long number here>' not available or load failed.

I get anywhere between 3 and 5 of these at boot time (press alt+f1 to show)

---

### Post by bingobingo on 2007-07-24
Sorry. crouger92, no anwser for you, you need a new post for that. I just what to add my two cents of Freezing problem. I have a PowerMate Eco and I tried adding the noapic to the boot with no effect, but the connection with the mouse seems to be there. Freezing last from 10 to 25 seconds long and is constant, cpu use spikes during these times. Cpu temp is usually 42 c but lately is at 55 c. 

This is really getting to be a drag. I need to use my imac all the more, because I can not take the situation any longer.

---

### Post by mrgnash on 2007-07-24
It's definitely something to do with my X700 mobility and compositing for me, because I can run without a freeze all day *until* I run either desktop effects, compiz-fusion or beryl. Also, it seems specifically related to the AIGLX method rather than XGL, and crops up regardless of whether I am using the 'ATI' or 'Radeon' driver. Unfortunately, I'd rather run without desktop effects of any sort than using the rubbishy fglrx driver and XGL.

---

### Post by FenrirVII on 2007-07-24
Ok im going to test here- just got a geforce 7600 GS and see what happens.. Here goes all those stupid tests.. again... 

update 1- Yes in minutes time.. (ive freakin done this like 40 times now). i uninstalled everything and reinstalled beryl/compiz/compizfusion.. Browser opened, yahoo, google, Playstation forums, Youtube- Watched a video of Killzone 2 sony press event and Not even a single hiccup, video ended well, loaded up the end flash of other videos to click on and everything appears stable- Im running LinuxMint 3 and things appear much better than before.. Not a single trace of lag....I will continually update my finds throughout the night, becuase its only been 7 minutes and i dont wanna get too  excited.

update 2- Ok this is just a basic procedure i normally did, 1 youtube video usually crashed the old graphics card I am now perfectly certain of.  2 youtube videos was rare to ever happen.. like 1%-2% of the attempts (let alone there were usually hiccups in the first that fore shadows an eventual freeze).... I finished watching the second video (original Halo 3 trailer- Still the best Halo Trailer!!) and moved onto my third video which is now over.. not a single hiccup nor any lag.  (video was COmpiz Fusion Development- pretty sweet video i think of what i was using :P)

Update 3- Now i got a little gutsy- Opened up 10 youtube videos (the compiz fusion development one- 5mins long.. Im running a weak Pentium 4 thats not very good at multitasking so i think the fault is there.. But there is no fault,  NO freezing, no hiccuping and No problems :D ran all 10 of them.. (audio was jumpled/horrible becuase there were 10 freakin videos playing at once hahaha sounded strange)

Update 4- Now an hour later again.. No crashing, Nothing.  I can wrap this up as Entirely to do with grahpics card issue i think for most people too maybe?  My what-happens is this- desktop freezes, keyboard does not work, yet i can still move the mouse... I had an Nvidia Gf MX 4000 and that was the sole cause of it.  So if have anything like that.. I think its definitely your graphics card.  beryl/compiz/compiz fusion loads up and works perfectly for a bit.. But then it just dies.. Now with my new 7600 GS its working perfectly.  So if it has those symptoms, i suggest running out to an electronics store, asking them about their return policy for their graphics cards (if somehow the problem persists), and buy a nice one thats better than yours or different in some way.  This problem had nothing to do with my installation or linux

---

### Post by Supremacy on 2007-07-25
> **FenrirVII said:**
> 
Update 4- Now an hour later again.. No crashing, Nothing.  I can wrap this up as Entirely to do with grahpics card issue i think for most people too maybe?  My what-happens is this- desktop freezes, keyboard does not work, yet i can still move the mouse... I had an Nvidia Gf MX 4000 and that was the sole cause of it.  So if have anything like that.. I think its definitely your graphics card.  beryl/compiz/compiz fusion loads up and works perfectly for a bit.. But then it just dies.. Now with my new 7600 GS its working perfectly.  So if it has those symptoms, i suggest running out to an electronics store, asking them about their return policy for their graphics cards (if somehow the problem persists), and buy a nice one thats better than yours or different in some way.  This problem had nothing to do with my installation or linux

wow. you are lucky. HOwever, I find that it may not be a gfx card issue. I run a 7900GS and it freezes. Maybe you just got lucky eh? lol

Regards,
Supremacy

---

### Post by FenrirVII on 2007-07-25
Maybe, i ran through like a hundred (not kidding) tutorials and changes.. my xorg.conf.. its very wierded out by now and everythings fine.. though in reading it it still says i have an Nvidia mx 4000 hahaha stupid thing.. anyways, i like to think its for hard work and this is pay off :D  hrmm But yeah, If you find a store who's return policy is easy, with no restocking fee or anything, shouldnt hurt to buy a 7600 GS to test out and see if its the graphics card?  Maybe we can all work up a "real" list of stable graphic cards.

---

### Post by BA53 on 2007-07-25
Well some of you only seem to encounter the problems running Beryl, Compiz, ... .

Has someone found an answer to the question, why the system freezes with a fresh install or even the live cd. 

Maybe this helps: Starting Thunderbird and clicking on some folders nearly always freezes my system. But it'll also freeze if I'm not starting any programs (but normally this takes longer).

I definitely don't want to install Windows again, but well I have to work with the computer. ;(

---

### Post by gtrtx on 2007-07-25
Hello,
I normally just lurk here, but I was having lockup issues and found a resolution. Figure this might help anybody that has similar hardware.

EVGA nForce i650 Ultra mobo
3.2 Ghz Pentium D processor
GeForce 7200 GS - Vid card.

I believe the main culprit in my freezing was my motherboard and APIC(Advanced Programmable Interrupt Controller). 

I seemed to have lockups of many kinds: mouse pointer moves..but nothing responds, mouse locks, sound stutters and locks. I have a feeling that these are all related to some sort of IRQ conflicts. 

Passing noapic or nolapic to the kernel(through GRUB) didn't stop the lock ups. Two things that DID stop the lockups where using the 386 kernel or disabling APIC in my BIOS settings.  I didn't see these as viable options, however, as they only allowed me to use 1 core of my dual core processor and this hindered performance.  I have a dual core processor, I want them both to work. 

I did try many of the things mentioned in this thread, and also some experimentation on my own in regards to my IRQ settings. Nothing worked. 

I finally thought to look for BIOS upgrade for my motherboard. I found one and applied it and since then it has been smooth sailing.  I've had the system running since Sunday with no lockups of any kind. Both processors are enabled. 

Anywho...just thought I'd share.

Good luck everybody....

tex

---

### Post by BA53 on 2007-07-25
Thanks for the tip with the mainboard.

I loaded the fail safe settings in the bios options and up to now the system is running fine. So at the moment this is definetly a new up time record (1 hour+) ;)

[B]
Don't count your chickens before they hatch. Problem still exists![/B]

---

### Post by gjrepicky on 2007-07-25
To add to the data set (or confusion).

I'm running a system on the opposite end of the spectrum from many of you -- 2001 vintage IBM T21 Thinkpad, P3 @ 800 MHz, 256 MB ram, 20 GB HD, Savage S3 video card.  No fancy effects enabled (obviously with this system!).  Feisty locks up unpredictably.  When it does I lose all control -- no mouse, no keyboard response, no nothing -- needs power-switch restart.  Seems to happen mostly in Thunderbird or Firefox, but that may reflect that during these lazy days of summer most of my time has been spent in these programs.  (I'm addicted to political commentary -- of the sane variety -- and following the Tour de France "live".  Interestingly, it seems to most often occur if I run off the right side of the screen while scrolling with the vertical slide bar click-and-dragging with the mouse (used plugged into the serial port).  I'll probably (reluctantly) reinstall Dapper until I find a fix -- but reading much of this thread, and the suggestions re: video cards, WiFi, etc, i suspect there's something more fundamental (and subtle!) at play here.

G.

---

### Post by prithwin on 2007-07-25
is there a documentation of the command line options of compiz.i type compiz --help and get these options i have no idea what they do,maybe one of them can stop this freeze

---

### Post by Digitallysick on 2007-07-25
Something interesting happened today, i ran sabayon from the live disk (64 bit version) and i had all the effects on, after a few hours it froze, i could move the mouse but nothing else. So, its NOT a distro issue in my case, it has to be something else. Im really thinking its a hardware conflict of some sort.

---

### Post by BA53 on 2007-07-26
Don't count your chickens before they hatch.

The problem still persits. Updating Bios and fail safe settings don't help. :mad:

---

### Post by BA53 on 2007-07-26
Posted Bug on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/128611](https://bugs.launchpad.net/ubuntu/+bug/128611)

---

### Post by soxs on 2007-07-28
This thread should be splitted, as it seems to contain a lot of diffrent bugs (mouse freezing/no mouse freezing; sound playing/sound freezing; unfreezing possible/only hardreboot)

This is a required step to get solutions for each pub/problem..

---

### Post by duchamp.fitz on 2007-07-28
I didn't read all 52 pages of the thread, so not sure if this has been mentioned.  After upgrading to fiesty, I had almost constant lockups (more specifically, I've learned, "kernel panics").  Scouring the forums for weeks, I finally discovered ubuntu was having problems with my linksys usb wireless card.  I've hated this card since I bought it anyway-terribly weak-so I was happy to buy a shiny new internal linksys card (with a nice big antenna).  Not one lockup since.  Hope this helps at least some of those having this frustrating problem.

---

### Post by Moonlit Knight on 2007-07-28
I don't know what's happening, my system (Ubuntu feisty fawn 7.04) freezes randomly and the mouse doesn't respond, but it seems that only happens when I'm surfing with firefox, I'm not running beryl neither the desktop effects.
Lspci shows
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I tried installing kernel-image-2.6.20-15-386 and running noapic nolapic, but this doesn't solve the problem.
Please I need help, it happened running the live cd too

---

### Post by oomingmak on 2007-07-28
> **soxs said:**
> This thread should be splitted, as it seems to contain a lot of diffrent bugs (mouse freezing/no mouse freezing; sound playing/sound freezing; unfreezing possible/only hardreboot)

This is a required step to get solutions for each pub/problem..
That's the point that I was trying to make earlier on.

---

### Post by Supremacy on 2007-07-28
> **duchamp.fitz said:**
> I didn't read all 52 pages of the thread, so not sure if this has been mentioned.  After upgrading to fiesty, I had almost constant lockups (more specifically, I've learned, "kernel panics").  Scouring the forums for weeks, I finally discovered ubuntu was having problems with my linksys usb wireless card.  I've hated this card since I bought it anyway-terribly weak-so I was happy to buy a shiny new internal linksys card (with a nice big antenna).  Not one lockup since.  Hope this helps at least some of those having this frustrating problem.

Since you changed your USB wireless card to internal you have no lockups. I am wondering whether it could be USB related. I don't have a wireless card at all, but maybe it could be the card reader I have constantly plugged in.

Just before mine crashed again, I was viewing the syslog and it was constantly adding lines about usb?? I reckon it could be the card reader I have. When I boot back into Linux I will see what difference it makes without it plugged in.

Regards,
Supremacy

---

### Post by marx2k on 2007-07-28
I can make my system freeze at will by either running 'compiz --replace' (currently working with latest build of compiz fusion) or 'metacity --replace' 

System fails to respond after that and only the mouse works.  This system was working GREAT with compiz fusion up until a few days ago.  Not sure of anything that may have changed, though there are daily builds of compiz.  It looks like right now my system is mainly working with the compiz desktop effects that comes with feisty as there IS a spinning cube, and all but none of the effects selected in ccsm are active (blur, paneling, etc)

Im running an NVidia 6800FX card on an AMD Athlon 2000+XP cpu in an FIC motherboard.  

Like I said, everything was great until just a few days ago.  I would love to know where to even start to look for the culprit! (I'm guessing that it's compiz as even today's compiz upgrade via aptitude froze my system as it was installing itself.)  I reboot with Alt+SysReq+S, Alt+SysReq+U, Alt+SysReq+B

I would really appreciate even a hint as to where to look. I wonder if removing compiz will remove the issue.  But at this point, even switching back to Metacity freezes the system :(

---

### Post by buntunub on 2007-07-28
It is indeed USB related I can testify! I never actually experienced hard lockups on my dv2415nr system, but quite often experienced momentary freezes, where I could move the mouse around but thats it. But these only lasted for a few seconds at a time so I thought nothing of it. I actually got my internal usb webcam working via luvcview but it would not record with audio. Anyway, long story short, I receive the same error messages when I activate and use my webcam, as when i added "noapic" to my boot parameters. Withing 5 minutes of booting up, I get "disabling IRQ7".  /var/log/messages revealed some kind of conflict on usb with my webcam. Now, (with noapic) I have not experienced any lockups or freezups whatsoever, but I can no longer reliably use my usb webcam. Hmmm.

---

### Post by psyke777 on 2007-07-28
My solution to the random freeze problem:

System Info:
Gigabyte GA-965P-DS3 motherboard
Core 2 Duo E6300
1Gb RAM
XFX 7950GT

1) Uninstall powernowd

2) With a text editor open (as root with "sudo") /etc/init.d/powernowd and change "ondemand" with "performance" (CPU always at max freq).

------------ original ---------------------
use_ondemand() {
for x in /sys/devices/system/cpu/*; do
echo -n ondemand >$x/cpufreq/scaling_governor;
---------------------------------------------

------------- modified ------------------
use_ondemand() {
for x in /sys/devices/system/cpu/*; do
echo -n performance > $x/cpufreq/scaling_governor;
-----------------------------------------------

3) kernel parameters: noapic nolapic irqpoll ht=on

Note: I still get messages about interrupt problems but no obvious impacts in performance.

---

### Post by Supremacy on 2007-07-28
> **psyke777 said:**
> My solution to the random freeze problem:

System Info:
Gigabyte GA-965P-DS3 motherboard
Core 2 Duo E6300
1Gb RAM
XFX 7950GT

1) Uninstall powernowd

2) With a text editor open (as root with "sudo") /etc/init.d/powernowd and change "ondemand" with "performance" (CPU always at max freq).

------------ original ---------------------
use_ondemand() {
for x in /sys/devices/system/cpu/*; do
echo -n ondemand >$x/cpufreq/scaling_governor;
---------------------------------------------

------------- modified ------------------
use_ondemand() {
for x in /sys/devices/system/cpu/*; do
echo -n performance > $x/cpufreq/scaling_governor;
-----------------------------------------------

3) kernel parameters: noapic nolapic irqpoll ht=on

Note: I still get messages about interrupt problems but no obvious impacts in performance.

Sounds interesting, however it may not work for me since I use a single core AMD64 CPU.

On top of my previous post, unplugging my card reader failed. It froze within minutes of lgging in this time. I have Compiz Fusion set to run on startup. I then started Avant (the dock thingy liek OSX). 

I have not yet tried viewing the syslog remotely yet. I might try that. Though, I dont just freeze (where you can move mouse), I completely lock and cannot move mouse and the only thing to do is press the reset button.

Regards,
Supremacy

---

### Post by Supremacy on 2007-07-29
ok, sorry for my double post, but i found one problem with my hardlocks. The following is recorded when I have an ssh connection ot my machine from a remote computer:

```
<3>[ 6508.493276] NTFS-fs warning (device sdf1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
<3>[ 6825.665108] NTFS-fs warning (device sdf1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.

```

I'll try searching and seeing if there may be a solution already. In my case it looks like NTFS though I dont have any NTFS partitions on my machine (or could it be my external HDD with data in NTFS)??

Regards,
Supremacy

---

### Post by marx2k on 2007-07-29
Which system log would anyone suggest looking at remotely when this sort of lockup occurs (freeze but with mouse movement)?

I would like to start tracking this down and since I can make the freeze happen at will (by enabling or disabling compiz), what would be anyone's suggestion?

---

### Post by Supremacy on 2007-07-29
> **marx2k said:**
> Which system log would anyone suggest looking at remotely when this sort of lockup occurs (freeze but with mouse movement)?

I would like to start tracking this down and since I can make the freeze happen at will (by enabling or disabling compiz), what would be anyone's suggestion?

I would use this command once you are logged in remotely.

```
sudo cat /proc/kmsg
```

Then, all you need to do is get the computer that has the problem to reproduce the error. The remote computer should give you the messages as to what might be wrong.

Regards,
Supremacy

---

### Post by soulglo83 on 2007-07-31
I have been having identical problems:  my computer freezes (generally while viewing flash videos or even downloaded videos, or using miro or democracy-player {both video players, and i use miro not dem-player}).  The system will freeze video output and continue processing audio for about 30 seconds.  during those 30 seconds the mouse cursor moves but the applications and desktop are unresponsive to clicks.  I cannot even change the caps locks on the keyboard!  i can however log in with ssh, and after doing so have produced the following:

dmesg output post crash:

[HTML][   25.184910] Enabling fast FPU save and restore... done.
[   25.184911] Enabling unmasked SIMD FPU exception support... done.
[   25.184916] Initializing CPU#0
[   25.184961] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   25.184980] spurious 8259A interrupt: IRQ7.
[   25.185765] Console: colour VGA+ 80x25
[   25.185964] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.186163] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.233504] Memory: 2067020k/2096000k available (1992k kernel code, 27724k reserved, 900k data, 328k init, 1178496k highmem)
[   25.233510] virtual kernel memory layout:
[   25.233511]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   25.233511]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.233512]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.233513]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.233513]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   25.233514]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   25.233515]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   25.233517] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.233627] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   25.233631] hpet0: 3 32-bit timers, 25000000 Hz
[   25.234634] Using HPET for base-timer
[   25.313420] Calibrating delay using timer specific routine.. 5337.69 BogoMIPS (lpj=10675394)
[   25.313447] Security Framework v1.0.0 initialized
[   25.313451] SELinux:  Disabled at boot.
[   25.313461] Mount-cache hash table entries: 512
[   25.313553] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   25.313558] monitor/mwait feature present.
[   25.313559] using mwait in idle threads.
[   25.313562] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.313563] CPU: L2 cache: 2048K
[   25.313565] CPU: Physical Processor ID: 0
[   25.313566] CPU: Processor Core ID: 0
[   25.313567] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   25.313573] Compat vDSO mapped to ffffe000.
[   25.313576] Remapping vsyscall page to ffffe000
[   25.313584] Checking 'hlt' instruction... OK.
[   25.329444] SMP alternatives: switching to UP code
[   25.329681] Early unpacking initramfs... done
[   25.528472] ACPI: Core revision 20060707
[   25.535285] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   25.537169] ACPI: setting ELCR to 0200 (from 0ca0)
[   25.539325] CPU0: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz stepping 02
[   25.539336] SMP alternatives: switching to SMP code
[   25.539384] Booting processor 1/1 eip 3000
[   25.549672] Initializing CPU#1
[   25.628596] Calibrating delay using timer specific routine.. 5333.43 BogoMIPS (lpj=10666868)
[   25.628600] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   25.628604] monitor/mwait feature present.
[   25.628605] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.628606] CPU: L2 cache: 2048K
[   25.628608] CPU: Physical Processor ID: 0
[   25.628609] CPU: Processor Core ID: 1
[   25.628610] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   25.628943] CPU1: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz stepping 02
[   25.628956] Total of 2 processors activated (10671.13 BogoMIPS).
[   25.736317] checking TSC synchronization across 2 CPUs: passed.
[    0.003991] Brought up 2 CPUs
[    0.044564] migration_cost=54
[    0.044731] Booting paravirtualized kernel on bare hardware
[    0.044786] Time: 22:47:37  Date: 06/30/107
[    0.044803] NET: Registered protocol family 16
[    0.044853] EISA bus registered
[    0.044856] ACPI: bus type pci registered
[    0.076759] PCI: PCI BIOS revision 3.00 entry at 0xfa6d0, last bus=2
[    0.076760] PCI: Using configuration type 1
[    0.076761] Setting up standard PCI resources
[    0.087698] ACPI: Interpreter enabled
[    0.087699] ACPI: Using PIC for interrupt routing
[    0.088117] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.088120] PCI: Probing PCI hardware (bus 00)
[    0.089441] Boot video device is 0000:01:00.0
[    0.089566] PCI: Transparent bridge - 0000:00:10.0
[    0.089590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.146284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.147154] ACPI Error (psargs-0355): [HPTF] Namespace lookup failure, AE_NOT_FOUND
[    0.147157] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LEG0.HPET._STA] (Node df8245f4), AE_NOT_FOUND
[    0.149141] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.149365] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.149590] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.149815] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.150040] ACPI: PCI Interrupt Link [LNK5] (IRQs *5 7 9 10 11 14 15)
[    0.150263] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.150491] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.150714] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.150937] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.151160] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151385] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[    0.151618] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151843] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
[    0.152066] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.152290] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.152513] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[    0.152737] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.152960] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.153185] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.153408] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.153682] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.153954] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.154227] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.154500] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.154771] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.155043] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.155316] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.155594] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.155865] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.156135] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.156407] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.156677] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.156947] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.157218] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.157488] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.157760] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.158030] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.158302] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.158576] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.158848] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.159120] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.159316] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.159324] pnp: PnP ACPI init
[    0.159747] ACPI Error (psargs-0355): [HPTF] Namespace lookup failure, AE_NOT_FOUND
[    0.159750] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LEG0.HPET._STA] (Node df8245f4), AE_NOT_FOUND
[    0.159800] ACPI Error (psargs-0355): [HPTF] Namespace lookup failure, AE_NOT_FOUND
[    0.159803] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LEG0.RTC_._CRS] (Node df82457c), AE_NOT_FOUND
[    0.163006] pnp: PnP ACPI: found 12 devices
[    0.163008] PnPBIOS: Disabled by ACPI PNP
[    0.163037] PCI: Using ACPI for IRQ routing
[    0.163039] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.273741] NET: Registered protocol family 8
[    0.273742] NET: Registered protocol family 20
[    0.273992] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[    0.273994] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.273996] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.273997] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[    0.273999] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.274001] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.274200] PCI: Bridge: 0000:00:03.0
[    0.274202]   IO window: d000-dfff
[    0.274204]   MEM window: efd00000-efdfffff
[    0.274207]   PREFETCH window: d0000000-dfffffff
[    0.274209] PCI: Bridge: 0000:00:10.0
[    0.274211]   IO window: e000-efff
[    0.274214]   MEM window: efc00000-efcfffff
[    0.274216]   PREFETCH window: efe00000-efefffff
[    0.274226] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.274233] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.274251] NET: Registered protocol family 2
[    0.319195] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.319270] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.319562] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.319716] TCP: Hash tables configured (established 131072 bind 65536)
[    0.319718] TCP reno registered
[    0.335197] checking if image is initramfs... it is
[    0.727938] Freeing initrd memory: 6784k freed
[    0.728355] audit: initializing netlink socket (disabled)
[    0.728367] audit(1185835657.312:1): initialized
[    0.728436] highmem bounce pool size: 64 pages
[    0.728494] VFS: Disk quotas dquot_6.5.1
[    0.728506] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.728538] io scheduler noop registered
[    0.728540] io scheduler anticipatory registered
[    0.728541] io scheduler deadline registered
[    0.728548] io scheduler cfq registered (default)
[    0.754145] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.754174] assign_interrupt_mode Found MSI capability
[    0.754175] Allocate Port Service[0000:00:03.0:pcie00]
[    0.754268] isapnp: Scanning for PnP cards...
[    1.106174] isapnp: No Plug & Play device found
[    1.118943] Real Time Clock Driver v1.12ac
[    1.118984] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.119092] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.119487] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.119604] mice: PS/2 mouse device common for all mice
[    1.119950] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.120048] input: Macintosh mouse button emulation as /class/input/input0
[    1.120071] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.120074] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.120218] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.120220] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.122544] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.122546] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.122620] EISA: Probing bus 0 at eisa.0
[    1.122625] Cannot allocate resource for EISA slot 1
[    1.122644] EISA: Detected 0 cards.
[    1.152683] TCP cubic registered
[    1.152689] NET: Registered protocol family 1
[    1.152703] Starting balanced_irq
[    1.152707] Using IPI No-Shortcut mode
[    1.152785] ACPI: (supports S0 S3 S4 S5)
[    1.152822]   Magic number: 15:830:806
[    1.152865]   hash matches device ptys0
[    1.152984] Time: tsc clocksource has been installed.
[    1.153025] Freeing unused kernel memory: 328k freed
[    2.282030] Capability LSM initialized
[    2.302422] ACPI: Fan [FAN] (on)
[    2.304580] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.304618] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.304622] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.305516] ACPI: Thermal Zone [THRM] (40 C)
[    2.568575] SCSI subsystem initialized
[    2.571810] libata version 2.20 loaded.
[    2.585358] usbcore: registered new interface driver usbfs
[    2.585374] usbcore: registered new interface driver hub
[    2.585388] usbcore: registered new device driver usb
[    2.586114] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 10
[    2.586116] PCI: setting IRQ 10 as level-triggered
[    2.586119] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 10 (level, low) -> IRQ 10
[    2.586126] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    2.586128] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.586210] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.586227] ehci_hcd 0000:00:0b.1: debug port 1
[    2.586230] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[    2.586235] ehci_hcd 0000:00:0b.1: irq 10, io mem 0xefffe000
[    2.586241] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.586293] usb usb1: configuration #1 chosen from 1 choice
[    2.586308] hub 1-0:1.0: USB hub found
[    2.586312] hub 1-0:1.0: 8 ports detected
[    2.602597] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.623463] Floppy drive(s): fd0 is 1.44M
[    2.627249] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    2.644717] FDC 0 is a post-1991 82077
[    2.693442] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 5
[    2.693444] PCI: setting IRQ 5 as level-triggered
[    2.693448] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUBA] -> GSI 5 (level, low) -> IRQ 5
[    2.693458] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    2.693461] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.693476] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    2.693486] ohci_hcd 0000:00:0b.0: irq 5, io mem 0xeffff000
[    2.754820] usb usb2: configuration #1 chosen from 1 choice
[    2.754839] hub 2-0:1.0: USB hub found
[    2.754845] hub 2-0:1.0: 8 ports detected
[    2.860828] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[    2.860830] PCI: setting IRQ 11 as level-triggered
[    2.860833] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 11 (level, low) -> IRQ 11
[    2.860838] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    2.860843] forcedeth: using HIGHDMA
[    3.383371] eth0: forcedeth.c: subsystem: 01019:2605 bound to 0000:00:14.0
[    3.383452] sata_nv 0000:00:0e.0: version 3.3
[    3.383663] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 10
[    3.383665] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSID] -> GSI 10 (level, low) -> IRQ 10
[    3.383678] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    3.383937] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001f800 irq 10
[    3.383958] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001f808 irq 10
[    3.383964] scsi0 : sata_nv
[    3.554676] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    3.698307] ata1: SATA link down (SStatus 0 SControl 300)
[    3.708692] ATA: abnormal status 0x7F on port 0x000109f7
[    3.708706] scsi1 : sata_nv
[    3.769186] usb 2-2: configuration #1 chosen from 1 choice
[    4.021458] ata2: SATA link down (SStatus 0 SControl 300)
[    4.031843] ATA: abnormal status 0x7F on port 0x00010977
[    4.032486] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 11
[    4.032488] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LFID] -> GSI 11 (level, low) -> IRQ 11
[    4.032502] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    4.032525] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001f300 irq 11
[    4.032543] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001f308 irq 11
[    4.032551] scsi2 : sata_nv
[    4.085285] usb 2-3: new low speed USB device using ohci_hcd and address 3
[    4.314759] usb 2-3: configuration #1 chosen from 1 choice
[    4.344608] ata3: SATA link down (SStatus 0 SControl 300)
[    4.354995] ATA: abnormal status 0x7F on port 0x000109e7
[    4.355010] scsi3 : sata_nv
[    4.631853] usb 2-4: new low speed USB device using ohci_hcd and address 4
[    4.667772] ata4: SATA link down (SStatus 0 SControl 300)
[    4.678157] ATA: abnormal status 0x7F on port 0x00010967
[    4.679049] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    4.679063] NFORCE-MCP51: chipset revision 161
[    4.679064] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    4.679070] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[    4.679075]     ide0: BM-DMA at 0xfd00-0xfd07, BIOS settings: hda:DMA, hdb:DMA
[    4.679081]     ide1: BM-DMA at 0xfd08-0xfd0f, BIOS settings: hdc:DMA, hdd:DMA
[    4.679086] Probing IDE interface ide0...
[    4.860339] usb 2-4: configuration #1 chosen from 1 choice
[    4.863381] usbcore: registered new interface driver hiddev
[    4.879286] input: Logitech Logitech Dual Action as /class/input/input1
[    4.879290] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:0b.0-3
[    4.889275] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input2
[    4.889282] input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:0b.0-4
[    4.906243] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input3
[    4.906248] input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:0b.0-4
[    4.906255] usbcore: registered new interface driver usbhid
[    4.906258] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.971058] hda: Maxtor 91080D5, ATA DISK drive
[    5.254315] hdb: MAXTOR 6L040J2, ATA DISK drive
[    5.314668] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.331777] Probing IDE interface ide1...
[    5.733066] hdc: TSSTcorpCD/DVDW SH-S162L, ATAPI CD/DVD-ROM drive
[    6.016325] hdd: Maxtor 6L250R0, ATA DISK drive
[    6.079794] ide1 at 0x170-0x177,0x376 on irq 15
[    6.144194] hda: max request size: 128KiB
[    6.144747] hda: 21095424 sectors (10800 MB) w/512KiB Cache, CHS=20928/16/63, UDMA(33)
[    6.144751] hda: cache flushes not supported
[    6.144775]  hda: hda1
[    6.156506] hdb: max request size: 128KiB
[    6.156637] hdb: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(133)
[    6.156771] hdb: cache flushes supported
[    6.156789]  hdb: hdb1 hdb2 < hdb5 >
[    6.180932] hdd: max request size: 512KiB
[    6.182466] hdd: 488397168 sectors (250059 MB) w/16384KiB Cache, CHS=30401/255/63, UDMA(33)
[    6.184037] hdd: cache flushes supported
[    6.184051]  hdd: hdd1 hdd2
[    6.196653] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.196659] Uniform CD-ROM driver Revision: 3.20
[    6.692431] Attempting manual resume
[    6.692433] swsusp: Resume From Partition 3:69
[    6.692434] PM: Checking swsusp image.
[    6.692600] PM: Resume from disk failed.
[    6.700333] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.700336] EXT3-fs: write access will be enabled during recovery.
[    9.304204] kjournald starting.  Commit interval 5 seconds
[    9.304212] EXT3-fs: recovery complete.
[    9.305551] EXT3-fs: mounted filesystem with ordered data mode.
[   19.256734] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.258817] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.268193] input: PC Speaker as /class/input/input4
[   19.416337] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   19.416353] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   19.452132] usbcore: registered new interface driver xpad
[   19.452136] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   19.530003] usb 2-2: USB disconnect, address 2
[   19.670269] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 7
[   19.670271] PCI: setting IRQ 7 as level-triggered
[   19.670275] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 7 (level, low) -> IRQ 7
[   19.670286] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   19.708222] NET: Registered protocol family 17
[   19.712332] usb 2-2: new full speed USB device using ohci_hcd and address 5
[   19.879890] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   19.917396] input: ImExPS/2 Generic Explorer Mouse as /class/input/input5
[   19.919023] usb 2-2: configuration #1 chosen from 1 choice
[   19.927977] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04E8 pid 0x326C
[   19.927986] usbcore: registered new interface driver usblp
[   19.927988] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   20.116353] fuse init (API version 7.8)
[   20.177905] lp: driver loaded but no devices found
[   20.195668] Adding 1646620k swap on /dev/disk/by-uuid/d60c9034-7ed9-4691-85ab-d2abc85e5739.  Priority:-1 extents:1 across:1646620k
[   20.337091] EXT3 FS on hdb1, internal journal
[   20.465115] kjournald starting.  Commit interval 5 seconds
[   20.465119] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   20.465349] EXT3 FS on hdd1, internal journal
[   20.465351] EXT3-fs: recovery complete.
[   20.465536] EXT3-fs: mounted filesystem with ordered data mode.
[   23.415785] NET: Registered protocol family 10
[   23.415850] lo: Disabled Privacy Extensions
[   26.691815] ACPI Error (psargs-0355): [HPTF] Namespace lookup failure, AE_NOT_FOUND
[   26.691820] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LEG0.HPET._STA] (Node df8245f4), AE_NOT_FOUND
[   26.702139] No dock devices found.
[   26.710884] input: Power Button (FF) as /class/input/input6
[   26.710901] ACPI: Power Button (FF) [PWRF]
[   26.710925] input: Power Button (CM) as /class/input/input7
[   26.710938] ACPI: Power Button (CM) [PWRB]
[   26.844528] Using specific hotkey driver
[   26.886358] ibm_acpi: ec object not found
[   26.934286] pcc_acpi: loading...
[   31.183870] Linux agpgart interface v0.102 (c) Dave Jones
[   31.221836] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   31.224701] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   31.224717] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   31.245310] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 5
[   31.245313] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNK5] -> GSI 5 (level, low) -> IRQ 5
[   31.418145] ppdev: user-space parallel port driver
[   32.118785] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   32.118788] apm: disabled - APM is not SMP safe.
[   32.355693] [fglrx] total      GART = 130023424
[   32.355697] [fglrx] free       GART = 114032640
[   32.355698] [fglrx] max single GART = 114032640
[   32.355700] [fglrx] total      LFB  = 268304384
[   32.355701] [fglrx] free       LFB  = 250474496
[   32.355702] [fglrx] max single LFB  = 250474496
[   32.355703] [fglrx] total      Inv  = 0
[   32.355704] [fglrx] free       Inv  = 0
[   32.355705] [fglrx] max single Inv  = 0
[   32.355706] [fglrx] total      TIM  = 0
[   32.737790] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   32.990912] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   33.004005] NFSD: starting 90-second grace period
[   34.904650] /dev/vmmon[5713]: Module vmmon: registered with major=10 minor=165
[   34.904698] /dev/vmmon[5713]: Module vmmon: initialized
[   35.076128] /dev/vmnet: open called by PID 5748 (vmnet-bridge)
[   35.076159] /dev/vmnet: hub 0 does not exist, allocating memory.
[   35.076182] /dev/vmnet: port on hub 0 successfully opened
[   35.076232] bridge-eth0: enabling the bridge
[   35.076240] bridge-eth0: up
[   35.076248] bridge-eth0: already up
[   35.076257] bridge-eth0: attached
[   35.202495] /dev/vmnet: open called by PID 5762 (vmnet-natd)
[   35.202528] /dev/vmnet: hub 8 does not exist, allocating memory.
[   35.202551] /dev/vmnet: port on hub 8 successfully opened
[   37.027594] Bluetooth: Core ver 2.11
[   37.027645] NET: Registered protocol family 31
[   37.027648] Bluetooth: HCI device and connection manager initialized
[   37.027653] Bluetooth: HCI socket layer initialized
[   37.072522] Bluetooth: L2CAP ver 2.8
[   37.072527] Bluetooth: L2CAP socket layer initialized
[   37.088805] Bluetooth: RFCOMM socket layer initialized
[   37.088819] Bluetooth: RFCOMM TTY layer initialized
[   37.088821] Bluetooth: RFCOMM ver 1.8
[   43.290550] eth0: no IPv6 routers present
[   45.124063] /dev/vmnet: open called by PID 6020 (vmnet-netifup)
[   45.124296] /dev/vmnet: hub 1 does not exist, allocating memory.
[   45.124501] /dev/vmnet: port on hub 1 successfully opened
[   45.130380] /dev/vmnet: open called by PID 6028 (vmnet-netifup)
[   45.130508] /dev/vmnet: port on hub 8 successfully opened
[   45.204501] /dev/vmnet: open called by PID 6043 (vmnet-dhcpd)
[   45.204706] /dev/vmnet: port on hub 8 successfully opened
[   45.211703] /dev/vmnet: open called by PID 6039 (vmnet-dhcpd)
[   45.211893] /dev/vmnet: port on hub 1 successfully opened
[   55.267160] vmnet1: no IPv6 routers present
[   55.550417] vmnet8: no IPv6 routers present
[/HTML]
lspci -vvnn:
> 00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a3] (rev a2)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [40] HyperTransport: Host or Secondary Interface
		Command: WarmRst+ DblEnd-
		Link Control: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config: MLWI=8bit MLWO=8bit LWI=8bit LWO=8bit
		Revision ID: 0.16

00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.1 RAM memory [0500]: nVidia Corporation Unknown device [10de:03bc] (rev a1)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efd00000-efdfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device [10de:0c55]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x8, ASPM L0s, Port 0
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x8
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 0, PowerLimit 0.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=9 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn+ LSEn+ ExtCTL- 64b-
		Link Config 0: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 1.0GHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 7
	Region 4: I/O ports at 1c00 [size=64]
	Region 5: I/O ports at 1c80 [size=64]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a3)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at effff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3) (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at efffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at fd00 [size=16]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at f800 [size=16]
	Region 5: Memory at efffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at 09e0 [size=8]
	Region 1: I/O ports at 0be0 [size=4]
	Region 2: I/O ports at 0960 [size=8]
	Region 3: I/O ports at 0b60 [size=4]
	Region 4: I/O ports at f300 [size=16]
	Region 5: Memory at efffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: efc00000-efcfffff
	Prefetchable memory behind bridge: efe00000-efefffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [b8] Subsystem: nVidia Corporation Unknown device [10de:cb84]
	Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 7
	Region 0: Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
		Masking: 00000000  Pending: 00000000
	Capabilities: [6c] HyperTransport: MSI Mapping

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2605]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at efffb000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at f200 [size=8]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV530 [Radeon X1600] [1002:71c2] (prog-if 00 [VGA])
	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:0144]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at efdf0000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at de00 [size=256]
	[virtual] Expansion ROM at efd00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <4us, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x8
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000

01:00.1 Display controller [0380]: ATI Technologies Inc RV530 [Radeon X1600] (Secondary) [1002:71e2]
	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:0145]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Region 0: Memory at efde0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <4us, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x8

/var/log/syslog:
> Jul 31 00:37:42 mathew-desktop gconfd (root-9787): Exiting
Jul 31 00:37:46 mathew-desktop gconfd (root-9813): starting (version 2.18.0.1), pid 9813 user 'root'
Jul 31 00:37:46 mathew-desktop gconfd (root-9813): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 00:37:46 mathew-desktop gconfd (root-9813): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 31 00:37:46 mathew-desktop gconfd (root-9813): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 00:37:46 mathew-desktop gconfd (root-9813): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 00:37:46 mathew-desktop gconfd (root-9813): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 00:38:16 mathew-desktop gconfd (root-9813): GConf server is not in use, shutting down.
Jul 31 00:38:16 mathew-desktop gconfd (root-9813): Exiting
Jul 31 00:38:21 mathew-desktop gconfd (root-9874): starting (version 2.18.0.1), pid 9874 user 'root'
Jul 31 00:38:21 mathew-desktop gconfd (root-9874): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 00:38:21 mathew-desktop gconfd (root-9874): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 31 00:38:21 mathew-desktop gconfd (root-9874): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 00:38:21 mathew-desktop gconfd (root-9874): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 00:38:21 mathew-desktop gconfd (root-9874): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 00:38:51 mathew-desktop gconfd (root-9874): GConf server is not in use, shutting down.
Jul 31 00:38:51 mathew-desktop gconfd (root-9874): Exiting
Jul 31 00:39:02 mathew-desktop gconfd (root-9934): starting (version 2.18.0.1), pid 9934 user 'root'
Jul 31 00:39:02 mathew-desktop gconfd (root-9934): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 00:39:02 mathew-desktop gconfd (root-9934): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 31 00:39:02 mathew-desktop gconfd (root-9934): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 00:39:02 mathew-desktop gconfd (root-9934): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 00:39:02 mathew-desktop gconfd (root-9934): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 00:40:02 mathew-desktop gconfd (root-9934): GConf server is not in use, shutting down.
Jul 31 00:40:02 mathew-desktop gconfd (root-9934): Exiting
Jul 31 00:40:16 mathew-desktop gconfd (root-10033): starting (version 2.18.0.1), pid 10033 user 'root'
Jul 31 00:40:16 mathew-desktop gconfd (root-10033): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 00:40:16 mathew-desktop gconfd (root-10033): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 31 00:40:16 mathew-desktop gconfd (root-10033): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 00:40:16 mathew-desktop gconfd (root-10033): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 00:40:16 mathew-desktop gconfd (root-10033): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 01:08:05 mathew-desktop -- MARK --
Jul 31 01:17:02 mathew-desktop /USR/SBIN/CRON[11180]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 31 01:28:05 mathew-desktop -- MARK --
Jul 31 01:29:27 mathew-desktop gconfd (root-10033): Exiting
Jul 31 01:29:39 mathew-desktop gconfd (mathew-6092): SIGHUP received, reloading all databases
Jul 31 01:29:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 01:29:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readwrite:/home/mathew/.gconf" to a writable configuration source at position 1
Jul 31 01:29:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 01:29:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 01:29:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 01:31:39 mathew-desktop gconfd (mathew-6092): SIGHUP received, reloading all databases
Jul 31 01:31:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 01:31:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readwrite:/home/mathew/.gconf" to a writable configuration source at position 1
Jul 31 01:31:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 01:31:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 01:31:40 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 01:32:09 mathew-desktop gconfd (mathew-6092): SIGHUP received, reloading all databases
Jul 31 01:32:09 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 01:32:09 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readwrite:/home/mathew/.gconf" to a writable configuration source at position 1
Jul 31 01:32:09 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 01:32:09 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 01:32:09 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 01:33:09 mathew-desktop gconfd (mathew-6092): SIGHUP received, reloading all databases
Jul 31 01:33:10 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 01:33:10 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readwrite:/home/mathew/.gconf" to a writable configuration source at position 1
Jul 31 01:33:10 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 01:33:10 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 01:33:10 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 01:34:39 mathew-desktop gconfd (mathew-6092): SIGHUP received, reloading all databases
Jul 31 01:34:39 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 31 01:34:39 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readwrite:/home/mathew/.gconf" to a writable configuration source at position 1
Jul 31 01:34:39 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 31 01:34:39 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 31 01:34:39 mathew-desktop gconfd (mathew-6092): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 31 01:39:19 mathew-desktop kernel: [10276.854841] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul 31 01:39:19 mathew-desktop kernel: [10276.854845] apm: disabled on user request.
Jul 31 01:39:51 mathew-desktop hcid[5854]: Stopping SDP server
Jul 31 01:39:51 mathew-desktop hcid[5854]: Unregister path: /org/bluez
Jul 31 01:39:51 mathew-desktop hcid[5854]: Exit

There at 1:08am u can see the crash, although there are practically no details about it in any of the output.  Another oddity is that im running very different hardware than most, here is my lspci:

> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation Unknown device 03bc (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

These problems appeared after a mobo/proc/ram upgrade (ecs nf650iSLIT-A, Intel E4400 Core-Duo, 2GB of Corsair DDR800).  I did what most people do after upgrading that extensively and I reinstalled, sure enough the problems reappeared immediately.  I am currently attempting an upgrade to Gutsy as a last ditch effort to fix this.  Failing this I might revert back to Dapper/Edgy (I'm not upset enough however to switch back too... well you know).

---

### Post by Supremacy on 2007-07-31
OK, so I continued on using a remote machine to obtain info on my freezes (hard lock. No mouse movement at all.)

Here's what kmsg outputted:
```
<6>[  203.095279] usb 2-8: reset high speed USB device using ehci_hcd and address 3
<6>[  225.469268] usb 2-8: reset high speed USB device using ehci_hcd and address 3
<6>[  454.908613] attempt to access beyond end of device
<6>[  454.908621] hdd: rw=0, want=28836344, limit=8611904
<6>[  454.908625] attempt to access beyond end of device
<6>[  454.908627] hdd: rw=0, want=28836348, limit=8611904
<6>[  454.908629] attempt to access beyond end of device
<6>[  454.908631] hdd: rw=0, want=28836352, limit=8611904
<6>[  454.908633] attempt to access beyond end of device
<6>[  454.908635] hdd: rw=0, want=28836356, limit=8611904
<6>[  454.908637] attempt to access beyond end of device
<6>[  454.908639] hdd: rw=0, want=28836360, limit=8611904
<6>[  454.908641] attempt to access beyond end of device
<6>[  454.908643] hdd: rw=0, want=28836364, limit=8611904
<6>[  454.908645] attempt to access beyond end of device
<6>[  454.908647] hdd: rw=0, want=28836368, limit=8611904
<6>[  454.908648] attempt to access beyond end of device
<6>[  454.908650] hdd: rw=0, want=28836372, limit=8611904
<6>[  454.908653] attempt to access beyond end of device
<6>[  454.908655] hdd: rw=0, want=28836312, limit=8611904
<6>[  454.908657] attempt to access beyond end of device
<6>[  454.908659] hdd: rw=0, want=28836316, limit=8611904
<6>[  577.386017] usb 2-8: device firmware changed
<6>[  577.386038] usb 2-8: USB disconnect, address 3
<5>[  577.386790] sdc: Write Protect is off
<7>[  577.386792] sdc: Mode Sense: 00 00 00 00
<3>[  577.386794] sdc: assuming drive cache: write through
<5>[  577.387435] sdc: Write Protect is off
<7>[  577.387437] sdc: Mode Sense: 00 00 00 00
<3>[  577.387439] sdc: assuming drive cache: write through
<3>[  577.633983] usb 2-8: unable to read config index 0 descriptor/start
<3>[  577.633989] usb 2-8: chopping to 0 config(s)
<7>[  897.661175] ppdev0: registered pardevice
<6>[  988.393312] attempt to access beyond end of device
<6>[  988.393320] hdd: rw=0, want=28836312, limit=8611904
<4>[  988.393323] printk: 12 messages suppressed.
<3>[  988.393325] Buffer I/O error on device hdd, logical block 7209077
<6>[  988.393784] attempt to access beyond end of device
<6>[  988.393786] hdd: rw=0, want=28836320, limit=8611904
<3>[  988.393788] Buffer I/O error on device hdd, logical block 7209079
<6>[  988.393823] attempt to access beyond end of device
<6>[  988.393825] hdd: rw=0, want=28836324, limit=8611904
<3>[  988.393827] Buffer I/O error on device hdd, logical block 7209080
<6>[  988.393861] attempt to access beyond end of device
<6>[  988.393863] hdd: rw=0, want=28836328, limit=8611904
<3>[  988.393865] Buffer I/O error on device hdd, logical block 7209081
<6>[  988.393894] attempt to access beyond end of device
<6>[  988.393897] hdd: rw=0, want=28836332, limit=8611904
<3>[  988.393899] Buffer I/O error on device hdd, logical block 7209082
<6>[  988.393926] attempt to access beyond end of device
<6>[  988.393928] hdd: rw=0, want=28836336, limit=8611904
<3>[  988.393930] Buffer I/O error on device hdd, logical block 7209083
<6>[  988.393955] attempt to access beyond end of device
<6>[  988.393958] hdd: rw=0, want=28836340, limit=8611904
<3>[  988.393959] Buffer I/O error on device hdd, logical block 7209084
<6>[  988.393986] attempt to access beyond end of device
<6>[  988.393988] hdd: rw=0, want=28836312, limit=8611904
<3>[  988.393990] Buffer I/O error on device hdd, logical block 7209077
<6>[  988.394016] attempt to access beyond end of device
<6>[  988.394018] hdd: rw=0, want=28836316, limit=8611904
<3>[  988.394020] Buffer I/O error on device hdd, logical block 7209078
```

Looks like my problem is HDD related. Will have to get a new HDD to see if the issue is resolved.

Regards,
Supremacy

---

### Post by lynxus on 2007-07-31
I get random system freezes, but found it was because of my network cable. Whenever it came loose and lost its connection the system would crash.

---

### Post by Supremacy on 2007-07-31
> **lynxus said:**
> I get random system freezes, but found it was because of my network cable. Whenever it came loose and lost its connection the system would crash.

It may be a network part of the kernel (whatever controls the network services)??

---

### Post by soulglo83 on 2007-07-31
ok if you read my post on page 53, DO NOT upgrade to gutsy if you share the same symptoms as me (keyboard becomes unresonsive, except to alt+prntscrn+b which is a hard reboot, i cant even turn on caps lock!) and the mouse moves, but otherwise the interface is unresponsive, aside from the mouse nothing else updates on the screen (video/the time in the corner, etc) and sound continues playing for roughly 15-20 seconds before completely halting.  I can still ssh to it, but i cannot restore the machine to a functioning state without rebooting (no stopping and restarting gdm doesn't work, it doesn't fail in the ssh session, but the 'sick' machine remains unresponsive).

DO NOT UPGRADE TO GUTSY!  The crashing is far more frequent and even involves sticking a key that is not being pressed so that it fills any text boxes that you click.  I have since downgraded to edgy, where after 45 minutes i have yet to see a crash.  This happened roughly 2-3 times every 8 hours i was on the computer with feisty, so I'll update you guys.

---

### Post by Bealer on 2007-07-31
> **soulglo83 said:**
> ok if you read my post on page 53, DO NOT upgrade to gutsy if you share the same symptoms as me (keyboard becomes unresonsive, except to alt+prntscrn+b which is a hard reboot, i cant even turn on caps lock!) and the mouse moves, but otherwise the interface is unresponsive, aside from the mouse nothing else updates on the screen (video/the time in the corner, etc) and sound continues playing for roughly 15-20 seconds before completely halting.  I can still ssh to it, but i cannot restore the machine to a functioning state without rebooting (no stopping and restarting gdm doesn't work, it doesn't fail in the ssh session, but the 'sick' machine remains unresponsive).

DO NOT UPGRADE TO GUTSY!  The crashing is far more frequent and even involves sticking a key that is not being pressed so that it fills any text boxes that you click.  I have since downgraded to edgy, where after 45 minutes i have yet to see a crash.  This happened roughly 2-3 times every 8 hours i was on the computer with feisty, so I'll update you guys.

Hmmm, this is a strange bug, especially as everyone has different hardware and symptoms. Saying not to upgrade isn't the right thing given the situation.

I for example, have that exact bug you mention in Feisty. It goes away if I use the 386 kernel. 

And when using Gutsy with the generic kernel it's fine. I've not had a single freeze.

---

### Post by soulglo83 on 2007-07-31
your probably right, it might work for other people to upgrade to gutsy.  in my opinion this looks like a kernel problem, to not be related directly to 3d video processing and to occur at random, it is almost certainly the kernel.  updating to gutsy means you get a newer kernel, which may or may not help you.  I have however since downgrading to edgy been playing counter strike through wine (which doesn't hard lock my computer everytime i join a server (which it did consistently in feisty)!) for the past 4 hours, and not even so much as a hiccup.  Edgy's stability is for me at least, leagues above feisty and gutsy.  For those who are hopeless but not so hopeless they will switch to MS, you should try downgrading to edgy.  Using another modern distro like mepis or linux mint (which are both currently based on ubuntu) or even some which arent (mandriva) will likely yield the same instability.

---

### Post by Digitallysick on 2007-08-01
I used sabayon 3.4a and i got the same freeze, i thought maybe it was my bios settings, i backed up my bios and then set it to defaults, and rebooted, i still got freezes, although it acted as if it was "working through" them, still after a few hours the same problem. Im thinking of going to gusty, but im worried it has the same kernel as sabayon3.4a?

---

### Post by Bealer on 2007-08-01
> **soulglo83 said:**
> your probably right, it might work for other people to upgrade to gutsy.  in my opinion this looks like a kernel problem, to not be related directly to 3d video processing and to occur at random, it is almost certainly the kernel.  updating to gutsy means you get a newer kernel, which may or may not help you.  I have however since downgrading to edgy been playing counter strike through wine (which doesn't hard lock my computer everytime i join a server (which it did consistently in feisty)!) for the past 4 hours, and not even so much as a hiccup.  Edgy's stability is for me at least, leagues above feisty and gutsy.  For those who are hopeless but not so hopeless they will switch to MS, you should try downgrading to edgy.  Using another modern distro like mepis or linux mint (which are both currently based on ubuntu) or even some which arent (mandriva) will likely yield the same instability.

Yeah I'm of the opinion that it's a kernel problem too. It's a strange one. Just so hard to pin down.

I did some experimenting last night. I went back to the Generic kernel in Feisty and haven't had a freeze. Early days, but got me wondering if they've released something that has fixed it for my setup. The 386 kernel works for me without a single problem, but I'd rather run the generic kernel.

Gutsy is fine for me. Or at least has been so far. One of my reasons for trying Tribe 3 was the newer kernel to see if it made a difference.

I've tried PC Linux OS 2007 and that was fine. Can't remember which kernel version it was running though. It even got my an xserver bug I get with Ubuntu.

And Edgy of course is rock solid, never had a problem with it. In Gutsy I just hope they fix the kernel problem, and (for me) my xserver problem (whereby my monitors resolution gets picked as 1680x1680!?!?). 

Did you say you'd tried the 386 kernel in Feisty? Might be worth a try.

---

### Post by Supremacy on 2007-08-01
> **Bealer said:**
> Yeah I'm of the opinion that it's a kernel problem too. It's a strange one. Just so hard to pin down.

I did some experimenting last night. I went back to the Generic kernel in Feisty and haven't had a freeze. Early days, but got me wondering if they've released something that has fixed it for my setup. The 386 kernel works for me without a single problem, but I'd rather run the generic kernel.

Gutsy is fine for me. Or at least has been so far. One of my reasons for trying Tribe 3 was the newer kernel to see if it made a difference.

I've tried PC Linux OS 2007 and that was fine. Can't remember which kernel version it was running though. It even got my an xserver bug I get with Ubuntu.

And Edgy of course is rock solid, never had a problem with it. In Gutsy I just hope they fix the kernel problem, and (for me) my xserver problem (whereby my monitors resolution gets picked as 1680x1680!?!?). 

Did you say you'd tried the 386 kernel in Feisty? Might be worth a try.

I myself run the i386 kernel and still get the freezes. Generic kernel did it as well. I think it varies form pc to pc, but it would be worth a try.

Regards,
Supremacy

---

### Post by Jack H on 2007-08-02
I have not followed all this closely, but have attempted to weather the freeze storm and finally 7.04 really went down.
      Here is what I observed.  The GUI login in both KDE and Gnome would not accept my user name and password.  I used Ctrl+Alt+F1 and went to the command line where the system accepted my username and password.  Then used startx to get into GUI (Gnome only) and the cripple system allowed me to send important data out to CD.
    Now here is the relevent observation.  I had been advised previously there was likely a problem with X11.  OK -- Next -- after I did too many requests of the crippled system the GUI disappeared and the line read (from memory (mine)) that the connection to the X server had failed.
     I suppose this is only a vague clue but that was what happened here.  Hope it helps someone who is more proficient at diagnostics.
     I since reinstalled 6.06 Dapper and, though the bells and whistles are reduced, this is much more satisfying -- A really good Linux experience again.  I will use extreme caution in the future about upgrading.  Thanks for the experience and my hindsight is much improved.

     Again -- hope this helps,   Jack

---

### Post by soulglo83 on 2007-08-02
OK for my freezing issue, which seems identical to the thread poster's and many others in this thread (visually what appears to be a hard lockup, mouse still moves, keyboard and gui completely unresponsive [cannot toggle caps/num lock but the alt+prntscrn+k/s/t/b/etc still work somehow]) The system can be rescued but only thru ssh to kill X.

Here is a forum post covering my machine specs/symptoms:
[http://ubuntuforums.org/showthread.php?p=3120369#post3120369](http://ubuntuforums.org/showthread.php?p=3120369#post3120369)

Here is a link to what I believe is a bug report for the issue:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/98783](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/98783)

Here is the bug I filed:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/129895](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/129895)

Its noted in the second link, to the previously existing bug, that its known that Xorg consumes lots of processor and ram (when web browsing its in the order of 10mb of ram a minute on a 2gb ram machine, if im watching youtube or watching video's outside of a flashplayer, it swells at about 50-80mb a minute) but it doesn't mention its impact on stability!  It is also severity low, from what I understand, a bug thats in a part of upstream and distribution that causes what appears to be a hard lockup is a HUGE concern!  The only 'fix' is to ssh in and kill X.  So I filed my own report, I did so because this thread has grown absurdly long and now holds posts like the one  above which are completely unrelated (as the user notes 'he hasn't read the thread').

---

### Post by Phayder92889 on 2007-08-03
I dunno if this will help anyone else, but it's been working fine for me after I killed the Beagle search tool at startup (if someone could help me figure out how to stop if from autostarting, that'd be great), because (I dunno what the real name for it is, help?) it was sucking up all of my RAM when I'd let the computer idle.

My computer would freeze completely, though. No mouse motion, I couldn't SSH into it, the keyboard only worked with the Alt+PrntScrn+B combo. Also, I updated my video drivers and correctly formatted a few lines that I'd entered into my xorg.conf.

My specs are as follows: 
AMD 3500+ 2.2gHz
1gb RAM (Something red by PATRIOT, it was a gift)
NVidia 7600GS-AGP (256mb)
I had Ubuntu Ultimate Gamer's Edition (it had a lot of cool stuff with it, not just games...), and upgraded it through Update Manager to Fiesty from Edgy

Uhh... Dunno if there's anything else I can say, but I've been stable for a while now, even expecting everything to freeze when I tried to do anything.

---

### Post by octopuskevin on 2007-08-04
I have been having the same problems reported by the majority of users i.e. system crash, mouse movement is fine, however keyboard lockup and hard reboot is required...

i few things i had noticed / done...

originally i thought it was my nividia card 5400,, in which i found the crashing happened more frequently when using beryl. so i upgrade the video drivers from the nvidia site but that did not help.

after removing the card and using the onboard video [SIS], crashes were less frequent, but again like most people, it would exhibit crashing during high load activity such as youtube videos or my favourite break.com :P

I also removed my gigabyte card and used the onboard, but that does not affect the change of crashing

has anyone experienced some strange things such as loss of video?
I found with the SIS card, sometimes the screen would flash BLACK for a half second, and than resume like normal. Normally the computer would end up crashing afterwards, but this symptom is quite rare.. however with the Nvidia card, not only would it flash black, it would sometimes be unable to acquire a video signal, and my monitor would flash the 'no input connected' regardless of DVI or VGA cable. while simultaneously going into a hard-lock with no keyboard inputs available.

I ran a mem test for a whole night, and there were no errors, so I do believe the problem not to be hardware based, but more of a kernel issue.

- Kevin

---

### Post by Digitallysick on 2007-08-04
I think i fixed my feisty fawn crashing,  i finally got tired of all the issues, and decided to reformat, (which i have tried before to no avail) but this time, since i have a lga 775 EMT64 processor, i downloaded feisty fawn 64bit, and installed it. I compiled compiz fusion from source. And im talking to you right now from it, with xgl and the effects on, im on day 4 with no freeze (a new record). I will check back in another week to let you guys know if im still running strong.

Maybe compling it from source was the issue, or something to do with the 32 bit install of feisty fawn.

---

### Post by soulglo83 on 2007-08-04
It also might be the updates rolled thru 08/03/07.  It seems to have slowed the memory loss to Xorg that was leading up to the cataclysmic system freeze (which was resulting in my computer becoming completely unresponsive, though the mouse remained moveable).  I'll keep my cpu on and let you guys know how its working out.

---

### Post by majoridiot on 2007-08-04
i started having these problems (screens would freeze, refresh rates would go wonky, keyboard 
frozen with mouse still movable but otherwise not functional) when i updated edgy last week.  i 
then upgraded to feisty with the same problems- only worse.

i did a fresh format and install of feisty, but the problem persisted and made the system unusable- 
it would reliably freeze within an hour... sometimes after only minutes.

at first, it seemed to be a firefox bug, then a mythtv bug.  eventually, it became apparent it was a 
system problem and not related to one app in particular.  by all appearances, it looks to be a problem 
with X- at least in my case.  when the "freeze" occurred, running *top* from an ssh showed X was
consuming 100% of the cpu.

i *think* (crossing fingers so as not to jinx things) i have fixed it... thanks to info from psyke777 in 
post #523 of this thread.

my system:

asus p5ne-sli mobo
core 2 duo e6300
2GB ram
2 7600 GTKO-sli vid cards

to recap psyke777's fix:

```
$ sudo apt-get remove powernowd
```

then

```
$ gksudo gedit /etc/init.d/powernowd
```

search for:

```
use_ondemand() {
        for x in /sys/devices/system/cpu/*/; do
	    echo -n **ondemand** >$x/cpufreq/scaling_governor;
	    status=$?
```

and change "ondemand" to "performance", so it reads:

```
use_ondemand() {
        for x in /sys/devices/system/cpu/*/; do
	    echo -n **performance** >$x/cpufreq/scaling_governor;
	    status=$?
```

then, add additional kernel parameters- noapic nolapic irqpoll ht=on:

```
$ gksudo gedit /boot/grub/menu.lst
```

in my case, my boot kernel went from:

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=42ab0f44-ab10-4ebd-a52d-cd514b97530f ro quiet splash
```

to:

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=42ab0f44-ab10-4ebd-a52d-cd514b97530f ro quiet splash noapic nolapic irqpoll ht=on
```

after rebooting, i've been at it for over two hours really taxing the system... running mythtvfrontend, 
3 firefox browsers, 4 gftps downloading at max and transcoding a dvd all at once without any problems.

no idea how this may or may not affect single core or AMD systems, but it looks like it fixed it for me.

(hopefully i will not need to correct that last statement with another post [-o< )

**EDIT:** four days later and not a single freeze.   lirc (mceusb2) "stutters" on key repeats, but that is
livable until the kernel and/or X are properly fixed.  both proc. cores function as they should.

---

### Post by soulglo83 on 2007-08-06
thank you so much majoridiot (your choice of a psudoname not mine!) i greatly appreciate this advice, apparently altering powernowd's behavior was the step I missed.  i have been up for 2 days and 3 hours and not so much as a hiccup.  thank god I can finally 'stick a fork in this one' its been such a pain in the ***!

---

### Post by fattom23 on 2007-08-06
What I did, and this got rid of the problem completely, was to temporarily add the gutsy repository to my sources and then upgraded the the 2.6.22-generic kernel.  No more freezes.  Actually, your problem sounds a lot like mine.  What happened was that everything was still working except for the mouse buttons.  If you primarily use the GUI, that's almost as good as locked up.  I switched to the new kernel about 24 hours ago, and haven't gotten a mouse lock-up yet.  Hope this helps you.  Peace.

---

### Post by majoridiot on 2007-08-06
> **fattom23 said:**
> What I did, and this got rid of the problem completely, was to temporarily add the gutsy repository to my sources and then upgraded the the 2.6.22-generic kernel.  No more freezes.  Actually, your problem sounds a lot like mine.  What happened was that everything was still working except for the mouse buttons.  If you primarily use the GUI, that's almost as good as locked up.  I switched to the new kernel about 24 hours ago, and haven't gotten a mouse lock-up yet.  Hope this helps you.  Peace.

that's good info to know.  although the info i posted above fixed my freeze problems, there are minor hiccups 
(with lirc, for example) that are annoying but workable for now.  hopefully we'll see 2.6.22 in the feisty repository 
soon, so the kernel options i had to add can be removed and everything will be back to normal.

---

### Post by fschaefer on 2007-08-06
Hi, fellow sufferers ;)

Here's my part of the Story.... and another solution...

I've had freezes for months now; my machine crashed often enough so that couldn't even think of using it productively. Fact is... all I did that time was trying to solve this mysterious problem...

I tried **every single** possible solution from this thread and from countless other forums. However, nothing worked. The system kept freezing, the screen would flash for a moment and then Xorg would leave me with 100% cpu usage, being able to do nothing but moving the mouse and ssh into the machine.

Accidentally, I booted into windows last week (maybe I should have done earlier ;) ) and guess what... Screen flashing for a moment and then... darkness. On the nvidia forum I had read that my dmesg-output might point out that it is a hardware issue, but after so many others had that problem, I didn't want to realize. However, after the Windows-freezes, I controlled every single capacitor in my computer. After finding a defect one in the power supply unit, I immediately got a new one.

Guess what: The system was freezing like nothing had changed.

Sorry, I didn't want to bore you with the anamnesis :). So... let's come up to the point. Did I mention I have an **Asus P4C-800E Deluxe Mainboard with passive northbridge cooler**?
After the new psu didn't change anything, I controlled the mainboard once again. I knew that the cpu temp was quite ok, but I wanted to know about the other parts.

**The northbridge cooler was so damn hot, I couldn't even touch it!** After removing the heatsink, I noticed that the die already had this kind of blue-magenta-color. I'm talking about that color, nobody wants his Northbridg to have :)

So I went to the next store and got a super-silent five-bucks-active-cooler. **No freezes for over 4 days now!!!**

I'm not saying that the majority of people in this thread might have a hardware-related problem like I did; I just want you to keep in mind that it might be worthwile looking at your hardware too.

---

### Post by Malmsdoom on 2007-08-07
I had exactly the same problems with random freezes originally described in the first post (feisty). Strangely enough there were no problems with edgy and I didn't move the computer for 1 millimetre during the upgrade. My problems are now gone, since I opened my tower and checked and reassembled the components. So in my case the feisty-kernel seemed to be more sensible to hardware issues then the edgy-kernel. I know that is an assertion with no logical fundament, but perhaps this post can help some people who are especially desperate.
Now my Feisty is rock-stable.

---

### Post by spartus4 on 2007-08-07
I think I have discovered a fix, atleast for Intel processor users.  I went into my system BIOS and disabled Thermal Throttling and SpeedStepping and I no longer have the Lockups.

Hope this help someone,

Spartus4

---

### Post by ArTaX on 2007-08-08
I have a HP Pavilion 6383eu:
AMD Turion 64 X2 TL-60
RAM 2GB DDR2
nVidia GeForce 7200

I experienced the same problem (screens would freeze, refresh rates would go wonky, keyboard frozen with mouse still movable but otherwise not functional) and i resolved all the problems booting with these options:
NOAPIC NOAPCI NOIRQPOLL **NOSMP**
I believe that the "solution" is the last option (NOSMP) but this disabled one core!
When i boot without nosmp (the system freezes) from cat /proc/cpuinfo the MHz of the cpus are 2000.000 but they really are 1600.000 ....
When i boot with nosmp the MHz of the only cpu are 1600.000 ...
It could be the way to get the solution to this problem?

---

### Post by oomingmak on 2007-08-08
Does anyone know what IOWait is?

Whenever I get my freezes, the system monitor shows a rapid increase in IOwait from zero to a solid 100%. This lasts for the duration of the freeze (after which IOwait returns to zero again, and the system unfreezes). No 'user' or 'system' CPU load is shown during this time, (it's just 100% IOWait).

---

### Post by Supremacy on 2007-08-09
OK, yesterday I got another one of my hard lock freezes. This time I was not running Compiz Fusion. I however was running GDesklets though they seemed to be fine. While I was using my machine I had another pc ssh into the computer for the duration of the time until it froze. Nothing was out putted by:```
sudo cat /proc/kmsg
```

However, I have noticed that it puts out alot of information regarding my USB devices. In particular, the storage devices. I still believe its kernel related.

Regards
Supremacy

---

### Post by octopuskevin on 2007-08-09
just like to mention, that while I still have not figured out what the problem is, I have been able to rule out software entirely. While it may have contributed to a certain extent, after formating with Edgy, than Feisty again [beta], upgrade it, and finally formatted and tried windows XP, the random crashing was still there. I must mention that crashes in xp are just awesome because it's like watching a donkey with broken legs trying to climb a hill.. screen keeps flashing black, and things randomly disappear... then everything goes back to normal until you click on something and all hell breaks loose with black boxes popping up everywhere... awesome fun to watch...

I'm going to try another power supply tomorrow and check out the motherboard for problems after my exam, so I'll post if I found my issue... it's possible that some of you may actually be dealing with a hardware issue than a software one.

- Kevin

---

### Post by Ocxic on 2007-08-09
my computer freezes any time I  try to use an administrative program, freezing just after i type in my password.. I believe it's iether a problem with either compiz or gksudo more investigation is needed...
Anyone experience anything like this.. terminal output yields nothing as of yet.. and sudo still works fine

---

### Post by Supremacy on 2007-08-10
> **Ocxic said:**
> my computer freezes any time I  try to use an administrative program, freezing just after i type in my password.. I believe it's iether a problem with either compiz or gksudo more investigation is needed...
Anyone experience anything like this.. terminal output yields nothing as of yet.. and sudo still works fine

I dont believe its at all Compiz Related though it does happen more frequently. I dont run Compiz that often and I still get freezes fairly often.

---

### Post by mrmonday on 2007-08-10
I haven't read all the thread, but I belive I am experiencing the same problems as I am experiencing random lock ups too... It is less frequent recently, and has been happening since edgy. If I open a terminal, or switch to a TTY, when it locks up I get something about a CPU soft lock up, followed by rt61MEnqueue errors. I belive rt61 is the chipset of my wireless card, which I have given up on since it doesn't work. Quite often it locks the mouse too, but I can generally still move it.

---

### Post by jjgomera on 2007-08-10
Normally ubuntu 7.04 is very stable and freeze only when i do "experiment". With gnome and without desktop effect
But yesterday i installed ktorrent, when i used it to download anything i had 3 hard freeze in half hour, only solution reset button :confused:

So i had to change the torrent client, the problem has disappeared.

Same problem in other ubuntu-based distro, guadalinex with kde, same and identical solution

Some months ago i used ktorrent without problem

---

### Post by chek2fire on 2007-08-10
I have the same problem with random crashes in my system.I have an intel 6600 with a motherboard asus P5N32-sli and nvidia 8800gts.My system some times crash but the mouse is working and some times it crash when i left it to download some files from internet.
I think feisty is the most unstable ubuntu version.I use ubuntu from dapper.

---

### Post by IVIisterX on 2007-08-12
Hello altogether!

I had the same problems written above; my machine did freeze at random times after restart.

I posted my configuration, my settings and my varied experience  in the following forums under the same nickname:

English: 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115275)

[https://bugs.launchpad.net/ubuntu/+bug/110394](https://bugs.launchpad.net/ubuntu/+bug/110394)

German:

[http://forum.ubuntuusers.de/viewtopic.php?p=876451#876451](http://forum.ubuntuusers.de/viewtopic.php?p=876451#876451)

[http://forum.ubuntuusers.de/viewtopic.php?p=861049#861049](http://forum.ubuntuusers.de/viewtopic.php?p=861049#861049)

In my case the problem with the freezes is apparently  solved by changing to Kernel 2.6.20-16-386.

Best regards

IVIr.X

---

### Post by hoggbottom59 on 2007-08-12
My system locked up on start up when the Desktop Effects were enabled.
It's all very stable without these turned on and I haven't had problems otherwise.

Do you use any restricted drivers?


Leon.

---

### Post by IVIisterX on 2007-08-12
Hello Leon!

Thank you for your answer. But the unchanged original feisty fawn alternate installation was freezing from the first time. As far as I know uses the original installtion by default no restricted drivers and no desktop effects.

Best regards

IVIr.X

---

### Post by IVIisterX on 2007-08-12
Hello Leon!

I have switched to Kernel 2.6.20-16-generic. Desktop effects and restricted driver are disabled. I test the system with these settings.

Best regards

IVIr.X

---

### Post by IVIisterX on 2007-08-12
Hello Leon!

That was a short test; until looking a video the machine did freeze completely. No mouse - no keyboard - only reset.

Now I am working with Kernel 2.6.20-16-386 again.

Best regards

IVIr.X

---

### Post by IVIisterX on 2007-08-12
Hello Leon!

I am back again! Under Kernel 2.6.20-16-386 was a freeze watching the same video. So I disabled the service powernowd again and switched back to kernel 2.6.20-16-generic. Now I am testing again.

Best regards
IVIr.X

---

### Post by chek2fire on 2007-08-12
i have generic kernel.Is better to update to 386?

---

### Post by regomodo on 2007-08-12
i've been getting loads on my laptop. randomly happens even though it's a fresh install with all the updates. Never used to when Feisty originally came out. Everything would lock and only the alt+sysrq+ r/s/e... got me out of it.

Got so p'd off that i went back to Debian Etch with Gnome (can't remember why i left it) and have had no issues yet.

PC is fine with no crashes that i can recall of.

---

### Post by IVIisterX on 2007-08-12
Hello chek2fire!

For my opinion the 2.6.20-16-386 kernel is more stable; but I think that this is not the only solution. Perhaps you have to make some changes in the APIC and APM settings in the Ubuntu services and the Bios of your mainboard. I am testing futher on which settings are optimal for my mainboard. Wether these settings are optimal for your mainboard I can say.
I found out, that in the case of my mainboard (ASUS P4C800 Deluxe) the ACPI 2.0 Support has to be enabled and in Ubuntu I had to install the ATI driver 8.39.4 for my ATI 9700 PRO and to disable the powernowd service to get more stability.

With these settings I had no freezes anymore; but if I only change one setting Ubuntu freezes at once.

Best regards

IVIr.X

---

### Post by soulglo83 on 2007-08-12
This really stinks...  I had thought I had the issue resolved by disabling powerstepping in my bios, adding noapic, nolapic, irqpoll, ht = on cheatcodes to my menu.lst, and even screwing with powernowd.  Well I have had my computer freeze 3 times in less than two hours, each time with the exact same schutt I've been seeing for the past few months.  I have always been a loyal Ubuntu user and have successfully converted my grandma, mother, 2 of my brothers, my girlfriend, and 4 of my best friends to using Ubuntu almost exclusively.  Now I (the Ubuntu guru amongst my friends) am unable to continue using it.  This kind of problem just being accepted as a 'low importance' bug that has reduced the average uptime of my computer to less than an hour and a half is truly pathetic.  Its not limited to Ubuntu as the other Distro's I have tried exhibit the same behavior.  I am (instead of continuing to lose work constantly, and pull my f'ing hair out all the time) just go back to using windows.  I really didn't mind the spyware and the crashing, and the slowness, so long as my computer was useable.  When it's possible just to type papers, send emails, and browse the web without my computer hard crashing every hour and a half, I might come back.  I have (until recently) had a great linux/ubuntu experience, but if Linux can't run stably on a dual core computer (which have been common for over a year now) it might just be advancing too slowly, and with too little regard for stability.  So long everyone, I'll more than likely check back in a few years when Linux is capable of running on my hardware.

EDIT:  My motherboard invalidated my Windows XP Pro install and without activation I would have to break the law or suffer a tragically crippled OS to use it.  Looks like life has a funny way of sorting these kidns of things out.  I'm currently trying DigitallySick's solution (to install the 64 bit ubuntu) and its working out great so far (4hours!)

---

### Post by Digitallysick on 2007-08-13
Im running Linux adam-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
 

64bit ubuntu, i used the compiz fusion installer located here , As long as i dont turn on the fancy effects like burn, im ok, i can use wobble windows, and the cube, etc, but nothing to amazing or else i get the freeze, so try it, and stick to the basic effects 

[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

my system is now about 93% stable with compiz fusion

---

### Post by chek2fire on 2007-08-13
i think that this crashes maybe is a bug.I have random freezes in feisty in ths system (intel 6600,nvidia 680i,nvidia 8800gts) but i have the same problems with random freezes and in an other pc in edgy and feisty again.This pc was P4 3,2,via chipset,ati 1950.The both systems have 2g memory modules.
The programme that freeze my system very often is vmware.When i am in vmware full screen and i want go back to window mode the system freeze and only the mouse is working.I dont why but edgy and feisty is very unstable distros.I write and a bug report here
 [https://bugs.launchpad.net/ubuntu/+bug/131973](https://bugs.launchpad.net/ubuntu/+bug/131973)

---

### Post by soulglo83 on 2007-08-13
ok feisty froze for me in an identical fashion using the 64bit ubuntu feisty install, it happened then happened again 45 minutes later.  I have since called MS and sorted out the activation of my account and I am now sadly back in windows.  Turns out it really wasn't as bad as I remembered it, and its actually been far more stable for me than the recent linux distros (on account of this particular freezing phenomena where xorg consumes 100% of the processor and the mouse moves but EVERYTHING else is unresponsive, even the keyboard wont allow me to toggle caps/num lock!, it can be restored by rebooting or sshing to it to kill xorg).  sorry after more than 2 years of loyally supporting ubuntu, I've had to go back.  I'll try it again here in a year or two when its stabilized a bit.

---

### Post by chek2fire on 2007-08-13
is better to help develop to find a solution for our problem and fix the bug.They have already answer to my bug report with some instruction for debugging
take a look
[https://bugs.launchpad.net/ubuntu/+bug/131973](https://bugs.launchpad.net/ubuntu/+bug/131973)

---

### Post by soxs on 2007-08-14
I recently tested some stuff:
- no network/internet connection -> random freezes
- exchanging of mouse/keyboard/tft/energie-*mountpoint* -> 8h playing wc3 tft (via wine) without one single freeze (wtf?), maybe good/bad luck?

Will du a more differentiated diagnoses/test...

(freeze: mouse moveable, nothing else is responsive)

---

### Post by chek2fire on 2007-08-14
do you have nvidia and you have install the latest nvidia driver?

---

### Post by majoridiot on 2007-08-14
just an update from here- [http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)

one week later, after making the changes outlined in the above post, i have yet to experience a single "freeze".
the system has had fairly heavy use, so i am satisfied this fix will work for me for now.  my only complaint is 
that the interrupts are slightly "off"... e.g. lirc is "jumpy" on repeating keys.

it is **extremely** disappointing that this problem- which seems to affect many, many users over multiple distros-
doesn't seem to be getting much interest from the devs of any of one (or a combination of) the usual suspects.

as yet, i have not seen any sort of explanation- just the usual "send logs, backtraces, etc" with no apparent
priority to get this fixed.  considering it could be the kernel, X, nvidia proprietary drivers, etc, etc, ad nauseum and that it renders affected machines pretty much useless, one would hope the 
various devs would be all over this.  this doesn't seem to be the case.  although the bandaid i applied
will get me through for the time being, i do look forward to getting it properly fixed.

(not bashing the devs, btw.  major kudos for everything they have done and continue to do!  i wouldn't go
back to windoze on my main system for anything!)

---

### Post by chek2fire on 2007-08-14
i have heard that the problem is with thel latest nvidia driver and beryl.I dont know if this is true

---

### Post by majoridiot on 2007-08-14
> **chek2fire said:**
> i have heard that the problem is with thel latest nvidia driver and beryl.I dont know if this is true

just as a point of interest, neither beryl nor compiz is running- nor installed- on my system having these issues.

the nvidia driver is 1.0-9755 as installed by the restricted drivers manager.

---

### Post by soxs on 2007-08-14
I have an ati radeon 9500pro/9700 and I am not using beryl nor compiz. (I am using xgl & the latest offical amd/ati driver, freezes occured aswell with the restricted drivers and all possible combos, even live cd froze, fresh install with no mod nor any user activity freezes in random periods of time)
Additionaly I have no wirelesscard.
So it's definitly no nvidea, no ati, no wirelesscard related issue, no Gnome/KDE/Xfce related problem(tested Gnome & Xfce & Openbox)

---

### Post by ferd on 2007-08-14
> **majoridiot said:**
> just an update from here- [http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)

one week later, after making the changes outlined in the above post, i have yet to experience a single "freeze".
the system has had fairly heavy use, so i am satisfied this fix will work for me for now.  my only complaint is 
that the interrupts are slightly "off"... e.g. lirc is "jumpy" on repeating keys.

it is **extremely** disappointing that this problem- which seems to affect many, many users over multiple distros-
doesn't seem to be getting much interest from the devs of any of one (or a combination of) the usual suspects.

as yet, i have not seen any sort of explanation- just the usual "send logs, backtraces, etc" with no apparent
priority to get this fixed.  considering it could be the kernel, X, nvidia proprietary drivers, etc, etc, ad nauseum and that it renders affected machines pretty much useless, one would hope the 
various devs would be all over this.  this doesn't seem to be the case.  although the bandaid i applied
will get me through for the time being, i do look forward to getting it properly fixed.

(not bashing the devs, btw.  major kudos for everything they have done and continue to do!  i wouldn't go
back to windoze on my main system for anything!)

Bless you for this fix. I thought I would have to buy a new computer. Instead, I installed Feisty so that your fix would work and it does!=D>:grin:

---

### Post by IVIisterX on 2007-08-19
Hello alltogether!

After another freeze a few days before I checked out the solution discribed in the following link:

[http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)

The summary:

Various freezes with different programs with these settings.

But since I took back the additional kernel parameters "noapic nolapic irqpoll ht=on" my machine runs stable without freezes with the kernels 2.6.20-15, 2.6.20-16 and 2.6.20-386.

So I come to the conclusion that the maintrigger for the freezes is the powernowd-Service. In the case of freezes first checkout wether the remove from powernowd brings more stability.

Best regards

IVIr.X

---

### Post by majoridiot on 2007-08-19
> **IVIisterX said:**
> Hello alltogether!

After another freeze a few days before I checked out the solution discribed in the following link:

[http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)

The summary:

Various freezes with different programs with these settings.

But since I took back the additional kernel parameters "noapic nolapic irqpoll ht=on" my machine runs stable without freezes with the kernels 2.6.20-15, 2.6.20-16 and 2.6.20-386.

So I come to the conclusion that the maintrigger for the freezes is the powernowd-Service. In the case of freezes first checkout wether the remove from powernowd brings more stability.

Best regards

IVIr.X

having already made the changes to powernowd, i removed the kernel parameters of "noapic nolapic irqpoll ht=on"
just to see what would happen...

result: the system did typical "freeze" after less than 3 minutes.

so, it might be worth trying just the changes to powernowd- but in my case, the kernel parameters need
changed as well to stabilize the system.

---

### Post by IVIisterX on 2007-08-20
Hello majoridiot!

Thx for your test. But I think that powernowd is only one trigger for these ominous  freezes. From machine to machine are different additional settings necessary to get 100% stability. In my case for example disabling APIC-Settings causes more instabiltity; without apic my machine freezes in a few minutes.

The stablity of Ubuntu Feisty Fawn seems to be a general problem on various machines and there is no general solution to eliminate these  freezes. Everyone has to experience with different settings for himself. 

Therefor- I think -  it is necessary, that as  many users as possible should post their experiences - only on this way everyone is able to solve his own problem.

Best regards

IVIr.X

---

### Post by majoridiot on 2007-08-20
> **IVIisterX said:**
> Therefor- I think -  it is necessary, that as  many users as possible should post their experiences - only on this way everyone is able to solve his own problem.


absolutely agreed.  the more info gathered, the better.

---

### Post by ntounix on 2007-08-21
I've had the freezing issue as well, however I've tracked almost all of my problems to devices.  I can make the system freeze by turning on my keyboard light.  I also found my wireless card is a culprit.  I have a usb/wireless mouse that seems to be doing it as well.  I'm slowly weeding them out.

---

### Post by Den-Can on 2007-08-21
I got the same problem ... I removed almost all the hardware and the system was still freezing ... Only the mouse cursor was still running ...
Everything back to normal after  I tried another video card ...
My Nvidia MX440SE was the problem ...

---

### Post by soxs on 2007-08-22
After installing Ubuntu 7.04 the 6th or 7th time on a diffrent hdx (the rest is the same hardware P4 2,4Ghz ; 1gb ram ; 80gb + 160gb hd s ; radeon 9500pro/9700)

now it's running stable (wtf??), 4 days!
after I#ve done all updates and made a backup I'll try to install the latest ati dirver and check wether this makes any diffrences (btw. how to spell (or is it pronounce? no, I think its spelling^^) diff(e)rence?)

---

### Post by iopo on 2007-08-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116752](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116752) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a Dell Inspiron 6000. In my case I made several installations and I tried out everything was suggested in this thread. I also tried several other distro (fedora 7, PcLos, Mandriva, Mint). No matter what, everytime, sooner or later I was having a freeze.

Then I notice that after every freeze I was getting the following error message at boot up (at least, under k-ubuntu and mint):

Uhhuh. NMI received for unknown reason b0 on CPU 0.
You have some hardware problem, likely on the PCI bus.
Dazed and confused, but trying to continue 

I ran all the tests and diagnostics I could find and nothing was wrong with my computer.

After a fresh install I decided to take a look at the BIOS menu. I changed the BIOS boot up option from "fast" (the default) to "normal" and voila'!! No more freezes (at least in the last 5 days)!

I'm not an expert, so I have no clue why it worked, but it made the trick!!

Best!

---

### Post by bobbybobington on 2007-08-23
I put 7.04 on my parents computer and it seems to suffer from the random freeze of doom. It will freeze almost completely randomly, although I think disabling the desktop effects seems to help out.  At this point its a matter of superstition, all I can do is 1. Tell my parents to REISUB and 2.Hope that  Gutsy will fix this prob.

---

### Post by Footer on 2007-08-23
59 pages of replies ... ?  Obviously, this problem is affecting LOTS of Ubuntu users ... I haven't read every reply (got to page 2 and then skipped to the end) but I'd like to add my .02 as well.  I've had apic problems in the past that I thought a BIOS update resolved.  However, I'm back to freezing up, mostly when I come back to the machine after several hours of idle time (I never turn it off) and when I open an OpenOffice document, it will freeze.  Seems like that's the only time.  I haven't run across anyone else mentioning that OpenOffice freezes their machine so just thought I'd toss that random tidbit out there.

Going to try some kernel parameter tweaking again (noapic) and see if that resolves this issue.  I'm quite tired of it.

Thanks!  :)

---

### Post by IVIisterX on 2007-08-23
Hello footer!

I can "ease" you - your are not alone! :-)
My machine did freeze under OpenOfficeOrg too. OOO is one of various programs which are affected by the freezes.
I detected that - in my case - one trigger for the freezes is definitly powernowd. 
The second trigger is the ATI-driver. If the restriceted driver is not installed, all the tested kernels freeze at random times. 
Thirdly I think it is necessary to enable APIC 2.0 Support - whatever this means - in the Bios to get more stability.
With these three settings my machine runs for this moment with out freezes with kernel 2.6.20-15-generic; 2.6.20-16-generic and 2.6.20-16-386 freeze at random times. 
The difference between 2.6.20-15 and 2.6.20-16 seems to be that 2.6.20-15 uses for openGL  Mesa GLX Indirect and 2.6.20-16 uses direct rendering. I checked this out by typing glxinfo in a terminal.

Best regards

IVIr.X

---

### Post by riccardol on 2007-08-24
Hi all,

After months of suffering I finally came to a deal :D

No kernel parameters are needed. After reading a bit of lkml, I came to this solution which works 100% for me:

At boot, as soon as you can get a tty or as soon as you can login into your desktop launch a terminal and:
  sudo /etc/init.d/powernod stop

So, I think that either something is screwed in kernel acpi code or in cpufreq* or powernow* kernel modules.

I'm a dev but don't have the time to solve the problem now(sorry). If anybody knows how to say it to some "interested" dev please do it :)

Really hope this helps :)

---

### Post by chek2fire on 2007-08-24
if you have random freezes you must reply to my bug report here
[https://bugs.launchpad.net/ubuntu/+bug/131973](https://bugs.launchpad.net/ubuntu/+bug/131973)
try to help dev to fix the problem

---

### Post by Footer on 2007-08-24
> **IVIisterX said:**
> Hello footer!

I can "ease" you - your are not alone! :-)
My machine did freeze under OpenOfficeOrg too. OOO is one of various programs which are affected by the freezes.
I detected that - in my case - one trigger for the freezes is definitly powernowd. 
The second trigger is the ATI-driver. If the restriceted driver is not installed, all the tested kernels freeze at random times. 
Thirdly I think it is necessary to enable APIC 2.0 Support - whatever this means - in the Bios to get more stability.
With these three settings my machine runs for this moment with out freezes with kernel 2.6.20-15-generic; 2.6.20-16-generic and 2.6.20-16-386 freeze at random times. 
The difference between 2.6.20-15 and 2.6.20-16 seems to be that 2.6.20-15 uses for openGL  Mesa GLX Indirect and 2.6.20-16 uses direct rendering. I checked this out by typing glxinfo in a terminal.

Best regards

IVIr.X

Hello Mr. X --

I was looking at my system last night for powernowd and found it not to be running.  But I discovered something similar:  powersaved  So I removed it with apt-get which of course stopped the daemon and it's been 18+ hours without a freeze.  Perhaps this was my problem?  I have the noapic parameter added to the kernel but haven't rebooted yet so it's not in effect.  Guess I'll wait it out and see what happens.

Tricky little bugger!

Thanks!

Edit:  Just rebooted my box after a freeze  :(  The noapic kernel parameter is in effect.  I guess disabling powersaved didn't solve my problem.  Perhaps noapic will???  Time will tell!

---

### Post by IVIisterX on 2007-08-24
> **chek2fire said:**
> if you have random freezes you must reply to my bug report here
[https://bugs.launchpad.net/ubuntu/+bug/131973](https://bugs.launchpad.net/ubuntu/+bug/131973)
try to help dev to fix the problem

Hello chek2fire!

I try to reply in your bug report at this weekend.

IVIr.X

---

### Post by IVIisterX on 2007-08-25
> **IVIisterX said:**
> Hello chek2fire!

I try to reply in your bug report at this weekend.

IVIr.X

Hello chek2fire!

Done! :lolflag:

IVIr.X

---

### Post by Supremacy on 2007-08-27
hi all,

I'd just like to put forward a question to those of you affected, how many of you have the java Runtime installed??

I was having the freezes and went to install Limewire (i wanted to see what the Linux version was like) and as a result it installed the JRE.

As of the current time (i'm in windows atm) I have not had any freezes. I did have it up for a period of 1 hour 20mins. I have yet to extensively test this. I was not running Compiz Fusion (it would freeze with it both on and off).

When I do test this even further I will let you know.

Regards,
Supremacy

---

### Post by soxs on 2007-08-27
I did some further test on a fresh install on a different hardware dev.
Without any graohics driver it ran fine for 5 days.
Day 6, I decided to install my grafics driver 8.40.4 for my radeon 9500pro (R300) via envy
Day 6 I got 1 freeze, day 7 no freezes (wtf?)... it seems to be totally random (maybe the 5 days was good luck? 6th day bad luck?)

I am confused, I hope gutsy will fix it...

---

### Post by chek2fire on 2007-08-27
i think the problem is from graphic card drivers both ati and nvidia.

---

### Post by soxs on 2007-08-27
atm i guess it is more than one bug, or at least there are diffrent combinations of bugs/programms to make it occure... as already mentioned I'm confused. (I had an *freezing* fresh install on another hardware dev, even without graphics-accel-drivers (wtf?), and now it only freezes only with graphics-accel-drivers installe?)

The errors beforefreezing are always the same (currently this peace of info is not avail, removed older .logs *g*)

---

### Post by semijoyful on 2007-08-27
I posted this to launch pad under bug#131973.

Hi, all!
I am a new Ubuntu (Feisty Fawn) user. Here's information about my system off the top of my head:
Dual boot PC (XP, Ubuntu)
Pentium 4 HT 3.2GHz
Elite Xpress Motherboard w/on board express ATI
Express AGP Nvidia Ge-Force
I believe the kernel is the newest one.

Right out of the gate, my computer has been experiencing hard freezes. The first time that I got one was when I was just accessing restricted drivers. This is not the only time, however. I can expereince these random freezes at any point that Ubuntu is running. I want to make this work, but if the OS causes me to re-boot my whole system before I can even finish a task, I am not sure my willingness will last long. I am new at this, and I'm curious if one can get me on the right track to solving this problem.
Greatly appreciative in advanced,

semijoyful

---

### Post by bootsbradford on 2007-08-28
Well, I have tried another 2 of the solutions in this thread:
[http://ubuntuforums.org/showpost.php?p=3134000&postcount=544]("http://ubuntuforums.org/showpost.php?p=3134000&postcount=544")
and
[http://ubuntuforums.org/showpost.php?p=3244975&postcount=592]("http://ubuntuforums.org/showpost.php?p=3244975&postcount=592")

As I feared, neither of them have worked. Mouse kept on working, music kept on playing, but everything else was jammed. :(

I continue to be surprised and really disappointed that nothing is seemingly being done to resolve this problem. I hope Gutsy will resolve it but I'm not sure why it has to wait until then. I was fine with Edgy so what is it about Feisty that has caused all these problems?

---

### Post by majoridiot on 2007-08-28
my main box remains freeze-free after the fix i described in post #544, although video has some obvious minor
issues across the three heads it runs.

last night, it struck me that my mythtv backend/frontend is running a fully updated feisty and has not had this problem.
the only major difference, other than it is running an AMD64 is that is not running a full gnome desktop, but openbox.
other than that, the suspects mentioned here (X, proprietary drivers, etc.) are all installed on that box and running
fine.

this makes me wonder if it may be a convergence of issues, including gnome.  just speculating.

when i get a chance, i'll put a full feisty desktop on that box and see how stable it is.

---

### Post by IVIisterX on 2007-08-28
Hello semijoyful, hello bootsbradford!

If we should help you solving your problems, you have to post additional informations.

semijoyful:
Have you done the solutions bootsbradford did post? Which kernel do you use? Which nvidia driver have you installed; do you use restriceted drivers?

bootsbradford:
Please post details to your hardware, kernel version and graphics driver version.

IVIr.X

---

### Post by bootsbradford on 2007-08-28
@IVIisterX (and anyone else who can help):

These are my basic specs:

Dell Dimension 8400
Intel(R) Pentium(R) 4 CPU 3.40GHz
RADEON X600/X550 Series
Ubuntu Feisty (Studio)/XP Dual Boot
Ubuntu Kernel 2.6.20-16-low latency (though crashed with others as well)

Does this help or is there anything you need to know? 

As mentioned earlier, the tell-tale signs are a complete look-up, with the exception of the mouse still being moveable and music still playing.

---

### Post by funnypanks on 2007-08-29
> **oomingmak said:**
> Does anyone know what IOWait is?

Whenever I get my freezes, the system monitor shows a rapid increase in IOwait from zero to a solid 100%. This lasts for the duration of the freeze (after which IOwait returns to zero again, and the system unfreezes). No 'user' or 'system' CPU load is shown during this time, (it's just 100% IOWait).

i have the EXACT same problem. the kenel i am using is Ubuntu, kernel 2.6.20-16-generic
same thing happens with Ubuntu, kernel 2.6.20-15-generic. and tribe 5 gutsy gibbon & tribe 4. and with x64 and 32 discs. yes i have wasted many cd's now lol. 

specs: acer laptop
t5500 
1.5gb ram
120gb ide HD
3945abg
gma 950
anything requested will be provided and any recommendations will be noted incl older ubuntu's. i love compiz fusion so it is a must. and my fastest way to test if this problem still exists is by opening synaptic and doing a search, right away it turns grey and after 5-15 seconds it's back and running. but FREAking annoying.i hope there is a fix. i am so close to uninstalling vista. but i cannot live with these freezes. i want that microsoft monkey off my back. also already tried noapic and nolapic

---

### Post by Footer on 2007-08-29
> **Footer said:**
> Hello Mr. X --

I was looking at my system last night for powernowd and found it not to be running.  But I discovered something similar:  powersaved  So I removed it with apt-get which of course stopped the daemon and it's been 18+ hours without a freeze.  Perhaps this was my problem?  I have the noapic parameter added to the kernel but haven't rebooted yet so it's not in effect.  Guess I'll wait it out and see what happens.

Tricky little bugger!

Thanks!

Edit:  Just rebooted my box after a freeze  :(  The noapic kernel parameter is in effect.  I guess disabling powersaved didn't solve my problem.  Perhaps noapic will???  Time will tell!

UPDATE (again):  Just experienced a freeze again.  This is with the noapic parameter added to the kernel, so that's not it.  As mentioned above, I had powersaved running but still experienced freezing.  Never did have powernowd running.

This is getting REALLY annoying.  I've been running Kubuntu for over 2 years now and don't want to switch to another distro (don't even get me started with Vista).  I'm running:

[INDENT]restricted Nvidia drivers
kernel 2.6.20-16-generic with the noapic parameter, otherwise stock
Kubuntu 7.04 64bit
AMD64 X2 Dual Core 4200+
2GB memory[/INDENT]

Not sure how much of these specifics matter since there seem to be so many of us with this freezing problem but at this point, I'm still searching for an answer.

Thanks!

Edit:  I'm going to try post #544.  I hadn't seen the powernowd tweak before this even though powernowd isn't installed so we'll see where that leads.

---

### Post by FuturePilot on 2007-08-29
Disabling powernowd worked for me. It's running on most computers. If your CPU supports CPU scaling, it's running. Disable it by adding ```
exit 0
``` right below the very first line (#! /bin/sh) of /etc/init.d/powernowd. Then Reboot.

---

### Post by diffuze on 2007-08-29
Same issue here, freeze on logout.
I have basically the same setup as **Footer**.

Sure, disabling the composite extension in xorg.conf resolves the issue but then I can't run Compiz so that's not an option.
Oddly, this only happens if I'm in Gnome. If I'm in KDE the logout et al works as intended. I just recently changed from using KDE to using Gnome, this is why I've never had this issue before.

By the way I changed from gdm to kdm thinking that would help but it's still the same.

I have had to hard-reboot several times now and it's only a matter of time before the filesystem gets corrupt.

:confused:

---

### Post by IVIisterX on 2007-08-29
@diffuze, Footer, funnypanks, bootsbradford, semijoyful and all the others with the same problem!

I was in the same situation as you all - my machine did freeze at random times. Only by experimenting I was able to reach a setting which is relatively stable. I mean to say, that there is no general solution for this problem. For example in my case the additional kernel parameters noapic nolapic irqpoll ht=on led to rapid freezes; in the case of majoridiot's machine the exact opposite is necessary - the additional parameters must be added. So everyone has to test the discribed "solutions" on his own machine.
But you should change only one setting at the same time and than test your system is more stable or not.
In my case there were differences how often the freezes came; some settings caused freezes a few minutes after reboot other settings caused freezes in 30 minutes max. In the moment there is one freeze every two days or longer.
To find your personal solution I will give you some tips:
 
1. Try to disable in System - Administration - Services the acpid, apmd and powernowd options and check out wether the system gets more stable or not.
2. Try to use restricted drivers and check out wether the system gets more stable or not.
3. Type in a terminal glxinfo and check wether the kernel uses direct rendering or not. In my case kernel 2.6.20-15-generic uses no direct rendering. Check out wether kernel 2.6.20-15 (no direct rendering) runs more stable than kernel 2.6.20-16-generic (direct rendering).
4. Check out the additional kernel parameters.
5. Test the "sudo /etc/init.d/powernowd stop " command in a terminal as fast as possible after restart.
6. Uninstall powernowd and test additonal the "sudo /etc/init.d/powernowd stop " command; in my case for example both is necessary to use kernel  2.6.20-16-generic in a stable mode.
7. Check your bios wether you find APIC settings and test wether enabling / disabling makes the system more stable or not. In my case for example the APIC 2.0 support has to be enabled to get more stability.
8. Nvidia users should test a downgrade from driver version 100.14.11 to 100.14.09

But once more - modify only  **_one_** setting at the same time!

Good luck

IVIr.X

---

### Post by Footer on 2007-08-29
Thanks Mr. X for all your valued suggestions and opinions ...

I can't help but think though how many Windoze users would go to these great lengths to make their system more stable (any operating system, not just Linux) ... ?  SHEESH!  Sure, GEEKs like us have no problem trying all this stuff, over and over and over again until we find the right combination that works.  But that's GEEKs like us!  Your average computer user is NOT going to go to this length to make a stable system under Linux.  Again, I hate to say this but it's things like this that are keeping Linux from getting main stream.  Granted, maybe it's only a handful of us power users with specific components in some combination that's causing this but the length of this thread tells me that this is not necessarily a random problem affecting just a mere few ...

JMHO!

:)

---

### Post by semijoyful on 2007-08-29
To Footer, I think you make a valid point.  I for one like the challenge, but that is certainly not a trait for all.  Still, I think there’s some good that can come out of lack of instant gratification.  Anyways, thanks Mr. X for the reply.  When I get some time, I will implement some of the solutions as my limited Linux knowledge will allow.  I’ll get to posting some more once I have given the suggestions a go.
Hanging in there,

semijoyful

---

### Post by diffuze on 2007-08-30
I agree with **Footer**. I don't mind issues like these, heck I've had a few over the years and I have no problems sitting and trying different things to eliminate them. For a totaly newbie this sort of thing IS a show stopper though. I sincerely hope the freeze issues will be resolved soon. Not for my sake but for those who try out linux for the first time. If someone tries Ubuntu with compiz over Vista and the pc freezes when they log out.. what are they supposed to think?

Thanks for the extensive reply **IVIisterX**. I'll look into this in the weekend when I have some time. :-D

---

### Post by semijoyful on 2007-08-31
Good news...I disabled in the Admin Services the acpid, apmd, and powernowd while running kernel 2.6.20-15-generic, and I am no longer having freezing problems:)  Thanks for the help, Mr. X

Sincerely,
semijoyful:guitar:

---

### Post by semijoyful on 2007-09-01
LOL, right after I made that post, it froze on me.  Stand by...
semijoyful

---

### Post by semijoyful on 2007-09-01
things have been stable for the last 1.5 hours.  In addition to the above, I also did #5, #6, and #8.  I have been doing all sorts of crazy things to get Ubuntu to freeze, but to no avail...that's a good thing.  FYI, I re-installed Ubuntu with Ubuntu Studio.  Not that that would keep it from freezing, but just to give US a plug.  Thanks again, Mr. X
semijoyful :D

---

### Post by soxs on 2007-09-01
I suggest anybody to test him/her options at least 24h (even this may be too short :-/) of runtime.
This bug ssems to be too.. strange to be called *fixed* after only x hours (x€[0;4]) freezingless runtime.

Till now  nothing can be confirmed nor abdonned...

---

### Post by IVIisterX on 2007-09-01
@soxs, @semijoyful! All the rest!

I think - additional to soxs - everyone has to test his system a couple of days; my system freezes sometimes after 2 days or longer. But generally it is a success that semijoyful's system doesn't anymore  freeze a few minutes after restart. So everyone should check out, which combination of settings brings the highest stability for the moment. I hope, that this problem will be fixed by the developers in the future.
Today there was an kernel update from 2.6.20-16.29-generic / -386 to 2.6.20-16.31-generic / -386. For ATI-users is the new driver version 8.40.4 available.
In this context I will describe an instruction for Ubuntu to install the newest nvidia / ati drivers with the Envy-tool:

1. Download the actual DEB-package from the homepage [http://albertomilone.com/nvidia_scripts1.html;](http://albertomilone.com/nvidia_scripts1.html;) for the moment it is the envy_0.9.7-0ubuntu8_all.deb.
2. You have to install the DEB-package by doubleclicking with "Gdebi".
3. Then you have two possibilities
3.1 You press CTRL - ALT - F1 and switch to the first console. You must log in as user; then type "sudo envy -t". At least you have to choose the matching option for your system - by the way the option "manually installation" lets you to choose an older driver.
3.2 You can use the graphical version  from applications - systemtools - envy or you type "sudo envy -g" in a terminal.
4. After a  successfully installation you have to choose "yes"  for "Do you want your xorg.conf to be automatically configured?"  and for the question for reboot.

By the way I detected,  if you have installed  different kernels (for example: 2.6.20-16 and 2.6.20-15) the kernel under which you install the graphics driver uses after reboot direct rendering;  the other uses indirect rendering (MESA) for OpenGL.

Until I am writing this reply I use 2.6.20-16.31-generic and ATI-driver 8.40.4 without a freeze; but wait and see and hope and ....

IVIr.X

---

### Post by soxs on 2007-09-01
I did it the same way.. and I went freezingless for about 16h... but then I started hardcoregaming  for 2h and the first freeze occured, after reboot a second freeze without gaming.
All in all freezes occure very rarely without gaming 1 or 2 times a week. With gaming once or twice a day (which is much to much).
Note: I have all powermanaging dameons/stuff activated.

---

### Post by oomingmak on 2007-09-01
> **funnypanks said:**
> i have the EXACT same problem. the kenel i am using is Ubuntu, kernel 2.6.20-16-generic
same thing happens with Ubuntu, kernel 2.6.20-15-generic. and tribe 5 gutsy gibbon & tribe 4. and with x64 and 32 discs. yes i have wasted many cd's now lol.
Ah, so I'm not alone then (or going mad). 

I get freezes on **totally** clean installs of Feisty with nothing at all added (not even graphics card drivers). I have also tried Tribe 3 very briefly, and that was the same. I don't seem to recall getting any freezes on Edgy, but then I'd only just started using Linux around that time, so I can't remember if I would have been on it for long enough to even notice (I was still reeling from the shock!).

Given that there is a 100% direct and visible correlation between the freezes and the IOWait overloads, you'd think that more people would have focussed on that aspect to see if it helped give more clues as to what might be causing the problem. I'm sure that we can't be the only two people that have witnessed these linked events.

However, this thread is now so full of a mish-mash of off-topic problems that are completely unrelated to the OPs post, that it makes it impossible to make any sense of it.

I'm wondering how long it will be before people start posting in here about their Windows XP crashes   :lol:

---

### Post by Digitallysick on 2007-09-01
doing this seemed to of helped me, i was getting alot of lock ups recently but not as bad i as i used to, i tried this and havent locked for days so far

sudo /etc/init.d/powernowd stop

---

### Post by johanPO on 2007-09-02
[QUOTE=funnypanks;3272532]i have the EXACT same problem. the kenel i am using is Ubuntu, kernel 2.6.20-16-generic
same thing happens with Ubuntu, kernel 2.6.20-15-generic. and tribe 5 gutsy gibbon & tribe 4. and with x64 and 32 discs. yes i have wasted many cd's now lol. 

/QUOTE]

If you have another CD, try another distro. Ubuntu is nice, but there are other options. I am now running PCLinuxOS2007 and that is stabile. I am contemplating to try out Debian 4.0 soon, as PCLoS is a bit limited in the repositories.

---

### Post by Footer on 2007-09-02
I've been watching the Xorg process via top and the %MEM it uses.  Upon reboot, it's about 5% or so.  As the machine runs for awhile it climbs.  I usually have 2 Firefox windows with multiple tabs each.  After 24+ hours, I've noticed Xorg creeping past 20%.  When I close and reopen Firefox, Xorg immediately goes down under 10%.

I'm not sure but I think Xorg might be directly related to this freezing issue.  My numbers above may not be exact but they're close for my machine.  I'm curious if anyone else has monitored Xorg via top and what their results are?  I haven't gone much past 25% for Xorg before restarting Firefox or rebooting the machine but I'm going to let it run for awhile this way (close & open Firefox to recoup the Xorg %MEM) and see where that leads (without a reboot or, fingers crossed, a freeze!).

Just some more food for thought!

Thanks!

---

### Post by IVIisterX on 2007-09-02
@footer!

Do you use direct or indirect rendering? Type in a terminal "glxinfo | grep render".

@soxs!

I think "hardcoregaming" uses direct rendering very strongly; I guess for a longer time, that the freezes are associated with OpenGL / direct rendering. On the other hand  it struck me, that sometimes the freezes occur 1 or 2 times a week and suddenly i have multiple freezes at one day. So i supposed, that for example a weekly update or something else is the trigger for these freezes.

@All the rest!

For ATI-users - like me too - i found an interssting wiki at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
Perhaps it does help someone.

Day 2:
 Until I am writing this reply I use 2.6.20-16.31-generic and ATI-driver 8.40.4 without a freeze during 4 and a half hours.

IVIr.X

---

### Post by Footer on 2007-09-02
> **IVIisterX said:**
> @footer!

Do you use direct or indirect rendering? Type in a terminal "glxinfo | grep render".



I guess I do use direct rendering:

```

glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce 7600 GS/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

```

Here's the kernel I'm using (64bit Kubuntu Feisty), it is the latest as I just updated it yesterday from the repositories:

```
uname -a
Linux kubuntu64 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

```

I'm currently just over 24 hours without a freeze, Xorg %MEM is at 11.4%.

Thanks!

---

### Post by soxs on 2007-09-02
> **IVIisterX said:**
> 
@soxs!

I think "hardcoregaming" uses direct rendering very strongly; I guess for a longer time, that the freezes are associated with OpenGL / direct rendering. On the other hand  it struck me, that sometimes the freezes occur 1 or 2 times a week and suddenly i have multiple freezes at one day. So i supposed, that for example a weekly update or something else is the trigger for these freezes.



Yes, I use direct rendering.
The freezes occure atm a lot more frequently... even without gaming at all (wtf?)...
Note: I am doing daily updates.


> **IVIisterX said:**
> 
@All the rest!

For ATI-users - like me too - i found an interssting wiki at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
Perhaps it does help someone.

This guide in fact might help, but it did not. I had to use envy to install my graphics card drivers corectly.

---

### Post by likemindead on 2007-09-02
Is there any hope for me? [I've already posted my plight here.]("http://ubuntuforums.org/showthread.php?t=541008") Thanks so much for any help. I'm in a real mess.

---

### Post by likemindead on 2007-09-02
Well, it looks like my running:
```
sudo /etc/init.d/powernowd stop
```
has worked for now.

I need to run this every time I boot?

Yikes.

So far, I was able to update and I'm running. For now....

---

### Post by orb9220 on 2007-09-02
I have done the powernowd thing. And I still can lockup my system.

All I have to have happening is a weak signal on wireless where it is connecting and disconnecting a couple times an hour and left click on icon to get list and try changing to multiple connects of different SSID's and sometimes even just the act of left click on icon can hardlock system requiring a reboot.

I have heard of others having constant issue's with nm-applet.

If I fiddle with nm-applet enough switching ssid's and left clicking icon is when I have the most lockups.

Sometimes I can left click icon and it would hardlock before displaying menu. Sometimes it displays and hardlocks.

And sometimes without any intervention while I am sleeping and downloading 3-6 torrents with ktorrent and firefox open I will wake up to a frozen system.

Still don't know if this is a Beryl/Nvidia,Network Layers,nm-applet issue.

I went for 4-6 weeks no lockups. Now having Lockups about once every 24hrs.

---

### Post by Digitallysick on 2007-09-02
*anger* my pc was fine, i thought maybe the issue was resolved but now it freezes about every 20 min, and every other reboot is a kernel panic! i dont know what to do anymore other than change distros, or try upgrading to gusty first, im worried it will just be the same or worse.  Ubuntu is becoming far to unstable, and i have no idea why

---

### Post by soxs on 2007-09-03
NOTE: I got around that since the day the kernel was updated from 2.6.16.xx to 2.6.16.zz.
Since that day I got daily lookups instead of weekly... even without gameing.
Note: Before kernel update, I deinstalled graphics card drivers and reinstalled after kernel update agian (succesfully with envy 8.40.4)

Edit: If it's hardware related, we should search for paralelism in hardwar config..
so I start here
P4 2.4ghz
1Gb ram
ATI 9500pr [R300] (driver: 8.40.4 via envy)
no wireless card!
ASUS CD/DVD
LG Multi Norm DVD Burner

lspci output
lspci```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by IVIisterX on 2007-09-03
@likemindead!

Yes  - you have to run this every time you boot.

@soxs!

Have you installed another kernel - perhaps 2.6.20-15; then please check out wether this kernel runs without direct rendering and wether this kernel is possibly more stable.

@All the rest!
With kernel 2.6.20-16.31-generic and ATI-driver 8.40.4  froze my system a few minutes ago. So I am back to kernel 2.6.20-15.27-generic with indirect rendering. Wait and see!

IVIr.X

---

### Post by soxs on 2007-09-03
I just tested the suggested fix to stop powernowd
```
/etc/init.d/powernowd stop
```

I was just playing 4hours wc3tft via wine without a single freeze.
I will tell you tomorrow if this fix holds what it promises atm.

---

### Post by funnypanks on 2007-09-03
just wanted to say that nspluginwrapper made freezes way more common, even when not using firefox. had 5 freezes while watching 30 minute show. also on my 64 bit system the 64bit os's had way less freezes. and thanks to the recommendation from johanPO i've tried PClinuxos 07.. 6 hours and no freezes. knock on wood!!! not a fan of kde, but with this stability ill manage for now, until there is a fix for ubuntu, already used 6 dvd's for ubuntu and i think that's enough for now. and you guys working on ubuntu are top notch. just for my system i gave up. (but my desktop is running gutsy tribe 5)
Pclinuxos07+compiz fusion = crack for nerds. :) but i miss gnome:(

---

### Post by FuturePilot on 2007-09-03
To all,
If this solution has worked for you
```
sudo /ect/init.d/powernowd stop
```
you will have to do that every time you reboot ***unless*** you disable powernowd completely. To do that 
```
gksudo gedit /etc/init.d/powernowd
```
Add
```
exit 0
```right below the very first line so it looks like this
```
#! /bin/sh
[COLOR="Red"]exit 0[/COLOR]

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/powernowd
NAME=powernowd
DESC=powernowd

test -x $DAEMON || exit 0

```
Then reboot and powernowd will be disabled and you will no longer have to manually stop it.
That said, I haven't had a freeze since I did that.:D\\:D/

---

### Post by soxs on 2007-09-04
Edit: two freezes happened just to my PC :-/ with this *fix* aktive :_(

---

### Post by mobad on 2007-09-04
OK... I think I may have a fix to this problem... but first, are the people who are having problems using the drivers ENVY installs or the newer drivers?

UPDATE: I forgot to note this but this will only fix ATi driver problems (or at least it's only been tested on ATi).

I noticed this problem as soon as I installed the newer drivers... for some reason it makes two Xorg's run, one of which you use and one which does nothing other than waste RAM which may cause your computer to crash.  

To see if you have this problem run "ps -A | grep Xorg" in the terminal, and if you have two Xorg's running then you have this problem and I have the fix (hopefully) to your crashes.

Now, there are two fixes to this problem, one easy and safe, and one harder and dangerous.

For the first fix just install the normal ubuntu ati restricted drivers and this should fix your problems.  Easy.  Simple.  Safe.  (I have not read the whole thread... it's over 60 pages so I'm not sure this will even work.)

For the second fix, well.. it can compromise the security of your computer but it will allow you to run the newer driver without crashes. (again hopefully) 

NOTE: THIS FIX WILL ONLY WORK IF YOU HAVE TWO XORG'S RUNNING!  RUN  "ps -A | grep Xorg" IN THE TERMINAL FIRST AND IF YOU HAVE TWO XORG'S THEN TRY THE BELOW.

Step 1: 
gksu gedit /usr/bin/killxorg

Step 2:
Paste the line below into the file.

echo "YOUR PASSWORD HERE" | sudo -S kill -9 `ps -d | grep -w Xorg | cut -c1-6`

Again very dangerous but it's better than allowing kill to kill without sudo.

Step 3:
sudo chmod 700 /usr/bin/killxorg

Step 4:
Go to System > Preferences > Sessions 
Click New
For the name type "KillXorg"
For the command type "killxorg"
(without quotes of course)
Then hit OK.

Step 5:
Restart or logout then back in.
Now type "ps -A | grep Xorg" in the terminal again and you should still get two Xorg's but one will say defunct.

Finish

I hope this will work but it is untested on computers other than mine.

---

### Post by majoridiot on 2007-09-04
> **mobad said:**
> OK... I think I may have a fix to this problem... but first, are the people who are having problems using the drivers ENVY installs or the newer drivers?...

in my case, i am using the ubuntu restricted drivers manager for nvidia.

> **mobad said:**
> I noticed this problem as soon as I installed the newer drivers... for some reason it makes two Xorg's run...

unfortunately, my box shows only one xorg running, so this was not an option.  my box is still showing best
stability (no freezes since the changes) with the powernowd/kernel parameter "fix" posted in #544.

it will be interesting to see what the root cause(s) of this will turn out to be, since it seems to manifest itself
in so many different ways and no one "fix" seems to work for everyone.

my system:

asus p5ne-sli mobo
core 2 duo e6300
2GB ram
2 7600 GTKO-sli vid cards
nvidia binaries installed with restricted drivers manager
2.6.20-16.29-generic kernel
no ndiswrapper
"generic" gnome desktop (no compiz, beryl, etc)
all drivers, codecs, etc. installed from ubuntu repos

i haven't updated to the new 2.6.20-16.31-generic kernel yet- wondering if it solves anything?

interesting discovery, mobad... let's see how many people find multiple xorgs like you.

---

### Post by freakalad on 2007-09-05
Hi guys,

I'm experiencing similar issues.
I've recently started moving my entire co's machines over to (k)ubuntu.
Central server works nice, fairly happy with PC's; problems start cropping up with laptops.

I currently have 2 (old-ish; 2-5 yrs old) notebooks converted; fresh installations.

I suspect it might have something to do with FireFox or the power management.

I'd be cruising along in FF as I always have in windoze, and all sessions would just lock up, from anywhere from 5 secs to 5 mins. This seems to happen every time something slightly resource intensive is required, such as a click on a link or submission, and not necessarily related to flash. Sometimes it's just random

Sessions would lock-up, and should I minimize or resize, it simply does not refresh.
On the older of the 2 laptops, this seems to extend to other apps, such as OpenOffice, but if I depress some of the 'special shortcut' buttons, it seems to force some kind of reload. On the newer laptop, this seems to be isolated to FireFox for now; Konqueror seems fine.

Any clue as to how to troubleshoot/resolve this issue. Could it be a java/JS issue?

---

### Post by IVIisterX on 2007-09-05
@mobad! @majoridiot!

I have only one xorg.

IVIr.X

---

### Post by tech9 on 2007-09-05
try disabling ipv6... that cause a lot of issues for me until I disabled it.

---

### Post by mobad on 2007-09-05
> **IVIisterX said:**
> @mobad! @majoridiot!

I have only one xorg.

IVIr.X

Hmm what are you using? ATI/Nvidia and are you using the Ubuntu Restricted driver or the newer ones EVNY installs or you installed your self.  This bug has only been noticed on the self installed newer ATI drivers or the one ENVY installs.

---

### Post by IVIisterX on 2007-09-05
@mobad!

ATI 8.40.4 installed by envy!

IVIr.X

---

### Post by mobad on 2007-09-06
> **IVIisterX said:**
> @mobad!

ATI 8.40.4 installed by envy!

IVIr.X

Hmm OK too bad, I guess I was wrong.  But it may be because I'm using 64bit Ubuntu or my graphics card is hooked up to my TV.

---

### Post by majoridiot on 2007-09-06
> **tech9 said:**
> try disabling ipv6... that cause a lot of issues for me until I disabled it.

i disable IPV6 on all of my boxes, as a matter of course at install time.  i can guarantee this is not the problem- at least here.

---

### Post by IVIisterX on 2007-09-06
@mobad!

No problem - thx.

Actually my system runs pretty stable with Ati-driver 8.40.4 and all  kernels (2.6.20-15-generic, 2.6.20-16.31-generic and 2.6.20-16.31-386) and added code exit=0 in etc/init.d/powernowd.

Knocking on wood

IVIr.X

---

### Post by Emerald Wolf on 2007-09-07
Here's one for ya'll t'gnaw on for a bit...After having to start this again, because the dang Ubuntu box crashed again....I guess I'm pretty thankful to have a Sparc box for a "footstool" :)

Anyway, I started out with a pretty stable HP Pavilion 513x, running Ubuntu 7.04 (upgraded from Edgy).  It had 256 mb of memory (PC2100).  Ubuntu peacefully lived with Win2k on an 80gb Maxtor hard drive.  The hard drive was one that I got from my mother in law since she was worried about always getting a SMART warning.  I'd reformatted (with Solaris) on the SPARC box and didn't have any trouble with it (about a year ago or so)....Later it got formatted into it's current state.  Recently (couple of weeks ago), either the hard drive started really heading south, or I got a virus.  Only through the Grace of God and FTP (with a little Knoppix on the side) was I able to rescue a good bit of data.  The drive still seems like toast though.

So now since the Pavilion is down, I thought it would be a good time to play with the SuperMicro P6DBE mobo a friend gave me.  Currently it has dual 1 Ghz PIII, 397 mb of PC100 ram, a 10 gb Fujitisu HD, OEM DVD writer, Audigy, and Matrox G400.  At first I only had Winbloze in it, seemed fine.  The only issue was one of the getting a bit warm. (54C) At this time I had a 250 GB Western Digital HD, with WIndows on a 15 gb partition.  After the uneventful Ubuntu install, things went downhill from there.  It ended up hosing the MBR, and after much finagling I ened up with Fiesty on the 10gb Fuju HD.  I've had the mysterious crashes with both Edgy and Fiesty, several different ram sticks (PC100 and 133), three different hard drives, with and without a SCSI controller (and Exabyte tape library).  My guess is there is a hardware tweak somewhere.  I've had the ACPI issues too (common to this board I guess).  The only other problem that I've seen with this board is that I'm missiing one of the proc holders.  But the proc seems well seated and not all that loose.  Esp, since the computer fires right back up after a crash.

Now when I say crash, it REALLY crashes.  No keyboard or mouse.  Not even the clock.  I've tried Telnetting in from the Sun box, no go.  I've looked in the var/logs/messages (kern) (dmesg) for some clue to what crashed.  The only odd thing were periodic blocks of entries that just say "Mark" .....I guess the only thing left to try is to drop the drive into another 'puter" and see what happens.

Oh, almost forgot, the only other commonality in the crashes that I've noticed is they usually happen when I'm doing an elevated amount of typing, say during a message or a terminal session.  In fact, I'd first had it start happening while fighting a java install.  I'd originally started searching for issues with Terminal, and then found out that typing forum replies would trigger it to.....Maybe a problem with the keybord settings in Xorg?

Catchya on the Flip Side.....

Emerald Wolf -- the power management fix did nothing for me...

PS -- sorry for the long post, I figure that lots of details my jar somebody's memory....

---

### Post by IVIisterX on 2007-09-07
@Emerald Wolf!

In your case it is interesting that your machine is an "antiquity"; please don't misunderstand this - this is not personal-intentioned. I think the only analogy to newer machines is the fact that the Matrox G400 uses OpenGl too. This confirmes my suspicion that beside powernowd the graphics driver is also  responsible for the freezes.
So please tell us, which graphics drivers do you use and how did you install them. Do you use direct rendering? Which kernel version do you use?

IVIr.X

---

### Post by Phloston on 2007-09-08
I had a lot of freezing problems, programs quitting, mouse not working, keyboard not working etc. I also had boot problems with CRC errors Kernel panics etc. Finally the computer refused to start at all.

My problem was a faulty memory module. When I removed that, everything went back to perfect working conditions. So what I first thought was a unstable Feisty showed to be HW problems.

---

### Post by yann negri on 2007-09-08
same for me. Using desktop. Got FF from a disk that came with a magazine. it freezes a lot  when I use firefox more than anything else. the mouse moves, but cant close panels, cant do nothing much. I'm only 11, just got rid of windows. dont understnad linux that much

---

### Post by Mayfairy on 2007-09-08
I'm experiencing freezes too. They usually happen once or twice a day (maybe more often cause I'm not home all the time) and it will eventually go away, usually in 30 mins or so. When the freezes occur I can move my mouse, but a bit slowly. Menu items or right click menu won't show up. Not even Ctrl+Alt+F1 works. Switching workspaces with Ctrl+Alt+-> does work occasionally. 

I'm pretty sure they started appearing after I installed Compiz Fusion and Emerald themes. Can't think of anything else I changed in my system at the time when the freezes started appearing. 

Some people said they thought it was Firefox causing the problems. I can confirm that it happens to me with and without Firefox running. Personally I blamed Azureus file checks at first but then I noticed it happened even when Azureus wasn't running. 
I'm using Nvidia card and drivers, running kernel 2.6.20-16-386. 
Just now when writing this I stopped powernowd and we'll see if it does anything. 

Hope my input helps to narrow down the possible causes for the problem.


EDIT: 
Just recently I read about this USB stick usage as swap file increaser ([http://ubuntu-tutorials.com/2007/07/02/swapboost-v01alpha-early-testers-wanted/](http://ubuntu-tutorials.com/2007/07/02/swapboost-v01alpha-early-testers-wanted/)). I just bought a new USB stick to try out that stuff. Soon I noticed I had no swap (not caused by this swapboost, cause I couldn't make it work) and looked deeper into the problem. 
'free' command told me there was no swap in my system. /etc/fstab had this line:
> # /dev/sda5 -- converted during upgrade to edgy
UUID=41a40150-937b-4201-b817-7299cf4845ba none swap sw 0 0

I googled a bit and stumbled upon this blog ([http://pa0r.blogspirit.com/archive/2005/09/13/ubuntu-swap-problem.html](http://pa0r.blogspirit.com/archive/2005/09/13/ubuntu-swap-problem.html)) that said:

> I had problems when I ran several programs like firefox, gMFSK, gprsdrive, Glade, together. It would just lock up the laptop (256 MB, 1.2 GHz). Somehow I had messed up the swap space when I upgraded from UBUNTU 0.4 to 0.5.

Swapon did not work. It said 'Unvalid parameter /dev/hda3'. cfdisk revealed that /dev/hda3 was available as type 82 (Linux swap partition). 'Free', however, showed no swap partition. And 'top' showed Swap:0.

The problem has been solved; the swap partition was not initialized. After a 'mkswap /dev/hda3' and 'swapon' I now have 1 GB of swap space available again.

Going to try and enable my swap to see if it helps.

---

### Post by Emerald Wolf on 2007-09-09
Okay, now these crashes are getting a little out of hand.  I started a replay, but had it crash (this would be the second time)  So here I am using the W2k partition to answer back...:-x  Anyway, my system is setup as such...

P6DBE Dual PIII mother board with 2 1 ghz processors
397 mb ram
Matrox G400 graphics card running 1028x768 @75hz, using the mga driver (I think DRI too)
Audigy sound card
10 gb fujitsu hard drive, dual booted with W2k and Ubuntu 7.04 (2.6.20-16)

The lock ups usually occur while typing. I first noticed them while using Terminal, and then with typing stuff into Firefox.  It's kinda strange since my kb is a plain PS/2 kb.  I looked over the logs, and didn't see anything as being stand out to cause a crash, but I did notice that in several cases there seemed to be a restart after a cetain event loading....(I'll post it here once I get back to the Ubuntu partition, the ext3 reader for Windoze I have has been kinda flaky)

Catchya on the Flip Side.....

Emerald Wolf -- argh!

---

### Post by rickyrockrat on 2007-09-09
If your mouse is moving, it is not locked up, and you can EVENTUALLY get into a virtual console, but It took 5 minutes (or more) before I finally got to one.
I am running 2.13 Ghz Duo-Core, on an ECS-Nforce 570 SLIT-A V5.1, with a GFX 8500 Nvidia PCI-E card with Nvidia binary drivers.
I am running 2.6.20-16-generic. (BTW, Ubuntu is the first Linux install I didn't have to tweak something (besides video) to get everything working)

My HDD light is on almost continually and I can't get most apps to run..but perhaps it is because I haven't waited long enough.  I can ping from my network.

I suspect something is running my HDD ragged.  I'll post back if I can find the offending party.

Mine is a fresh install of 7.04 for x86_64Amd.

Oh, see if your numlock key responds by lighting the numlock LED.  This should tell you if the kernel is getting and responding to the keyboard.  I've had to unplug, then re-plug my keyboard to get it to rsespond.


It seems Feisty has had a lockup issue since April.  This is not good.

---

### Post by Emerald Wolf on 2007-09-09
I lose the mouse too when mine crashes....

I'll have to try replugging the keyboard.  Funny thing, the Pavilion that I'd been running Ubuntu on (also 7.04) actually had the much maligned ATI driver, and it worked fairly well with the older All in Wonder (r128).  Never had any trouble with it.

Heh, now it won't crash so I can test the replug method....:rolleyes:

Catchya on the Flip Side.....

Emerald Wolf -- actually been eyeing a CRON job as a possible culprit....

---

### Post by rickyrockrat on 2007-09-09
SO... It took almost an hour, but I finally got to a login (luckily I was already logged in as root on a text console, since attempted logins on other consoles only resulted in timeouts).  I ran top, which took about 15 minutes to load.  I started killing ('k' in top) apps that were using a lot of RAM/Swap.  I finally killed the app that had run the system out of memory, and I was able to recover - but this took ALOT of patience on my part.

The system was not hung, just completely resource starved.  Here is an interesting link for my system.  I will try it and see if it fixes my other hangs (I know they were hangs since I couldn't even ping the system).

[http://ubuntuforums.org/showthread.php?t=542126&highlight=duo-core+ubuntu+lockup](http://ubuntuforums.org/showthread.php?t=542126&highlight=duo-core+ubuntu+lockup)

I'll post anything else I can find that might effect this.

---

### Post by Emerald Wolf on 2007-09-09
Yeah, the kernel quits talking to everybody apparently.  The next crash that I had, I got nada on the num lock, and replugging the keyboard did nothing.  I even tried plugging in a USB keyboard.  As of right now, I'm using the USB keyboard...The only thing that I've seen that's kinda odd is in the /var/log/message is this weird bit about gconfd.....Is this normal?

Sep  9 15:22:48 Frankenputer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0
.dbus.get.nis_domain
Sep  9 15:22:48 Frankenputer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0
.dbus.get.nis_servers
Sep  9 15:42:33 Frankenputer -- MARK --
Sep  9 15:43:32 Frankenputer gconfd (paul-5102): starting (version 2.18.0.1), pid 5102 user 'paul'
Sep  9 15:43:32 Frankenputer gconfd (paul-5102): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-onl
y configuration source at position 0
Sep  9 15:43:32 Frankenputer gconfd (paul-5102): Resolved address "xml:readwrite:/home/paul/.gconf" to a writable configurati
on source at position 1
Sep  9 15:43:32 Frankenputer gconfd (paul-5102): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only
 configuration source at position 2
Sep  9 15:43:32 Frankenputer gconfd (paul-5102): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-onl
y configuration source at position 3
Sep  9 15:43:32 Frankenputer gconfd (paul-5102): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only confi
guration source at position 4
Sep  9 15:43:41 Frankenputer gconfd (paul-5102): Resolved address "xml:readwrite:/home/paul/.gconf" to a writable configurati
on source at position 0

One of the bits that I've noticed some time before a crash is the "-MARK" line, Usually 2-10 of them, and then is crashes....Hope this helps...

Catchya on the Flip Side.....

Emerald Wolf -- odd...

---

### Post by soxs on 2007-09-10
I just killed my feisty... and installed gutsy which is fairly stabel... did not expirience a single freeze.

---

### Post by Mayfairy on 2007-09-10
> **rickyrockrat said:**
> SO... It took almost an hour, but I finally got to a login (luckily I was already logged in as root on a text console, since attempted logins on other consoles only resulted in timeouts).  I ran top, which took about 15 minutes to load.  I started killing ('k' in top) apps that were using a lot of RAM/Swap.  I finally killed the app that had run the system out of memory, and I was able to recover - but this took ALOT of patience on my part.

The system was not hung, just completely resource starved.  Here is an interesting link for my system.  I will try it and see if it fixes my other hangs (I know they were hangs since I couldn't even ping the system).

[http://ubuntuforums.org/showthread.php?t=542126&highlight=duo-core+ubuntu+lockup](http://ubuntuforums.org/showthread.php?t=542126&highlight=duo-core+ubuntu+lockup)

I'll post anything else I can find that might effect this.

Now that seems to be the same problem that I have. Some people here seem to exprience lock-ups, freezes, crashes etc. What program was it that used all the memory for you? 
I also tried ssh'ing into my box from another computer without any kind of response.

Pointing back to my previous post in this thread it seems that enabling swap partition didn't fix the problem, but it might have eased it a bit. 

Last freeze I experienced was this morning. I had just woken up and my computer had been running all night long. Programs that were on were Azureus, Firefox, Terminal and Yakuake.. of course Compiz, Emerald, Screenlets and Kiba-dock running too along with the usual. 
I moved mouse a bit and then it started. Sysinfo screenlet told me memory and processor usage were at 99%. Managed to hit Ctrl+F1 eventually and after few tries I could log in from the console, but nothing else. Left computer to do whatever it was doing and came back after an hour or two. Everything was cleared already. 
Something is really hogging my system resources. 

Some system specs:
AMD Athlon64 2800+ (running 32-bit Ubuntu Feisty)
1Gb RAM
GeForce 6600GS 
Asrock-939 dual sata2 motherboard

I think I'll go and buy another Gig of RAM. Going to need it anyways. We'll see if that helps at all.

---

### Post by soxs on 2007-09-10
As a final move I have a zip ready to submit, which contains all log data from my last feisty freeze. If anybody can tell me where to submit I'll do so..

---

### Post by Keyper7 on 2007-09-10
Okay, here's my not-so-feisty (pun intended) situation:

Running Ubuntu 7.04 amd64 in a HP Pavilion DV6258SE
(Turion X2, 2 Gig RAM, GeForce Go 6150)

Compiled vanilla kernel 2.6.22.6 and installed nvidia driver 100.14.11
and I'm currently using compiz fusion, screenlets and kiba-dock.
CF is from trevino's repositories, screenlets are from official
repositories and kiba-dock is compiled from SVN source.

I'm experiencing A LOT of random freezes, but didn't notice any
pattern so far, except that they appear to be more frequent if
the system is loaded (firefox with lots of tabs, for example).
During the freezes, top accuses Xorg of eating 100% of the CPU.

However, of all the dozens of freezes I had, only ONE was permanent.
In all the other freezes the system returned to normal 5-10 seconds after.
Even on the permanent one, I could do a soft shutdown because my
power button was set to shutdown without asking, and it worked.

I boot with no extra parameters, but noapic did no good. Neither did
GL_YIELD="NOTHING" or indirect rendering while running compiz.

I didn't test extensively, but the freezes appear to completely go away
if compiz is disabled. But I supposed that doesn't mean compiz is to
blame. Could be the nvidia driver or the kernel in combination with it.

Gonna do some fine tuning and try to find out if some specific compiz
plugin is responsible for the freezes. It's definitely not the animation
plugin, though, since it was disabled when I experienced the permanent
freeze.

Does anyone here has a similar situation?
(almost all freezes temporary, disabling compiz solves it)

-Keyper7

---

### Post by Emerald Wolf on 2007-09-10
Well, I'm still keeping my fingers crossed, but I think I finally figured out my bug.  I ended up switching to a USB keyboard, and haven't had a freeze yet...(Well, I had both hooked up, and it only locked up after hitting a few keys on the PS/2 keyboard.  After unplugging the PS/2, I've not had a lock up yet.)

Now if I can just get Enlightenment to play a little nicer...:)

Catchya on the Flip Side.....

Emerald Wolf -- Is going to try the Pavilion again here soon....

---

### Post by Keyper7 on 2007-09-11
What the heck just happened here?

I'm about to complete two hours of usage with compiz fusion enabled without noticeable freezes.

All I did in the last hours was disable some services I don't use, such as hplip and bluetooth, I can't even remember exactly which ones I disabled (I did it through the gnome service tool, though, so it will be easy to redo my steps, since it's just a matter of checking and unchecking checkboxes)

I'll do some fine search tomorrow and try to discover exactly what I did.

---

### Post by Digitallysick on 2007-09-11
for me, with beryl disabled, i had no freezes ever, with the 32 bit or 64 bit ubuntu, finally i switched to 64 bit from the 32 bit, did a fresh install and used the compiz installer scripts to build from source. It runs well unless i turn on certain effects (like fire, or gl screen savers) then it freezes, but if i keep just the cube, and wobble windows going, its fine. so i stick with that and i don't push my luck

---

### Post by Keyper7 on 2007-09-11
> **Keyper7 said:**
> What the heck just happened here?

I'm about to complete two hours of usage with compiz fusion enabled without noticeable freezes.

All I did in the last hours was disable some services I don't use, such as hplip and bluetooth, I can't even remember exactly which ones I disabled (I did it through the gnome service tool, though, so it will be easy to redo my steps, since it's just a matter of checking and unchecking checkboxes)

I'll do some fine search tomorrow and try to discover exactly what I did.

Oh, wait, here are the freezes again. Damn it.

However, they are remarkably rarer now, I still don't know why.

---

### Post by rickyrockrat on 2007-09-11
Well, my Ubuntu locked up again.  I cannot ping it, and num lock does not respond on the keyboard, but if it is resource starved, it could take some time to respond.  Mouse is not moving.  About 20 minutes ago I hit Ctrl-Alt-f1 several times, and it appears my monitor *may* be slowly repainted at like a couple pixels a minute.  I have work to do, so I just reset it.

FYI, everybody, the MARK in your syslog is only syslog telling you it is still alive and nothing is being written to syslog (i.e. nothing is happening), but with the logs being split into multiple files, it is hard to tell WHAT is going on.

It looks like the last log I can find is in user.log telling me gconfd is exiting

If you want to have ALL your messages from syslog, dumped to one file (for debug only), edit the /etc/syslog.conf and uncomment/ add a line like the following:

*.*  -/var/log/all

This should give you just one place to look while debugging this beast.
I am doing a full upgrade of all modules for feisty and try again with this single file and fully updated system.

---

### Post by IVIisterX on 2007-09-11
@All novices in this forum!

Before you post your problems: 

Please check out majoridiots "soulutions" posted under
[http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)
Please check out FuturePilot's post under
[http://ubuntuforums.org/showpost.php?p=3305810&postcount=635](http://ubuntuforums.org/showpost.php?p=3305810&postcount=635)
Please check out my "solutions" posted under [http://ubuntuforums.org/showpost.php?p=3275045&postcount=610](http://ubuntuforums.org/showpost.php?p=3275045&postcount=610)

Combine these approaches - but change only one setting at the same time!

For my system I found the ideal settings:

powernowd uninstalled, ACPI 2.0 support enabled in BIOS (what ever this is), exit 0 added in /etc/init.d/powernowd, kernelupdate to 2.6.20-16.31-generic, ATI-driver 8.40.4 installed by Envy. No freezes with all kernels (2.6.20-15-generic, 2.6.20-16.31-generic and 2.6.20-16.31-386) since one week! 

Many thanks

IVIr.X

---

### Post by soxs on 2007-09-11
Got freezies again, even gutsy has this damn desease...

---

### Post by johanPO on 2007-09-11
It is an Ubuntu desease... I had it on Ubunutu, Mint and Mepis 6.5. I tried PCLOS, Sabayonne, Fedora, Suse and right now Mepis 7.0 (ubunut based) and none of them had it this desease...

Just try them out and you will see that there are other distros out there that are mabye not better or worse but  at least a lot more stabile.

---

### Post by rickyrockrat on 2007-09-11
The main issue with removing powernowd is that laptops will have battery life and heat issues, and it makes no sense to edit a script that starts a daemon that has just been removed (post 544)...Oh, I see the script now just changes 

/sys/devices/cpu/cpu0/cpufreq/scaling_governor from ondemand to performance.

That, however does not work on 2.6.16-generic for duo-core, since that directory does not even exist (at least on my machine).

I will see if my BIOS has the APIC 2.0 enabled or not. APIC stands for Advanced Programmable Interrupt Controller, BTW.


This is, unfortunately just a band-aid and no help for laptop folks.  I wish I had time to run this into the ground, but unfortunately my machine is SUPPOSED to be a Linux development box, not one I have to screw with.

Fine. I started digging into the lkml (please don't flood the list with questions - they won't answer, and you will just generate noise on the list).  Here is a reference to this in the 2.6.20 kernel:
[http://lkml.org/lkml/2007/7/26/408](http://lkml.org/lkml/2007/7/26/408)

Notice, of course that it is x86_64...but apparently this is the cause of SOME lockups.

---

### Post by jb201116 on 2007-09-11
Simple solution,

UPGRADE your BIOS to the latest version on the your manufacturers site

Next amend your boot loader to add the following
 -noapic apic=off

Also try upgrading any network controller drivers and your graphics drivers to either a generic set that is Linux recommended or to the latest on the manufacturers site. 

Finally reboot.

works a treat especially if its a Dell

I was having this exact same problem on my Dell did everything above and have now got Feisty running smoother than Microcrap

jb201116

---

### Post by iq007 on 2007-09-12
Just stop dbus service and the freezes will disappear:

sudo /etc/init.d/dbus stop

---

### Post by Supremacy on 2007-09-12
> **iq007 said:**
> Just stop dbus service and the freezes will disappear:

sudo /etc/init.d/dbus stop

Sounds interesting. I'll give that a go. What system specs do you have?

Regards,
Supremacy

---

### Post by iq007 on 2007-09-12
I have a Dual Core Intel, but this does'n really matter, as the freeze reproduces on many different systems. I think the freeze is caused by a check which HAL (Hardware abstraction layer) performs from time to time. The log entry during the freeze is this:

Sep 12 15:04:44 Ubuntu kernel: [  483.860000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Sep 12 15:04:55 Ubuntu kernel: [  483.860000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
Sep 12 15:04:55 Ubuntu kernel: [  483.860000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Sep 12 15:04:55 Ubuntu kernel: [  488.900000] ata1: port is slow to respond, please be patient (Status 0xd0)
Sep 12 15:04:55 Ubuntu kernel: [  493.888000] ata1: device not ready (errno=-16), forcing hardreset
Sep 12 15:04:55 Ubuntu kernel: [  493.888000] ata1: soft resetting port

So it has to do with cdrom-hdd being on the same IDE channel I think. Please tell me if disabling dbus fixes the problem.

Good luck.

---

### Post by mzilhao on 2007-09-12
it didn't work for me... just had another freeze... 
getting really tired of this. i'll install gutsy in the weekend, if the freezing continues i'm giving up on ubuntu and installing fedora 8.

---

### Post by Mayfairy on 2007-09-12
> **IVIisterX said:**
> @All novices in this forum!

Before you post your problems: 

Please check out majoridiots "soulutions" posted under
[http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)
Please check out FuturePilot's post under
[http://ubuntuforums.org/showpost.php?p=3305810&postcount=635](http://ubuntuforums.org/showpost.php?p=3305810&postcount=635)
Please check out my "solutions" posted under [http://ubuntuforums.org/showpost.php?p=3275045&postcount=610](http://ubuntuforums.org/showpost.php?p=3275045&postcount=610)

Combine these approaches - but change only one setting at the same time!

For my system I found the ideal settings:

powernowd uninstalled, ACPI 2.0 support enabled in BIOS (what ever this is), exit 0 added in /etc/init.d/powernowd, kernelupdate to 2.6.20-16.31-generic, ATI-driver 8.40.4 installed by Envy. No freezes with all kernels (2.6.20-15-generic, 2.6.20-16.31-generic and 2.6.20-16.31-386) since one week! 

Many thanks

IVIr.X

These did nothing to me. After waiting for especially long freeze to wear off for over half an hour I rebooted my machine and noticed somehow Emerald theme didn't get loaded. Didn't enable it and continued working for 5 hours or so and no freezes anymore. Just now I enabled Emerald themes and waiting for my system to freeze any second.

---

### Post by soxs on 2007-09-12
It's somehow crazy... it seems to be determined to freeze or not when booting...
I do the exact same actions after reboot and I get a freeze... strange, odd
testing linux mint, fedora 7/8

---

### Post by Emerald Wolf on 2007-09-12
Too bad there isn't a way to compile a list of the hardware everybody is fighting with against settings.  My guess is that it's a combination of hardware.  I personally kinda entered into the problem assuming a hardware issue (that's what you get with old crap :lolflag:  But it seems that the rest of ya'll have more cutting edge machines that shouldn't have issues to PS/2 connectors/ports.  My guess is that it's a combination of hardware that causes the issues.  Wouldn't that be a real stinker if it's something stupid like IRQ conflicts?

Catchya on the Flip Side.....

Emerald Wolf -- Like I said somewhere above, I was running Ubuntu 7.04 (the 2.6.2-16 kernel IIRC) on a Pavilion 513x w/256 mb ram and an ATI All in Wonder (I don't recall what driver) and never had so much as a hiccup until either a virus got it or the HD went south.....(HD had been giving the SMART warning for some time.)

---

### Post by Mayfairy on 2007-09-13
I *think* I have made some progress. Changed some boot options and my system seems to be much more stable than before. Only one freeze and it wasn't even a bad one. 
What I did was add these arguments on my /boot/grub/menu.lst: noapic acpi=off nolapic irqpoll ht=on
Also apt removed powernowd, but it didn't make the freezes go away alone. Might have some impact with the boot arguments I used.

---

### Post by IVIisterX on 2007-09-13
> **Mayfairy said:**
> I *think* I have made some progress. Changed some boot options and my system seems to be much more stable than before. Only one freeze and it wasn't even a bad one. 
What I did was add these arguments on my /boot/grub/menu.lst: noapic acpi=off nolapic irqpoll ht=on
Also apt removed powernowd, but it didn't make the freezes go away alone. Might have some impact with the boot arguments I used.

I made the same experience: it is not enough to change one setting; you have to find the right combination. But if your system seems to be more stable, you are on the right way.

IVIr.X

---

### Post by Mayfairy on 2007-09-14
Nope.. It's still the same. :(
Everything was fine for two days straight, but now the freezes are back and worse than ever. :mad:

---

### Post by OmniCloud on 2007-09-14
> **Mayfairy said:**
> Nope.. It's still the same. :(
Everything was fine for two days straight, but now the freezes are back and worse than ever. :mad:Same here...

I have a DELL PC and I've had a few bad installs, but my older version of Ubuntu never froze this much...

Before I go and read the whole thread, can some1 just let me know if there have been ANY complete removals of this freeze issue? 

I think I may just goto Fedora if there hasn't...

Looks pretty much the same anyway, and I don't care for all the hi-tech visual effects...

I just use the wiggily web pages and cube rotate--and I'm good...

---

### Post by OmniCloud on 2007-09-14
> **jb201116 said:**
> Simple solution,

UPGRADE your BIOS to the latest version on the your manufacturers site

Next amend your boot loader to add the following
 -noapic apic=off

Also try upgrading any network controller drivers and your graphics drivers to either a generic set that is Linux recommended or to the latest on the manufacturers site. 

Finally reboot.

works a treat especially if its a Dell

I was having this exact same problem on my Dell did everything above and have now got Feisty running smoother than Microcrap

jb201116Are you talking about a desktop Dell? Because I have that...and despite the freezes I'm perfectly happy with Ubuntu...

Honestly I have waaay too much apps that I've had to search for and tweak to get to work the way I want, and a fresh install of Fedora or something means you have to go and install a bunch of codecs/dependicies and what not just to visit youtube and other popular sites. 

If this solution works on Dells, can you give me or point me to a step by step, I'm not exactly computer literate:-(

---

### Post by zhinker on 2007-09-14
I doubt this is a hardware problem.  I've been running Fiesty on my Dell with an ATI card since April and my computer never froze...until yesterday that is when I did a fresh reinstallation of Feisty (nothing responds except the mouse, though pressing Alt+Prnt Screen+(R, E, I, S, U, B, sequencially in that order) will restart my computer.  The only physical change to my computer is a new wireless card I added a couple weeks ago and when reinstalling Fiesty I shrunk the swap from around 800 to 700Mb and resized the drivers.  So I'm thinking this has to be something that's software only.

---

### Post by mzilhao on 2007-09-14
just had a freeze with gutsy... i give up. i'm going to install fedora 8.

---

### Post by IVIisterX on 2007-09-16
Hello altogether!

After 10 days without any freezes by multiple starts every day i had two freezes at friday evening. The first 8 minutes after start; the second 9 minutes after reset. Since another reset my system is working without any additional freezes up to the moment.
I guess furthermore, that there are some periodical processes which are responsible for the freezes. Is there perhaps anything else like the periodical harddisc checking? Does anyone else know something about periodical actions?

IVIr.X

---

### Post by joe.turion64x2 on 2007-09-16
Some weeks ago I had problems to install Fedora 7 x86 in my laptop: it wanted my USB mouse to be connected or it refused to work, unless I kept 'moving and clicking' the touchpad. Then I tried with Fedora 7 x86_64 and everything is working now (no mouse issues at all!).

After that I tried to install VectorLinux and, guess what? it refused to install unless my USB mouse was connected. Reading the release notes in both distributions I found that both had the 2.6.21 kernel, and both refused to work unless I went 64 bit. 

So, since Linux's with kernel prior to 2.6.21 work like a charm in my machine (in x86 mode) I am starting to think that either my chipset (ATI X1100) is not quite well supported by kernels 2.6.21+ x86 (and I am supposed to run the machine at full capabilities), or my mainboard is defective (which I rather doubt).

Does your machines support 64 bit? Perhaps that is the solution for you, or perhaps keep clicking.

Thanks.
Joe.

---

### Post by Footer on 2007-09-16
Hello Mr. X!

I too am on Day 10+ without a reboot or freezing issue.  I think my freezing problem is mostly due to Superkaramba which causes Xorg to freeze per this bug report:

     [http://bugs.kde.org/show_bug.cgi?id=143255](http://bugs.kde.org/show_bug.cgi?id=143255)

I normally have two applets open but when I'm leaving the machine idle for awhile or overnight, I shut down one of them so I only have one running.  Basically, doing this and watching the Xorg process percentage vs. top as well as closing Firefox and reopening every so often, has for the most part eliminated my freezes.  My Xorg is at about 15.2% currently and if it starts getting close to 20%, I'll just usually log off and back on which usually lowers it.

That Superkaramba bug has been around for awhile now with no resolution and although it says it's applicable to Gentoo packages, I think it affects U(K)ubuntu as well.  At least that's been my experience.

---

### Post by arvevans on 2007-09-16
Similar problem here, but I fixed mine.
I use an AMD X2 64-bit 3200 system with a Via Chipset based motherboard.  After much research I found that AMD dual-core CPUs have a low-power_slow-clock mode that kicks in during periods of low activity.  When I went into BIOS/CMOS and turned this feature OFF, the frequent "White Screen of Death" went away and has not returned.

Fixing all similar problems may not be this simple, but this did work for me.  If you are experiencing similar problems with an AMD X2 (dual core) 64 bit CPU based system, then it is worth a try.

Arv
_._

---

### Post by majoridiot on 2007-09-16
just as an update, i have experienced only one freeze since making the changes i have previously detailed... and
that was a "hard" lock-up, so i'm not willing to say it wasn't due to other issues.

i'm currently running fully-updated fesity installs on 3 machines.  the two amd64 (running 32 bit) work just fine
and have never frozen.  the dual core E6300 is the only box that experiences this problem.  all three run asus
motherboards and nvidia cards with restricted drivers.  other than the cpu, the only major difference in the box that
freezes is that it runs 3 screens, where the others drive a single head only.

for what it's worth...

---

### Post by JoBangles on 2007-09-17
Hi, I have just developed similar problems over the last few days. Up to then all was O.K. When I play a video the system hangs part way through the video. I ran "System Monitor" in parallel and soon as it froze I hit "Kill Process" with no result and when I hit "End Process" system froze. If I had a game of "Solitaire" running I could continue to play but as soon as I clicked on the top menu bar the system froze. I ran software to check hard drive and all O.K. Following is excerpts from "/var/log/messages" most at the point when I hit the reset button, the last two definitely when system froze. Any help greatly appreciated and thanks in advance. 

"/var/log/messages extracts:"

gconfd (grm-7235): Failed to send buffer

gconfd (grm-6019): Resolved address "xml:readwrite:/home/grm/.gconf" to a writable configuration source at position 0

gconfd (grm-6094): Resolved address "xml:readwrite:/home/grm/.gconf" to a writable configuration source at position 0

gconfd (grm-6092): Resolved address "xml:readwrite:/home/grm/.gconf" to a writable configuration source at position 0

Sep 16 14:49:09 HAL gconfd (grm-6010): Failed to send buffer
Sep 16 15:18:04 HAL -- MARK --
Sep 16 15:38:05 HAL -- MARK --
Sep 16 15:58:05 HAL -- MARK --
Sep 16 16:18:05 HAL -- MARK --
Sep 16 16:38:05 HAL -- MARK --
Sep 16 16:58:06 HAL -- MARK --
Sep 16 17:18:06 HAL -- MARK --
Sep 16 17:38:06 HAL -- MARK --
Sep 16 17:58:06 HAL -- MARK --
Sep 16 18:18:07 HAL -- MARK --

Sep 16 19:38:59 HAL kernel: [ 4226.900193] ide: failed opcode was: unknown
Sep 16 19:38:59 HAL kernel: [ 4227.000708] hdb: status timeout: status=0xd0 { Busy }
Sep 16 19:38:59 HAL kernel: [ 4227.000711] ide: failed opcode was: unknown
Sep 16 19:38:59 HAL kernel: [ 4227.340094] ide0: reset: success
Sep 16 19:38:59 HAL kernel: [ 4247.340350] hdb: dma_timer_expiry: dma status == 0x41
Sep 16 19:38:59 HAL kernel: [ 4257.338478] hdb: DMA timeout error
Sep 16 19:38:59 HAL kernel: [ 4257.338492] hdb: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Sep 16 19:38:59 HAL kernel: [ 4257.338497] ide: failed opcode was: unknown
Sep 16 19:38:59 HAL kernel: [ 4257.439015] hdb: status timeout: status=0xd0 { Busy }
Sep 16 19:38:59 HAL kernel: [ 4257.439018] ide: failed opcode was: unknown
Sep 16 19:38:59 HAL kernel: [ 4257.778402] ide0: reset: success
Sep 16 19:38:59 HAL kernel: [ 4277.778651] hdb: dma_timer_expiry: dma status == 0x41
Sep 16 19:38:59 HAL kernel: [ 4287.776780] hdb: DMA timeout error
Sep 16 19:38:59 HAL kernel: [ 4287.776795] hdb: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Sep 16 19:38:59 HAL kernel: [ 4287.776800] ide: failed opcode was: unknown
Sep 16 19:38:59 HAL kernel: [ 4287.877321] hdb: status timeout: status=0xd0 { Busy }
Sep 16 19:38:59 HAL kernel: [ 4287.877324] ide: failed opcode was: unknown
Sep 16 19:38:59 HAL kernel: [ 4288.216713] ide0: reset: success

Sep 17 09:45:39 HAL gconfd (grm-6086): Failed to send buffer

Sep 17 11:04:30 HAL gconfd (grm-9008): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 17 11:04:46 HAL exiting on signal 15

Sep 17 11:06:28 HAL gconfd (grm-6006): Resolved address "xml:readwrite:/home/grm/.gconf" to a writable configuration source at position 0

Sep 17 11:09:01 HAL gconfd (grm-5830): Resolved address "xml:readwrite:/home/grm/.gconf" to a writable configuration source at position 0
Sep 17 11:09:57 HAL gconfd (grm-5830): Failed to send buffer
Sep 17 11:12:11 HAL kernel: [  279.831214] cdrom: This disc doesn't have any tracks I recognize!
Sep 17 11:28:32 HAL -- MARK --
Sep 17 11:37:43 HAL gconfd (grm-5830): Exiting

Sep 17 13:57:59 HAL gconfd (root-6879): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 17 13:58:59 HAL gconfd (root-6879): GConf server is not in use, shutting down.
Sep 17 13:58:59 HAL gconfd (root-6879): Exiting
Sep 17 14:11:55 HAL -- MARK --
Sep 17 14:31:56 HAL -- MARK --

Sep 17 14:40:02 HAL gconfd (grm-6032): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 17 14:40:09 HAL gconfd (grm-6032): Resolved address "xml:readwrite:/home/grm/.gconf" to a writable configuration source at position 0

Sep 17 15:01:37 HAL gconfd (grm-5999): Resolved address "xml:readwrite:/home/grm/.gconf" to a writable configuration source at position 0
Sep 17 15:03:11 HAL gconfd (grm-5999): Failed to send buffer
Sep 17 15:03:16 HAL gconfd (grm-5999): Failed to send buffer

---

### Post by Mayfairy on 2007-09-17
> **majoridiot said:**
> just as an update, i have experienced only one freeze since making the changes i have previously detailed... and
that was a "hard" lock-up, so i'm not willing to say it wasn't due to other issues.

i'm currently running fully-updated fesity installs on 3 machines.  the two amd64 (running 32 bit) work just fine
and have never frozen.  the dual core E6300 is the only box that experiences this problem.  all three run asus
motherboards and nvidia cards with restricted drivers.  other than the cpu, the only major difference in the box that
freezes is that it runs 3 screens, where the others drive a single head only.

for what it's worth...

If you're referring to this [http://ubuntuforums.org/showpost.php?p=3134000&postcount=544]("http://ubuntuforums.org/showpost.php?p=3134000&postcount=544")
then I can confirm that. I've had one or two freezes after that. 
Later on I tried updating to Gutsy kernel (2.6.22.) but it didn't work so I downgraded back to 2.6.20.16 and was forced to play around with Nvidia drivers and reinstall Emerald and some other stuff the kernel upgrade had screwed up. After that not a single freeze. I'm not sure if that kernel confusion had any impact on clearing these freezes, but like majoridiot already told his instructions sure eased a situation for me. 

[quote=majoridiot]no idea how this may or may not affect single core or AMD systems, but it looks like it fixed it for me.[/quote]
Got AMD Athlon64 3000+ (not a 2800+ as I mentioned in some post above) and can say that it affects single core AMD system as well. 
[quote=majoridiot]in my case, my boot kernel went from: /boot/vmlinuz-2.6.20-16-generic root=UUID=42ab0f44-ab10-4ebd-a52d-cd514b97530f ro quiet splash
to: 
/boot/vmlinuz-2.6.20-16-generic root=UUID=42ab0f44-ab10-4ebd-a52d-cd514b97530f ro quiet splash noapic nolapic irqpoll ht=on[/quote]
I ended up using all those and 'acpi=off'' also. 

OOPS! 
Now that I checked that I actually had applied all those mentioned above I saw this kernel confusion had brought my kernel options back to 'ro quiet splash' and not a single freeze after that. Thinking back what I did when I noticed my kernel didn't work was reinstalling Emerald and updating my Nvidia drivers.

---

### Post by OmniCloud on 2007-09-17
It seems the effects are hit and miss depending on the configuration of your PC...

I love Ubuntu, but to be honest, I really don't use that much eye candy...

I'm probably gonna get a mac and then switch my Dell over to Fedora...

I really love Ubuntu tho, is the terminal commands the same in Fedora? 

like *sudo apt-get install *

just did a little research and it seems Fedora has it's ups and downs as well....

Looks like I'm gonna have to stick with Ubuntu and find a solution to this problem...

*Goes to read entire thread*

lol

I tried nopaic thing, that's gonna need some time tho, since i hardly ever shutdown my PC...I will have to see if still freezes...

However, I may have found  a solution to the freezing--although it is still unacceptable...

When my desktop freezes, you can literally see that the CPU is still functioning in the background, and even if you hard shutdown and come back, firefox will ask you to restore your session...So It's kinda like the computer is not really restarting--I'm just coming back to the same problem..

So if I have another freeze, I just load up another Distro (fedora in this case) from a live CD, and shut down the comp from that actual disc. Then when I boot-up Ubuntu I'm back to normal...

I do plan on sticking with Ubuntu, but if a stable solution isn't found that WORKS 99 percent of the time, I'll just put Fedora on my Mac when I get it...

My dream PC--MacOX tiger partitioned with Ubuntu....

---

### Post by rickyrockrat on 2007-09-18
I've been with RedHat since 5.2, and Fedora has it's issues.  Their install system (yum, not apt-get) has gotten buggered on a couple systems.  Fedora is beta - if you want something more stable, use CentOS.  You will have a lot more fiddling with your system than with Ubuntu, and yes the commands are the same (some will be new, some missing, but std Unix on all).  

Sorry for the sidetrack.  My Duo-Core2  will run for a week then freeze. Other times it runs just a day or less.  This absolutely sucks - I feel like I'm running the POS windblows.

The unfortunate part about this thread is that all kinds of "freezes" are in this thread, and the freezes are extremely hard to duplicate (i.e. predict when it will happen). I'm running with apic=ht, we will see....

---

### Post by Digitallysick on 2007-09-18
Well im frustrated i seemed to fair better with 64bit ubuntu and installing compiz from the source install scripts vs apt-get, but my distro has froze so many times in the last month im going to reformat with xfce 64bit ubuntu and see how well it goes, i also have sabayon 64bit, i will try if it doesn't work out well for me.

---

### Post by mrjoeyman on 2007-09-18
Just in case it makes any difference to anyone, I have had the freeze problems and tried aaallllllllllllllll of the stuff here in the forum to get rid of it, and finally something worked that no one said anything about. It may not work for anyone else but I have the ati radeon 9100 and I changed the interrupt irq in the bios from 7 to 5.  I have no idea what it did, but it worked.

---

### Post by Keyper7 on 2007-09-18
Damn, am I the only one around here who does not have any bios options except for the ordinary ones (boot order, password, date setting, etc.)?

---

### Post by Danyl on 2007-09-19
> **semijoyful said:**
> I posted this to launch pad under bug#131973.

Hi, all!
I am a new Ubuntu (Feisty Fawn) user. Here's information about my system off the top of my head:
Dual boot PC (XP, Ubuntu)
Pentium 4 HT 3.2GHz
Elite Xpress Motherboard w/on board express ATI
Express AGP Nvidia Ge-Force
I believe the kernel is the newest one.

Right out of the gate, my computer has been experiencing hard freezes. The first time that I got one was when I was just accessing restricted drivers. This is not the only time, however. I can expereince these random freezes at any point that Ubuntu is running. I want to make this work, but if the OS causes me to re-boot my whole system before I can even finish a task, I am not sure my willingness will last long. I am new at this, and I'm curious if one can get me on the right track to solving this problem.
Greatly appreciative in advanced,

semijoyful

Just thought I'd add that I've been experiencing this exact same problem.

Have tried fresh installs, run diagnostics on my hard drives but to no avail. I'm thinking it may actually be the restricted modules causing problems as on one attempt, when upgrading from Edgy, the terminal froze at this point:

"Setting up linux-image-generic (2.6.20..16.28.1)
Setting up linux- restricted- modules- 2.6.20-16.generic (2.6.20.5-16.29)"

I've gone back to Windows until a sure fire fix has been developed.

---

### Post by soxs on 2007-09-19
Back on gutsy gibbon again...
I've tested..
Fedora core 7 which is hardly usable... total freezes every 5-10 mins, will test fedora 8(8. Nov07)
LinuxMint worse than gutsy but better than fedora, ~ the freezing frequency of my feisty fawn ubuntu (wow, in fact Mint is just an extension..)

I am not going to test opensuse or debian (I dislike suse and debian is simply outdated for desktops and not very userfriendly, oldschoolstuff)

So I stick with ubuntu... at least for the moment at fresh install it *seems* to be stable

Note: I am never ever going to unburry microsuxxs crap again... I got the ubuntu taste^^

---

### Post by majoridiot on 2007-09-19
> **Mayfairy said:**
> Got AMD Athlon64 3000+ (not a 2800+ as I mentioned in some post above) and can say that it affects single core AMD system as well. 

i've got 2 boxes running AMD 64's... both 3400+bx, asus k8ne mobos and nvidia FX5500's (one pci and the other
is AGP).  both are configured pretty much identically and run the restriced nvidia driver.

strangely, both are rock-solid and have *never* frozen.

> **soxs said:**
> Back on gutsy gibbon again...
I've tested..
Fedora core 7 which is hardly usable... total freezes every 5-10 mins, will test fedora 8(8. Nov07)
LinuxMint worse than gutsy but better than fedora, ~ the freezing frequency of my feisty fawn ubuntu (wow, in fact Mint is just an extension..)

I am not going to test opensuse or debian (I dislike suse and debian is simply outdated for desktops and not very userfriendly, oldschoolstuff)

So I stick with ubuntu... at least for the moment at fresh install it *seems* to be stable

Note: I am never ever going to unburry microsuxxs crap again... I got the ubuntu taste^^

great info to have- thanks.  if nothing else, maybe this will quell the ubuntu bashers and prove that this seems to 
be a linux-wide problem- depending on your hardware and configuration.  hopefully the kernel devs will suss the
problems soon.

---

### Post by JoBangles on 2007-09-19
It,s O.K. I installed a 3rd. 80gig hard drive and fresh installed Ubuntu

---

### Post by bootsbradford on 2007-09-20
I'd be interested if someone can explain this...

I've been having a variety of problems with Feisty, depending on which video driver I have:

**_Option 1: Open source driver_**
PC was freezing regularly since Feisty (fine with Edgy), with music still playing, mouse still moving, only option to hold down power button etc. 

So i went to the Restricted Drivers Manager and tried to install the ATI driver...

**_Option 2: fglrx driver (incorrectly configured)_**
Besides Firefox crashing much more often, this was fine **and the freezing completely stopped**, though the driver was clearly not configured properly as 'fglrxinfo' in the terminal reported:

> Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

So I ran the command: 'sudo aticonfig --initial --force'

This moved me to...

**_Option 3: fglrx properly configured_**
'fglrxinfo' returned the correct ATI info (as opposed to the mesa stuff)

However, I've now been experiencing 2 major problems:
[LIST=1]
[*]Open Office does not open
[*]I cannot log out of a session and log into another, I just have to reboot
[/LIST]

I am now back to the open source driver and waiting for my crash, though still wondering why there are so many problems with whatever I try! :(

These are my basic specs:

Dell Dimension 8400
Intel(R) Pentium(R) 4 CPU 3.40GHz
RADEON X600/X550 Series
Ubuntu Feisty (Studio)/XP Dual Boot
Ubuntu Kernel 2.6.20-16-low latency (though crashed with others as well)

---

### Post by joe.turion64x2 on 2007-09-20
> **bootsbradford said:**
> I'd be interested if someone can explain this...

I've been having a variety of problems with Feisty, depending on which video driver I have:

**_Option 1: Open source driver_**
PC was freezing regularly since Feisty (fine with Edgy), with music still playing, mouse still moving, only option to hold down power button etc. 

So i went to the Restricted Drivers Manager and tried to install the ATI driver...

**_Option 2: fglrx driver (incorrectly configured)_**
Besides Firefox crashing much more often, this was fine **and the freezing completely stopped**, though the driver was clearly not configured properly as 'fglrxinfo' in the terminal reported:



So I ran the command: 'sudo aticonfig --initial --force'

This moved me to...

**_Option 3: fglrx properly configured_**
'fglrxinfo' returned the correct ATI info (as opposed to the mesa stuff)

However, I've now been experiencing 2 major problems:
[LIST=1]
[*]Open Office does not open
[*]I cannot log out of a session and log into another, I just have to reboot
[/LIST]

I am now back to the open source driver and waiting for my crash, though still wondering why there are so many problems with whatever I try! :(

These are my basic specs:

Dell Dimension 8400
Intel(R) Pentium(R) 4 CPU 3.40GHz
RADEON X600/X550 Series
Ubuntu Feisty (Studio)/XP Dual Boot
Ubuntu Kernel 2.6.20-16-low latency (though crashed with others as well)
Try to launch OpenOffice from command line, it should report the error (type oowriter for example).

I had that same problem (the freezing after logging out) with Debian Etch (and my ATI card + fglrx). It seems to be a fglrx problem.

Joe.

---

### Post by rickyrockrat on 2007-09-21
Ha! I finally caught something in the log files!  This is a 64-bit, duo-core with NVIDIA proprietary drivers.  I was doing nothing but reading (not scrolling) a web page.  I get the hard lock - no mouse movement.  I hit reset, then extract this out of my log (BTW, this only shows up in the specail log file I created that dumps ALL messages out). I have apic=ht on the kernel cmd line.
For those of you that can tell, it does appear to be a timer tic related issue, and I checked the NVIDIA binary for the NVRM, and it is there, so it certainly looks like the NVIDIA driver is involved, and it looks like to me that the NVIDIA driver is causing the soft lockup - it appears to be the co-juncture of two interrupts - the apic timer and the NVIDIA card, which would explain the random nature of the lockups.
I am going to bug the nvforums to see if there's something up.

I've split the lines after the time/date stamp, so the time preceeds the line it contains the time for.

Sep 20 22:15:01 duo-core CRON[13033]: (pam_unix) session opened for user debarchiver by (uid=0)
Sep 20 22:15:01 duo-core /USR/SBIN/CRON[13034]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
Sep 20 22:15:01 duo-core CRON[13033]: (pam_unix) session closed for user debarchiver
Sep 20 22:16:01 duo-core kernel: [380375.466346] 
NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000188 00000466 00000009
Sep 20 22:16:01 duo-core kernel: [380375.466749] 
NVRM: Xid (0001:00): 30,  L1 -> L0
Sep 20 22:16:08 duo-core kernel: [380382.549809] 
NVRM: Xid (0001:00): 6, PE0001 
Sep 20 22:16:08 duo-core kernel: [380387.232589] 
Losing some ticks... checking if CPU frequency changed.
Sep 20 22:16:16 duo-core kernel: [380389.554311] 
BUG: soft lockup detected on CPU#0!
Sep 20 22:16:16 duo-core kernel: [380389.554314] 

Sep 20 22:16:16 duo-core kernel: [380389.554315] 
Call Trace:
Sep 20 22:16:16 duo-core kernel: [380389.554317]  
<IRQ>  [softlockup_tick+250/288] softlockup_tick+0xfa/0x120
Sep 20 22:16:16 duo-core kernel: [380389.554362]  
[update_process_times+87/144] update_process_times+0x57/0x90
Sep 20 22:16:16 duo-core kernel: [380389.554369]  
[smp_local_timer_interrupt+52/96] smp_local_timer_interrupt+0x34/0x60
Sep 20 22:16:16 duo-core kernel: [380389.554374]  
[smp_apic_timer_interrupt+89/128] smp_apic_timer_interrupt+0x59/0x80
Sep 20 22:16:16 duo-core kernel: [380389.554381]  
[apic_timer_interrupt+102/112] apic_timer_interrupt+0x66/0x70
Sep 20 22:16:16 duo-core kernel: [380389.554478]  
[_end+137457846/2130485360] :nvidia:_nv003521rm+0x20/0x22
Sep 20 22:16:16 duo-core kernel: [380389.554592]  
[_end+139664360/2130485360] :nvidia:_nv007342rm+0x2a/0xc7
Sep 20 22:16:16 duo-core kernel: [380389.554676]  
[_end+137841826/2130485360] :nvidia:_nv012286rm+0x60/0xbb
Sep 20 22:16:16 duo-core kernel: [380389.554759]  
[_end+137815668/2130485360] :nvidia:_nv012227rm+0x7d/0x9c
Sep 20 22:16:16 duo-core kernel: [380389.554842]  
[_end+137815234/2130485360] :nvidia:_nv012488rm+0x4c8/0x5c1
Sep 20 22:16:16 duo-core kernel: [380389.554925]  
[_end+137840042/2130485360] :nvidia:_nv012495rm+0x292/0x2a7
Sep 20 22:16:16 duo-core kernel: [380389.555008]  
[_end+137840007/2130485360] :nvidia:_nv012495rm+0x26f/0x2a7
Sep 20 22:16:16 duo-core kernel: [380389.555090]  
[_end+137814734/2130485360] :nvidia:_nv012488rm+0x2d4/0x5c1
Sep 20 22:16:16 duo-core kernel: [380389.555173]  
[_end+137840042/2130485360] :nvidia:_nv012495rm+0x292/0x2a7
Sep 20 22:16:16 duo-core kernel: [380389.555256]  
[_end+137814005/2130485360] :nvidia:_nv012496rm+0x3a/0x3f
Sep 20 22:16:16 duo-core kernel: [380389.555332]  
[_end+137709409/2130485360] :nvidia:_nv012444rm+0x59/0x83
Sep 20 22:16:16 duo-core kernel: [380389.555409]  
[_end+137709496/2130485360] :nvidia:_nv012445rm+0x2d/0x38
Sep 20 22:16:16 duo-core kernel: [380389.555490]  
[_end+137853991/2130485360] :nvidia:_nv012273rm+0xbf/0xd3
Sep 20 22:16:16 duo-core kernel: [380389.555573]  
[_end+137815773/2130485360] :nvidia:_nv012274rm+0x4a/0x66
Sep 20 22:16:16 duo-core kernel: [380389.555674]  
[_end+140128650/2130485360] :nvidia:_nv005240rm+0xe3/0x19c
Sep 20 22:16:16 duo-core kernel: [380389.555768]  
[_end+140472733/2130485360] :nvidia:_nv002937rm+0x1c9/0x54a
Sep 20 22:16:16 duo-core kernel: [380389.555861]  
[_end+140471234/2130485360] :nvidia:_nv002935rm+0x382/0x5ef
Sep 20 22:16:16 duo-core kernel: [380389.555976]  
[_end+139493742/2130485360] :nvidia:_nv008236rm+0x1dd/0x647
Sep 20 22:16:16 duo-core kernel: [380389.556089]  
[_end+139540685/2130485360] :nvidia:_nv008244rm+0x48/0x56
Sep 20 22:16:16 duo-core kernel: [380389.556203]  
[_end+139495058/2130485360] :nvidia:_nv008231rm+0xba/0x823
Sep 20 22:16:16 duo-core kernel: [380389.556306]  
[_end+140165978/2130485360] :nvidia:_nv005225rm+0x3b6/0x680
Sep 20 22:16:16 duo-core kernel: [380389.556409]  
[_end+140118173/2130485360] :nvidia:_nv005226rm+0x7d/0xc7
Sep 20 22:16:16 duo-core kernel: [380389.556478]  
[_end+137467895/2130485360] :nvidia:_nv002680rm+0x99/0xbe
Sep 20 22:16:16 duo-core kernel: [380389.556549]  
[_end+137489362/2130485360] :nvidia:rm_isr_bh+0x71/0xa4
Sep 20 22:16:16 duo-core kernel: [380389.556630]  
[_end+140890236/2130485360] :nvidia:nv_kern_isr_bh+0x4f/0x5e
Sep 20 22:16:16 duo-core kernel: [380389.556706]  
[_end+140890370/2130485360] :nvidia:nv_kern_isr+0x77/0x86
Sep 20 22:16:16 duo-core kernel: [380389.556713]  
[tasklet_action+91/160] tasklet_action+0x5b/0xa0
Sep 20 22:16:16 duo-core kernel: [380389.556720]  
[__do_softirq+95/208] __do_softirq+0x5f/0xd0
Sep 20 22:16:16 duo-core kernel: [380389.556729]  
[call_softirq+28/40] call_softirq+0x1c/0x28
Sep 20 22:16:16 duo-core kernel: [380389.556734]  
[do_softirq+44/144] do_softirq+0x2c/0x90
Sep 20 22:16:16 duo-core kernel: [380389.556738]  
[do_IRQ+217/256] do_IRQ+0xd9/0x100
Sep 20 22:16:16 duo-core kernel: [380389.556745]  
[ret_from_intr+0/10] ret_from_intr+0x0/0xa
Sep 20 22:16:16 duo-core kernel: [380389.556748]  
<EOI>  [pci_conf1_read+0/256] pci_conf1_read+0x0/0x100
Sep 20 22:16:16 duo-core kernel: [380389.556764]  
[copy_user_generic_string+23/64] copy_user_generic_string+0x17/0x40
Sep 20 22:16:16 duo-core kernel: [380389.556845]  
[_end+140891272/2130485360] :nvidia:nv_kern_ioctl+0x377/0x3c4
Sep 20 22:16:16 duo-core kernel: [380389.556933]  
[_end+140891412/2130485360] :nvidia:nv_kern_unlocked_ioctl+0x1c/0x23
Sep 20 22:16:16 duo-core kernel: [380389.556938]  
[do_ioctl+47/160] do_ioctl+0x2f/0xa0
Sep 20 22:16:16 duo-core kernel: [380389.556944]  
[vfs_ioctl+674/736] vfs_ioctl+0x2a2/0x2e0
Sep 20 22:16:16 duo-core kernel: [380389.556948]  
[vfs_write+341/416] vfs_write+0x155/0x1a0
Sep 20 22:16:16 duo-core kernel: [380389.556956]  
[sys_ioctl+108/176] sys_ioctl+0x6c/0xb0
Sep 20 22:16:16 duo-core kernel: [380389.556966]  
[system_call+126/131] system_call+0x7e/0x83
Sep 20 22:16:16 duo-core kernel: [380389.556983] 

Sep 20 22:16:16 duo-core kernel: [380389.557076] 

NVRM: Xid (0001:00): 30,  L0 -> L0
Sep 20 22:17:22 duo-core syslogd 1.4.1#20ubuntu4: restart.

---

### Post by rickyrockrat on 2007-09-21
This certainly seems related.  I'll try a different binary as suggested.
[http://www.nvnews.net/vbulletin/showthread.php?t=93110&page=6](http://www.nvnews.net/vbulletin/showthread.php?t=93110&page=6)

---

### Post by rickyrockrat on 2007-09-21
The 9746 driver does not work with the 8500GT I have, but there is a new driver, 100.14.19, released a few days ago that I am now running. I will keep you posted.

---

### Post by rickyrockrat on 2007-09-21
BTW, the all entry I used to catch this is:
# All messages go here
*.* -/var/log/all
Add those two lines to /etc/syslog.conf, tell syslog to reload it's config, and you're good to go. I use /etc/init.d/sysklogd reload.

---

### Post by soxs on 2007-09-21
May you please consider editing your posts instead creating a new post? Thx
I am currently running xserver-xgl (with drivers from the *restricted-drivers-manager*) with compiz-fusion and is quite stabel (~0.5 freezes a day... mostly while using firefox, pidgin always running in the back)

---

### Post by sparky64 on 2007-09-21
Decided to try again.
While i was trying out sabayon i noticed on boot up that acpi was not supported on my mobo. when i checked my bios i found it disabled.
Renabled hibernation/cool and quiet etc.
I also did not have a feisty disk handy so did a fresh install of edgy (separate home partition)and did a full upgrade.
I used automatix to load nvidia drivers etc. And crossed fingers.
Been running for 7 days now without a problem (no beryl don't want to push my luck).
On a side note i miss being able to see whats going on on boot up. It can provide lots of useful info.

---

### Post by soxs on 2007-09-22
I am not really used to boot up msg stuff, but I would remove the option "quite" from the grub booting menu... or press <STRG><ALT><F1> at boot

---

### Post by funnypanks on 2007-09-22
ok this is almost a certain fix for MANY laptop owners. its gonna sound like somebody drank too much moon shine before saying this, but it worked for me and many others report it working. if u have a laptop made by acer,samsung, asus, toshiba and maybe even some hp. check to see if your dvd burner is the TSSTcorpCD/DVD TS-L632D. the firmware on that drive has many issue, ecspecially with the acer and asus. updating the firmware to the samsung firmware fixes the issue, and yes the samsung firmware will work on the acer and asus will a little work in windows. instead of re-inventing the wheel here is where i read how to do it, and i will say the only time i get a short lived freeze now is when i search in synaptics and then it works again, but no more random repeating freezes. the firmware i used it the SC03 and can vouche for it, as always with flashing non proprietary firmwar [COLOR="Red"][SIZE="4"]USE AT YOUR OWN RISK[/SIZE][/COLOR]

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75295/comments/97](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75295/comments/97)

this is the bug when this solution is first posted and many people after   Christian Mayrhuber  wrote on 2007-05-02 also report it working. i hope this helps many people. 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)

best way to find out if this will help you is to leave a music cd or some dvd in the drive while your using the computer and if the computer doesn't freeze as much or at all (in my case) this SOLUTION WILL WORK FOR YOU

i also disable powernowd but it doesnt freeze even when on.

---

### Post by funnypanks on 2007-09-22
i should also mention that i am using gutsy gibbon but the fix is meant for feisty and carries over very nicely for gutsy

---

### Post by Mayfairy on 2007-09-22
I'm too lazy to copy and paste my earlier message, but you'll see it if you scroll up a little. Everything went fine with my latest configuration (described in my post) for a few days but I was away from my computer for few days and when my computer uptime hit 4 days or so the freezes started again. 
After that I edited my menu.lst boot options with 'noapic nolapic acpi=off ht=on irqpoll' and everything's fine again for now. Only problem is that my hard drive starts whenever I start some application and then stops again. Must be something to do with those boot options. That can't be healthy for my HD.

EDIT: Turned out it was the 'acpi=off' option that made my HD start and stop whenever it wanted, and apparently mounting and unmounting every time cause I sometimes got an unsuccessful mount of filesystem message. Gotta hope 'acpi=off' wasn't the thing that kept the freezes from happening.

EDIT2: So far so good. Took 'acpi=off' away and my HD acts properly again. No freezes in 2 days. Try out the things in majoridiot's guide and see if they'll help you too.

---

### Post by vievie on 2007-09-24
Just back after months on Mandriva 2007.1, it seems this crazy problem is still unsolved.

Will it be solved in Gusty Gibbon?  tears....

---

### Post by OmniCloud on 2007-09-24
**sudo nvidia-xconfig --add-argb-glx-visuals --composite**

I made a mistake and ran this command in the terminal, now I can't access my desktop without safe mode? 

any can tell me how to reverse this command to default or something?

---

### Post by rickyrockrat on 2007-09-24
> **OmniCloud said:**
> **sudo nvidia-xconfig --add-argb-glx-visuals --composite**

I made a mistake and ran this command in the terminal, now I can't access my desktop without safe mode? 

any can tell me how to reverse this command to default or something?
Um, it's a little off topic, but there should be a /etc/X11/xorg.back (or some extension like that.  copy this file back over the /etc/X11/xorg.conf file and you should be good to go...  Always back  up stuff before you run comands!

---

### Post by OmniCloud on 2007-09-25
Ok...but how do I access the terminal? Loading up Ubuntu just gives me a text-based desktop? It says username, and then the area I'm in (desktop in this case) and that's it? 

Do I just use that command from the go?

sry for going off topic, I don't like creating threads for problems that can be fixed quickly...

---

### Post by Mayfairy on 2007-09-25
> **OmniCloud said:**
> Ok...but how do I access the terminal? Loading up Ubuntu just gives me a text-based desktop? It says username, and then the area I'm in (desktop in this case) and that's it? 

Do I just use that command from the go?

sry for going off topic, I don't like creating threads for problems that can be fixed quickly...

Navigate to correct directory by 'cd /etc/X11/'

Then by 'ls' you should see entries like: xorg.conf, xorg.conf.20070925195820 etc.

Let's break this xorg.conf.20070925195820 into pieces: 2007-09-25-19:58:20 might seem more familiar. Date and time in that order. If you haven't modified your xorg file before there should only be one with date and time, but if there's several be sure to check the correct date. 

You can copy your old working xorg file to replace your current non-working one by typing 'sudo cp xorg.conf.1234567890 xorg.conf' and then reboot to make your computer work properly again. 

If by some reason you don't have any old xorg files to replace your current one you'll have to reconfigure xorg yourself by doing 'sudo dpkg-reconfigure xserver-xorg' and then choose the right values. If you don't know what to answer then the default option is your safest bet.

---

### Post by OmniCloud on 2007-09-25
TKS guys!!!!!! these forums r the best!!!

---

### Post by Hubi17 on 2007-09-27
I also used to have a random system freeze every now and then under feisty. the system would be totally unresponsive, the only thing that worked was the mouse. After reading on these forums and the bug reports i found a link to a german site that stated that the integrated dvd drive/burner of my samsung q35 need a firmware update. After updating the firmware from SC02 to SC03 (these are the samsung versons i believe) i havent had any more freezes so i believe this to have been the problem.

link the the launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)
link to the german site:
[http://www.caiacoa.de/wiki/index.php/Samsung_R40-T2050_Chasubi#DVD-Brenner](http://www.caiacoa.de/wiki/index.php/Samsung_R40-T2050_Chasubi#DVD-Brenner)

Since most of the dvd drives seems to be mostly from TSSTCORP (same on my asus notbook), perhaps updating the firmware can help some others, too

good luck

---

### Post by rickyrockrat on 2007-09-28
All,
I upgraded my NVIDIA proprietary driver to x86_64-100.14.19 and I have not had this issue for a week - without changing anything else.  It appears, at least in my case the NVIDIA driver (which make sense since that is what the log file showed).  I will check back in a couple weeks.

---

### Post by thatcher695 on 2007-09-28
aftter reading all these posts, I'm not sure what the fix is for my freeze.  I am a new ubuntu user, having just installed it.  My system freezes doing just about anything.  I have a Nvidia NV4 RIVA TNT card.  Do I get a proprietary nvidia driver?  if so where?  There are no options in my xorg.conf as others seem to have.  I just know that the screen with various display modes.

---

### Post by funnypanks on 2007-09-28
> **Hubi17 said:**
> I also used to have a random system freeze every now and then under feisty. the system would be totally unresponsive, the only thing that worked was the mouse. After reading on these forums and the bug reports i found a link to a german site that stated that the integrated dvd drive/burner of my samsung q35 need a firmware update. After updating the firmware from SC02 to SC03 (these are the samsung versons i believe) i havent had any more freezes so i believe this to have been the problem.

link the the launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)
link to the german site:
[http://www.caiacoa.de/wiki/index.php/Samsung_R40-T2050_Chasubi#DVD-Brenner](http://www.caiacoa.de/wiki/index.php/Samsung_R40-T2050_Chasubi#DVD-Brenner)

Since most of the dvd drives seems to be mostly from TSSTCORP (same on my asus notbook), perhaps updating the firmware can help some others, too

good luck
nice same fix i posted earlier. also must mention that people that are using asus DO NOT >>>DO NOT update to AS99 as it is known to give even more problems than previous drivers. recommendation is SC03 and SC04

---

### Post by Shazaam on 2007-09-28
> **thatcher695 said:**
> aftter reading all these posts, I'm not sure what the fix is for my freeze.  I am a new ubuntu user, having just installed it.  My system freezes doing just about anything.  I have a Nvidia NV4 RIVA TNT card.  Do I get a proprietary nvidia driver?  if so where?  There are no options in my xorg.conf as others seem to have.  I just know that the screen with various display modes.

What are your system specs? BTW, that Riva card is pretty old.......

---

### Post by thatcher695 on 2007-09-28
system is a mixture of parts.  It currently consists of 

Intel Celeron CPU 2.4GHz (ASUS motherboard)
a scsi controller with CD & Tape drive
ide hard drive & cd rw/dvd rom
NV4 RIVA TNT
a generic pci 10/100 ethernet card

---

### Post by Digitallysick on 2007-09-28
I finally ended up with random freezes in sabayon as well, so here i am back with gutsy gibbon 64bit, its rock solid until i try compiz or any "enabled" graphics

---

### Post by Shazaam on 2007-09-28
> **thatcher695 said:**
> system is a mixture of parts.  It currently consists of 

Intel Celeron CPU 2.4GHz (ASUS motherboard)
a scsi controller with CD & Tape drive
ide hard drive & cd rw/dvd rom
NV4 RIVA TNT
a generic pci 10/100 ethernet card


Memory?

---

### Post by Digitallysick on 2007-09-28
I haven't checked my memory i guess i could run memtest off the live cd and see what happens? My pc runs fine under xp/vista (gag)

---

### Post by thatcher695 on 2007-09-28
memory - 512MB

OS is Ubuntu 7.04

---

### Post by thatcher695 on 2007-09-28
> **thatcher695 said:**
> memory - 512MB

OS is Ubuntu 7.04
I added the following to xorg.conf in section "Device", Identifier is NV4 [RIVA TNT], driver is "nv"

option  "NvAGP" "0"
option  "RenderAccel" "Off"
option "NoRenderExtnesion" "Off"

Now the X server crashes instead of consuming 100% cpu.  I grabbed these from someones post but now I can't find the post.  Is there perhaps some other options I should use.  Where would I find the options listed and what they do?

---

### Post by Digitallysick on 2007-09-28
Welp, i give up, i will come back to ubuntu when i either build a new pc, or linux can support my hardware better. as of now im going back to windows vista ( i hate it really bad)  but im out of options

---

### Post by Hubi17 on 2007-09-29
Sorry for double posting your solution funnypanks, but this thread has become so long that I was unable to read all the posts before, and I just wanted to post the solution that worked for me to help others and to motivate them not to give up on Ubuntu :D

The community here is just awesome!!

---

### Post by cmost on 2007-09-29
For me, the freezing issue was the Nvidia driver.  I experienced hard lockups that were driving me nuts.  They started last spring with the release of the Nvidia 100.14.11 but I didn't put two and two together until after I went to the trouble of tediously diagnosing every piece of hardware and then finally totally rebuilding my machine from the Motherboard up!!!!  Imagine how frustrating it was to spend hundreds of dollars on upgrades and STILL have the same freeze!!!  After I downgraded my graphics driver back to Nividia 1.0-9755, I haven't had any issues whatsoever.  I run a full 3D desktop with Beryl 0.2.x  NOTE:  The latest nvidia driver, 100.14.19 also causes my system to freeze but instead of a hard lockup, everything freezes except for the mouse pointer.  It's ridiculous.  I went back to trusty 9755 and all is well with the world again.  I have an Nvidia GeForce 7300 GS on PCIe by the way.  Perhaps the Nvidia driver is causing your issue as well.

---

### Post by euthyfro on 2007-09-29
I'd give that a try, but i've always used Envy for my nvidia drivers.  how did you roll back to Nividia 1.0-9755?

---

### Post by Ruazinn on 2007-09-29
I had exactly this problem about a month ago when I first installed Fiesty on my AMD Athlon 64 X2 system with the Nvidia GeForce 7500 LE card.  I dicked around with the system so much, that to solve the problem I decided to do a fresh install from scratch.  Then I installed Automatix2, which has the 1.0-9755 version of the Nvidia driver.

So... anyone, does Compiz Fusion work well with this driver?

---

### Post by Supremacy on 2007-09-29
> **Ruazinn said:**
> I had exactly this problem about a month ago when I first installed Fiesty on my AMD Athlon 64 X2 system with the Nvidia GeForce 7500 LE card.  I dicked around with the system so much, that to solve the problem I decided to do a fresh install from scratch.  Then I installed Automatix2, which has the 1.0-9755 version of the Nvidia driver.

So... anyone, does Compiz Fusion work well with this driver?

I've tried it but all I get is freezes which I have to hard reset to get back to normal. I have the latest driver at the moment but it still happens.

---

### Post by funnypanks on 2007-09-30
> **Hubi17 said:**
> Sorry for double posting your solution funnypanks, but this thread has become so long that I was unable to read all the posts before, and I just wanted to post the solution that worked for me to help others and to motivate them not to give up on Ubuntu :D

The community here is just awesome!!

you're right and i think i can finally make vista my back up os now

---

### Post by euthyfro on 2007-09-30
I went off to try the older nvidia drivers but found getautomatix down or something, so i gave majoridiot's fix [http://ubuntuforums.org/showpost.php...&postcount=544]("http://ubuntuforums.org/showpost.php...&postcount=544")&  a try, after 6 hours i haven't had a freeze.  i know people have been having freezes after a day or 2 but if the frequency of these goes down 2 a daily basis instead of every couple hours or minutes it's solved enough for me.
i'm running:
AMD x2 4200 cpu
evga nforce-4 mainboard
geforce 7300le 256mb video card
1.5 gb RAM (after losing a 512 stick because of memtest failure)
I just gave it a performance test by playing some neverwinter nights & it was a bit choppy & froze for a few seconds a couple times but that might just be from the memory i lost.
 I've been keeping an .odt called "misaki's medical records" (yes, my computer's name is Misaki, she mostly downloads & plays fansubbed anime, so it seemed appropriate) & really didn't have anything important to put in there til now.

And this is the real advantage of gnu/linux, all you guys & our 74 page thread fixing each other's problems.  M$ and the rotten apple may have developers locked in a dark room working on this kinda stuff but we've got each other and baby, that's alright.

---

### Post by Mayfairy on 2007-10-01
> **Ruazinn said:**
> I had exactly this problem about a month ago when I first installed Fiesty on my AMD Athlon 64 X2 system with the Nvidia GeForce 7500 LE card.  I dicked around with the system so much, that to solve the problem I decided to do a fresh install from scratch.  Then I installed Automatix2, which has the 1.0-9755 version of the Nvidia driver.

So... anyone, does Compiz Fusion work well with this driver?

I downgraded to Nvidia 1.0-9755 driver also, and then applied boot options described in Majoridiot's post up above and these two changes together did it for me. No more freezes. 
Compiz Fusion does work quite nicely for me. I don't remember anything not working for me with these drivers. Not doing much gaming so I wouldn't know if these drivers have any impact on them. 

> I went off to try the older nvidia drivers but found getautomatix down or something, so i gave majoridiot's fix [http://ubuntuforums.org/showpost.php...&postcount=544&](http://ubuntuforums.org/showpost.php...&postcount=544&) a try, after 6 hours i haven't had a freeze. i know people have been having freezes after a day or 2 but if the frequency of these goes down 2 a daily basis instead of every couple hours or minutes it's solved enough for me.
Going a little offtopic here, but I've heard Automatix is said to cause a lot of grief when trying to update to newer version of Ubuntu. Now that you got your drivers I'd recommend you to get rid of Automatix. People say Easyubuntu is better alternative for Automatix. That's what I'm using myself.
Please, everyone feel free to correct me on this by PM if you think/know I'm wrong. 

> And this is the real advantage of gnu/linux, all you guys & our 74 page thread fixing each other's problems. M$ and the rotten apple may have developers locked in a dark room working on this kinda stuff but we've got each other and baby, that's alright.
Even though some of the posts here are offtopic and not too helpful I really like the way things are handled here. Most of the time the users have better input and knowledge on things than some developers who only have limited amount of resources to use for testing things out.

---

### Post by IVIisterX on 2007-10-01
Hi, everyone!

First of all I can tell you, that my machine had no freezes since 14 days with kernel 2.6.20-16.31-386 and ATI drver 8.40.4.

Secondly I found some informations to ACPI  in the german BIOS-Compendium
( [http://www.bios-info.de/bios/compend.htm](http://www.bios-info.de/bios/compend.htm) ):

For faultless function the complete hardware, all cards and all drivers must support ACPI. Then the OS takes the control for the Power Management and the Plug and Play functions. It is recommended, that for best results the APM function should be disabled in BIOS and a potential ACPI option should be enabled in BIOS. By the way it is possible - when ACPI is enabled and controlled by the OS - that there are problems with recording processes with CD's and DVD's.

The "ACPI 2.0 support" option, which I use with success, is only available in AMI-Bios and allocates more  tables for ACPI than ACPI 1.0 does. The current version of ACPI is 3.0a.

So I think, if someone has problems with freezes, it may be that not all components/drivers  support ACPI correctly and it is necessary to disable this function by using additional kernel parameters. On the other side it is perhaps possible, that it is necessary to make correct or optimal APM / ACPI settings in the BIOS.

Best regards

IVIr.X

---

### Post by euthyfro on 2007-10-01
"but I've heard Automatix is said to cause a lot of grief when trying to update to newer version of Ubuntu. Now that you got your drivers I'd recommend you to get rid of Automatix."

i know Automatix isn't very good & that's what i was going to do i couldn't even get Automatix in the 1st place.  when i "wget http://www.getautomatix.com/apt/key.gpg.asc" it just kept failing & retrying.   
so is there another source to get the older drivers from?

---

### Post by euthyfro on 2007-10-01
A condition update: no freezes at all last night, i have been getting these mini-hangs were it's 1 of those "soft-freezes" where the cursor responds but they only last 10-30 seconds & everything i tried to do during the mini-freeze is done when responsiveness returns.  then i woke up this morning to find myself hard-frozen on the screen saver, making me think it must be the nvidia driver doing it.

---

### Post by majoridiot on 2007-10-02
> **euthyfro said:**
> "...so is there another source to get the older drivers from?

the nvidia linux driver archive can be found here:

[http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

---

### Post by euthyfro on 2007-10-02
thanx, that is a handy site
but...
After getting the 1.0-9755 driver & uninstalling the newer 1, i ran the "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" command, got a "you can't do this from inside X" message that seemed reasonable to me so i bounced out of X run the same command & got:
"sh: cannot open NVIDIA-Linux-x86-1.0-9755-pkg1.run"
starting to feel like a conspiracy to keep me using this crap-tacular new driver.

---

### Post by peos on 2007-10-02
I to have similar freezes. I run the latest long term support release, server edition in vmware. So the graphics driver is vmware. I also have vnc enabled so I log in
two different way, don't know if that affect graphics driver or not. But I have
no accelration or Nvidia/ATI-driver to blaim.

My freezes appears every single minute, making the system useless.
But I'v found some very interesting facts:
%metacity --replace always works to make it work again, for a minute or so.
choosing any other wm, like olvwm make all freezes go away.
The freeze is really just that all mouse clicks are lost, it's still possible to type
and to move the mouse.

My conclusion is that at least in my case it is metacity or it's connection to mouse input 
that is seriously broken.
I cannot find anything in any logs that gives me any hint. I have noapic and all those fixes
in menu.lst because of vmware anyway. 

This has been a long thread, but I haven't seen any solution that I've not tried.
Any new ideas anyone? This is most annoying.

   Regards
   PeO

---

### Post by majoridiot on 2007-10-02
> **euthyfro said:**
> thanx, that is a handy site
but...
After getting the 1.0-9755 driver & uninstalling the newer 1, i ran the "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" command, got a "you can't do this from inside X" message that seemed reasonable to me so i bounced out of X run the same command & got:
"sh: cannot open NVIDIA-Linux-x86-1.0-9755-pkg1.run"
starting to feel like a conspiracy to keep me using this crap-tacular new driver.

be sure the file is executable:

```
$ cd </path/to/NVIDIA-Linux-x86-1.0-9755-pkg1.run>
$ chmod +x NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

also be sure to read the README, etc.- it has all the info necessary to compile and install the driver.  also, there is
a wealth of nvidia driver install info available in these forums.  it's not really that hard to get installed. ;)

---

### Post by rahimveron on 2007-10-03
Has anybody found any solution to this
Specs:
Pentium 4, 2.4 Ghz
Intel 845GVSR with onboard graphics
512 RAM

---

### Post by soxs on 2007-10-03
I am currently running on Ubuntu 7.10 beta. I still get freezes (hard locks).
APM ACPI idependant (change boot & bios options at any possible combo)
P4 2,4Ghz does not support speed stepping(at least I got told so at boot time and in the logs)
Disabled powernow with no success
As I allreday tested multiple CD/DVD drives, this can NOT be the reason.

I did not test the latest driver form ati (the beta ones), as I have an old  ATI card (ATI Radeon 9500 pro)

Atm I am locking forward to buy a Notebook/Laptop and check if that will stop freezing and the freezes are triggered by bad hardware and/or strange hardwarecombo etc..

I hope somebody fixes this issue...
I myself guess it's a kernelbug as fedora has it aswell or my PC is ready for the graveyard (split it into peaces and sell them at ebay and see which guy wants his money back ^^ )

Greets soxs

---

### Post by IVIisterX on 2007-10-03
> **soxs said:**
> I am currently running on Ubuntu 7.10 beta. I still get freezes (hard locks).
APM ACPI idependant (change boot & bios options at any possible combo)
P4 2,4Ghz does not support speed stepping(at least I got told so at boot time and in the logs)
Disabled powernow with no success
As I allreday tested multiple CD/DVD drives, this can NOT be the reason.

I did not test the latest driver form ati (the beta ones), as I have an old  ATI card (ATI Radeon 9500 pro)


Hello soxs!

Do you use ATI 8.40.4 - this driver supports the Radeon 9500 series?

Please install kernel 2.6.20.16-386 for testing.

In my case I so was able to switch between direct and indirect rendering. If I install the ATI 8.40.4 with envy under kernel 2.6.20-16-generic, so the generic kernel uses direct rendering and the 386 kernel uses indirect rendering. Type glxinfo in a terminal. For my machine indirect rendering is absolutely stable.

Thirdly you can try the following additional kernel parameters:

apic=off noapic apm=on irqpoll pnpbios=off

Perhaps this works!? The pnpbios=off parameter was necessary because linux shows this message at start if the acpi=off noacpi parameter is added. For apm=on you have to enable apm in bios. Check the /var/log/messages wether apm is correctly started. There must be a line like:
Oct  3 18:30:23 LinuxOS kernel: [   68.593632] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

IVIr.X

---

### Post by euthyfro on 2007-10-03
After getting the 1.0-9755 drivers installed, i rebooted to find 

"NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184
NVRM: RM/client version mismatch!!
NVRM:    aborting to avoid catastrophe!"

so with versions not matching x crashed of course, my question is why did the nvidia installer build the wrong kernel module & how can i upgrade that after i reinstall the 1.0-9755 drivers?
cuz when i reinstall that it's just gonna build me the 1.0-7184 again

---

### Post by cmost on 2007-10-03
Before attempting to install the 9755 driver, you should uninstall the restricted drivers using Synaptic.  Then, when you install the 9755 driver it will be the only driver available.

---

### Post by euthyfro on 2007-10-03
nice, it's always the simplest solution i overlook.  i'll run along & do that now

---

### Post by oomingmak on 2007-10-03
> **euthyfro said:**
> i have been getting these mini-hangs were it's 1 of those "soft-freezes" where the cursor responds but they only last 10-30 seconds & ***everything i tried to do during the mini-freeze is done when responsiveness returns***.
This is exactly what I (and others) have been getting.

Do you get IOWait flooding when this happens? (i.e. solid 100% IOWait seen on the CPU monitor).

---

### Post by euthyfro on 2007-10-03
I don't know if it's 100% cpu usage cuz i haven't had the system monitor open when they've happened, very well may be the case.

And after following cmost's sensible advice on removing the restricted modules then installing the driver, it did indeed build the correct kernel module, but x still crashed in a horrible manner, this time i didn't even get the text-based ubuntu command line, just a black screen, pressing enter let me see the logs on the crash, but all they had were a few lines containing no errors ending with -back trace.
I was able to ctrl+alt+f1 a command line, but still no dice on actually running the 1.0.9755 driver

---

### Post by mightyzug on 2007-10-03
i had this same problem w/ random lockups after i used envy to install the latest nvidia driver.  they were few and far between, but unacceptable nonetheless. 

i used envy to remove the latest nvidia driver and used envy again to manually install the 9639 driver, it appears to have fixed the problem and my eyecandy isn't suffering one bit for it either.  :)

---

### Post by jaffa_nz on 2007-10-03
Kia ora

Dell d620, 2gb ram 2.0ghz, intel 945GM/GMS/940GML video card. runs compiz-fusion beautifully.  Ubuntu Feisty.  (mate same config h/w with kubuntu feisty, same prob)

..until the sod locks up.  cursor movement only, hard restart required.  have added these lines to improve from 3 or more to 1 per day hang.
noapic apic=off to boot grub kernel load line
now trying noapic apic=off apm=off irqpoll pnpbios=off  see how it goes

i noticed (by accident) that sounds still plays. but thats about it...

I built this just 3 days ago, using the sources.list web generator to get country source repositories, patched everything. no particular changes from norm,  running kernel  2.6.20-16-generic #2 SMP, built fusion from this link 

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

are brains waaay better than the average install and tweak working on this problem properly?  honestly read about 30 posts and was fighting eye-lid failure so not sure?

its clearly not soley around video issue, dvd issues i have none.  ??  i don't want to admit defeat when surrounded by winxp/ vista lovers !!! the shame...

---

### Post by euthyfro on 2007-10-03
I as well can get the 9639 driver running from envy, however its nvidia settings only have 1440x900 resolution & i prefer 1400x1050.  if i could just edit that into the xorg.conf i'd be rocking.
Now where y'all think i should put that in?

---

### Post by euthyfro on 2007-10-04
...if i can get it that way at all considering i don't find 1440x900 in the config file anywhere either

---

### Post by MarkieB on 2007-10-04
Mine is intermittent; it has its good days, 4hrs+ uptime. Vista works perfectly. However, startup in the mornings is occasionally a struggle, needing a good few resets before it boots into grub

I haven't yet changed the cmos battery, nor flashed the bios, so those'll be further angles in the future - less of a priority while Vista is working so well

My trouble is, when I try to add noapic nolapic irqpoll etcetera to the grub entry, it seems to reset itself with a quiet splash. I tried update-grub, it seems as though that command itself resetted the menu.lst entry

other than that, menu.lst seems to reset itself after a few boots at random

Now that I've altered powernowd, the [whole system including mouse] freezes seem better, although now the trouble is gksudo; most guis I try to make work with admin privileges [including sudo] the app hangs - date/time setting, gedit, nautilus..  

Furthermore firefox hangs when trying to load a video from youtube

I've tried the 386 kernel, as well as the low-latency kernel, as it's 32-bit vista, thinking it's the 64-bit OSs that are flaky, although that seems no improvement on simply disabling powernowd - save that without powernowd the cpu frequency applet is indicating a very low speed for both cores;

Ethernet connection was misbehaving on bad days, is it an idea to downgrade hal?

before reinstalling, is the gksudo error a typical side-effect of the measures to prevent freezing?

ps system monitor is telling me 0 bytes of swap being used; I've deleted the UUID in case all those hard reboots were twisting it, although is this normal when say 250MB of ram is being used? A good way to make the swap file work without involving youtube? Mplayer/VLC won't play videos either..

CPU core 2 duo E6750
MB ASrock conroe945g-dvi
HD wd 5000AAKS
LAN Realtek rtl8111/8168B pciE gigabit
2 giga memory

---

### Post by mightyzug on 2007-10-04
> **euthyfro said:**
> ...if i can get it that way at all considering i don't find 1440x900 in the config file anywhere either

i dunno what to tell ya there, 1440x900 is my default resolution and the driver changeover was 100% envy so i never had to touch any of my settings, nothing changed but the driver

---

### Post by IVIisterX on 2007-10-04
> **euthyfro said:**
> ...if i can get it that way at all considering i don't find 1440x900 in the config file anywhere either

Hello euthyfro!

A helpful Editor for xorg.conf is xorg-edit 07.06.15 ( [http://sourceforge.net/projects/xorg-edit/](http://sourceforge.net/projects/xorg-edit/) ). This editor gives you the possibility to generate modelines and has a backup- and testfunction.

Best regards

IVIr.X

---

### Post by funnypanks on 2007-10-04
> **oomingmak said:**
> This is exactly what I (and others) have been getting.

Do you get IOWait flooding when this happens? (i.e. solid 100% IOWait seen on the CPU monitor).

that is what WAS happening to me. check if u have a dvd drive which is the ts-l632d. if it is check post 710.

---

### Post by rickyrockrat on 2007-10-05
> **euthyfro said:**
> After getting the 1.0-9755 drivers installed, i rebooted to find 

"NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184
NVRM: RM/client version mismatch!!
NVRM:    aborting to avoid catastrophe!"

so with versions not matching x crashed of course, my question is why did the nvidia installer build the wrong kernel module & how can i upgrade that after i reinstall the 1.0-9755 drivers?
cuz when i reinstall that it's just gonna build me the 1.0-7184 again

I haven't figured out who is doing it, but a there is a driver being created in
/lib/modules/2.6.xxx-xxx/volatile/ that is called nvidia.ko.  This driver can be renamed to something else, then do:
sudo rmmod nvidia
sudo modprobe nvidia
Then try to start X.  See if that fixes your issue.

---

### Post by euthyfro on 2007-10-05
"This driver can be renamed to something else"
but what should it be named? & how do i rename files as root from the terminal?

---

### Post by Asnem on 2007-10-05
I am trying to convert from Windows to Ubuntu, but I am having the problem with mouse not responding to clicks (pointer moves).  Keyboard is flaky also.  I have tried disabling powernowd and several other suggestions here to no avail.  I have an ATI card...

Has any progress been made on this issue?

I posted details of my setup over here : [http://ubuntuforums.org/showthread.php?p=3479611]("http://ubuntuforums.org/showthread.php?p=3479611")

---

### Post by yhan on 2007-10-05
Hi 

Does anyone solved that random freeze problem ? 

 I've been experiencing that problem since I installed Ubuntu 7.04. That machine used to run Debian Sarge with no problems at all. 

This is  single core AMD Athlon 2600+, with a nforce2 chipset (motherboard Asus A7N8X Bios version : 10/06/2003 A7N8X2.0)
The video card is a Nvidia ( nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1))

That machine is used as Media Center (with mythtv), with 2 Hauppauge 250 and as workstation. 

The system used to freeze after 2 days beeing up. 

At first, I tried to : 

Install the lastest kernel from the repositories, no changes, frozen after 2 days 
Disabling powernowd, frozen after 6 days
Disabling ACPI, frozen after 12 days

Now, I'm starting to have no idea of what else I could try to get a rid of that nasty bug. 

The thing I know, is the problem comes from the Nvidia driver (btw I use the lastest from the rep), X start suddently to use all the cpu of the machine. 
X uses so much CPU, the machine can't be pinged !!

I wrote that tiny script to try to catch the problem and kill and reload the graphical env. I have a serious doubt it's gonna work :
```

PS=/bin/ps
AWK=/usr/bin/awk
ECHO=/bin/echo
GREP=/bin/grep
LOGGER=/usr/bin/logger
TOP=/usr/bin/top
KILL=/bin/kill
PERCENTCPU=`$TOP -n1 -b|$GREP Xorg | $AWK '{print $9}'`
XORGPID=`$PS -ef |$GREP /usr/X11R6/bin/X | $GREP -v grep | $AWK '{print $2}'`
PERCENTCPU=`$ECHO $PERCENTCPU | $AWK -F "." '{print $1}'`
if [ ! -z $PERCENTCPU ]
then
   if [ $PERCENTCPU -gt 90 ]
   then
     $ECHO "monitorXorg - Xorg using more than 90% of CPU, probably crashed, rel oading it ..." | $LOGGER
     $ECHO "monitorXorg - Xorg using more than 90% of CPU, probably crashed, rel oading it ..."
     $KILL -9 $XORGPID
     /etc/init.d/gdm restart
   else
     $ECHO "Xorg percent pid : $XORGPID cpu : $PERCENTCPU"
     $ECHO "MONITORXORG : Xorg percent pid : $XORGPID  cpu : $PERCENTCPU" | $LOG GER
   fi
fi
```

Am I the only one to experience that kind of problem ? 
What can I do to get a rid of that ?

---

### Post by euthyfro on 2007-10-06
> **rickyrockrat said:**
> I haven't figured out who is doing it, but a there is a driver being created in
/lib/modules/2.6.xxx-xxx/volatile/ that is called nvidia.ko.  This driver can be renamed to something else, then do:
sudo rmmod nvidia
sudo modprobe nvidia
Then try to start X.  See if that fixes your issue.

:biggrin: my comrades!
In the Dialogues Euthyphro was admonished by Sokrates for trying to do the right thing but trapping himself in a situation more complicated than he expected or it needed to be.

So i uninstalled my 10.14.19 drivers ready to follow these instructions as best i could.  Keep in mind i'm still command-line impaired & have only been doing this for less than a year (if i can't copy & paste it i'll prolly screw it up).  As is now habitual, my efforts yielded no usable x screen so i envy'ed up the mostly usable 10.14.19 & decided to take aq look at where i stood in synaptic. 
w/glx-legacy gave me the 9639 i couldn't get my desired screen resolution so mplayer plain didn't work, neither did glxgears & my $h!+ still froze on those 3D screensavers
plain glx was being a b!+<h to install, even thru synaptic or the __pkg1.run file
glx-new got me my resolution, my programs, glxgears worked at 4500+ frames but 3D gaming was hella choppy & oh those chills.
So i'm looking around...hey! i used to have all the restricted kernel modules installed b4 i started this process, so i grab that & the plain old glx from synaptic = no usable x but then installing from the 9755's .run file gets everything going, screen resolution, glxgears at around 4000 frames, just got done playing an hour of neverwinter nights, things are feeling pretty fixed.
...let's just see if i'm back here after 4 & a half days w/a frozen computer.

---

### Post by IVIisterX on 2007-10-07
Hi, everyone!

Because my machine has no freezes with kernel 2.6.20-16.32-386 and MESA with indirect rendering, I made the following interesting test:

On the page [http://www.unixboard.de/vb3/showthread.php?t=33850](http://www.unixboard.de/vb3/showthread.php?t=33850) I found an instructions manual to get direct rendering with MESA. After configuring and restarting my system I had really direct rendering with MESA. But both kernels 2.6.20-16.32-generic and 2.6.20-16.32-386 freeze a few minutes after restart and using firefox. So I had to reinstall the ATI driver 8.40.4 with envy.

In this context I have a question:

If I change the AGPmode in the xorg.conf file to "4", the ATI Catalyst Control Center shows an  8x AGPmode under kernel 2.6.20-16.32-generic and an 0x AGPmode under kernel 2.6.20-16.32-386. Why does the driver overwrite the xorg.conf settings and where is perhaps a possibility to change this setting?

Thanks and Greetz

IVIr.X

---

### Post by Digitallysick on 2007-10-07
Anyone went to gutsy gibbon and see if they still have the freeze? when i tried the beta last i had the same problem

---

### Post by ricosrealm on 2007-10-08
I had the same fatal lockup problem when I tried Gutsy today.  The LiveCD and installed image both locked up my system quite frequently.  When it happened, I could move the mouse, but no app or visual updates where occuring anywhere on the screen.  CTRL-ALT-BKSP didn't work to kill the X server.  System was completely frozen and I had to do a hard reboot.  From the LiveCD is was pretty predictable... it would happen after 20 mins of use.  I thought it was virtual memory related so I installed to make sure.  Still happened on real installed image.  I have a Dapper image running perfectly fine with ati radeon driver ( ATI Radeon X700 vid card ) and with dual screen.  Not the same luck with gutsy. I will attempt to actually copy over the same X server config from my stable Dapper image and see what happens.

---

### Post by sageb1 on 2007-10-08
This post is purely speculative. YMMV

ATI's Linux drivers crash FF and later betas, even off the LivedCD because the ATI guru who created it, based on rudimentary study of LInux OpenGL library, was originally trained as a Microsoft developer and did not tweak gcc and/or used a 3rd party C++ compiler.

He also probably based his hack on Microsoft C GL source code, including assembler.

Solution to problem: ask ATI for the source code for the drivers and compile them yourself (as drivers not executables).

**This suggestion is only for experienced Linux developers / users who know how to program in C and C++, and have some assembler experience.  If you fear tweaking the source code, then use an Intel 945-based board and have quit of ATI.

But this is just my opinion. YMMV.

:guitar:

---

### Post by sageb1 on 2007-10-08
Why FF and later betas freeze ATI cards:

"ATI/AMD: X.Org fully supports the Radeon R100 and Radeon R200 cards. Radeon R300 cards are supported by a new reverse engineered driver under development.[4] In June 2007, the X.Org developers announced initial support for the AMD R500 graphics card. The work was done independently by reverse-engineering.[5] In September 2007, an AMD representative said the company will make specifications and a skeleton reference driver available for the R500 and later devices; a 2D free driver is expected by the end of the year.[6] On 2007-09-12, two initial interface documents about AMD's 2D hardware were released and are available from the X.Org website.[7]" -- [http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS#Manufacturer_support](http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS#Manufacturer_support)

cards up to Radeon R200 would be reliable but we need to confirm your video card specs, gents.

Since R300 and up are still in development, anyone with a video card that is R300 or better should be getting more freezes than the R100 and R200 crowd.

Is OpenGL reverse engineered under Linux from Microsoft code? IDTS.

Judging from the Graphics and FOSS Wikipedia article, Intel graphic chipset before the introduction of ATI probably are an alternative but people spoiled by Doom-like games will throw up their hands and pull out their hair if the I950 graphic chipset is almost as slow as Ubuntu 3.0 on a 500 MHz eMachine with 128 MB of ram and a 10 GB HD!:lolflag:

Any Linux developers here?  The ATI  driver is a kluge. :mad:

:guitar:

---

### Post by jaffa_nz on 2007-10-08
HI. Helpful discussion around the video card guts and the like;

for those who have a basic  Intel Corporation Mobile 945GM/GMS/940GML and not a fancy ATI or Nvidea card..  any assistance other than the grub boot line additions and a few changes around powernowd ??

What are the bug reports that are logged,?  anybody have the addresses so i can explore what work has been done.

I'm presuming that gutsy is equally fckd in this delightful Power Rest manner?  Man what happened to the Ubuntu that would survive even the most ignorant tweaking still providing you with a desktop.  now you build outta the box and its stuffed... not good.

Imagine if i had this problem on a purchased pc with ubuntu loaded.  like dell would be of any real use if the forums aren't solving it... lol i dread to think

---

### Post by soxs on 2007-10-08
halo, I am ready for screwing up my PC! just got somehow around killing alsa stuff (I will wait till the final version is availiable for DL and stay till then on LinuxMint3.1)

give me advices what to do and I'll follow, I've nothing to loose!

---

### Post by jaffa_nz on 2007-10-11
Kia Ora.
Well none of the apic modifications etc recommended worked for my Dell D620 dual-core 2.0ghz 2gb ram lappy.  They did however provide longer times between freezes.

so the only alternative being Mickey-useless-soft, instead i followed the links below to upgrade to current kernel for gutsy. recompiled vmware, ndis etc...


[http://ubuntuforums.org/showthread.php?t=511974&highlight=gusty+gibbon](http://ubuntuforums.org/showthread.php?t=511974&highlight=gusty+gibbon)


extremely annoying to say the least.

---

### Post by IVIisterX on 2007-10-12
> **jaffa_nz said:**
>   They did however provide longer times between freezes. 

Hello jaffa_nz!

If changes at the apic/apm-settings provide longer times between freezes, you are on the right way. My theory is, that the freezes depend on more than one trigger. One trigger is possibly  powernowd, secondly there are  the apic/apm-settings and last but not least direct rendering.

So, for the first you have to find out optimal settings for apic; then you can test the other options. I did it the same way.

IVIr.X

---

### Post by jaffa_nz on 2007-10-14
hi ya.

good points my man.

the development kernel did hang once, but i powered it off so quick i can't be sure. lol  So will be keeping an eye on kernel 2.6.22-14 generic to see how this goes.

ridiculous result from what i can only describe as a bloody good and if previously bugged, fixable OS since Hoary Hedgehog days.

Anybody have the links to logged tickets regarding this freeze problem with the powers that be.  Are their any not relating to Video ... ?

cheers all

---

### Post by MarkieB on 2007-10-14
I've identified that mine is partly a result of an unsuitable Bios; ASrock conroe 945g-dvi MoBo, the only stable Bios is 1.40 made for windows logo testing, not up-to-date with stepping chips [limits my E6750 to 800MHz in windows], hence the freezes seemed to have gone when I stopped powernowd altogether [limiting the cpu to 800MHz in ubuntu] ; tinkering with it [setting use_ondemand to 'performance'] is relatively ineffective, although worked before a Feisty reinstall, when there were possibly other troubles with the system

2.6.22-14 gives freezes as before; I blame ASrock mostly, as it stands to reason that it's up to the Bios to allow the faster speeds, it's hardly powernowd's fault that it causes freezes when trying to work at speeds faster than the Bios is made for

---

### Post by soulglo83 on 2007-10-15
About the ATI fglrx driver being the cause I have a little unique insight as you can see from 3 earlier posts of mine in this thread.  I had when this bug surfaced for the first time, been using 7.04 w/ an AMD Athlon w/ an ATI PCI-E 1600XP and the fglrx drivers 8.34.x and everything was honky dory.  I than decided it was time to replace my aging Athlon XP and purchased a core 2 duo and supporting mobo and ram.  Everything else in my case remained the same, even the OS install.  I was very relieved when the computer POSTed the first try and booted into my OS (Ubuntu 7.04 post Automatix updating) and appeared to function normally.  Until I encountered random crashing.  I assumed it was the old OS install and reinstalled 7.04.  Again everything was appearing fine, until the random crashing resumed in the same fashion as before, seemingly unpredictably.  

The crash always took on the following form:

My mouse cursor would move around a completely static screen (nothing would update/refresh except the cursor), if sound was playing it would continue playing for roughly 25-60 seconds before stuttering or stopping altogether.  

My keyboard was dead, dead as hell.  I could not get into my other tty's using ctrl+alt+f keys and couldn't even toggle caps or num lock.

When ssh'ing into my box, I found that by running top, X.org was consuming 100% of my processor clocks, and was continuing to consume more and more memory (which continued until it was running into swap!).  

So I took the following actions:

1.  I disabled powernowd in BIOS, apt-get removed it, and disabled it in my I think init.rc (Don't remember exactly which script, but the point is, IT WAS DISABLED!)

This bought me some time, but the crashing still came on randomly.

2. I added a ton of cheat codes to my /boot/grub/menu.cfg

This didn't do squat as far as I could tell (but powernowd was still disabled so it might have made the same difference that step did, which was minimal).

3.  Upgraded to Gutsy, crashing was more frequent than before, reverted back to 7.04

4.  Learned from this thread, that ssh'ing into my box to forcefully kill X, would permit me to get back into my computer!  

This would only work once though, the 2nd time it crashes it was dead for good and needed hard rebooted.  

5.  Gave up on 3D acceleration, reverted to the X11/VESA driver.

This bought me a little more time to save documents and such before having to hard reboot.  When it crashes, now there is a strange visual corruption following my mouse cursor, however the screen beneath still responds, and when the screen refreshes parts of the screen, the corruption is cleared.  Running the shutdown -r now at the command line, or clicking shutdown through the menu or w/ the power button, all result in a crash.  The system does not finish running its shutdown script, and the computer needs killed, hard.

6. Gave up and started booting into the other half of my dual boot configuration ( XP :{ )

7. A fortnight later I purchased an NVIDIA 8600GT I booted back into Feisty, and have since not crashed even once!

8.  Upgraded to gutsy

Still sailing smoothly, and this was a HUGE pain in my tukkas, for real.  I am so glad to be back in ubuntu, and after struggling like hell to figure this out, I have concluded it is the combination of Firefox, a core 2 duo, and fglrx.  A bizarre synergism if you will.    Depending on what remedies I used the crash took different forms but remained very unpredictable (sometimes occuring without ever using firefox, but it seemed the more firefox I was using the quicker the crash occured).

Try using anything other than an ATI card if you are truly experiencing random freezing that appears to have the symptoms outlined at the start of this post.  I hope this helps someone!

EDIT:  I forgot, a seemingly unrelated crash occuring in Counter Strike 1.6 through Wine and Steam, has been fixed.  This crash came on randomly and resulted in a lack of visual updates to the screen and immediate and repetitive audio stuttering.  The keyboard was unresponsive and computer needed hard killed.  Thought for the longest time this was a sound card issue, turns out, it was resolved when I purchased an NVIDIA card!  Since then I can run CS 1.6 through steam, and it runs flawlessly, everything (Except the mozilla start screen when you enter a server, that remains to be fixed, its a bug in wine) is completely perfect and framerate is very high.  

Also wanted to stress, how pleased I am with the NVIDIA card, my old ATI card caused me nothing but headaches, it has caused me so much grief!

---

### Post by majoridiot on 2007-10-15
> **soulglo83 said:**
> and after struggling like hell to figure this out, I have concluded it is the combination of Firefox, a core 2 duo, and fglrx... Also wanted to stress, how pleased I am with the NVIDIA card, my old ATI card caused me nothing but headaches, it has caused me so much grief!

i agree for the most part that core 2 duos and firefox are somehow two of the players in this problem, but i run two
nvidia 7600GTKOs and freeze without powernowd disabled and added grub parameters.  running firefox was guaranteed
to cause a freeze within minutes... however, it would occasionally freeze without firefox running.

please post back with the stability using the 8600- i'm building a new core2duo mythtv backend for 720p and will get an 8600 if
they are more stable than using a 7600.

---

### Post by erikcw on 2007-10-18
I'm having this problem also.

Started about a month ago.  Upgraded to Gutsy, no change.

I'm on a Pentium D 830 with an ATI RV380 (Radeon X600).  I'm using the DRI radeon driver.

---

### Post by soxs on 2007-10-19
+P4 2,4Ghz
+ATI Radeon 9500pro/9700 [R300 NE]
+fglrx
+firefox
+gutsy gibbon
---------------
3 freeze daily -.-

gona buy a notebook with nvidea card

---

### Post by soulglo83 on 2007-10-22
ok... earlier i had stated in the post on page 78 that all the problems had been resolved from switching my box over to an NVIDIA gpu.  i may have exaggerated a little, as the crashing has stopped i had assumed the problem was resolved.  apparently the problem is just taking on another form.  Xorg no longer consumes 100% of my processor clocks, and the screen refreshes normally (i CAN use my mouse!) but my keyboard dies (often repeating a key, like kkkkkkkkkkkkkkk or mmmmmmmmmmm whenever a text entry field comes into focus.  but i can generally shut my box down safely.  before w/ the ati card, and an otherwise identical setup, my computerwould (with the fglrx driver) randomly hard freeze, w/ a useless keyboard.  the mouse would still move buy it was over a screen that didn't update at all (aside from the mouse cursor) .  so the screen didn't respond to clicks or shutdown, the only way to shut it down was to ssh to it.  so apparently i am still getting this f'ing bug!  at least w/ the nvidia card it is far more manageable!

i have however noticed that generally fast and frequent typing have an effect on the bug!  despite changing keyboards, changing my xorg.conf by hand, and dpkg-reconfigure xserver-xorg'ing, it appears that the problem persists.  majoridiot (again I feel your name should be major_knows_a_ton_and_is_helpful but what do i know), does your crashing occur when you dont run your 7600's in SLI?  also, if you use the vesa driver does this change the effect of the crashing? or is it identical?  

so far I have thought the culprits to be (in descending order by likeliness):
1.  intel core2 duo or supporting mobos
2.  AMD/ATI's fglrx drivers (still occurs w/ vesa rendering for me)
3.  AMD/ATI cards
4.  Firefox
5.  linux kernel's keyboard handling
6.  Xorg
7.  powernowd
8.  non-traditional keyboard/mouse combo (is the mouse/keyboard a usb device in a ps2 adapter and port?) or usage

what do you guys think, what are the culprits? where do we start looking?

---

### Post by maciste on 2007-10-22
I had this problem with Kubuntu feisty updating the kernel to 2.6.22, and i resolved it restoring the original kernel 2.6.20. Yesterday i've updated Feisty to Gutsy (kernel 2.6.22) and now i'm having keyboard and mouse freeze after two hours of no use computer.

---

### Post by majoridiot on 2007-10-22
> **soulglo83 said:**
> ... my keyboard dies (often repeating a key, like kkkkkkkkkkkkkkk or mmmmmmmmmmm whenever a text entry field comes into focus.... the mouse would still move buy it was over a screen that didn't update at all (aside from the mouse cursor) .  so the screen didn't respond to clicks or shutdown, the only way to shut it down was to ssh to it.

majoridiot... does your crashing occur when you dont run your 7600's in SLI?  also, if you use the vesa driver does this change the effect of the crashing? or is it identical?

the keyboard, mouse and screen symptoms you describe are all manifestations of this bug (or bugs?) i have experienced 
and seem to definitely involve both the nvidia and ati proprietary drivers.

i run three screens- two in "twinview" and the third as a seperate screen... in my case, after two or three minutes after 
this bug hits, it will also change the resolution of the first twinview screen to a seemingly random resolution/refresh rate.

since i need 3 screens, i have not tried running the "nv" or "vesa" drivers for longer than it takes to install ubuntu.  
as soon as i get a chance, i'll give it a try and see if it is any more stable but i'm not expecting much.

to this idiot, it feels like there's an interrupt problem somewhere... and since it doesn't appear to be isolated to any 
particular mobo/cpu/video card, i dug a little deeper and found that this is a fairly wide-spread and recent problem
that seems to point directly to the X server.  there are mailing list and forum postings across the spectrum of distros-
including osX- where the only apparent commonality is X11.

my guess is that something was changed that borked the way X handles interrupts.

---

### Post by soxs on 2007-10-23
> **soulglo83 said:**
> 
1. intel core2 duo or supporting mobos
2. AMD/ATI's fglrx drivers (still occurs w/ vesa rendering for me)
3. AMD/ATI cards
4. Firefox
5. linux kernel's keyboard handling
6. Xorg
7. powernowd
8. non-traditional keyboard/mouse combo (is the mouse/keyboard a usb device in a ps2 adapter and port?) or usage

1. P4 2,4, as allready mentioned, so this can be abdoned
2. impossible, I get freezes while running the live cd with mesa drivers aswell on a freshinstall with mesa.
3.possible, going to test my brothers stone age nvidea
4. impossible, simply starting my PC and leaving it alone will make my PC freeze..
5. not enough knowledge to judge
6. seems to be very likely, but gain, not enough knowledge to judge
7. P4 des not support it and I turned it off by default
8. I use PS2 for keyboard, mouse aswell, seems to be unlikly

---

### Post by jaffa_nz on 2007-10-24
Kia Ora

Performed the upgrade to 7.10... cripes that was smoother than water down a window.  Fantastic

... until the freeze returned. oh my lord. bugger.


.. so i'm redoing these steps to see about stability - [http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)

Anybody have an idea where the Ubuntu propellors are at in resolving this issue?

---

### Post by kjuib on 2007-10-25
I tried to add irqpoll after the noapic but I seem to get another error...
"can't set config #1, error -62"
I was really hoping irqpoll would work :confused:

---

### Post by marhei on 2007-10-27
I'm running here ubuntu feisty and gutsy on a abit ab9 mobo without any problem
hardware:
1 SATA hard disc is connected on mobo SATA8
SATA-mode in BIOS=AHCI

solution for freezes live-CD: when you are able to boot the live-CD the first thing to do is uninstalling "powernowd"

now you are able to install without freezes.

after install boot the system and uninstall  "powernowd"

---

### Post by soxs on 2007-10-28
Does anybody know where the boot log is stored? I saw some errors, but time was to short to read...

---

### Post by wawarren on 2007-10-28
Just wanted to thank psyke777, and Majoridiot for recapping his fix. 

I had full system lockups with no mouse movement or anything, but this still worked for me (so far 9+ hours) 

Dual opteron (dual core) 
Nvidia Quadro FX 4500

---

### Post by Asnem on 2007-10-28
> **majoridiot said:**
> 
to this idiot, it feels like there's an interrupt problem somewhere... and since it doesn't appear to be isolated to any 
particular mobo/cpu/video card, i dug a little deeper and found that this is a fairly wide-spread and recent problem
that seems to point directly to the X server.  there are mailing list and forum postings across the spectrum of distros-
including osX- where the only apparent commonality is X11.

my guess is that something was changed that borked the way X handles interrupts.

Is anyone actually trying to fix this?  Can you post some links to those other threads you mentioned?

You'd think a thread with 80 pages now would get someone's attention...

---

### Post by soxs on 2007-10-29
This bug seems to be really wicked. I installed the latest ATI driver and my PC is running fine for 2 days now. (Note: First I had 2 hardlocks which I think compiz is to blame for, after I disabled desktopeffects everything went fine)
I still don't trust this peace...

---

### Post by MarkieB on 2007-10-31
> **soxs said:**
> Does anybody know where the boot log is stored? I saw some errors, but time was to short to read...
/var/log/boot?

---

### Post by ferd on 2007-10-31
> **yhan said:**
> Hi 

Does anyone solved that random freeze problem ? 

 I've been experiencing that problem since I installed Ubuntu 7.04. That machine used to run Debian Sarge with no problems at all. 

This is  single core AMD Athlon 2600+, with a nforce2 chipset (motherboard Asus A7N8X Bios version : 10/06/2003 A7N8X2.0)
The video card is a Nvidia ( nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1))

That machine is used as Media Center (with mythtv), with 2 Hauppauge 250 and as workstation. 

The system used to freeze after 2 days beeing up. 

At first, I tried to : 

Install the lastest kernel from the repositories, no changes, frozen after 2 days 
Disabling powernowd, frozen after 6 days
Disabling ACPI, frozen after 12 days

Now, I'm starting to have no idea of what else I could try to get a rid of that nasty bug. 

The thing I know, is the problem comes from the Nvidia driver (btw I use the lastest from the rep), X start suddently to use all the cpu of the machine. 
X uses so much CPU, the machine can't be pinged !!

I wrote that tiny script to try to catch the problem and kill and reload the graphical env. I have a serious doubt it's gonna work :
```

PS=/bin/ps
AWK=/usr/bin/awk
ECHO=/bin/echo
GREP=/bin/grep
LOGGER=/usr/bin/logger
TOP=/usr/bin/top
KILL=/bin/kill
PERCENTCPU=`$TOP -n1 -b|$GREP Xorg | $AWK '{print $9}'`
XORGPID=`$PS -ef |$GREP /usr/X11R6/bin/X | $GREP -v grep | $AWK '{print $2}'`
PERCENTCPU=`$ECHO $PERCENTCPU | $AWK -F "." '{print $1}'`
if [ ! -z $PERCENTCPU ]
then
   if [ $PERCENTCPU -gt 90 ]
   then
     $ECHO "monitorXorg - Xorg using more than 90% of CPU, probably crashed, rel oading it ..." | $LOGGER
     $ECHO "monitorXorg - Xorg using more than 90% of CPU, probably crashed, rel oading it ..."
     $KILL -9 $XORGPID
     /etc/init.d/gdm restart
   else
     $ECHO "Xorg percent pid : $XORGPID cpu : $PERCENTCPU"
     $ECHO "MONITORXORG : Xorg percent pid : $XORGPID  cpu : $PERCENTCPU" | $LOG GER
   fi
fi
```

Am I the only one to experience that kind of problem ? 
What can I do to get a rid of that ?

This is what I did. I removed my RAM sticks. Then I sprayed the motherboard slots and RAM sticks with electronic cleaner and dried them with compressed air for cleaning electronic components. I reinstalled the RAM sticks. I then installed Gutsy and have no problems for the last  four days. Previously I was experiencing hard freezes every few minutes and it was driving me insane.:guitar:

---

### Post by Beergood on 2007-10-31
Since you guys obviously have no clue I'll let you in on a little secret. The problem lies with the Nvidia driver. If you go back to the default nv driver the freezing problem goes away like magic. Actually, if you turn off the DPMS (display power saver) this also solves the problem.

If everyone can confirm what I'm discovered we should forward this thread to Nvidia.

---

### Post by Asnem on 2007-11-01
Some of the problems happen on ATI and with the Vesa driver.  Read the whole thread before posting random guesses..

---

### Post by soxs on 2007-11-01
> **MarkieB said:**
> /var/log/boot?
thx
Note: New ATI drivers made the race (at least for me^^)
No freeze for 5 days now! Yeha!

---

### Post by soulglo83 on 2007-11-01
> **Beergood said:**
> Since you guys obviously have no clue I'll let you in on a little secret. The problem lies with the Nvidia driver. If you go back to the default nv driver the freezing problem goes away like magic. Actually, if you turn off the DPMS (display power saver) this also solves the problem.

If everyone can confirm what I'm discovered we should forward this thread to Nvidia.

I think its strange that we (everyone except beergood apparently) 'have no clue' since the crashing outlined by the other posters in this thread appears even with nv, ati, fglrx, vesa, etc.  I think its safe to say the nvidia binaries (while not 100% perfect yet [close in my opinion]) are not to blame.

There are a variety of theories, one that I saw a few pages back involved a TSST corp DVD burner w/ bad firmware.  I myself possess the same derivative of that drive, and after flashing with an update ROM, it appears to have improved my stability remarkably.  It still hasn't fixed all the symptoms (mouse moving, keyboard unresponsive, etc.) that were outlined in this thread.

---

### Post by sparky64 on 2007-11-01
I have had the same problems with freezing - only when inactive for a couple of mins.
It rendered my system virtualy unusable. (along with network problems )

I am now running mandriva.
After a week i got round to installing Lm sensors and configuring. Less then 4 hours later my system locked up solid. 
Left it for a couple of days and suffered several freezes but since uninstalling Its been rock steady.
May be worth a try.

edit problem on both fiesty and gibbon.

---

### Post by maciste on 2007-11-05
Are you using SuperKaramba?? i've removed it, and since last week i didn't have any freeze.

---

### Post by majoridiot on 2007-11-05
updating my previous posts:

i recently upgraded my main system to a Q6600 quad core and gustsy.  thus far, i have not experienced a freeze, however
the system has not had a lot of use- so i can not say for certain it is stable.

i took the core2 duo from that box and built a new mythtv backend server on a gigabyte GA-P35-DS3L with an nvidia 8600GTS.
the backend is running mythbuntu 7.10 (AWESOME!).  it installed like a dream, properly configured all of the hardware and 
seemed very stable.

however, it started the typical "freezing"  a few days later- which seemed to be triggered when browsing with firefox.
the first couple of freezes, i let it sit and it seemed to "recover" after 3-5 minutes.  it did not seem to freeze when using 
the mythtv frontend to watch recordings, etc.  it may have been freezing without my knowledge, since video continues
to play during a "typical" freeze... but the remote never failed, nor was there any indication that the system was "frozen" 
while using the mythtv frontend.

mythbuntu did not install powernowd, so that is eliminated as a suspect in my case.  simply adding the kernel boot parameters
mentioned previously once again fixed things and  it has been rock-solid ever since.

---

### Post by valluvar on 2007-11-07
Thanks Baeler! Turning off APIC got the system working. No interrupt seems messed up so everything works. However cpu scaling is off (the machine i have is an acer 4520 notebook with a dual core athlon), battery monitor et al is also off. Need to figure out how to get them up without APIC. Any clues ? Had the same issue with 7.10 so that is not the solution. My biggest worry is thermal as the thermal module and the amdpowernowd module dont load anymore without APIC. the following are the options i used with the kernel  noapic nolapic acpi=off apm=power_off pci=assign-busses

---

### Post by Supremacy on 2007-11-08
I recently upgraded to Gusty (7.10) and it didn't solve the problem. I'm yet to try kernel parameters but when I do i'll post my findings.

---

### Post by utnubuuser on 2007-11-08
hello --  getting freeze up from yahoo site - don't know if it's related, but I've wondered if it might have something to do with the TOTEM suite?

---

### Post by Supremacy on 2007-11-08
> **utnubuuser said:**
> hello --  getting freeze up from yahoo site - don't know if it's related, but I've wondered if it might have something to do with the TOTEM suite?

nah, i don't believe it is. I got freezes when I was using no programs just on the desktop

---

### Post by joe.turion64x2 on 2007-11-09
Fedora 8 has been released (8-XI-07) and it is really nice, definitely worth a try, and hopefully your freezes will vanish in the air.

---

### Post by Supremacy on 2007-11-12
> **joe.turion64x2 said:**
> hopefully your freezes will vanish in the air.

funny you say that. I downloaded Fedora 8 last night and installed it this afternoon. I was happily using Compiz Fusion at its full use without a freeze for more than 2 hours.

---

### Post by arsham on 2007-11-12
Ok
I've reached to a safe zone now
I must say kernel noapic nolapic acpi=off apm=power_off pci=assign-busses didn't help

I have a fresh installed gutsy , and I managed to download these packages from feisty release : 

x11-common_7.2-0ubuntu11_i386.deb 
xorg-dev_7.2-0ubuntu11_all.deb     
xserver-xorg-input-all_7.2-0ubuntu11_i386.deb
xorg_7.2-0ubuntu11_i386.deb        
xserver-xorg_7.2-0ubuntu11_all.deb  
xserver-xorg-video-all_7.2-0ubuntu11_i386.deb


Now almost 1 hour and 30 mins I don't have any freeze at all , ( it was at least 10 mins )

My kernel version is : 2.6.22-14-generic

Only 2 condition : 
I have disconnected my external USB HDD , I will try to connect it in next 6 hours and see if it is about the ehci module or not
I will try the latest 2.6.23.1 tomorrow again to see if there is problem or not

But without compiz , I have no freeze at all

Computer specs :
GC : intel 915GM
CPU : centrino 1.6
RAM : 1GB

Programs that are running currently :
swiftweasel ( firefox )
Wingide ( Python based IDE )
ZDE ( Zend Studio , a java based program )
Amarok
CSM
Konsole
Gaim
Skype
vlc

:guitar:

---

### Post by joe.turion64x2 on 2007-11-12
> **Supremacy said:**
> funny you say that. I downloaded Fedora 8 last night and installed it this afternoon. I was happily using Compiz Fusion at its full use without a freeze for more than 2 hours.
So your session lasted just 2 hours because you finished it or because it froze?

---

### Post by Supremacy on 2007-11-12
nah, I shut down and switched back to windows cause I had things to do that I needed windows. Seems fine to me. Dunno what causes them in Gutsy and Feisty. It is really funny cause I would really only get 15-30 mins of use and Fedora gave me 2 hours worth.

It didn't freeze. I ended the session.

---

### Post by arsham on 2007-11-13
Ok
I went to sleep , and came back , omg , everything in stable mood!
just one thing:
Everytime the freeze occurred a sound like what I set to incoming message for gaim is heard , right the time the freeze.
so the only thing I haven't run was gaim
now for next 24 hours I will test that

Including , I used another kernel : 2.6.22-14-386

Computer specs :
GC : intel 915GM
CPU : centrino 1.6
RAM : 1GB

Programs that during last 24 hours ( without any crashs ):
swiftweasel ( firefox )
Wingide ( Python based IDE )
ZDE ( Zend Studio , a java based program )
Amarok
CSM
Konsole

:guitar:

---

### Post by arsham on 2007-11-13
Ok
I had 3 freeze in a row for less than 10 mins
In the first one , every programs I had to run were open (amarok , gaim , skype , firefox , wingide , zend studio , acrobat reader )
The second and 3rd , only the gaim with compiz

I observed in some incoming messages from gaim , I have the freeze
Maybe some plugins in gaim needs to do something that causes the crash

In the other situations that I had 24 hours stable , I had gaim with no incoming messages , but lots of java/python/native programs running

System specs:
Centrino 1.6
1GB RAM
External USB HDD attached
GC : intel 915GM

Kernel : 2.6.22-14-386

I have gutsy , but manually installed these packages from feisty repos :
x11-common                     1:7.2-0ubuntu11
xserver-xorg-input-all         1:7.2-0ubuntu11
xorg                           1:7.2-0ubuntu11
xserver-xorg                   1:7.2-0ubuntu11
xserver-xorg-video-all         1:7.2-0ubuntu11

I hope these informations help

---

### Post by Asnem on 2007-11-15
If I leave mine alone for a while, it starts working better.  In fact, it was working perfectly for 3 days, until I unplugged my monitor (which is also my USB hub).  Once I plugged it back in, the mouse and kb started misbehaving again, only working in the plane where it had focus; it's like the focus gets stuck on one object, and doesn't switch to another object or window when you move the mouse.

I just bought another motherboard to see if my problem is Asus or ACPI related.

---

### Post by andremonteiro on 2007-11-18
Same thing happens here. ](*,)]
My graphics card is an (ATI) Radeon XPress 200M and **seems it locks only when firefox is open.**

It happens, for example, when I browse through [http://www.deviantart.com](http://www.deviantart.com) to the widescreen wallpapers section. Would all you please try it, so we can get more information about those freezes? Thanks.

---

### Post by wakeboarder on 2007-11-18
Me thinks it's Bill Gates who snuck a little nasty bug into the linux kernel to make his Windows look better...

:guitar:

---

### Post by Asnem on 2007-11-19
I have solved my freezing problem.  My problem was with the GUI freezing where the mouse pointed would move, but you couldn't click or use the keyboard.  You could use the mouse and keyboard in a limited fashion but only in one area of focus.

My problem turned out to be a bad mouse, and possibly power supply.  I think it's primarily the mouse, however.  I have a Logitech MX518 (which works fine in XP).  I replaced it with an old MX300, and Linux has been stable for several days now.

Anyone that has the mouse/kb/focus problem should try a new mouse, and disconnect the old one.  I tried a new mouse before, but left the old one connected also, and still had the problem.  It's only when I disconnected the old mouse that the problem went away.

---

### Post by applegrew on 2007-11-21
I have been using Kubuntu Feisty for over 2 months. Since a month before I started getting recurrent (at 5 mins interval) xserver restarts. As suddenly it came, as suddenly this problem is now gone (oh wait it did happen twice last week).

Anyway, but since yesterday I am having exactly this same problem as all u guys have described. I could use my keyboard but gui was not responsibe to clicks. I could see the "kdm_greet[6845]	Internal error: memory corruption detected" messgae. I have a HP dv5200 TX laptop with NVidia Geforece 7400 Go, Intel Centrino Duo 1.73GHz, 1GB RAM.

---

### Post by shiggs on 2007-11-21
hey folks, i decided to give gusty a try.. and now I am here so I guess you can figure out the problem.

I did a fresh install from the 10/16 iso (2.6.22-14-generic #1 SMP) on a hp/compaq nx9420 w/ 7900gtx (actually quadro nvs 510m). t7400 cpu, sata disk, centrino, broadcom nic & bt, etc.

With the restricted drivers i could barely browse the w/ firefox before a hard lock up.

So i installed the latest NV beta as recommended above, all went well after installing some packages and fixing that mess of sources.list.  

Except  I can't seem to get compiz effects running. The window decorator seems to crap out, and I can only get them back by typing metacity --replace (obviuosly not compiz).

Is there no more emerald in the compiz fusion?  It was not installed.

thanks

---

### Post by shiggs on 2007-11-21
OK fixed the compiz issue.  Did 2 things at once so not sure which did it

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

and made sure gtk-window-decorator was being used (specified in compizconfig-settings-manager)

Hopefully no crashes

---

### Post by soxs on 2007-12-02
@shiggs: sudo apt-get install emerald
and make sure your xorg.conf (/etc/X11/xorg.conf) is configured properly (attached mine)


Is there anybody left who still has troubles? Mine were fixed with the 8.42. drivers on my ATI PC and my Nvidia never had any^^...

---

### Post by IVIisterX on 2007-12-05
> **soxs said:**
> @shiggs: sudo apt-get install emerald
and make sure your xorg.conf (/etc/X11/xorg.conf) is configured properly (attached mine)


Is there anybody left who still has troubles? Mine were fixed with the 8.42. drivers on my ATI PC and my Nvidia never had any^^...

Hello soxs! Hello to  "the rest of the world"!

I think your right. I did the upgrade to gutsy gibbon and then I installed the ati driver 8.42.3 with envy.

I can use the system now with driect rendering activated and with out freezes until I am working. The machine freezes only if I activate Gltext screenesaver and the screensaver starts. Then the screensaver freezes after a few minutes at random times. Only reset is possible.

The machine freezes too, if I activate compiz. Then I get freezes at random times. The machine freezes including the mouse cursor. Again only reset is possible.

Upgrading to gutsy gibbon brought another problem for me:

Firefox closed without any messages on various sites. In a test with flock - using firefox version 1.5.x - there were no problems. After a new installation from firefox directly  from the mozilla site there are no problems anymore. There seems to be a bug in gutsy gibbon.

So long 

IVIisterX

---

### Post by soulglo83 on 2007-12-31
I have tried everything, and have responses laced throughout the history of this thread.  i have seen numerous work arounds and semi-remedies, but nothing actually fixed my freezing... until now!!!!! 

i have found a FIX, assuming your freezing is characterized by an unresponsive keyboard, a memory hungry Xorg, and an otherwise unresponsive desktop (though weirdly, the mouse's location continues to update on the screen)... remove mouseemu

**sudo apt-get remove mouseemu**

this package is only useful if you are emulating a 2 or 3 button mouse w/ a mac 1 button mouse.  otherwise it causes all sorts of nasty input/output race conditions to occur.  The bug is documented [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/113344](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/113344) regarding its funky keyboard/mouse behavior.

i removed this package over 2 weeks ago, and since have yet to experience any lock ups or weird mouse/keyboard behavior.  it even improved my mouses response time(especially in counter strike, my kill/death ratio is much better now).

remove the package, you have nothing to lose (unless you have a one button mouse, in that case, you probably shouldnt be using linux in the first place).

let me know if this helps anyone!

---

### Post by arsham on 2007-12-31
I didn't have the mouseemu package installed
I think that was a wrong theory for me , but thanks.

---

### Post by metalpres on 2007-12-31
im running gutsy but i am having freezing issues as well, my system is stable when just sitting, but i keep getting display freezes when using the compiz desktop zoom,  the system wont freeze but the display locks up, background processes continue working like downloads, music or video (video freezes on display but is actually still playing) .  so the only option is the reset the box.  it happens most frequently when watching vides in firefox like youtube or whatever while zoomed in, but it happens other ramdom times as well.

im running an ati radeon 9600 with the stock gutsy drivers,  no restricted drivers.  any thoughs on what could be causing it would be great, it seems like it may be some sort of memory leak maybe,

---

### Post by Lorin Ricker on 2008-01-01
I'm new to Ubuntu, just installed Gutsy a couple of weeks ago, and have been using/learning it off&on since.  Just a couple of days ago, I ran into exactly the symptoms, system-hang, described herein, and I opened a thread in Abs. Beginners asking for help:  [CUPS hangs my system -- Ubuntu 7.10]("http://ubuntuforums.org/showthread.php?p=4055147#post4055147").

Obviously, I guessed wrong about what was causing the hangs, and just today my forum research led me to this particular thread.

My plan is to try the advice to remove mouseemu per soulglo83's post #822 -- if that doesn't work (more hangs within a few hours or days), I'll move on to try majoridiot's post #544 -- and I'll post my own results here shortly.

If you're interested, please see my own post #5 in the above thread... Where's Official Support on this whole system-hang thing???  :confused:  This seems like a real show-stopper for Ubuntu and Linux in general...  Shouldn't the Community be able to expect some official response, even if only "we're aware of this and working on it...", from Canonical?

I'm just a newbie looking for calibration here, not intending negativity or criticism.  I am now an Ubuntu convert for the long-haul, and will be looking for ways to constructively contribute beyond "I have a problem"... just as soon as I learn something useful!  :)

---

### Post by candtalan on 2008-01-02
> **Lorin Ricker said:**
> Where's Official Support on this whole system-hang thing???  :confused:  This seems like a real show-stopper for Ubuntu and Linux in general...  Shouldn't the Community be able to expect some official response, even if only "we're aware of this and working on it...", from Canonical?

I'm just a newbie looking for calibration here, not intending negativity or criticism.  I am now an Ubuntu convert for the long-haul, and will be looking for ways to constructively contribute beyond "I have a problem"... just as soon as I learn something useful!  :)
The community does not run from a central location like a proprietary operation does. If a project is widely supported then more work gets done on it. Unless a consensus of symptoms can be gathered then nothing systematic can be used in troubleshooting. Some opinions include suspected hardware problems. Linux including ubuntu is developing at a blistering pace so even if no specific solution is found, updates to packages may well sort things out.
You are contributing to knowledge on this in this thread - more information, data and tests are useful. Most FOSS organisations and groups also welcome financial donations too.

hth

---

### Post by Lorin Ricker on 2008-01-02
Thank you, candtalan -- that's the kind of "calibration" I was hoping to receive.  Your words are encouraging and your guidance is helpful!  I do have a 25+ year sw-dev background, in the proprietary world (VMS), and so, respectfully, I'm still getting my bearings here!  :)  I do understand that this is not an "us vs. they" proposition -- there's only "_we_", and I like that!

 I just wish that I could offer something more useful -- obviously we all do, given that this is an 800+ (and counting) post thread, and lots of us are still chasing the same random freeze problem.

I've done some digging on Launchpad/Ubuntu for this problem.  At a first-glance minimum, the following Bugs have been reported:

[#117651]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117651") (ubuntu randomly freezes)
[#103400]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103400") (compiz freezes x server after screensaver kicks in)
[#108527]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108527") (X freezes when compiz is enabled on ATI cards)
[#120347]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120347") (xorg hang after longer (12h) idle time)

...at a minimum -- there may be other bug reports that are directly related, tho' using different words/symptoms to describe the same overall problem.  I don't see any definitive direction, and no solution or fix yet proposed, in any of the above.  All of these are currently marked Status:Incomplete and Importance:High.  I offer this research only to "tie some things together", as I'd not seen any other postings this thread which indicated that any official support had been mustered.

OK.  Now, on to the remove mouseemu experiment...

LMR

---

### Post by Lorin Ricker on 2008-01-02
OK -- In the "nice try but no cigar" department, my attempt to remove mouseemu resulted in:

```

$ sudo apt-get remove mouseemu
   ...
Package mouseemu is not installed, so not removed
   ... 0 to remove ...

```

So, that's not it, at least for my system (thanks for the try, soulglo83!).

Onward to try stuff in post #544... Note that I'm posting this from Firefox in Ubuntu, up for about 2 hours, but limited use (my previous posts were from FF in Windows, same PC).  Hope things don't freeze while/until I get the next experiment with reboot done!...

---

### Post by Lorin Ricker on 2008-01-02
I've now performed the fix-steps in post #544 (majoridiot), referred to as "psyke777's fix" -- rebooted, observing that:

a) time to reboot (from grub-menu to login screen/prompt) has gotten much longer, from about 60 seconds (pre-fix) to now just over 2 minutes (120 seconds).

b) time to login (from <Enter> after pwd to X ready-to-go) is also much longer, from about 20 seconds (pre-fix) to over 35 seconds.

c) mouse cursor seems a bit sluggish, sticky, as does typing (I'm a fast typist).

d) Apps (e.g., term, games, firefox) seem subjectively and noticeably slower to launch, by a few seconds each.

Can any of this be attributed to the kernel-boot parameters I've now got?

```

kernel   /boot/vmlinuz-2.6.22-14-generic root=UUID=2509e989-d3c6-4ff3-bfc0-da27f6c789b2 ro quiet splash noapic nolapic irqpoll ht=on

```

I just added " noapic nolapic irqpoll ht=on" after "splash".  Can anyone pls point me at doc/man which describes what these four parameters actually mean/do?  Tx.

Another question: :confused:  The first two of those fix-steps had me do

```

sudo apt-get remove powernowd

```

followed by an edit of ```
/etc/init.d/powernowd
``` -- Why did I need to do that config-file edit if I first removed the powernowd package?  What does that config-file do if the package is removed? :confused:

Result so far -- I'm now rebooted with a slower (apparently) system -- waiting to see if more "random freezes" actually do occur.  I'm monitoring this thread, plus the above-mentioned Bug Report(s), to see if more definitive advice obtains.

LMR

---

### Post by kevinmedina on 2008-01-02
I'm having the same problem and it has been bothering me for months.  I just implemented majoridiot's suggestion but with no results - positive or negative.  From the looks of this thread, this is a pretty widespread problem.  With so many people experiencing the same problem is it possible it's a result of a conflict from a relatively recent update?  I began experiencing this issue around last summer/fall, just around the time this thread began.  If that's the case, I really hope canonical is trying to churn out a fix for this... It's really bad when my Ubuntu is crashing more often than my XP :-(

Regardless, I'm a hardcore fan and wouldn't stray from newly forged loyalty :-D

---

### Post by soxs on 2008-01-04
Ok, I am currently running fine with an (?) nvidia PC.

Now my brother has my motherboard/graphicscard/stuff combo, the exact same combo except HDs.
And, although I had fixed the PC running fine with my install, a fresh install showed the same problems again. I confiured the xorg.conf myself to ensure making no mistakes and applied the latest ati driver (7.11 or 7.12), but this did not really help.

As far as I can tell from my own experience: It has nothing to do with acpi or apm, I had my PC running fine with all that stuff running just fine!
Now that peace of crap hangs itself randomly even when disabling acpi apm IRQsuff and well .. I don't really know what to do.
The only  thing I can remember I had done was installing without internet access. This is tested currently, and after having installed and doing a 24h run I will come back here again and give some results. This is the only and final thing I can think of.

Any further suggestions are appreciated...

@kevinmedina:
this bug is somehwo stonaged. I had serious trubble with edgy and feisty (both frooze on live cd and on fresh installs without any modifications aswell without graphics drivers and applied fixes aswell as with graphics drivers and applied fixes). Gutsy is somehow more stabel, I donot get any freezes on live cd anymore, but wehn installed, the same f*** starts again...

---

### Post by komplexitee on 2008-01-05
This describes a display freeze problem that seems to have been fixed by installing the ATI X300 driver version suggested by Ubuntu.

"Random" freezes occurred after a few minutes of use with the receipt of a NMI interrupt.  The display and keyboard were frozen but the mouse cursor moved.  This happened twice.  The computer had run Fedora Core 8 and Windows XP Pro within the week without any problems.

I installed the ATI driver version suggested by Ubuntu and haven't had the problem since (several hours of use).

Factoids (attached info files are below):

Ubuntu 7.10, clean install with patches applied.
Added Eclipse and Java SDK 6.
The computer is a Dell 4700 with an ATI Radeon X300.

The last kernel messages before the freeze were:
kernel: [  533.620610] [COLOR="SeaGreen"]Uhhuh. NMI received for unknown reason b1 on CPU 0.[/COLOR]
kernel: [  533.620617] [COLOR="SeaGreen"]You have some hardware problem, likely on the PCI bus.[/COLOR]
kernel: [  533.620619] [COLOR="SeaGreen"]Dazed and confused, but trying to continue[/COLOR]

Kernel messages related to the ATI driver:
kernel: [   41.733705] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
kernel: [   41.737423] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
kernel: [   41.737569] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
kernel: [   41.991134] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
kernel: [   45.209777] [fglrx] total      GART = 130023424
kernel: [   45.209785] [fglrx] free       GART = 114032640
kernel: [   45.209789] [fglrx] max single GART = 114032640
kernel: [   45.209792] [fglrx] total      LFB  = 134086656
kernel: [   45.209796] [fglrx] free       LFB  = 108843008
kernel: [   45.209800] [fglrx] max single LFB  = 108843008
kernel: [   45.209804] [fglrx] total      Inv  = 0
kernel: [   45.209808] [fglrx] free       Inv  = 0
kernel: [   45.209811] [fglrx] max single Inv  = 0
kernel: [   45.209813] [fglrx] total      TIM  = 0

I have the full syslog sequence for the pre-crash and post-fix boots if that is of interest.

ATI configuration info:
$ lspci -n | grep 0300
01:00.0 0300: 1002:5b60
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

-- Jim

---

### Post by elizh on 2008-01-07
I have a tower w/ intel core2 6600 @2.40 gh cpu (32 bit). 
It has a GeForce 7600 GT graphics card with driver 'nvidia'.

uname -a
Linux anise 2.6.20-16-generic #2 SMP Tue Dec 18 05:45:12 UTC 2007 i686 GNU/Linux

This system was built and shipped by system76. 

In recent days I have been getting the lockup a couple of times a day. Not only is it non-recoverable, but I actually have to let my machine rest for several minutes for it to reboot successfully.  

I am not running mouseemu or powernowd or ATI video drivers.  I would be happy to provide whatever logs people think might be helpful. 

At present I'm begging to go back to Red Hat. But maybe I should look around carefully in case it's really due to all this newfangled hardware... 

Two example failure sequence descriptions below.

Regards,

Eliz

One, firefoxy:

1) gnome window mgr, 'human' theme, running firefox only. 
2) have a couple tabs open in firefox.
3) try to load a page. In this case it was the Sports Illustrated live update nfl game page, although mostly that page runs fine.
4) firefox dies
5) click on firefox icon to restart. 
6) get the spinning icon for application start
7) spinning icon goes away, but no firefox. Well, better restart my session then.
8) select 'logout'  from System>quit
9) now I have a black tty window showing the tail end of the boot sequence, but no prompt, whether login or shell. Now I'm doomed. 
10) can enlist a second person to help type the 'sekiub' soft shutdown seqence, or hard boot. 
Sigh. Why isn't there a soft shutdown binding I can actually type?

Two, more typical: 

I'm running a Firefox with several tabs open, maybe GAIM, a couple of shell windows. Possibly the Gimp or our Java3D graphics client. 

1) I minimize a window, and it leaves a trail of outlines in decreasing sizes. Danger! Danger!
2) some patch of screen fails to update, but apps are still running and mouse still moves. Sometimes the Java3D display is still updating. 
3) But things deteriorate quickly.  I try to exit applications but there is no gui response.
I try switching ttys but never get a password prompt after entering my user id. ssh does not allow login.  And so it goes. I only recently learned about the soft shutdown sequence, so I haven't tried it much. As mentioned, it does require a second person to help with the typing...

---

### Post by elizh on 2008-01-09
OK, here's a little more info. 

In the latest occurrence, I was running our under-development computer game. During a period of network update, the java swing based clock froze up (I understand this runs via X). The Java3d updates (which do their own graphics, not using X) continued.  So I loaded a web page... continue as above.  After the cascading rectangles,  I was able to kill the x session with ctl-alt-backspace, giving me a completely black screen without even the old boot sequence messages visible. Can't switch ttys, can't soft boot, nothing. 

E

---

### Post by Lorin Ricker on 2008-01-15
For the record, and having applied the fix from post #544, referred to as "psyke777's fix" (see also my post #829), I can now report that... This "fix" has no beneficial effect on random freezes for my PC.

In other words, having off-&-on booted into Ubuntu (and having to continue using Windoze for "real work"), I am still experiencing the random freezes as described throughout this thread.

I've got an auto-notification on Launchpad Bug #117651, "ubuntu randomly freezes", but have seen no positive activity since my posts of a week ago (2-Jan).  Is this ever going to get analyzed and fixed?  Ubuntu is practically useless "to replace Windows" -- other than for playing Mah-Jong -- until this gets resolved.

---

### Post by soxs on 2008-01-15
If you have some cheap nvdia / ati board liing around, try it. Otherwise check for defuncting ram. I myself can't explain it, in fact, nobody can. We are making radnom guesses.
When I get a new Pc , I think about sending in my old PC which had that f**ing problemaswell, to the devs.

---

### Post by majoridiot on 2008-01-15
as an update, both my quadcore box and my core2duo box have been running fine with no freezes for a few weeks **without** the added kernel options 
from post #544 that i had previously been using.

the core2 box is a mythbuntu backend/frontend that gets heavy use, including a lot of HD media.  the quadcore has been stressed heavily many times
and has fully-locked once... but exhibited behavior of a misbehaving app and not a freeze as in the past.

i'm at a loss to explain the sudden disappearance of the freezing issue on my machines.  honestly, i think i missed a kernel update at some point, as when i
went back to check menu.lst i noticed the added kernel boot parameters were missing from both machines.

i'm happy all seems to be ok here, but i still wonder what is going on overall with the whole situation.

---

### Post by soxs on 2008-01-16
I reduced the problem to ati drivers/malconfigured xorg.conf.
I removed the atidrivers, removed the aticard plugged in an old nvidia card, installed the ubuntu drivers and its just runing fine. Either something is colliding with the ati card, maybe bios or whatever or its a lack of support for radeon 9500pro/9700 chips

---

### Post by Alchera on 2008-02-12
This problem (also in Gutsy) could be the result of [PowerNowd]("http://www.deater.net/john/powernowd.html") being run as a service. PowerNowd is a lap top specific service dealing with frequency scaling that desktops can do without.

---

### Post by manuhalo on 2008-02-14
I'm having the same problems on my acer notebook, a centrino dual core with a nvidia GeForce Go7300 video card. I'm running compiz on Nvidia proprietary drivers, but that's not the problem, as I've tried disabling both and reverting to nv drivers - and I still experienced freezes. After a bit of experimentation it seems to me that the issue only arises when the laptop is being charged or is otherwise connected to the wall socket; I'm guessing that either gnome power manager or some other daemon/program that gets loaded when the pc realizes it has got plenty of power to feed on has something to do with the freezes. Symptoms are the usual iowaits boosts in the cpu monitor, pc being unresponsive for a small time frame and sometime freezing completely to the point I have to shut it down forcedly. Oh, I tried the noapic boot option etc but didn't work.

For the record, I had a small freezing while typing this. Any clue?

EDIT: now using the full "noapic nolapic acpi=off pci=noacpi" boot option string, I do get an error message at start about an unrecongnized parameter (guess one of these options is redundant) but so far so good. fingers and toes crossed, sorry for the useless post :)

---

### Post by kelt65 on 2008-02-25
I can't believe this is still no addressed - this thread is from 2005? I've been using Ubuntu for a few years now with no probs from my Nvidia 6800 based card + compiz but with the FX3400 at work Gutsy locks up so frequently it is entirely unusable. I've tried every hint mentioned on this thread to no avail. RHEL 4 doesn't have this problem BTW.

Removed compiz entirely and tried the various kernel boot options mentioned here. Still locks up. This is terrible!

---

### Post by soxs on 2008-02-26
No info, no fix.
No dev, no fix.

And atm we neither have enough info nor a dev, puttings his effort into this...

---

### Post by bran on 2008-02-27
> **utnubuuser said:**
> hello --  getting freeze up from yahoo site - don't know if it's related, but I've wondered if it might have something to do with the TOTEM suite?

I uninstall totem as part of setting up a new install still farting and stalling.  Intel vid on my lappy

---

### Post by alwayshere on 2008-02-27
im using feisty fawn as the only os on my macbook and i have no problems so if you give me a command ill post my results if thats any help the only thing i could suggest is to turn off desktop effects as i have had them conflict with other stuff in the past ,but i now have them enabled with no problems at all.

---

### Post by vievie on 2008-03-27
Is this fixed?

I had to move to Mandriva since Feisty Fawn had this problem.  I have to say, at least, mandriva is pretty usable, rather than freeze every minutes ...

---

### Post by soxs on 2008-03-28
For me it was a mallfunction/usupported thermal control of my motherboard -.- new PC and everything works fine...

---

### Post by Lorin Ricker on 2008-03-28
> **vievie said:**
> Is this fixed?

I had to move to Mandriva since Feisty Fawn had this problem.  I have to say, at least, mandriva is pretty usable, rather than freeze every minutes ...

I've become a non-technical beta-tester of v8.04 (Hardy Heron) -- my early test results are that this **seems to fix** the system-freezes that I was experiencing regularly with v7.10 (Gutsy).  However, as my testing on my own "problematic" PC have been cursory and informal, I intend to do more lengthy "serious use" testing over the next few days & weeks, so take my feedback as tentative.

Caveat:  This sort of in-situ, ad-hoc testing is problematic for concluding, decisively, that "this problem is fixed."  It's sort of like the logical fallacy of "you cannot prove a negative"...  In other words, how long should the "it hasn't frozen yet" uptime-duration be before you can conclusively say "it's fixed"?  If you observed it not freeze for a week, would that convince you that it wouldn't freeze in a week and an hour?

Since I've heard no technical explanation (other than the anecdotal in this long thread) as to what is causing this problem, what's at the root of it, it's not possible to say that "the code's been fixed, and this problem is now reliably history".

On the other hand, some of the preliminary release-notes text at:

[http://www.ubuntu.com/testing/hardy/beta]("http://www.ubuntu.com/testing/hardy/beta")

especially about the Linux kernel 2.6.24 included in v8.04 (Hardy), are promising that this system-freeze problem is properly addressed and fixed.

I hope this helps...

---

### Post by rickyrockrat on 2008-04-02
I can confirm that this is happening with the latest kernel (2.6.24.2) custom compiled  and with the binary drivers from NVIDIA.
I am running a core 2 (6420) at 2.13Ghz with a GeForce 8500 with 169.09 driver.

I am running a 64-bit system. I can't tell if it is a Linux kernel issue or it is a problem with the Nvidia kernel driver. Since it isn't open source, I'm blaming the binary driver.

I get a hard freeze about once a week.

---

### Post by soxs on 2008-04-02
I heard about this being addressed properly in hardy, so you might want to check out the beta.

---

### Post by Fredizdman on 2008-04-08
I had this same problem about a month or go, and turning off superkaramba solved it for me.If I turn on superkaramba I get a freeze anytime I run more than one widget, strange, huh? There is a bug report on superkaramba causing freezes and many people there said it was their problem. Good luck!

---

### Post by NickArgyle on 2008-04-10
Well, I had random freezes in both feisty and gutsy. I recently reinstalled gutsy, and instead of using nvidia-glx-new, I installed Envy, and now that I have the official and current hardware specific graphics drivers, I have not has a single freeze all week. This is the first time I have ever had such a solid install of ubuntu! I was getting freezes every 10-20 minutes, but now it is perfect!

---

### Post by -Zeus- on 2008-04-10
why was this resurrected???  Fiesty is far out of date.  A new thread should probably be started for those expierincong this with Gutsy and/or Hardy

---

### Post by rickyrockrat on 2008-04-14
All,
For my Duo-Core, Nvidia box running 64-bit Linux, I have had the lockup with a custom-compiled vanilla kernel 2.6.12.2, and using the open-source NV driver for my GeForce 8500 GT. The interesting lines from my log file are:
Apr 13 02:51:33 duo-core kernel: [563004.544830] NVRM: Xid (0001:00): 6, PE0001 
Apr 13 02:51:33 duo-core kernel: [563004.546357] NVRM: Xid (0001:00): 6, PE007e 
Apr 13 02:51:33 duo-core kernel: [563004.548035] NVRM: Xid (0001:00): 6, PE007e 
 
So this appears to be a Linux kernel bug and has nothing to do with Ubuntu, unless Ubuntu has a special NV driver.

---

### Post by rickyrockrat on 2008-04-14
> **-Zeus- said:**
> why was this resurrected???  Fiesty is far out of date.  A new thread should probably be started for those expierincong this with Gutsy and/or Hardy

Many are still using Feisty since it is more stable than Gutsy, and not everybody likes to upgrade every time a new release comes out. I for one would just like to USE my computer to get work done. :)

---

### Post by soxs on 2008-04-15
Well, if your PC freezes with gutsy, you should update/upgrade your OS... this is some primitive logic.. at least for me it sounhd s logic..
For those, getting to run feisty run smooth, this thread does not matter.
For those, using feisty and getting freezing/random lockups.. I suggest them to upgrade...

---

