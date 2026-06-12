---
title: "Random Lockup, REISUB sometimes works"
date: 2015-02-09
forum: General Help
---

### Post by harrispartyof3 on 2015-02-09
Ive used Ubuntu 12.04 for 4 years with not a single complaint, upgraded to Ubuntu 14.04 last year. I built a new desktop three months ago and after several reinstalls I've been experiencing lockups at seemingly random intervals. Sometimes the computer will run for days with no problem, other times like this morning it will lockup 15 seconds after login. Usually I try REISUB to restart after the lockup but after updating last week that sometimes doesn't work. Originally I thought it was the video driver crashing leaving me with a frozen display since programs would keep running(rhythm box would finish playing current song but stopped after song finished, handbrake would successfully finish ripping the DVD) so I then tried logging into the computer via tty1 but of course the screen would stay frozen on the gui desktop, then I tried ssh but a connection couldn't be made after the computer locked up. Ive heard of a kernel panic screen but have yet to see that. Occasionally everything will freeze besides the cursor but after a few seconds that will freeze too, if that gives anyone any clues. The lockups don't seem to be from any one program, sometimes the computer will lockup in a Steam game, sometimes with just Firefox open, so overheating doesn't seem to be the culprit to me.

---

### Post by oldfred on 2015-02-09
Can you open a terminal & run top to see if some process has run away using all of RAM or CPU?

---

### Post by harrispartyof3 on 2015-02-09
Looking at the output theres a 20%total CPU usage and about 3Gigs of RAM in use. The program using the most resources is firefox, with about 40% of one core(4 core 3.8ghz) and about 10% of my 8Gigs of ram. This seems a bit much for firefox but its always been like this as far as I can remember. A while back I left top running in a terminal where I could see it if the computer crashed, thinking the same thing you are and when it crashed all the numbers seemed within reason, no exessive RAM or CPU usage.

---

### Post by harrispartyof3 on 2015-02-20
Just crashed again, but for some reason ssh connected this time (maybe because I was connected to the computer via remote desktop?) so I ran top in terminal and turns out the process Xorg is using 100% CPU and 2% of 8GB of RAM. So now its obvious that the desktop environment is crashing, anyone know how to find a cause?

---

### Post by oldfred on 2015-02-20
What video card/chip and what video driver?

       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
#What is installed
dkms status

---

### Post by harrispartyof3 on 2015-02-22
"sudo lshw -c display" & "sudo lshw | grep -A 11 display" gave me:
  ```
*-display               
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:88 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fe000000-fe07ffff
```

