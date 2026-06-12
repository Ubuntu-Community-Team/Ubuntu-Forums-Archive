---
title: "wrong screen resolution after update"
date: 2016-01-26
forum: General Help
---

### Post by alfredo10 on 2016-01-26
So, one more annoying issue to fix during my Ubuntu 12.04 LTS install... and before asking why 12.04 and not a later release, it's because of a software I need to run which is not supported for later releases. Sorry to sound grumpy but I've been trying to make this work for more than a week now, facing constant errors and about 4 re-installs by now...

Now, current issue: I run the update manager to bring the system up to date and now my screen resolution is changed to 1024x768, I don't remember which resolution it had before but it's way lower now, I believe the correct one is 1920x1280.

I'm not a super user! I don't know much about this stuff, all I can say is I have an AOC e2343Fsk monitor, 23" if I remember correctly and Nvidia card I believe, not sure how to check this.

I tried a few of the xrandr commands suggested in a few forum answers and wikis but it is not working!!!:mad:

I would like to hear suggestions on how to fix this, hope to be able to wake up tomorrow and finally make this work!

have a nice day/night,

Alfredo

---

### Post by Vladlenin5000 on 2016-01-26
AOC e2343Fsk is a FullHD monitor which means **1920x1080**, not 1920x1280.
The presence of a Nvidia card may require proprietary drivers that you probably had before. Search for "additional drivers", check what's offered and install the recommended one, reboot and you should be good to go (the additional drivers dialog will also inform about the graphics card).

---

### Post by alfredo10 on 2016-01-26
Maybe I'm doing something wrong, Ubuntu instructions are just not made for us who are not computer literate.

