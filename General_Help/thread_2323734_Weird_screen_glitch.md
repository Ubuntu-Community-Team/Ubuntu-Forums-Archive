---
title: "Weird screen glitch"
date: 2016-05-07
forum: General Help
---

### Post by trey11 on 2016-05-07
Trying to install Lubuntu 16.04 on an old laptop and this keeps happening. [IMG]http://i.imgur.com/1NYrdiw.jpg?1[/IMG] Anyone know what the problem could be?

If any of this helps the specs are:
CPU: AMD Sempron 5200+
1GB RAM
Graphics: NVIDIA GeForce 7150m/nForce 630m
HP Pavilion dv6500

---

### Post by DuckHook on 2016-05-07
Welcome to the forums, trey11.

I am unfamiliar with your HW. So what follows is an educated guess...

[LIST=1]
[*]Your monitor is going (not unusual in old HW)
[*]Your driver is mismatched to your GPU which in turn is quite under-powered.[/LIST]
What driver are you using? nVidia's proprietary or the open source Nouveau?

---

### Post by trey11 on 2016-05-08
The prorpietary ones. Version: 7.15.11.7967

---

### Post by DuckHook on 2016-05-09
I have no idea what driver version that is. Have never seen such version numbering for nVidia. How did you install them? If from repositories, please uninstall through the same "Additional Drivers" tab in "Software & Updates". If you have any data on the laptop, backup first.

[LIST=1]
[*]Have you ever tried the Nouveau driver?
[*]If so, did it work?
[*]If not, then perhaps you should try it&#8213;it is the default.
[*]Does display work properly in LiveUSB/DVD?
[/LIST]

---

### Post by trey11 on 2016-05-10
I should probably mention that i'm still on windows 7 so that's the driver version for that. The problem is that whenever i try to install any linux distro my screen always messes up like that. If im reading right, Nouveau drivers wont work with windows so im not really sure if i can install them. I've also tried the alternate install for lubuntu in a VM and it worked, but when i installed it onto my laptop in the end my screen messed up again. I've been using a usb stick to install the distros with, idk if that might have anything to do with it i assume no.

---

### Post by DuckHook on 2016-05-10
I think I see the problem. Windows has nothing to do with Linux and each can't use drivers made for the other. The two operating systems are like apples and symphonies. For a better understanding of the differences, please see my signature: *Linux is not Windows*.

Since you are trying a new install, then the driver is Nouveau.

I'm heading out for a few hour. Will try to research the proper driver for your video card when I get back.

---

### Post by trey11 on 2016-05-10
I was actually able to fix it somewhat by maneuvering through that mess of a screen to display settings and changing the resolution. However i still get the same screen when im at the log in screen and i also hear a pop as i boot into lubuntu. It's not that big a deal since i can still easily log in but i would like to fix it if possible.

---

### Post by DuckHook on 2016-05-11
Now that you can log in, open a *terminal*, run the following commands and post the results back to this thread:```
xrandr
``````
cat /etc/default/grub
``````
lspci -vn | grep -iA13 vga
``````
sudo apt install read-edid && sudo get-edid | parse-edid
```Linux is very finicky about case and accuracy, so it's best to copy and paste these commands into *terminal*. Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by trey11 on 2016-05-11
```
 Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800      59.98 +
   1024x768      59.92* 
   800x600       59.86  
   640x480       59.38  
   720x400       59.55  
   640x400       59.95  
   640x350       59.77  
VGA-1 disconnected (normal left inverted right x axis y axis)
TV-1 connected (normal left inverted right x axis y axis)
   720x576       50.00 +
   1024x768      50.00  
   800x600       50.00  
   720x480       50.00  
   640x480       50.00  
   400x300       50.00  
   320x240       50.00  
   320x200       50.00  
 
```

```
 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
 
```

```
 00:12.0 0300: 10de:0531 (rev a2) (prog-if 00 [VGA controller])
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 40000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

00:18.0 0600: 1022:1100
    Flags: fast devsel
    Capabilities: <access denied>
 
```

```
 Section "Monitor"
    Identifier "&#65533;&#65533;&#65533;&#65533;o}&#65533;&#65533;&#65533;&#65533;"
    ModelName "&#65533;&#65533;&#65533;&#65533;o}&#65533;&#65533;&#65533;&#65533;"
    VendorName "SEC"
    # Monitor Manufactured week 0 of 2007
    # EDID version 1.3
    # Digital Display
    DisplaySize 330 210
    Gamma 2.20
    Option "DPMS" "false"
    Modeline     "Mode 0" 69.30 1280 1296 1344 1416 800 801 804 816 -hsync -vsync 
EndSection
 
```