"lspci | grep VGA" gave me:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)
```

"xwininfo -root" gave me:
```
xwininfo: Window id: 0x1dd (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1920
  Height: 1080
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1920x1080+0+0
```

"dkms status" gave me:
```
bbswitch, 0.7, 3.13.0-24-generic, x86_64: installed
bbswitch, 0.7, 3.13.0-43-generic, x86_64: installed
bbswitch, 0.7, 3.13.0-44-generic, x86_64: installed
bbswitch, 0.7, 3.13.0-45-generic, x86_64: installed
nvidia-340, 340.76, 3.13.0-44-generic, x86_64: installed
nvidia-340, 340.76, 3.13.0-45-generic, x86_64: installed
nvidia-340-uvm, 340.76, 3.13.0-44-generic, x86_64: installed
nvidia-340-uvm, 340.76, 3.13.0-45-generic, x86_64: installed
virtualbox, 4.3.10, 3.13.0-44-generic, x86_64: installed
virtualbox, 4.3.10, 3.13.0-45-generic, x86_64: installed
```

---

### Post by oldfred on 2015-02-23
There are Multiple threads on the 750ti. I was thinking of one of those cards but still use Intel internal chip or an older nVidia for now.

These are the older threads. But bottom line is you need the very newest kernel, support software & nVidia driver, not even sure if 340.xx is new enough. Not sure if 15.04 has all the pieces now or you still need the ppa. Do not download the nVidia driver directly. And make sure you purge any older drivers before installing another.

 Maxwell 750 - kernel 3.15 required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)
 open-source driver support for Maxwell, there's none right now, at least not mainline.  Feb 2014

There are mulitple theads with similar issues and 750ti nVidia card. You can search forum for newer info. I prefer to use google and site:ubuntuforums.org

---

### Post by harrispartyof3 on 2015-04-14
So this was my train of thought last night: if my computer is crashing  from graphics card issues, the obviously it cant crash if there's no gui,  so I started BOINC as per usual, then ran ```
sudo stop  lightdm
``` then ran ```
top
``` in the tty1 console and went to bed. Checked  it this morning and it of course crashed about 1.5 hours after going to  bed, the typical frozen display on the screen and the computer was also no longer doing any processing from BOINC so it had indeed crashed. Now either I'm severely misunderstanding how graphics card drivers  work or the problem, wouldn't graphics drivers not be in use with no  gui since it's just text based and is pretty straight forward for the os  to tell the gpu what to output? or is the problem a part of the os is  looking for something the driver is supposed to give it and therefore  hangs?

And for future reference in a couple weeks when 15.04 comes out, how do I purge graphics drivers and where do I get the nvidia driver if not directly from nvidia? (link to how-to anyone?) and what do you mean about the ppa, which are you referring to?

---

### Post by Scunizi on 2015-04-14
As it was mentioned before... 
If it's the video driver crashing or causing something else in your system to crash, you can update it via XSWAT's ppa .. I also think there is another ppa offering nvidia drivers.

---

### Post by Scunizi on 2015-04-14
Another thought.. if you did the "upgrade" instead of a fresh install it may have caused some issues.  I typically keep my /home on a separate drive or partition.  This makes it super simple to just install fresh instead of upgrading.. I've had issues for years using the upgrade path.  Most likely due to my home built machine but I really don't know.

---

### Post by Bashing-om on 2015-04-14
harrispartyof3; Hello ...

Along with oldfred's advise; Nvidia recommends the 346 driver version:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)  -->
[http://www.nvidia.com/download/driverResults.aspx/83686/en-us](http://www.nvidia.com/download/driverResults.aspx/83686/en-us)
Available in 15.04, else as oldfred advises, from PPA .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
This is a fresh install of 14.04 that I've been using the whole time, so  that rules out the upgrade problem. Ok so I've been using the nomodeset  technique described on  [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)  to work around the booting into a black screen issue I run into about  every other day, but today when I was editing the boot parameters to add  nomodeset the computer hung. now if I'm not mistaking at this point in  the boot process no graphics drivers or even the kernel has been loaded  yet, that is leading me to believe it may be a hardware problem.  Thoughts? The crashing also seems to be more common (more common, not only) during some kind of stress such as games or BOINC processes, maybe its the heat affecting the hardware defect?

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; Whelllppp ...

Ram chips ?
how 'bout running the "mem test" from grub's boot menu ? Let it run for at least 3 passes and see what the ram test out as ?

And for hardware - overheating ? Overheating will cause a shut down of the system for sure. Maybe open the box up and clean/blow it out ( protect the fans that they do not spin up !!) . 

When you are able to boot up once again;
Install a sensors package ?
```

apt-cache show lm-sensors

```

Then also, what does :
```

free -m
top

```
relate to the memory usage ?


And finally, purge all the old Nvidia drivers and install the proprietary 346 driver from PPA ??

[INDENT][INDENT][INDENT]find the cause
[INDENT][INDENT][INDENT][INDENT]fix the issue
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
The case is clean (kind of a clean freak when it comes to computers) and I've been using lm-sensors to monitor the temperatures since the build, cpu never above 45°C and gpu never above 50°C (gpu fan never goes above 55%) so those never overheat, but the case temperature (system temp) is usually bouncing between 42°C and 46°C since I'm using the Lian-Li PC-TU100 case, great lan party case but terrible cooling for a gaming computer... I've played around with the ram before but I will try again, I'll run the mem test tonight and report back in the morning. As for ram use, 6 of 8GB is free. I'll try reinstalling the drivers again but I don't have much confidence since this will be the 5th time.

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; My my;

You have been busy .

A driver conflict as you have installed so many times ?
```

dpkg -l | grep -i nvidia

```
to see what is installed .. and then take action ?

[INDENT][INDENT][INDENT]hey, it's a thought
[/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
This is what "dpkg -l | grep -i nvidia" spit out:```
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-340                                          340.76-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA CUDA runtime library
ii  libcuda1-346                                          346.59-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA CUDA runtime library
rc  nvidia-340                                            340.76-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA binary driver - version 340.76
ii  nvidia-346                                            346.59-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA binary driver - version 346.59
ii  nvidia-modprobe                                       340.24-1~ubuntu14.04.1                                 amd64        utility to load NVIDIA kernel modules and create device nodes
rc  nvidia-opencl-icd-340                                 340.76-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-346                                 346.59-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.47-0ubuntu1~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver

```
I have no idea if that means there's a conflict or not
Also, any particular reason to use the 346 driver instead of the 349? I was just using the  349 but I'm switching back to 346 with the "additional drivers" gui simply because its easy and apparently already installed

---

### Post by harrispartyof3 on 2015-04-21
Yep after changing to 346 when I boot all I get is a black screen, so I added "nomodeset" to the boot parameters and that circumnavigated that issue, we shall see if the crashing still occurs.

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; Hey, hey;

All I see if the 346 driver installed. But will be good to do a bit of cleanup:
Let’s remove all the packages marked as rc ( removed but config files remain)
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Nvidia does advise the 346 version, not to say the 349 would not be better .. or for that matter the 340 .

Strange that you continue to have the requirement to boot with the 'nomodeset' parameter. What results if you purge the proprietary Nvidia driver ? can you then boot up on the default open source driver ?

[INDENT][INDENT]cause and effect
[INDENT][INDENT][INDENT]something not going on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
That did seem to clean it up a tad
```
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-346                                          346.59-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA CUDA runtime library
ii  nvidia-346                                            346.59-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA binary driver - version 346.59
ii  nvidia-modprobe                                       340.24-1~ubuntu14.04.1                                 amd64        utility to load NVIDIA kernel modules and create device nodes
ii  nvidia-opencl-icd-346                                 346.59-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.47-0ubuntu1~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver

```
so the computer did crash, but it did manage to reboot right into the desktop with no black screen, so that was weird. I can boot on the default driver but the resolution is capped at 1280X720 or something, the resolution is the only reason I need/want another driver.

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; Maybe;

Making a bit of progress.

any idea what:
> 
ii  nvidia-modprobe                                       340.24-1~ubuntu14.04.1

is; and why that old version is still hanging about ?
As off the top of my head I do not recall encountering this module before .

[INDENT]sometimes I do wonder
[/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
I have no idea, all of my driver work has been straight copy and paste from tutorials n such so I would have to assume it's remnants of a previous attempt a few weeks ago, I have no idea what any of those are to be honest.
Hopefully if this cant be figured out the next ubuntu release in a few days will fix the issue [-o<
note on the heat causing the crash: it's seeming more likely since the computer will run games for an hour or so then crash, then crash every 10-15 minutes after the initial crash unless I give it a rest and poke around on the forums or similar.

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; Hey;

Time for me then to 'research' and think.

[INDENT][INDENT][INDENT]I will be back
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; WELL ...

That is a fast " I be back " !

This:
[http://manpages.ubuntu.com/manpages/utopic/man1/nvidia-modprobe.1.html](http://manpages.ubuntu.com/manpages/utopic/man1/nvidia-modprobe.1.html)
says:
> 
The  nvidia-modprobe  utility  is  used  by  user-space  NVIDIA  driver
       components to make sure the NVIDIA kernel module is loaded and that the
       NVIDIA character  device  files  are  present.   These  facilities  are
       normally  provided  by Linux distribution configuration systems such as
       udev.   When  possible,  it  is   recommended   to   use   your   Linux
       distribution's native mechanisms for managing kernel module loading and
       device file creation.  This utility is provided as a fallback  to  work
       out-of-the-box in a distribution-independent way.

Should not be needed .

So OK, let's see what the system might do IF that module were removed:
```

apt-get remove -s nvidia-modprobe

``` maybe then the system will do it's job and load the Nvidia driver properly ?

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
Ran that command and so far so good, Ill put some load on the system and see how soon (hopefully never) it'll crash

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; Sorry;

My instruction not complete to your satisfaction.
the -s flag on apt-get is (S)imulate. It does not implement anything, it does say what it would do if - remove - were invoked.
IF it looks as if with the -s flag there will be no adverse effect, then one can do the remove .

But in truth, I bet the 340 version of nvidia-modprobe should not be there at all .. as in my view it sure could cause a version conflict .

If ya want confirmation on what might happen you are encouraged to post that " apt-get remove -s nvidia-modprobe " output for our inspection.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
This is what the output was: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsigsegv2 linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-headers-3.13.0-48 linux-headers-3.13.0-48-generic
  linux-image-3.13.0-44-generic linux-image-extra-3.13.0-44-generic m4
  pcb-common pcb-gtk
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-modprobe
0 upgraded, 0 newly installed, 1 to remove and 112 not upgraded.
After this operation, 76.8 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 382717 files and directories currently installed.)
Removing nvidia-modprobe (340.24-1~ubuntu14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

```

---

### Post by harrispartyof3 on 2015-04-21
I think I figured out what the 340 nvidia-modprobe was doing, after removing it BOINC no longer sees the GPU so apparently that was allowing the program to communicate and use the card.

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; Yepper;

Looks to me like 'nvidia-modprobe' should be removed, and I see no adverse effects in doing so.

Reboot, and see what results.
I do not expect there to be any change as the module assists in building/loading the driver. As the driver is already built and presumably loaded ?? But. maybe in a re-boot situation then the 346 driver will load with no conflict issue to deal with ?

Then maybe time to read the instructions and see what the log file relates ?
```

cat /var/log/Xorg.0.log

```
see if the system is screaming and hollering .

[INDENT][INDENT][INDENT]on the road to recovery
[/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-21
no luck, ran the gputest from geeks3d.com and it crashed after about 10 seconds, but on the bright side I found a good gpu tester!
"cat /var/log/Xorg.0.log" gave me all kinds of stuff, this is what I found pertaining to the gpu:
```
[     6.900] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     6.900] (**) NVIDIA(0):     device LG Electronics 27MP65 (DFP-2) (Using EDID
[     6.900] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[     6.900] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     6.900] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     6.900] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
[     6.900] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[     6.900] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[     6.901] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     6.901] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     6.901] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     6.901] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     6.901] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     6.901] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     6.901] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[     6.901] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     6.901] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     6.901] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[     6.901] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     6.901] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     6.901] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     6.901] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     6.901] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     6.901] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     6.901] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[     6.901] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     6.901] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     6.901] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[     7.135] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     7.135] (**) NVIDIA(0):     device LG Electronics 27MP65 (DFP-2) (Using EDID
[     7.135] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[     7.135] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     7.135] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     7.135] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
[     7.135] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[     7.135] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[     7.135] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     7.135] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     7.135] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     7.135] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     7.135] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     7.135] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     7.135] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[     7.135] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     7.135] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     7.135] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[     7.136] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     7.136] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     7.136] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     7.136] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     7.136] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     7.136] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     7.136] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[     7.136] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     7.136] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     7.136] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[     7.158] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.037] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     8.037] (**) NVIDIA(0):     device LG Electronics 27MP65 (DFP-2) (Using EDID
[     8.037] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[     8.037] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.037] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     8.037] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
[     8.037] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[     8.037] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[     8.037] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.037] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     8.037] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.037] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.037] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     8.037] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.037] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[     8.037] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.037] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.037] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[     8.037] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.037] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     8.037] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.037] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.037] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     8.037] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.037] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[     8.037] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.037] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.037] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[     8.073] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.105] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.439] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     8.439] (**) NVIDIA(0):     device LG Electronics 27MP65 (DFP-2) (Using EDID
[     8.439] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[     8.439] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.439] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     8.439] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
[     8.439] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[     8.439] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[     8.439] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.439] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     8.439] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.439] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.439] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     8.439] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.439] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[     8.439] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.439] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.439] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[     8.439] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.439] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     8.439] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.439] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.440] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     8.440] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[     8.440] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[     8.440] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[     8.440] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     8.440] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[     9.351] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    23.956] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    23.956] (**) NVIDIA(0):     device LG Electronics 27MP65 (DFP-2) (Using EDID
[    23.956] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    23.956] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[    23.956] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    23.956] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
[    23.956] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[    23.956] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[    23.956] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[    23.956] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    23.956] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[    23.956] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    23.956] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    23.956] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[    23.956] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    23.956] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[    23.956] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    23.956] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    23.956] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[    23.956] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    23.956] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[    23.956] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    23.956] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    23.957] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:
[    23.957] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    23.957] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
[    23.957] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    23.957] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".

```

There's more than what I could see in the terminal, so I attached the log file, had to compress it the forums wont let me upload a .log file

---

### Post by Bashing-om on 2015-04-21
harrispartyof3; Hummm ...

Right off the top of my head, I do not know what would cause such a condition. UnGood.
On my "work" station I do not have the ability to deal with a .zip file .
How about this as an alternative:
```

sudo apt-get install pastebinit
cat /var/log/Xorg.0.log | pastebinit

```
The resultant is a URL where that file was downloaded to.
Pass that URL back here and I can read the file then in my browser.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]more than one way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-22
[http://paste.ubuntu.com/10868141/](http://paste.ubuntu.com/10868141/)

Ran the memtest, six passes zero errors

---

### Post by Bashing-om on 2015-04-22
harrispartyof3; Welp ??

I think then for ram we can say it is not an issue;
As the 346 module does build and does load, - per the Xorg.0.log file - I can not see the driver at fault .. hummm 
As you say BOINC requires ' nvidia-modprobe ' did you re-install the module ?
and if so now what version is installed ?
```

dpkg -l | grep -i nvidia

```

Not at all know what to make of this:
> 
[     5.615] (EE) open /dev/fb0: No such file or directory

where my output:
```

sysop@1404mini:~$ ls -al /dev/fb0
crw-rw---- 1 root video 29, 0 Apr 22 12:33 /dev/fb0
sysop@1404mini:~$

```

And do not know if that relates to all the screaming and hollering about:
> 
[     6.298] (WW) NVIDIA(GPU-0): The EDID for LG Electronics 27MP65 (DFP-2) contradicts itself:


Does the Nvidia 346 driver still use the configuration file ' /etc/X11/xorg.conf ' ?
Might take a look and see:
```

cat /etc/X11/xorg.conf

```
if there are any hints here as to what is going on.

Just do not know presently what to advise.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-22
The 340.42 nvidia-modprobe is the current version after the reinstall of nvidia-modprobe.
the fb0 device doesn&#8217;t seem necessary from what I can see on other threads as it seems to be used when not using a desktop environment or for a remote desktop connection, also I would have to believe that it is independent of the contradicting issue since that seems to be the gpu complaining the monitor has a bad list of capable resolutions/refresh rates (assuming that is what it is complaining about from other hints in the log file)

the only xorg configuration files are backups from December 22 of 2014, there appears to be two from that day, not sure why they were created either. One backup is empty (when opening with gedit) but the other contains: ```
Section "Device"
    Identifier "Default Card 1"
    BusID "PCI:1@0:0:0"
EndSection

```

---

### Post by Bashing-om on 2015-04-22
harrispartyof3; Well ..

Not to leave you hanging. I am still 'looking' .
Does not seem reasonable to me that nvidia-modprobe version 340.42 should be installed; as the driver version is 346.

I do think we want to generate a new xorg.conf file.

Might be that we need to install nvidia-settings ?
is it installed ?

[INDENT][INDENT]meanwhile
[INDENT][INDENT][INDENT]back at the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-22
nvidia-settings is already installed, apt-get says its the latest version

---

### Post by Bashing-om on 2015-04-23
harrispartyof3; Hey;

Like a dog with a bone, still worrying over BOINC and nvidia-modprobe - integration into the system.
Confirm please:
the base install of ubuntu  is release 14.04;
Package: boinc-client -> Version: 7.2.42+dfsg-1
Package: boinc-manager ->Version: 7.2.42+dfsg-1
the file ' /etc/default/boinc-client ' does exist

And looking at "nvidia-modprobe" : how did you get version 340.42 on your system ?
Per : [http://packages.ubuntu.com/search?suite=all&arch=any&searchon=names&keywords=nvidia-modprobe](http://packages.ubuntu.com/search?suite=all&arch=any&searchon=names&keywords=nvidia-modprobe)
you should be running version 340.24-1~ubuntu14.04.1 - near as I can tell .

We get over these little things, then I think we should move the current ' /etc/X11/xorg.conf ' files out of the way and generate a new one. Then look at the ' /var/log/Xorg.0.log ' file once more, see if it now shows all clean !

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-23
boinc client and manager are both 7.2.42 and the boinc-client file does exist.
I installed nvidia-modprobe with ```
apt-get install nvidia-modprobe
```
Should I try ubuntu 15.04 and see if the problem disappears?

---

### Post by Bashing-om on 2015-04-23
harrispartyof3; Well ..

As to going the 15.04 route, I would not yet .. as 15.04 only has 9 months support, then it is upgrade time yet again.
release 14.04 is stable and has support 'till 2019

Let's see what the system says about ' nvidia-modprobe ' :
```

apt-cache policy nvidia-modprobe

```
see if we can get an idea of where that version is coming from.
I look at it as a version conflict ( libraries ) could be one cause. And not having a valid xorg.conf file as another reason to fail.

[INDENT]keep in mind
[INDENT][INDENT][INDENT]I once thought I was wrong
[INDENT][INDENT][INDENT]it could happen again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-23
that returned:```
nvidia-modprobe:
  Installed: 340.24-1~ubuntu14.04.1
  Candidate: 340.24-1~ubuntu14.04.1
  Version table:
 *** 340.24-1~ubuntu14.04.1 0
        100 http://us.archive.ubuntu.com/ubuntu/ trusty-backports/multiverse amd64 Packages
        100 /var/lib/dpkg/status


```

---

### Post by Bashing-om on 2015-04-23
harrispartyof3; That is a load off .

confirmed the correct version of nvidia-modprobe is installed.
So. onto step 2 . Move the current  config file and regenerate a new one:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nvidia-xconfig

```
Now restart so that the Nvidia driver can take effect.

What now does the Xorg log file relate ?

[INDENT][INDENT]Got a good feeling about this
[/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-23
There was no xorg.conf to move but a new one was created:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 346.59  (buildmeister@swio-display-x86-rhel47-04)  Tue Mar 31 14:42:07 PDT 2015

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by harrispartyof3 on 2015-04-24
Upgraded to 14.10, ran the gpu test that crashed within 10 seconds yesterday, been running for hours no problems, don't know why it worked but so far so good.

---

### Post by harrispartyof3 on 2015-04-24
BOINC no longer recognizes the gpu though, and nvidia-modprobe is still installed

---

### Post by Bashing-om on 2015-04-24
harrispartyof3; Hey ;

That is now the only problem ?
Might try re-configuring boinc .. or perhaps (RE-)installing ?
```

sudo dpkg-reconfigure boinc-client

```

see what hints we get ?

[INDENT][INDENT]maybe do else
[/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-24
so before the upgrade when the computer crashed REISUB sometimes worked, now it never works. so my thoughts are that I've been experiencing two different kinds of crashes, one that kills the display and another that kills everything. I left a ssh session open on another computer with top running and that lost connection too when the computer crashed so no hints there.. But the crashing doesn't appear to be related to system load anymore, since the gpu test no longer crashes the pc. i reconfigured BOINC via your command. Here's what boincs log says: ```
Fri 24 Apr 2015 10:11:09 PM EDT |  | Starting BOINC client version 7.4.8 for x86_64-pc-linux-gnu
Fri 24 Apr 2015 10:11:09 PM EDT |  | log flags: file_xfer, sched_ops, task
Fri 24 Apr 2015 10:11:09 PM EDT |  | Libraries: libcurl/7.37.1 OpenSSL/1.0.1f zlib/1.2.8 libidn/1.28 librtmp/2.3
Fri 24 Apr 2015 10:11:09 PM EDT |  | Data directory: /var/lib/boinc-client
Fri 24 Apr 2015 10:11:09 PM EDT |  | **CUDA: NVIDIA GPU 0: GeForce GTX 750 Ti (driver version 346.59, CUDA version 7.0, compute capability 5.0, 2047MB, 1752MB available, 1606 GFLOPS peak)**
Fri 24 Apr 2015 10:11:09 PM EDT |  |** App version needs OpenCL but GPU doesn't support it**
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Application uses missing NVIDIA GPU
Fri 24 Apr 2015 10:11:09 PM EDT |  | **App version needs OpenCL but GPU doesn't support it**
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Application uses missing NVIDIA GPU
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677198_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677203_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_874697_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677205_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677204_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677206_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_874666_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677207_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_874680_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677208_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677196_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_874687_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_874696_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_874668_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_677211_0
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1306058_2
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_1_1429700402_1013897_1
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_1_1429700402_1015887_1
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1313182_1
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1313542_1
Fri 24 Apr 2015 10:11:09 PM EDT |  | **App version needs OpenCL but GPU doesn't support it**
Fri 24 Apr 2015 10:11:09 PM EDT | SETI@home | Application uses missing NVIDIA GPU
Fri 24 Apr 2015 10:11:09 PM EDT |  | Host name: MiniPC
Fri 24 Apr 2015 10:11:09 PM EDT |  | Processor: 4 AuthenticAMD AMD A10-7850K Radeon R7, 12 Compute Cores 4C+8G [Family 21 Model 48 Stepping 1]
Fri 24 Apr 2015 10:11:09 PM EDT |  | Processor features: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb xsaveopt hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold vmmcall fsgsbase bmi1
Fri 24 Apr 2015 10:11:09 PM EDT |  | OS: Linux: 3.16.0-34-generic
Fri 24 Apr 2015 10:11:09 PM EDT |  | Memory: 7.66 GB physical, 7.92 GB virtual
Fri 24 Apr 2015 10:11:09 PM EDT |  | Disk: 107.61 GB total, 84.72 GB free
Fri 24 Apr 2015 10:11:09 PM EDT |  | Local time is UTC -4 hours
Fri 24 Apr 2015 10:11:09 PM EDT |  | VirtualBox version: 4.3.18_Ubuntur96516
Fri 24 Apr 2015 10:11:09 PM EDT |  | Config: GUI RPCs allowed from:
Fri 24 Apr 2015 10:11:09 PM EDT | Milkyway@Home | URL http://milkyway.cs.rpi.edu/milkyway/; Computer ID 609996; resource share 100
Fri 24 Apr 2015 10:11:09 PM EDT | World Community Grid | URL http://www.worldcommunitygrid.org/; Computer ID 3211796; resource share 100
Fri 24 Apr 2015 10:11:09 PM EDT | SETI@home | URL http://setiathome.berkeley.edu/; Computer ID 7444362; resource share 100
Fri 24 Apr 2015 10:11:09 PM EDT | World Community Grid | General prefs: from World Community Grid (last modified 31-Dec-1969 19:00:01)
Fri 24 Apr 2015 10:11:09 PM EDT | World Community Grid | Host location: none
Fri 24 Apr 2015 10:11:09 PM EDT | World Community Grid | General prefs: using your defaults
Fri 24 Apr 2015 10:11:09 PM EDT |  | Reading preferences override file
Fri 24 Apr 2015 10:11:09 PM EDT |  | Preferences:
Fri 24 Apr 2015 10:11:09 PM EDT |  | max memory usage when active: 3921.41MB
Fri 24 Apr 2015 10:11:09 PM EDT |  | max memory usage when idle: 5882.12MB
Fri 24 Apr 2015 10:11:09 PM EDT |  | max disk usage: 10.00GB
Fri 24 Apr 2015 10:11:09 PM EDT |  | suspend work if non-BOINC CPU load exceeds 20%
Fri 24 Apr 2015 10:11:09 PM EDT |  | (to change preferences, visit a project web site or select Preferences in the Manager)
Fri 24 Apr 2015 10:11:09 PM EDT |  | gui_rpc_auth.cfg is empty - no GUI RPC password protection
Fri 24 Apr 2015 10:11:09 PM EDT |  | Not using a proxy
Fri 24 Apr 2015 10:11:10 PM EDT |  | Suspending computation - time of day
Fri 24 Apr 2015 10:15:10 PM EDT | SETI@home | Sending scheduler request: To fetch work.
Fri 24 Apr 2015 10:15:10 PM EDT | SETI@home | Requesting new tasks for NVIDIA GPU
Fri 24 Apr 2015 10:15:14 PM EDT | SETI@home | Scheduler request completed: got 0 new tasks
Fri 24 Apr 2015 10:15:19 PM EDT | Milkyway@Home | Sending scheduler request: To fetch work.
Fri 24 Apr 2015 10:15:19 PM EDT | Milkyway@Home | Requesting new tasks for NVIDIA GPU
Fri 24 Apr 2015 10:15:21 PM EDT | World Community Grid | General prefs: from World Community Grid (last modified 31-Dec-1969 19:00:01)
Fri 24 Apr 2015 10:15:21 PM EDT | World Community Grid | Host location: none
Fri 24 Apr 2015 10:15:21 PM EDT | World Community Grid | General prefs: using your defaults
Fri 24 Apr 2015 10:15:21 PM EDT |  | Reading preferences override file
Fri 24 Apr 2015 10:15:21 PM EDT |  | Preferences:
Fri 24 Apr 2015 10:15:21 PM EDT |  | max memory usage when active: 3921.41MB
Fri 24 Apr 2015 10:15:21 PM EDT |  | max memory usage when idle: 5882.12MB
Fri 24 Apr 2015 10:15:21 PM EDT |  | max disk usage: 10.00GB
Fri 24 Apr 2015 10:15:21 PM EDT |  | don't compute while active
Fri 24 Apr 2015 10:15:21 PM EDT |  | don't use GPU while active
Fri 24 Apr 2015 10:15:21 PM EDT |  | suspend work if non-BOINC CPU load exceeds 20%
Fri 24 Apr 2015 10:15:21 PM EDT |  | (to change preferences, visit a project web site or select Preferences in the Manager)
Fri 24 Apr 2015 10:15:22 PM EDT |  | Suspending GPU computation - computer is in use
Fri 24 Apr 2015 10:15:22 PM EDT |  | Suspending network activity - computer is in use
Fri 24 Apr 2015 10:15:39 PM EDT |  | Resuming GPU computation
Fri 24 Apr 2015 10:15:39 PM EDT |  | Resuming network activity
Fri 24 Apr 2015 10:15:39 PM EDT |  | App version needs OpenCL but GPU doesn't support it
Fri 24 Apr 2015 10:15:39 PM EDT |  | App version needs OpenCL but GPU doesn't support it
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | Scheduler request completed: got 17 new tasks
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] App version uses non-existent NVIDIA GPU
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] App version uses non-existent NVIDIA GPU
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084844_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1403516_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084833_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1403515_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084832_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084843_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1403525_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084842_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1309660_1; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1390275_1; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1403522_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084839_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084838_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1403530_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_modfit_fast_15_3s_136_simmodBPL2_2_1429700402_1084837_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1403529_0; aborting
Fri 24 Apr 2015 10:15:39 PM EDT | Milkyway@Home | [error] Missing coprocessor for task de_80_DR8_Rev_8_5_00004_1429700402_1343382_2; aborting
Fri 24 Apr 2015 10:15:51 PM EDT |  | Suspending GPU computation - computer is in use
Fri 24 Apr 2015 10:15:51 PM EDT |  | Suspending network activity - computer is in use
Fri 24 Apr 2015 10:15:58 PM EDT |  | Suspending computation - computer is in use
Fri 24 Apr 2015 10:16:16 PM EDT |  | Resuming GPU computation
Fri 24 Apr 2015 10:16:16 PM EDT |  | Resuming computation
Fri 24 Apr 2015 10:16:16 PM EDT |  | Resuming network activity
Fri 24 Apr 2015 10:16:20 PM EDT |  | Suspending computation - computer is in use
Fri 24 Apr 2015 10:16:20 PM EDT |  | Suspending network activity - computer is in use
Fri 24 Apr 2015 10:16:52 PM EDT | World Community Grid | General prefs: from World Community Grid (last modified 31-Dec-1969 19:00:01)
Fri 24 Apr 2015 10:16:52 PM EDT | World Community Grid | Host location: none
Fri 24 Apr 2015 10:16:52 PM EDT | World Community Grid | General prefs: using your defaults
Fri 24 Apr 2015 10:16:52 PM EDT |  | Reading preferences override file
Fri 24 Apr 2015 10:16:52 PM EDT |  | Preferences:
Fri 24 Apr 2015 10:16:52 PM EDT |  | max memory usage when active: 3921.41MB
Fri 24 Apr 2015 10:16:52 PM EDT |  | max memory usage when idle: 5882.12MB
Fri 24 Apr 2015 10:16:52 PM EDT |  | max disk usage: 10.00GB
Fri 24 Apr 2015 10:16:52 PM EDT |  | don't compute while active
Fri 24 Apr 2015 10:16:52 PM EDT |  | don't use GPU while active
Fri 24 Apr 2015 10:16:52 PM EDT |  | suspend work if non-BOINC CPU load exceeds 20%
Fri 24 Apr 2015 10:16:52 PM EDT |  | (to change preferences, visit a project web site or select Preferences in the Manager)

```
So BOINC is recognizing the gpu, but why does it not see its opencl capability?

---

### Post by Bashing-om on 2015-04-24
harrispartyof3; Humm ...

No error when boinc was re-configured ?
Maybe make sure the proprietary driver loaded :
```

lsmod | grep nvidia
sudo lshw -C display

```
read the log file and see what is built in /var/log/Xorg.0.log

Mind ya I have no experience with boinc .. so I can offer but basic advise.

BUT, BUT ... IF all of boinc is purged, AND nvidia-modprob purged is the system then stable ?
If so at least we know where to point fingers .


[INDENT][INDENT]what I do not know fills a bigger book than
[INDENT][INDENT][INDENT]that I do know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-24
BOINC reconfigured perfectly, purged both, crashed, reinstalled both, crash, and REISUB is working now... so no progress made I suppose

---

### Post by Bashing-om on 2015-04-25
harrispartyof3; YUK !

How about this as a thought. Release 14.10 is soon to be End_Of_Life, how about a clean fresh install of 15.04 ? 15.04 has support for the Nvidia 750ti .

Install 15.04, make sure it is stable on the default install (in the install stage DO NOT check "install 3rd party software");
install the supported proprietary driver;
Still stable; then install boinc.

My thought; When you have done all I can think of to do ->

[INDENT][INDENT][INDENT]install anew - clean and fresh - firm foundation
[/INDENT][/INDENT][/INDENT]

---

### Post by harrispartyof3 on 2015-04-26
Still crashing... Will this ever end?

---

### Post by chaaderf on 2015-04-26
I'm definitely not an expert about linux and I need help in many cases myself. But some time ago I heard of one Ubuntu based system, that was fresh installation, with whole system crashing/freezing when using Firefox. In that case the solution was to reconfigure the packages on the system. So I suspect they've run something like "sudo dpkg -a --configure". But I have no deeper knowledge about this. I hope you'll find a solution!

---

### Post by harrispartyof3 on 2015-06-13
Today I decided to take a gamble and try a different psu, so I swapped out my new 600w psu for a 3 year old 450w psu and so far after 7 hours no problems with crashing. I may have just solved this 6 month old problem....

---

### Post by Bashing-om on 2015-06-13
harrispartyof3; fingers crossed !

Yeah, flakey power supply can and does cause flakey problems.

On more than one occasion I have changed out the power supply just to see if that fixes undermined problems. Though a volt meter will not lie, flakey things do happen. 

[INDENT][INDENT]yo do good work
[/INDENT][/INDENT]

---