From this page: [https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
I tried this: 

```
alfredo@alfredo-MS-7309:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
alfredo@alfredo-MS-7309:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
alfredo@alfredo-MS-7309:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  
  1920x1080_60.00 (0x6e)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz
alfredo@alfredo-MS-7309:~$ xrandr --addmode default 1920x1080_60.00
xrandr: Failed to get size of gamma for output default
```

The screen resolution now shows up in the "Displays" menu in "System Settings", but if I select it I get:
> The selected configuration for displays could not be applied
required virtual size does not fit available size: requested=(1920,1080), minimum=(640,480), maximum=(1024,768)

Maybe I'm just not in the right track.

Also, the "Additional Drivers" tab in "system Settings" has a lock on it and doesn't perform any action if I click on it.

Thanks for your help,

Alfredo

---

### Post by maglin2 on 2016-01-26
As far as I recall the Additional Drivers icon always had a padlock on it, but it responded to a mouseclick or select/enter by any user.

Do you have any more joy if you go to it by a dash search for 'drivers', then select/enter rather than through system settings (unlikely, but worth trying).

Failing that you could have a look here 
[http://askubuntu.com/questions/22118/can-i-install-extra-drivers-via-the-command-prompt](http://askubuntu.com/questions/22118/can-i-install-extra-drivers-via-the-command-prompt)
for a command line approach.

---

### Post by alfredo10 on 2016-01-26
Doesn't work through Dash either.

Tried to follow the command line approach but it already fails in the first line, it's not showing what it should and instead returns some kind of error:

```
alfredo@alfredo-MS-7309:~$ jockey-text --list
Traceback (most recent call last):
  File "/usr/bin/jockey-text", line 128, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 421, in run
    self.list()
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 476, in list
    for h_id in self.backend().available(self.argv_options.mode):
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 115, in backend
    self._dbus_iface = Backend.create_dbus_client()
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 722, in create_dbus_client
    obj = bus.get_object(DBUS_BUS_NAME, '/DeviceDriver')
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
alfredo@alfredo-MS-7309:~$
```

Suggestions?

---

### Post by alfredo10 on 2016-01-26
I tried the other suggestion:
> you need to run sudo apt-get install nvidia-current and as the previous answer said, sudo nvidia-xconfig afterwards. Then do sudo reboot and you should have a working system.
and now it's worse, I only get 800x600 resolution :mad:

So I uninstalled the nvidia drivers and am back to where I started, with still low 1024x768 resolution in my screen.

---

### Post by Vladlenin5000 on 2016-01-26
Weird, weird...

It's not the time to use xrand yet and hopefully it won't be needed*. You need to install a proper driver first otherwise no other resolutions will be available. 
Preemptively remove any nvidia driver that might have been partially installed already:
```
sudo apt-get remove --purge nvidia*
```

Then you can try jockey (Additional drivers) again, unlock, select the one recommended, apply, reboot when finished.
Alternativelly you can try the suggestion linked in post #4.
Do not install nvidia-current. Use the exact name of the recommended driver on the list you obtained by* jockey-text --list*, which such be the same as before. Apply, reboot.

Meanwhile, please post the results of *lspci *so we can have a wider perspective of the system.


* Even the recommended proprietary driver may not identify correctly the monitor. If not, then all things rand.

---

### Post by alfredo10 on 2016-01-26
Vladlenin5000, thanks for your answer, but because of so many issues I'm having (it's not just the monitor) I decided to give one last try by installing Ubuntu 14.04. Now my screen flickers constantly and suddenly freezes, so there's certainly a problem on using nvidia cards on any Ubuntu.

I had already tried purge and running jockey again but it gave me the same long error as I pasted on post #5.

I'm on the verge of giving up on this, I have been battling with Ubuntu for 10 days now and still can't make it work properly, already tried 12.04 and 14.04, not sure what else to do.

---

### Post by Vladlenin5000 on 2016-01-26
> Meanwhile, please post the results of *lspci *so we can have a wider perspective of the system.
And hopefully understand what's happening.

---

### Post by alfredo10 on 2016-01-26
lspci result:
```
cletero@cletero-MS-7309:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: NVIDIA Corporation MCP61 SMU (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:09.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
cletero@cletero-MS-7309:~$
```

I run *lsmod | greb nouveau* and apparently it's the nouveau driver that's installed.

I'm also getting an error message on start up, I will post a pic soon, didn't have time to copy it before the screen frooze.

---

### Post by alfredo10 on 2016-01-26
Here is the error message I get, sorry if there are any errors, I had to copy it from the picture I took with my phone, as I wasn't allowed to paste it here:

> 
Sorry, Ubuntu 14.04 has experienced an internal error.
-Package
linux-image-3.19.0-25.generic 3.19.0-25.26~14.04.1 [modified: boot/vmlinuz-3.19.0-25-generic]
-ProblemType
KernelOops
-Title
BUG: unable to handle kernel paging request at ffffc900107d8000
-Annotation
Your system might become unstable now and might need to be restarted.
-ApportVersion
2.14.1-Oubuntu3.11
-Architecture
amd64
-Date
Tue Jan 26 20:59:36 2016
-Dependencies[COLOR=#0000cd] (Empty)[/COLOR]
-DistroRelease
Ubuntu 14.04
-Failure
oops
-InstallationDate
Installed on 2016-1-27 (0 days ago)
-InstallationMedia
Ubuntu 14.04.3 LTS "Trusty Tahr" -Beta amd64(20150805)
-OopsText [COLOR=#0000cd](Empty)
[/COLOR]-PackageArchitecture
amd64
-ProcVersionSignature
Ubuntu 3.19.0-25.26~14.04.1-generic 3.19.8-ckt2
-SourcePackage
linux-lts-vivid
-Tags
kernel-oops trusty
-Uname
Linux 3.19.0-25-generic x86_64
-Upgrade status
No upgrade log present (probably fresh install)


---

### Post by Geoffrey_Arndt on 2016-01-26
Here's a thread from askUbuntu about your graphics system.    The one post to look at and try (in my view) is the very last post.   Would appreciate your feedback on results:

[http://askubuntu.com/questions/588538/whats-the-correct-driver-to-use-with-a-geforce-6150se-nforce-430-on-lubuntu-14](http://askubuntu.com/questions/588538/whats-the-correct-driver-to-use-with-a-geforce-6150se-nforce-430-on-lubuntu-14)

---

### Post by alfredo10 on 2016-01-27
I had seen a similar thread yesterday but it was too late already, so I decided to try your suggestion early today.

**THANK YOU THANK YOU THANK YOU and off course thanks to all guys who helped before ;)**

Now I will try installing Bricscad (Engineering drawing software) and see how it goes.

A few notes:


[LIST=1]
[*]Boot from the DVD and press Space to choose different methods of installation.
[*]Choose Experienced Install. [COLOR=#0000cd](This depends on the CD you are using, I just used the default install)[/COLOR]
[*]Install Ubuntu.
[*]After install is done, press CTRL+ALT+F1 and login. [COLOR=#0000cd](Again, depends on the CD you are using, mine restarts the computer automatically, it opens the tray and asks you to remove the cd first)[/COLOR]
[*]Update your system: [COLOR=#0000cd](Is it really necessary?? It takes forever and due to my problem the system froze when the upgrade was about to finish, downloading upgrades during install doesn't help to make it faster either, but luckily second time it finished on time before the system froze :) **OR **maybe this step can be done in Safe Mode?? )[/COLOR]

  sudo apt-get update 

  sudo apt-get upgrade
[*]Install the driver:

  sudo apt-get install nvidia-304 [FONT=arial][COLOR=#0000CD](No problem here, just 4 more painfull minutes hoping the system wouldn't freeze!!)[/COLOR][/FONT]
[*]DO NOT run nvidia-xconfig (THIS IS IMPORTANT). [COLOR=#0000cd](Didn't do it)[/COLOR]
[*]Reboot the system (just press CTRL+ALT+DEL) [COLOR=#0000cd](This took me to an endless screen asking  for my password and never re-booted, just kept coming to ask for my  password, so I just used shut down and manually restarted my computer)[/COLOR]
[*]Login normally.
[*]Open Nvidia X server settings from the dash.
[*]Backup your configuration (you can copy and paste it to a txt file) [COLOR=#0000cd](Not sure what I have to copy here, as it contains various screens)[/COLOR]
[/LIST]
[COLOR=#0000cd]
[/COLOR]EDIT: Two more things[COLOR=#0000cd]:
[/COLOR]1) If there's a way to minimize the terminal during the upgrade process without using the mouse it would be great, the flickering gets worse when too many lines start to run in the window (like at the end when it starts installing the upgrades) and that's what seems to freeze the system, maybe if the terminal was hidden, as nothing would move the screen would hardly flicker.
2) Where can I file a suggestion for this forum? When I log in, I'm not taken back to this page but instead it takes me to the forum home page, which is kind of annoying.

Thanks again,

Alfredo[COLOR=#0000cd]
[/COLOR]

---

### Post by alfredo10 on 2016-01-27
I hope this is not fooling me.

After shutting down the computer to run some errands I came back and would enter into a black screen, only the mouse pointer was showing. Had to turn-off and start again twice before it booted properly :?

EDIT: YES! THIS KEPT HAPPENING! NOW I COULD NOT ENTER MY UBUNTU OS! ONLY SEE A BLACK SCREEN WITH A MOUSE POINTER WHICH I CAN MOVE AROUND! 

SUMMARY: after this, I logged in recovery mode, everything normal, even the resolution, turned off, entered in normal mode, everything fine, turned off, entered in normal mode, now the screen Is purplish with tiny lines moving around and of course, the mouse pointer... Going to sleep now... 

AND VERY ANGRY!!!!  ANY HELP??

---

### Post by alfredo10 on 2016-01-28
So today I tried to log in and was received again by a black screen and the mouse pointer... so I tried something, although I couldn't see anything in the screen: I pressed Ctrl+Alt+T to open terminal, typed in sudo reboot and then my password to reboot from the terminal, and voila, the computer rebooted, I logged into Ubuntu again and everything works... VERY STRANGE!!! Not sure what will happen when I have to log off again.

Any ideas??

---

### Post by Geoffrey_Arndt on 2016-01-28
To start off with, when everything is working . . . go into "System Settings>Software & Updates>Additional Drivers" (the tab), and take a look and see which specific driver is being used (it should be listed along with a marked radial button).   If there is still inconsistency, I would suggest to consider a full re-install using 15.10 - - and during the install process, ensuring fast internet availability with the options checked to install proprietary packages and drivers.    

If all works well, the system will then have those drivers installed "before" you do your first restart-boot up (thereby reducing the chances of black-screens).

If all the above still doesn't produce a working and stable system - - then, install a different base Desktop Environment by trying either Ubuntu Mate, or Xubuntu . . . perhaps better luck with the open source drivers on DE's that don't require 3d acceleration.

---

### Post by alfredo10 on 2016-01-28
> **Geoffrey_Arndt said:**
> To start off with, when everything is working . . . go into "System Settings>Software & Updates>Additional Drivers" (the tab), and take a look and see which specific driver is being used (it should be listed along with a marked radial button).

Thank you Geoffrey, I will try this tomorrow, if not, will see if I do the reinstall with 15.10.

Have a nice day, 

Alfredo

---

### Post by alfredo10 on 2016-02-01
Once again here:

System settings shows the driver being used is "*nVidia legacy binary driver - version 304.131 from nvidia-304 (propietary, tested)*".

It is the same driver whether I enter in save mode and then select the* "resume normal boot*" option (or something like that) or the few times it works by directly booting into Ubuntu.

As I said before, I can use terminal even if I can't see the screen, and then do a screenshot and save it. So I tried using ```
dpkg -l | grep nvidia
``` I get this results: 

> ii  nvidia-304                                304.131-0ubuntu0.14.04.1                       amd64        NVIDIA legacy binary driver - version 304.131
ii  nvidia-libopencl1-304                              304.131-0ubuntu0.14.04.1                       amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                              304.131-0ubuntu0.14.04.1                       amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver

Which are the same whether the display works or not.

Any ideas, besides installing 15.10? I'll do that if I have some time later this week, I've already gone through about 8 reinstalls and am a bit tired of it right now.

Also, I have a Debian Wheezy install disc which doesn't seem to have any problems when I try it, but I didn't like Debian too much (and Wheezy is already *obsolete*)), maybe will also try Linux Mint, I'll see.

One last question, off-topic: is it safe to use my internet when I entered in safe mode as I'm doing now? :)

Thanks again guys,

Alfredo

---