---

### Post by DuckHook on 2016-05-11
It appears that you have a TV connected. Is this so? If so, try booting up without the TV connected. It is confusing Lubuntu. We can figure out how to handle the TV afterwards. Also, provide more specs on your TV. It is not showing up in edid. Your monitor should be capable of 1280x800. Try setting it to that resolution without the TV interfering.

---

### Post by trey11 on 2016-05-11
I dont have a TV connected.

---

### Post by DuckHook on 2016-05-11
Interesting. Lubuntu thinks you do. I'm responding from a doctor's waiting room right now, so can't really give good advice right now. Will have more in a few hours.

---

### Post by DuckHook on 2016-05-11
Your system is registering a phantom display. This happens with some video cards, and I haven't the foggiest idea why. This means that your video card is telling Lubuntu that a phantom TV with an oddball resolution of 720 x 576 is connected to the internal TV port. This confuses Lubuntu because it does not know what or where to output its video signal, nor what resolution to use. The result is the muddled screen that you originally saw. When you manually selected 1024 x 768, you fortuitously picked a resolution that the video card reports as supported by both your real monitor and your phantom TV. But this setting is specific to your user profile and is not invoked until after you log in, which is why you still have a muddled screen prior to login.

We can try working through some solutions, but first, a word of warning: video issues are notoriously difficult because they involve the one peripheral that allows you to see what you are doing. We will be experimenting with workarounds that may lead to loss of video output. Please be prepared to deal with that should it arise.

1. First, try running a LiveUSB session and see it the display works properly. If the display works properly in a LiveUSB, then we know that we can always use a LiveUSB to back out any configuration changes that we've made to your laptop. Also, by querying a LiveUSB session, we can get some hints about what settings it is using to enable a working display. So, if you have not already done so, try running a LiveUSB session and tell us what happens.

2. When wrestling with display issues, I sometimes install *ssh* if I can. *ssh* allows you to connect to the problem machine via another computer, even when you cannot see what is on the display. It is only useful if you have another computer to use. It is also rather complicated for new users, so I only mention it as an option. Let's try a few other things first, but tell us whether you have another computer to use.

3. On your problem system, the next time you power up, do *not* log in. Instead, at the login screen, press <Ctrl>+<Alt>+>F1> and see if you can get to a command line display. If a display is available, then this will act as a further recovery option. You get back to the GUI with <Ctrl>+<Alt>+>F7>.

Let us know which of these three recover options work for you.

---

### Post by DuckHook on 2016-05-11
Once familiar with your recovery options, try the following:

1. Open terminal.

2. Make a copy of grub for safekeeping as follows:```
sudo cp /etc/default/grub /etc/default/grub_old
```
3. Edit grub with:```
sudo nano /etc/default/grub
```
4. Find the line that looks like:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
5. Edit it to add:```
video=TV-1:d
```...so that it looks like:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=TV-1:d"
```Write to file with <Ctrl>+<o>, then exit nano with <Ctrl>+<x>

6. Update grub with:```
sudo update-grub
```
7. Reboot and see if this works

---

### Post by trey11 on 2016-05-11
1st option doesnt work cause my usb stick has stopped working for some  reason. The other 2 options do in fact work though. Whenever i do ```
 
sudo nano /etc/default/grub 
```

it comes back with Sudo: nano: command not found

---

### Post by DuckHook on 2016-05-11
:confused:

Your install is seriously wonky or corrupted if you cannot sudo nano.

Better start at the beginning then. Tell us what you've installed, how you installed and the steps you took to get there. Earlier you confused a Windows driver for Lubuntu. Is this a dual boot?

Also, be careful with the use of case. Unlike Windows, Linux is case-sensitive. sudo and Sudo are two different things.

---

### Post by trey11 on 2016-05-11
It's a dual boot yes. All i did was install it using the Alternate installation. I couldn't do it the normal way cause the screen was messed up right away so i couldn't read any of the steps. The capital S in Sudo: nano: command not found was just a typo on my part it came back as a lowercase s.

---

### Post by DuckHook on 2016-05-11
Please do:```
sudo apt-get install nano
```...then follow remaining steps.

---

### Post by trey11 on 2016-05-11
Still the same.

---

### Post by DuckHook on 2016-05-11
You may have to reinstall, but before doing so, post output from:```
id
```Do not jump to reinstalling right away. We can guide you through the installation process to add the critical```
video=TV-1:d
```...parameter to your installation so that you can see what is going on.

---

### Post by trey11 on 2016-05-11
```
 uid=1000(trey) gid=1000(trey) groups=1000(trey),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),112(lpadmin),123(sambashare)
 
