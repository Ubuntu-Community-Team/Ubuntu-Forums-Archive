---
title: "Ubuntu 16.04 with Nvidia GeForce GT 730 - Resolution cannot be set to 2650x1440"
date: 2017-09-18
forum: General Help
---

### Post by dblagbro on 2017-09-18
I have been running Ubuntu for years, dual monitors but I had DVI and VGA before and then I got a new monitor for my birthday about a month ago and have been fighting to get native resolution out of it since.  I had an ATI Radeon 6950 originally, couldn't get it to work so, before I found out 14.04 was not compatible, I tried upgrading to 16.04, then ran into the whole ATI doesn't make a driver for it issue.

Fortunately I had an old GeForce 210 sitting around, used that with the same resolution I had working in 14.04 using ATI card (1920x1080) until the replacement came in:

So I ordered a Nvidia GeForce GT 730 4GB DDR5 card and plugged it in - same problem... I have been through installing the NVIDIA drivers via CLI, using tips such as shutting down lightdm first, installing CUDA, blacklisting intel and Nouveau items in the /etc/modprobe.d/blacklist file...   I have tried using nvidia-current (via apt), nvidia-375, nvidia-341, and others.  When I install 'nvidia-current' it only loads 304 version.

My setup is using DVI-0 at 1920x1080 (that monitor's native resolution) and it won't go above that for my new monitor which supports 2650x1440 and is connected as HDMI-0 according to xrandr.   The Video cards is suppose to support much more than that.

I cannot for the life of me find a way to increase the resolution.

Using xrandr I found links indicating to do "xrandr --newmode" and then "xrandr --addmode" but I get an error when doing the "--addmode" option:


First I have ran:
"cvt 2640 1440" and found my settings for my monitor.

Then I made this a new mode:
"sudo xrandr --newmode "2650x1440_60.00" 320.75  2640 2832 3112 3584  1440 1443 1453 1493 -hsync +vsync"

And that takes ok, but then when I go to add that mode as this:

"sudo xrandr --addmode HDMI-0 2650x1440_60.00"

I get the following:
"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32
"



Output of xrandr after adding the new mode:

"
Screen 0: minimum 8 x 8, current 3840 x 1200, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1080+1920+120 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1280x720      60.00  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   640x480       59.94  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  59.94    50.00    60.05    60.00    50.04  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    59.94    59.93  
  2650x1440_60.00 (0x2bc) 320.750MHz -HSync +VSync
        h: width  2640 start 2832 end 3112 total 3584 skew    0 clock  89.49KHz
        v: height 1440 start 1443 end 1453 total 1493           clock  59.94Hz
"

Any time that I have loaded the later Nvidia drivers (later than 304) I get a blank screen with a flashing cursor.   I can use "ctrl" + "alt" + "F1" to get a terminal and then "sudo apt purge nvidia*" and then reboot (note: just reboot isn't working often, it needs to cold start to work and then reboots fine - not sure if that note helps here) and all is well again.

The Nvidia utility nor the Display manager help me get above 1920x1080 too.

I've been racking my head against this for a few weeks, replaced hardware, tried booting from Live USB (with persistence) to the same situation.

Any guidance would be greatly appreciated - thank you :-)

---

### Post by oldfred on 2017-09-18
It sounds like you have installed too many video drivers.

With drivers you have to totally purge old drivers before attempting to install a newer one.
And you do not install from nVidia directly but from Ubuntu repository or if very new card from ppa to get very newer nVidia driver.

If you still have AMD driver I would purge that, but have no idea how.

       Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers
[/URL]
 We typically do not suggest running the .run files from nVidia.
As then you have to rerun the dkms on every kernel update.
Where versions of nVidia installed from repository just work.
And if you have a very new nVidia card, and need a driver newer than in default repository, there is a ppa with all the new versions pre-configured. 
   #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
    
      
 [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
   If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  
    


[URL="http://www.geforce.com/drivers"]
[/URL]

---

### Post by mastablasta on 2017-09-19
> **dblagbro said:**
> I have been running Ubuntu for years, dual monitors but I had DVI and VGA before and then I got a new monitor for my birthday about a month ago and have been fighting to get native resolution out of it since.  I had an ATI Radeon 6950 originally, couldn't get it to work so, before I found out 14.04 was not compatible, I tried upgrading to 16.04, then ran into the whole ATI doesn't make a driver for it issue.


it's only true that AMD does not make catalyst drivers for the card anymore, however they do help with opensource Radeon driver that replaces is and it improved a lot. should be bale to handle resolution change as well, though it might need a switch to be used.

> 
Any time that I have loaded the later Nvidia drivers (later than 304) I get a blank screen with a flashing cursor.   I can use "ctrl" + "alt" + "F1" to get a terminal and then "sudo apt purge nvidia*" and then reboot (note: just reboot isn't working often, it needs to cold start to work and then reboots fine - not sure if that note helps here) and all is well again.


had a same issue with a 2GB. i think i will follow this closely. i posted to nvidia forums about it,  i also asked for help their support staff. i couldn't get anywhere isnce i couldn't run their debug software. it never occured to me i could drop to CLI from blinking cursor. in the end i returned the card back to the shop after 7 frustrating days. just like  you i couldn't get native resolution (1680 x1650). using nouveau i got a stretched 1280 x 768. so i know the card worked. but as soon as i loaded up the drivers (and i tried many of them) i was at blinking cursor.

later on i ordered the same card for the old windows XP machine. and one thing that is curious is that the card always boots to DVI output. no matter what monitor is set as primary or even if i turn off th eother monitor. you see i have TV connected on DVI there, while the PC monitor is on VGA. yet on reboot (or boot) it is always black and turned off first. only when system loads monitor will turn on from standby mode. 

some further experiments showed that on system start the picture is running on TV (DVI-->HDMI cable). booting linux live on that machine simply ignores the monitor and just loads the screen on TV (even if it's off):

i wonder... if you have the chance - can you try plugging monitor to other outputs? does picture show anywhere else?

finally if you are realyl stuck you should contact nvidia support , just make sure you run their diagnostic software (instructions on their website) and give them the output they need it. 

finally if oyu manage to solve it let us know. i would love to replace the aging ATI 9600 256 MB with a 2GB nvidia GT 730 on that pc. no more freezes and some old games would work...

---

### Post by dblagbro on 2017-09-19
Dear oldfred - thank you for your attention.     I have purged old drivers as I moved to new ones, often going back to the default intel ones, then going back to "sudo apt install nvidia-current" for best performance (1920x1080 at best though) so I don't think I had too many drivers... and your guidance seems to have shown that with the following - let me know if this looks wrong, but I believe I only have 'nvidia-current' which loads as 304 for my card:

> dblagbro@Workstation:~$ sudo dpkg -l | grep -i nvidia[sudo] password for dblagbro: 
ii  libcuda1-304                                          304.135-0ubuntu0.16.04.1                                amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                            304.135-0ubuntu0.16.04.1                                amd64        NVIDIA legacy binary driver - version 304.135
ii  nvidia-current                                        304.135-0ubuntu0.16.04.1                                amd64        Transitional package for nvidia-current
ii  nvidia-opencl-icd-304                                 304.135-0ubuntu0.16.04.1                                amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       375.26-0ubuntu1                                         amd64        Tool for configuring the NVIDIA graphics driver
dblagbro@Workstation:~$ 
dblagbro@Workstation:~$ 
dblagbro@Workstation:~$ sudo dkms status
nvidia-304, 304.135, 4.4.0-96-generic, x86_64: installed
dblagbro@Workstation:~$ 
dblagbro@Workstation:~$ 
dblagbro@Workstation:~$ 
dblagbro@Workstation:~$ sudo lsmod | grep nvidia
[sudo] password for dblagbro: 
nvidia              11407360  79
drm                   364544  2 nvidia
dblagbro@Workstation:~$ 





Now per Nvidia's site, I should be able to run 384.69 I think... I selected my card (GT 730 with Linux x64 - using this tool: [http://www.nvidia.com/download/driverResults.aspx/123103/en-us](http://www.nvidia.com/download/driverResults.aspx/123103/en-us) ) and got this:

> [COLOR=#000000][FONT=&quot][h=2]LINUX X64 (AMD64/EM64T) DISPLAY DRIVER[/h] 
[/FONT][/COLOR]
[TABLE="width: 100%"]
[TR]
[TD="class: contentsummaryleft"]Version:[/TD]
[TD="class: contentsummaryright, colspan: 2"]384.69[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]Release Date:[/TD]
[TD="class: contentsummaryright, colspan: 2"]2017.8.22[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]Operating System:[/TD]
[TD="class: contentsummaryright, colspan: 2"]Linux 64-bit[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]Language:[/TD]
[TD="class: contentsummaryright, colspan: 2"]English (US)[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]File Size:[/TD]
[TD="class: contentsummaryright, colspan: 2"]77.06 MB[/TD]
[/TR]
[/TABLE]


However that didn't work... I did some digging about having to purge nvidia* first, and then stop lightdm, and I even had to blacklist some items - I followed these instructions:  (first answer) [https://askubuntu.com/questions/481414/install-nvidia-driver-instead-of-nouveau](https://askubuntu.com/questions/481414/install-nvidia-driver-instead-of-nouveau)


After that failed for me, and I re-purged all Nvidia and ran the NVIDIA*.run file with the '-uninstall' option, I also tried using the 3rd party option found here with no success - same blank screen with the flashing cursor but I could get text login with the CTRL + ALT + F1 option:   [https://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen](https://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen)


.... so that above is where I've been until now.   I am going to try this suggestion you provided but it seems mostly the same as my previous steps:  [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
The one thing that is new in that link is the PRIMEprofile portion... fingers crossed but wanted to share the above info from those commands I ran in case that highlights anything to you that I missed.     I do see somethings in there about creating an Xorg.conf file but with 16.04 I think that is no longer relevant??  Not sure, graphic problems are new to me as I've mostly used Linux as CLI only on servers for work.   ...they sure seem to be a new challenge! :-)

Also going to try out those "ubuntu-drivers" steps...  wish me luck and thanks again!

---

### Post by oldfred on 2017-09-19
sudo dkms status shows the 304 driver which is now a legacy driver for much older cards.
I am sure you need a newer driver, not sure if 340 or even very newest for your card. 

I think the nVidia card I am using open source on became legacy with 340.

---

### Post by dblagbro on 2017-09-19
So I am back in text only mode.    I installed the "reccomended" nvidia-375 using the autoinstall option "sudo ubuntu-drivers autoinstall" command.

This time I've noticed a dmesg error ending with:
"
NVRM: RmIOnitAdapter failed! (0x30:0xfff:654)
NVRM: rm_init_adapter failed for device bearing minor number 0
"

Some googling of that lead me to working on getting a FreeDOS disk ready and planning on trying a BIOS update for the Dell XPS 8700 from A07 to A10...  but "diskpart" being so slow on my working PC, that's still formatting and that is also a vague guess that may not fix it.

...figured I'd check back in to see if that info about the NVRM error indicates anything specific I have missed again.

Continued THANKS!

---

### Post by dblagbro on 2017-09-19
Update:  No Joy on the BIOS upgrade.   Still getting the NVRM: RmInitAdapter failed! error.

I purged the nvidia* drivers again, and went back to intel, and still having issues booting.    However, where I was working after doing that I now go through a login screen cycling.  Enter password, it's right, but it returns to the login prompt.   Repeats....  I can drop to CTRL + ALT + F1 and get into CLI.     So to recap, I was previously only getting blank screen on my CTRL + ALT F7, now that terminal lets me login but keeps going back to the password prompt.    

Question:   with the above instructions I also removed bumblebee, primus, and bbbswitch-dkms - might I have to put those back on manually?     I had not remove those, just purged nvidia* previously.

...I also now keep getting to a "ststemctl reboot" and "Emergency Shell" prompts....  this is also new on this system.

---

### Post by dblagbro on 2017-09-19
I'm noticing the following in the dmesg log when it boots to the GUI login screen (in the "Emergency Mode" it is not giving me the GUI login screen).    I know "nouveau" was one of the things I tried blacklisting when following some other instructions previously; guessing that may be the next thing I try but want to see if this triggered any suggestions to do something else first:

"
nouveau 0000:01:00.0: disk: ERROR 4 [INVALID_VALUE] 84 [] chid 0 mthd 0c28 data 0000a5ef
"

---

### Post by dblagbro on 2017-09-19
I'm back to where I had started...  I still have to use "nvidia-current" drivers and they won't load any nvidia-xxx where xxx is newer than 304....


dblagbro@Workstation:~$ 
dblagbro@Workstation:~$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00001287sv000010DEsd00000990bc03sc00i00
model    : GK208 [GeForce GT 730]
driver   : nvidia-375 - distro non-free recommended
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin


== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


dblagbro@Workstation:~$ sudo dpkg -l | grep -i nvidia
ii  libcuda1-304                                          304.135-0ubuntu0.16.04.1                                amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                            304.135-0ubuntu0.16.04.1                                amd64        NVIDIA legacy binary driver - version 304.135
ii  nvidia-current                                        304.135-0ubuntu0.16.04.1                                amd64        Transitional package for nvidia-current
ii  nvidia-opencl-icd-304                                 304.135-0ubuntu0.16.04.1                                amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       375.26-0ubuntu1                                         amd64        Tool for configuring the NVIDIA graphics driver
dblagbro@Workstation:~$

---

### Post by oldfred on 2017-09-19
If you have done the full purge, I do not understand why you still get 304? That should be gone.

---

### Post by dblagbro on 2017-09-19
So I've opened a case with Nvidia support....  their first level helpdesk couldn't fix it so waiting on additional support.

Thanks - will inform what I find out!

---

### Post by mc4man on 2017-09-19
> **oldfred said:**
> If you have done the full purge, I do not understand why you still get 304? That should be gone.

If he keeps installing nvidia-current then that's what he'll get.
>  I still have to use "nvidia-current" drivers ... 

---

### Post by oldfred on 2017-09-19
Either not GT730 or parser suggesting nVidia driver is wrong.
Is it really 7300? Which is an old card.

This says all the current new drivers 375 thru 384 should work for GT730. Newest probably only available in the ppa.
[https://www.geforce.com/drivers](https://www.geforce.com/drivers) 

My 620 says this It does show 304 as an option as well as many others:

```
sudo ubuntu-drivers devices
model    : GF108 [GeForce GT 620]
vendor   : NVIDIA Corporation
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-340 - third-party free
driver   : [COLOR=#ff0000]nvidia-384 - third-party free recommended[/COLOR]

```

---

### Post by mastablasta on 2017-09-20
> **oldfred said:**
> 
This says all the current new drivers 375 thru 384 should work for GT730. Newest probably only available in the ppa.

exactly. but they don't for some reason. i never could figure out the reason as i had to return the card before "return period" expired. and i never could get to command line, to run nvidia diagnostic program.

i thought i made some mess because before radeon drivers were loading (i was trying to replace the old ATI card).

edit: just went to search for the old post and inddeed found same error message.

```
Mar 23 17:41:21 tatie-desktop kernel: [   31.005799] NVRM: RmInitAdapter failed! (0x26:0x65:1292)
 Mar 23 17:41:21 tatie-desktop kernel: [   31.005814] NVRM: rm_init_adapter failed for device bearing minor number 0
 Mar 23 17:41:21 tatie-desktop kernel: [   31.005847] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5
```

My nvidia forums post: [https://devtalk.nvidia.com/default/topic/820757/linux/can-not-install-gt-730-on-kubuntu-14-04/](https://devtalk.nvidia.com/default/topic/820757/linux/can-not-install-gt-730-on-kubuntu-14-04/)
note how it apparently works/worked with no issues on OpenSuse (last post)

and here were my attempts at BIOS (it was updated to have the latest one and i tried some settings as i wrongly thought the voltage could be an issue): [https://paste.ubuntu.com/25577957/](https://paste.ubuntu.com/25577957/)

Nvidia support was very helpfull and they tried their best, but we could not resolve the issue.

---

### Post by dblagbro on 2017-09-25
... just to keep this updated, been working with Nvidia support who is unsure what's going on too.      They agree with you oldfred....

Also have same issue when booting from Live USB with 16.04 with persistence to rule out it's not something with my OS...  :-(   ... hoping to find fix as I am still engaged with Nvidia support.

---

### Post by mastablasta on 2017-09-28
subscribed. i hope they figure it out. none of later drivers work, while nouveau works (somewhat).

if this is resolved i could do a computer upgrade + i plan to add Linux on the Windows XP PC which now has this card, since more and more apps are now losing winxp support or their support is pathcy. i could then use WinXP for gaming and Linux for other stuff.

---