```
Nothing came back from 
video=TV-1:d

Why would a reinstall matter if the screen messes up before i even install?

---

### Post by DuckHook on 2016-05-11
I don't understand what you mean by "nothing came back from..."

The last thing I knew, you couldn't edit *grub* using *nano*

What is happening?

---

### Post by DuckHook on 2016-05-11
> **trey11 said:**
> Why would a reinstall matter if the screen messes up before i even install?The TV-1 parameter is just an educated guess. The point would be that, if it is the culprit, a reinstall of the full desktop version could have this parameter set as part of the install process so that:

1. You could see everything that was happening during the install, and
2. You would have a normal installation that contained (among other things) important apps like nano.

---

### Post by trey11 on 2016-05-12
I put video=TV-1:d in hit enter and nothing different came up, it just acted like i hit enter without typing anything in. Im not even sure i can get a reinstall to work now cause my usb stick isn't working now. Looking like a hopeless situation lol. Anyways thanks for all the help i really do appreciate it.

---

### Post by DuckHook on 2016-05-12
> **trey11 said:**
> I put video=TV-1:d in hit enter and nothing different came upIt doesn't work that way. It's not an app or a script that does anything on its own. It's a kernel parameter that must be passed to the kernel at boot. And the only way to do that is using the procedures that I have already written down: editing GRUB so that the parameter appears next to "quiet splash"> Looking like a hopeless situation lol. Anyways thanks for all the help i really do appreciate it.No problem. That's what we volunteer for. Nothing is ever really hopeless. However, sometimes, it just takes more blood, sweat and tears than other times.

It's time for go to plan 'B" to do the editing part, even if it involves a trick that I don't really like to use.

Open a terminal and do:```
sudo -i leafpad /etc/default/grub
```This should open your regular GUI editor in root mode and load the GRUB configuration file. Now you should be able to follow the rest of the steps to edit the proper line, update GRUB and reboot.

**EDIT**
Before doing any of the above, let's check to make sure that we've got the right display description. xrandr doesn't always return the right term. Post back the results of:```
ls -la /sys/class/drm
```

---

### Post by trey11 on 2016-05-12
My mistake, i thought you wanted me to put video=TV-1:d in like a script as well. Ive already made it so it appears next to quiet splash. 

```
 total 0
drwxr-xr-x  2 root root    0 May 12 13:26 .
drwxr-xr-x 60 root root    0 May 12 13:21 ..
lrwxrwxrwx  1 root root    0 May 12 13:21 card0 -> ../../devices/pci0000:00/0000:00:12.0/drm/card0
lrwxrwxrwx  1 root root    0 May 12 13:21 card0-LVDS-1 -> ../../devices/pci0000:00/0000:00:12.0/drm/card0/card0-LVDS-1
lrwxrwxrwx  1 root root    0 May 12 13:21 card0-TV-1 -> ../../devices/pci0000:00/0000:00:12.0/drm/card0/card0-TV-1
lrwxrwxrwx  1 root root    0 May 12 13:21 card0-VGA-1 -> ../../devices/pci0000:00/0000:00:12.0/drm/card0/card0-VGA-1
lrwxrwxrwx  1 root root    0 May 12 13:21 controlD64 -> ../../devices/pci0000:00/0000:00:12.0/drm/controlD64
lrwxrwxrwx  1 root root    0 May 12 13:21 renderD128 -> ../../devices/pci0000:00/0000:00:12.0/drm/renderD128
lrwxrwxrwx  1 root root    0 May 12 13:21 ttm -> ../../devices/virtual/drm/ttm
-r--r--r--  1 root root 4096 May 12 13:21 version
 
```

---

### Post by DuckHook on 2016-05-12
> **trey11 said:**
> My mistake, i thought you wanted me to put video=TV-1:d in like a script as well. Ive already made it so it appears next to quiet splash.No problem. Your output confirms that the term "TV-1" is accurate. Now do the update-grub instruction and reboot. How does it look?

---

### Post by trey11 on 2016-05-12
Still the same. What exactly was i suppose to edit? If it was to add video=TV-1:d it was already there. Also after i exited out of grub i got this 

(leafpad:3245): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.IBRGHY': No such file or directory

(leafpad:3245): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(leafpad:3245): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Y2URHY': No such file or directory

(leafpad:3245): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by trey11 on 2016-05-12
In the GNU GRUB under Ubuntu theres an option that says Advanced options for Ubuntu, then 4 other options
Ubuntu, with Linux 4.4.0-22-generic
Ubuntu, with Linux 4.4.0-22-generic (recovery mode)
Ubuntu, with Linux 4.4.0-21-generic
Ubuntu, with Linux 4.4.0-21-generic (recovery mode)
If i choose the second one and let it start up it fixes everything but only if i start up that way.

---

### Post by DuckHook on 2016-05-12
You were supposed to edit the file:```
/etc/default/grub
```.The */etc/default/* part is the path to the file. *grub* is the file itself. GRUB makes the script that your system runs *at boot*. You generate the script by invoking *update-grub*. It is the only script that will modify your kernel (well, for our purposes, anyway). Your original output did not have the *video=TV-1:d* parameter in it, so unless you were able to successfully edit GRUB using some other method, I don't know how it got in there. To be sure that it is right, please post again the results of:```
cat /etc/default/grub
```The critical line should look like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=TV-1:d"
```The *video=TV-1:d* has to be inside the quote marks.

There are many further things we can try, but let's get rid of the phantom screen first. To check again whether it is still there or gone, post results of:```
xrandr
```

---

### Post by DuckHook on 2016-05-12
> **trey11 said:**
> In the GNU GRUB under Ubuntu theres an option that says Advanced options for Ubuntu, then 4 other options
```
Ubuntu, with Linux 4.4.0-22-generic
Ubuntu, with Linux 4.4.0-22-generic (recovery mode)
Ubuntu, with Linux 4.4.0-21-generic
Ubuntu, with Linux 4.4.0-21-generic (recovery mode)
```
If i choose the second one and let it start up it fixes everything but only if i start up that way.Thanks for your patience. Believe it or not, we are making progress. *Recovery mode* tries to boot up as simple a system as possible, but you are unlikely to want to stay in that sort of an environment for real work.

Please give us the output from my previous posting and we will proceed to next steps in good time.

---

### Post by DuckHook on 2016-05-12
> **trey11 said:**
> Still the same. What exactly was i suppose to edit? If it was to add video=TV-1:d it was already there. Also after i exited out of grub i got this 

```
(leafpad:3245): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.IBRGHY': No such file or directory

(leafpad:3245): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(leafpad:3245): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Y2URHY': No such file or directory

(leafpad:3245): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```BTW, all that gobbledegook was because we used *leafpad* with *sudo* instead of *nano*. It's basically harmless and can be ignored (it's also why I didn't want to sudo leafpad except as a last resort).

---

### Post by trey11 on 2016-05-12
```
 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=TV-1:d"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
 
```

```
 Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800      59.98 +
   1024x768      59.92* 
   800x600       59.86  
   640x480       59.38  
   720x400       59.55  
   640x400       59.95  
   640x350       59.77  
VGA-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
 
```

---

### Post by DuckHook on 2016-05-12
Excellent! We got rid of the phantom TV. If you compare your *xrandr* output now to what it was before, you will see the TV-1 no longer shows up.

You can now change your resolution to 1280 x 800 (which not only gives you more screen real-estate but gets rid of the jaggies in your fonts and is the preferred resolution for your hardware).

Next, let's try adding the *nomodeset* parameter to GRUB so that the line now looks like:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=TV-1:d nomodeset"
```While we are at it, take the comment character (#) out of GRUB_GFXMODE and change it to your native resolution of 1280x800, so that line looks like:```
GRUB_GFXMODE=1280x800
```(remember to delete the # character at the beginning of the line). grub-update and reboot, choosing normal boot and not recovery. Tell us what happens.

---

### Post by trey11 on 2016-05-12
That fixed it :D Thank you so much.

---

### Post by DuckHook on 2016-05-12
This was one of the tougher ones as such things go because it was a combination of two separate problems. I want to commend you for your patience and perseverance. Glad everything worked out for you.

You may want to either copy your GRUB file to an external storage (like your non-working USB stick :P) or print it out for future use if you should, for example, install from scratch. You will be able to straighten out your video simply be copying this GRUB file into your new install.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

