---
title: "After resume, laptop screen blank, monitor screen on."
date: 2023-06-14
forum: General Help
---

### Post by Bucky Ball on 2023-06-14
Hi all. I have an ASUS Tuf Gaming A15 laptop running xubuntu-core 20.04. Video card is an NVIDIA GeForce GTX 1650 Ti. I have a Samsung monitor connected via HDMI, dual-monitor style.

As background to how I got here, here's the **original issue**: Occasionally, I open the laptop to resume and both the laptop and monitor screens are black with a blinking cursor in the top left corner.

I attempted to fix this by running this command

```
sudo ubuntu-drivers autoinstall
```

From here

[https://askubuntu.com/questions/1251005/ubuntu-20-04-boots-to-black-screen-with-flashing-cursor](https://askubuntu.com/questions/1251005/ubuntu-20-04-boots-to-black-screen-with-flashing-cursor)

Dumb. Rebooted and that screwed things royally! (I'd had an endoscopy 12 hours earlier so probably should have been in bed rather than doing this!)

Could get to grub, but that's it. I chose the recovery kernel from there, got rid of all nvidia drivers and eventually back to square one-ish by installing the nvidia proprietary 530 driver from Software and Updates. Except now, I have a new problem. 

To the **current issue**: When I open the laptop lid to resume, the monitor comes alive, works as expected, but the laptop screen stays completely black. No flashing cursor. Blackness. As I'm pretty sure I was running the nvidia driver 530 before the chaos, I'm presuming the graphics driver is not the cause of the current issue, but some change made by the autoinstall of ubuntu-drivers is.  

When I open up ARANDR and open an old configuration there which is for both screens, both screens come alive, so no, this is not a hardware problem with the laptop screen. When it's working, everything's working as expected.  

No idea what's happening and hoping someone here might. Any help greatly appreciated. Any further info required, don't hesitate to ask.

PS: For what it's worth, I tried adding 'nomodeset' in /etc/default/grub at the appropriate line, but no dice. That got me two black screens.

---

### Post by MAFoElffen on 2023-06-14
I read your linked AskUbuntu link.
 
Please do this:
```

uname -r
lsb_release -a | grep 'Description'
grep 'model name' /proc/cpuinfo
echo $XDG_SESSION_TYPE

```
And post the output within CODE Tags.

I see that with the AMD Ryzen CPU that your laptop has, that others that have the same are having a problem waking from suspend, until they tried newer kernels (5.19 and 6.0)...

Maybe trying to run 22.04.2 from a LiveUSB and shut the lid / open it, to test if it's newer kernel corrects that(?) That would be an easy test, without having to actually change anything on your current installation (yet).

---

### Post by Bucky Ball on 2023-06-14
Thanks for the response.

```
5.7.0-050700-lowlatency
Description:	Ubuntu 20.04.6 LTS

model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics
model name	: AMD Ryzen 5 4600H with Radeon Graphics

x11
```

I'll presume that makes sense.

> I see that with the AMD Ryzen CPU that your laptop has, that others that have the same are having a problem waking from suspend, until they tried newer kernels (5.19 and 6.0)...

Maybe trying to run 22.04.2 from a LiveUSB and shut the lid / open it, to test if it's newer kernel corrects that(?) That would be an easy test, without having to actually change anything on your current installation (yet). 

To remind, I didn't have this current problem - ever - previous to trying to fix the original problem (the very occasional blinking cursor on both screens on resume), when I run the old config for dual-screens from ARANDR, the setup works faultlessly on this kernel, so not sure a newer kernel is the way to go.

As for trying 22.04 to fix the ORIGINAL issue rather than the current one, that was only happening ... 5-10% of the time? So 90-95% of the time, the machine was working faultlessly on the kernel I'm using now. For all I know, that particular issue could indeed be fixed! At least the monitor screen works on resume every time. There's a positive!

Maybe I could add the config from ARANDR somewhere so that's used when resuming rather than whatever is being used now (which fails the laptop screen). Is there somewhere we can see the error message it's throwing when the screen fails? (A message comes up on the laptop screen when resuming, but so fast I can't read.) I'll have a further dig around tomorrow. 

At this point, going back to square one and where I was prior to 'ubuntu-drivers autoinstall' would be just dandy. To that end, I tried and didn't get far reversing that command. I tried answer 1 at the following link which removed all nvidia drivers so I had to boot to recovery and install nvidia driver 530 from 'Additional Drivers'. Which got me to where I am now.

[https://askubuntu.com/questions/1410298/can-you-reverse-ubuntu-drivers-autoinstall](https://askubuntu.com/questions/1410298/can-you-reverse-ubuntu-drivers-autoinstall)

The ideal scenario would be to reverse all changes made by the ubuntu-drivers command, but I have a feeling that is pretty much impossible.

---

### Post by MAFoElffen on 2023-06-14
Bucky-- I remember you, and I know you were past staff, as I was. I don't remember you remember your posts from 12 years ago as being as cynical. Both of us are older now. I am sorry that you have been having troubles.

I meant what I said (plainly), that other people with that specific CPU have and nVidia seem to be having 'problems waking from suspend' with older kernels. I put nothing more into that. I didn't see where they were having problems with just one display of two after a suspend. I know you have been around longer than I, and mostly you share your knowledge in hardware and networking. I have always respected and enjoy your posts.

I know you know that waking problems are usually a combination with the processor, the kernel and the graphics driver... sometimes the graphics engine.

My workstation is AMD CPU and nVidia. Using 'ubuntu-drivers autoinstall' usually breaks my system. It should work, but maybe my system is just picky. So I have to remove and purge each, then try each to see which works best. Just saying, I feel your pain. LOL

How did you end up with a low latency Kernel series? Wasn't the low-latency kernel originally used for embedded systems, and had scheduling differences in the 'CONFIG_PREEMPT'?
> 
Overall, unless it does not meet an exact preemption specification, the low-latency kernel fits well low-jitter, low-latency, soft &#8220;real-time&#8221; workloads. Dedicated devices (e.g.,life-supporting medical equipment) with catastrophic consequences in case of failure are instead better suited to a fully-preemptive solution than a balanced one.

That description does not read as being for machines that go into a suspend state. Just an observation. 

I see on the nVidia Forum, where some users are having troubles with low-latency kernels and nVidia drivers, where when they are having problems, that they are having to completely purge the old drivers, before reinstalling them again... (The same versions.)

Logically, low latency kernels are put into a hyperactive state to make them more responsive, sort of like the Kernel asking the CPU "are you done yet" much more often than a normal kernel. I hear from many sources that low-latency kernels should not have the nVidia driver low-latency left on, and vsync left on, or else you get screen tearing... 

But also that with low-latency kernels, that the CPU scaling driver should be set to "performance"... which does affect how far it goes into a sleep state, which also affects how it wakes up from suspend. Lets rule a few things out first. We can check the power profile and it's settings via
```

grep . /sys/devices/system/cpu/cpufreq/policy0/scaling_driver
grep . /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
powerprofilesctl get
grep . /var/lib/power-profiles-daemon/state.ini

```
If in the last command, if returns something other than 
```

Driver=<the actual scaling_driver or placeholder>
Profile=performance

```
Then do 
```

sudo powerprofilesctl set performance

```
Then check the state.ini file again to make sure it made the change in that setting...

Put it into a suspend state and test what it does when it wakes... <crossing fingers>

---

### Post by Bucky Ball on 2023-06-14
Hi there. Yep, remember you too. Sorry I came across as cynical. Far from intended. I'm bi-polar and a bit autistic, so context is sometimes a bit lost. Apologies again. I do appreciate your help. And no, I wasn't aware that waking problems are usually a combination with the processor, the kernel and the graphics driver. I was never at the level many of the other staff were technically and totally rusty on all that stuff now! I set the machine up just right long ago and just open the lid and use it now! 

As for the low-latency kernel, I'm a musician/musicologist and was using this machine for audio production running Bitwig as a DAW and other audio bits and pieces (and a bit of vid production running Blender). I was intending to produce music wholly and solely on Ubuntu, but gave up and now use Windows for all that stuff. Just too much stuff I couldn't do/use on Linux without some major hoop jumping. And even then, not guarantee for 100% of things. But I still have that kernel and works fine. But I hear what you're saying about the low-latency kernel and suspend, so ...

To my current issue and your instructions. Here I go ...

```
grep . /sys/devices/system/cpu/cpufreq/policy0/scaling_driver
acpi-cpufreq

grep . /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance schedutil 

powerprofilesctl get
powerprofilesctl: command not found

grep . /var/lib/power-profiles-daemon/state.ini
grep: /var/lib/power-profiles-daemon/state.ini: No such file or directory

sudo powerprofilesctl set performance
sudo: powerprofilesctl: command not found
```

As you can see, no joy there. I didn't try suspend after that as I imagine nothing's changed as the last command wasn't recognised. Note that I am using Xubuntu-core, so perhaps that has something to do with why those commands at the end are going nowhere. (Update: Just checked; I have no 'power' anything in /var/lib, so that explains that.)

**Update**: May or may not be pertinent, but found another way to activate the laptop screen. I went to 'Display' and the laptop screen was there, available, but simply disabled. I enable, it springs to life, all normal.

So, bottom line, when I close the lid, it disables the laptop screen. When I open the lid, the monitor screen is enabled, but laptop screen remains disabled and I have to enable manually (using ARANDR config or Display), but when I do, fine. As mentioned, attached monitor screen working A-OK throughout current issue. Thankfully! ;) My original issue appears fixed (two black screens with blinking cursors), but now, new issue seemingly created by running that 'ubuntu-drivers autoinstall' command.

---

### Post by MAFoElffen on 2023-06-15
I did not realize that Xubutu had an Xubuntu-Core... Hmmm. I just searched through the Repo's and didn't realize that power-profile-daemon didn't hit the repo's until Precise. The method for changing that changed at 18.04 and SystemD.

Wait a few while I dig into this and see what was what with Power Profiles for Focal. We both can see that it is in the sysfs.

Dead-end... Spinning up an Xubuntu 20.04.6 VM and seeing for myself. In the Doc's there was something about the ondemand.service affecting power in Focal, but I need to check for myself. If not, I can always come up with a short startup script to change that at login...

Be right back after I explore that for you.

---

### Post by Bucky Ball on 2023-06-15
Cheers. Thanks a heap for your help. I've put in an hour or two at this end, tried a few things to no avail. I did discover something. The ubuntu-drivers autoinstall appeared to screw Cuda, so I have reinstalled that. Everything working, all checks out, but no difference to the resume issue. 

Yep, have been using xubuntu-core for years now. (Since 16.04? I think. Long time so not positive when I discovered it.)

**Update**: this may or may not be of some assistance. This is the script ARANDR is using to fix it. 

```
xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off
```

eDP is the laptop screen, but ya prob knew that. :) HDMI = Samsung monitor. They are positioned monitor on my left, laptop on my right with monitor as the primary screen.

---

### Post by MAFoElffen on 2023-06-15
Okay... Sort of convoluted. Found this by Doug S: [https://askubuntu.com/questions/1322492/how-to-set-as-default-performance-mode-on-ubuntu-20-04-instead-of-powersave](https://askubuntu.com/questions/1322492/how-to-set-as-default-performance-mode-on-ubuntu-20-04-instead-of-powersave)

Doug S'es Option #1 didn't work for me... But maybe because it was running in a VM.

I would opt for Option #2. That seemed to work:
```

sudo systemctl stop ondemand.service
sudo systemctl disable ondemand.service
sudo nano /etc/default/grub

```
Add ''cpufreq.default_governor=performance" to the GRUB_CMDLINE_LINUX_DEFAULT line like this
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash cpufreq.default_governor=performance"

```
Save and exit, then do
```

sudo update-grub

```
Reboot and check 
```

grep . /sys/devices/system/cpu/cpufreq/policy0/scaling_driver

```

---

### Post by Bucky Ball on 2023-06-15
Thanks for that. From memory, same result as last time. Think that was same command. 

```
grep . /sys/devices/system/cpu/cpufreq/policy0/scaling_driver
acpi-cpufreq
```

... there's a / missing from your last code tag above. :) Incidentally, didn't have machine in 'performance' previously. I avoid as uses more power. Graphics card set to 'demand' in Nvidia x server settings.

As the workaround at this point, although tedious, is as simple as opening arandr and running the script or opening Display and enabling the screen and everything works dandy, I'm wondering how simple the actual solution is. Can't be that involved. Could it? 

Is there anywhere I can see, either online or on my machine, what the 'ubuntu-drivers autoinstall' actually did/changed/uninstalled/installed? Might be able to figure out from there what's blocking this screen resuming.

---

### Post by MAFoElffen on 2023-06-15
Thanks. I just edited that. 

Well dang. Nothing I have found seems to work for that... I'm still playing with this VM to see if anything else works. 

I need to get some sleep. Wife already went to bed.

---

### Post by Bucky Ball on 2023-06-15
Cheers, MAFoElffen. Really appreciate it. I just edited my last post. I'm figuring this might be straightforward and who knows, maybe I'll stumble over a solution later tonight. Welcome Sandman ...

Update: I'm wondering if the bash script in maddy6's post by Lawrence Ong here ...

[https://forums.debian.net/viewtopic.php?p=678688#p678688](https://forums.debian.net/viewtopic.php?p=678688#p678688)

... might be of use, with a few tweaks, not that I'd have much of a clue about how to perform those tweaks. From the script, I'm figuring that this line 

```
sudo -u <user> env DISPLAY=:0 /usr/bin/xrandr --auto
```

... would be the one to tweak. It needs to point to my arandr script that starts both screens in the correct configuration. I'm guessing.

I'll keep digging.

**Further Update:** Whilst pondering breakfast, I had a thought. Below is the bash script from the page I link to above which they advise to put in /etc/pm/sleep.d/.

```
#!/bin/bash
case "$1" in
thaw|resume)
sleep 5
sudo -u <user> env DISPLAY=:0 /usr/bin/xrandr --auto
;;
*)
;;
esac
```

Here is the bash script I already have on my machine that ARANDR has conveniently written to get the two screens working just right.

```
#!/bin/sh
xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off
```

Wondering if it might be as simple as tweaking the script I found online by adding the line from my ARANDR bash script, like so (and replacing <user> with my username).

```
#!/bin/bash
case "$1" in
thaw|resume)
sleep 5
sudo -u <buckyball> env DISPLAY=:0 /usr/bin/xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off
;;
*)
;;
esac
```

[s]Or, even simpler, copying the ARANDR bash script directly to /etc/pm/sleep.d/ and calling it something like '20_ASUS-Screens'.[/s] NOTE: This didn't work. Maybe I needed a restart. 

Feasible? Or am I barking at the moon? Wouldn't be the first time and won't be the last! ;) Basically, looking for a way to override whatever is keeping that screen disabled on resume. Seeing as I don't know what that is and have failed to discover where I might find out, this may be a clunky workaround.

---

### Post by Bucky Ball on 2023-06-17
Another day, another failure! 

I tried all of the above last night. Created a file in /etc/pm/sleep.d called '20_asus-screen' and tried it with various scripts. No dice. 

So this is where I'm at with it currently. On the strength of the last answer here 

[https://askubuntu.com/questions/1252243/ubuntu-20-04-cannot-resume-from-suspension](https://askubuntu.com/questions/1252243/ubuntu-20-04-cannot-resume-from-suspension)

and something I think you mentioned earlier, I have installed the 5.8 kernel, booted on that and ... no difference whatsoever. But it did throw a new error at boot which I didn't quite catch all of, but did catch this bit:

> Failed to add display topology.

And that was that.

---

### Post by MAFoElffen on 2023-06-17
That is 'genius' to create a script there!

Shouldn't that script have rather been like this:
```

#!/bin/bash
case "$1" in
thaw|resume)
sleep 5
sudo -u buckyball env DISPLAY=:0 /usr/bin/xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off
;;
*)
;;
esac

```
I, myself, when giving someone an example of what to try will use the left ad right arrows to annotate code, for a placeholder to where things should be substituted...

For example
```

chown <username>:<usergoup> ./sample.tx 
# becomes
chown mafoelffen:mafoelffen ./sample.txt

```

---

### Post by #&amp;thj^% on 2023-06-17
> **Bucky Ball said:**
> Another day, another failure! 

I tried all of the above last night. Created a file in /etc/pm/sleep.d called '20_asus-screen' and tried it with various scripts. No dice. 


You know I was thinking about you a few nights ago, and here you are now. Good to see you Bucky Ball.
Mine works, but I'm running all "Devel" sources ATM
```
 cat /etc/pm/sleep.d/00_screen
#!/bin/bash
case "$1" in
thaw|resume)
sleep 5
sudo -u me env DISPLAY=:0 /usr/bin/xrandr --auto
;;
*)
;;
esac

```
And basically the same card:
```
inxi -GS
System:
  Host: voyager-zfs Kernel: 6.2.0-20-generic arch: x86_64 bits: 64
    Desktop: Xfce v: 4.18.1 Distro: Ubuntu 23.04 (Lunar Lobster)
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 530.41.03
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 22.1.8 driver: X:
    loaded: nvidia unloaded: fbdev,modesetting,nouveau,vesa
    gpu: nvidia,nvidia-nvswitch resolution: 1920x1080~120Hz
  API: OpenGL v: 4.6.0 NVIDIA 530.41.03 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2

```
Both monitors come to life when prompted by Mouse or keyboard.
And of course I'm not suggesting Devel sources.
This is my Wife's Desktop so it is a full blown XFCE4 session.

---

### Post by Bucky Ball on 2023-06-17
Thanks to you both for the input. :)

> **MAFoElffen said:**
> 
Shouldn't that script have rather been like this:
```

#!/bin/bash
case "$1" in
thaw|resume)
sleep 5
sudo -u buckyball env DISPLAY=:0 /usr/bin/xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off
;;
*)
;;
esac

```
I, myself, when giving someone an example of what to try will use the left ad right arrows to annotate code, for a placeholder to where things should be substituted...

For example
```

chown <username>:<usergoup> ./sample.tx 
# becomes
chown mafoelffen:mafoelffen ./sample.txt

```

Doh! Of course. Bit outta da loop. Got it now.

I tried the revised script and ... no diff.
___

> **1fallen said:**
> You know I was thinking about you a few nights ago, and here you are now. Good to see you Bucky Ball.
Mine works, but I'm running all "Devel" sources ATM
Code:

```
#!/bin/bash
case "$1" in
thaw|resume)
sleep 5
sudo -u me env DISPLAY=:0 /usr/bin/xrandr --auto
;;
*)
;;
esac
```

Hi 1fallen! Yes, long time, and ain't that the way?!? Here I am! And happy to have a couple of familiar names and friendly users helping me. Glad you're both still around. Massive contribution to the community there. ;)

I tried your version of the script in the file I created, also now named /etc/pm/sleep.d/00_screen, and ... no diff.
___

(NB: For all attempts, I change the username to my own.) 

After entering each script and saving, I'm doing a chmod ...

```
sudo chmod +x 00_screen
```

... closing the lid and reopening, but maybe I should be rebooting the machine then trying. 
___

Doing the 'ubuntu-driver autoinstall' was dumb (they told me not to make any important decisions for 24 hrs after the endoscopy!) and definitely threw the spanner in the works that's caused this. If only I could find that spanner!

---

### Post by Bucky Ball on 2023-06-18
Further info. Out of curiousity, thought I'd have a look at the output on my machine of the command 'inxi -GS' that you used, 1fallen. For what it's worth and in case it is of any help to anyone, the following is the output of 'inxi -GS' with the screen black after resume.

```
System:
  Host: Tuffy Kernel: 5.8.0-050800-lowlatency x86_64 bits: 64 
  Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Graphics:
  Device-1: NVIDIA driver: nvidia v: 530.41.03 
  Device-2: AMD Renoir driver: amdgpu v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: amdgpu,ati,nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: 
  renderer: AMD RENOIR (DRM 3.38.0 5.8.0-050800-lowlatency LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6 
```

... and below is the inxi output after running the arandr script that sets the displays just right (so both screens are on).

```
System:
  Host: Tuffy Kernel: 5.8.0-050800-lowlatency x86_64 bits: 64 
  Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Graphics:
  Device-1: NVIDIA driver: nvidia v: 530.41.03 
  Device-2: AMD Renoir driver: amdgpu v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: amdgpu,ati,nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa 
  resolution: 1920x1080~144Hz, 1920x1080~60Hz 
  OpenGL: 
  renderer: AMD RENOIR (DRM 3.38.0 5.8.0-050800-lowlatency LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6
```
___

Update: Bit more info. I just ran the following command.

```
journalctl | grep systemd-sleep
```

... and got a whole lot of this for output.

```
Jun 18 15:57:37 Tuffy systemd-sleep[3449]: Suspending system...
Jun 18 16:20:53 Tuffy systemd-sleep[3449]: System resumed.
Jun 18 16:21:00 Tuffy systemd-sleep[3612]: Suspending system...
Jun 18 16:21:11 Tuffy systemd-sleep[3612]: System resumed.
Jun 18 19:11:00 Tuffy systemd-sleep[13660]: Suspending system...
Jun 19 00:43:14 Tuffy systemd-sleep[13660]: System resumed.
Jun 19 02:40:15 Tuffy systemd-sleep[28666]: Suspending system...
Jun 19 11:27:45 Tuffy systemd-sleep[28666]: System resumed.
Jun 19 12:40:26 Tuffy systemd-sleep[39235]: Suspending system...
Jun 19 13:47:56 Tuffy systemd-sleep[39235]: System resumed.

```

And I mean a whole lot of that, dating way back. The takeaway from the output is that it is not actually throwing an error when I open the lid. According to the laptop, it's resumed.

---

### Post by #&amp;thj^% on 2023-06-19
Dang Bucky Ball the only thing I see on my end is:
```
sudo journalctl | grep systemd-sleep
[sudo] password for me: 
[me@arch-me ~]$ 

```
I never had a need to use this before 23.04 and your using 20.04
XFCE4=Xfce 4.14.2 on your end and mine is now on  Desktop: Xfce
    v: 4.18.1 just thinking out-loud here.
I need to see if 20.04 has any difference with this first. Give me a day I'm still playing catch-up from all other obligations first. :D

---

### Post by Bucky Ball on 2023-06-19
Cheers, 1fallen. Appreciate it. I'm not in any panic or rush about this, so all good. Currently using the machine with that laptop screen off most the time right now. If I need it, it's there pretty quick by using ARANDR and up it pops in jiffy. :)

---

### Post by #&amp;thj^% on 2023-06-20
Bucky Ball the only thing I see now (on Debian testing) is that I always
Blacklist nouveau or I will add it to grub. (on-lookers beware this may leave you with a broken boot)
First option:
```
sudoedit /etc/default/grub 
```
Add this to the line, "GRUB_CMDLINE_LINUX"
```
GRUB_CMDLINE_LINUX="nouveau.modeset=0"
```
Or in my case I'll just use:
```
sudo nano /etc/modprobe.d/blacklist-nouveau.conf

```
Add this to it:
```
blacklist nouveau
options nouveau modeset=0

```
Now we update initramfs:
```
sudo update-initramfs -u

```
```
blacklist nouveau
options nouveau modeset=0

```
Update grub if the first option is used:
```
sudo update-grub
```
With nVidia:
```
inxi -G 
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 535.54.03
  Device-2: Syntek Integrated Camera driver: uvcvideo type: USB
  Display: server: X.Org v: 1.21.1.7 driver: X: loaded: nvidia gpu: nvidia
    resolution: 1920x1080~120Hz
  API: OpenGL v: 4.6.0 NVIDIA 535.54.03 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2

```

---

### Post by MAFoElffen on 2023-06-20
Hmmm...

The only difference I see in the two is the command...

For BuckyBall:
```

sudo -u buckyball env DISPLAY=:0 /usr/bin/xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off

```
For 1fallen (works for him), and what was recommended elsewhere
```

sudo -u me env DISPLAY=:0 /usr/bin/xrandr --auto

```
I was thinking about this when Bucky first posted what was suggested on that external link, when it had '--auto' and what he changed it to...

If you look at man page xrandr ([https://manpages.ubuntu.com/manpages/lunar/en/man1/xrandr.1.html](https://manpages.ubuntu.com/manpages/lunar/en/man1/xrandr.1.html))
```

       --auto For connected but disabled  outputs,  this  will  enable  them  using  their  first
              preferred  mode  (or, something close to 96dpi if they have no preferred mode). For
              disconnected but enabled outputs, this will disable them.

```
That sort of confirms what I was thinking about that... That issuing that command would it would check the outputs and see if devices were connected, and if it saw connected devices, it would enable the ports... Without really doing any complicated changes. Sort of a tickle to get things going again.

@BuckyBall --- Have you tried that with just that command (simplified)?

---

### Post by #&amp;thj^% on 2023-06-20
> **MAFoElffen said:**
> Hmmm...

The only difference I see in the two is the command...

For BuckyBall:
```

sudo -u buckyball env DISPLAY=:0 /usr/bin/xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off

```

For 1fallen (works for him), and what was recommended elsewhere
```

sudo -u me env DISPLAY=:0 /usr/bin/xrandr --auto

```
I was sure he already did this, but maybe not...
I was thinking about this when Bucky first posted what was suggested on that external link, when it had '--auto' and what he changed it to...
> **MAFoElffen said:**
> 
If you look at man page xrandr ([https://manpages.ubuntu.com/manpages/lunar/en/man1/xrandr.1.html](https://manpages.ubuntu.com/manpages/lunar/en/man1/xrandr.1.html))
```

       --auto For connected but disabled  outputs,  this  will  enable  them  using  their  first
              preferred  mode  (or, something close to 96dpi if they have no preferred mode). For
              disconnected but enabled outputs, this will disable them.

```
That sort of confirms what I was thinking about that... That issuing that command would it would check the outputs and see if devices were connected, and if it saw connected devices, it would enable the ports... Without really doing any complicated changes. Sort of a tickle to get things going again.

Yep I seen the man page, but with "Nvidia-Driver " installs everyone's mileage will vary. This has worked on my end for a month or more now. (Debian/Ubuntu)
> **MAFoElffen said:**
> 
@BuckyBall --- Have you tried that with just that command (simplified)?

I'm curious as well...

---

### Post by MAFoElffen on 2023-06-20
Funny thing is, all 3 of us have nVidia 1650ti's (your wife's as mobile version. My 1090ti fried (physically & literally) and I couldn't shell out that much at the time to replace it. So all 3 of us have the same hardware there.

---

### Post by #&amp;thj^% on 2023-06-20
Well we might think it's funny but Bucky Ball might not. :)
here's a shot from resume.
And on Debian I don't need the script just OOTB
Driver from Nvidia site
dmesg
```
 8697.145610] evbug: Event. Dev: input8, Type: 4, Code: 4, Value: 458808
[ 8697.145626] evbug: Event. Dev: input8, Type: 1, Code: 53, Value: 1
[ 8697.145630] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[ 8697.229609] evbug: Event. Dev: input8, Type: 4, Code: 4, Value: 458808
[ 8697.229625] evbug: Event. Dev: input8, Type: 1, Code: 53, Value: 0
[ 8697.229628] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[ 8697.357619] evbug: Event. Dev: input8, Type: 4, Code: 4, Value: 458792
[ 8697.357636] evbug: Event. Dev: input8, Type: 1, Code: 28, Value: 1
[ 8697.357639] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[ 8697.449320] evbug: Event. Dev: input8, Type: 4, Code: 4, Value: 458792
[ 8697.449326] evbug: Event. Dev: input8, Type: 1, Code: 28, Value: 0
[ 8697.449329] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0

```
And:
```
sudo journalctl -b | grep resume
[sudo] password for me: 
Jun 20 15:49:14 kaisenlinux kernel: ACPI: PM: Low-level resume complete
Jun 20 15:49:15 kaisenlinux systemd[1]: Starting nvidia-resume.service - NVIDIA system resume actions...
Jun 20 15:49:15 kaisenlinux suspend[93079]: nvidia-resume.service
Jun 20 15:49:15 kaisenlinux logger[93079]: <13>Jun 20 15:49:15 suspend: nvidia-resume.service
Jun 20 15:49:15 kaisenlinux systemd[1]: nvidia-resume.service: Deactivated successfully.
Jun 20 15:49:15 kaisenlinux systemd[1]: Finished nvidia-resume.service - NVIDIA system resume actions.

```
Whoops left out the good part:
```
  GNU nano 7.2         /etc/modprobe.d/blacklist-nouveau.conf                   
blacklist nouveau
options nouveau modeset=0
```

---

### Post by Bucky Ball on 2023-07-02
Apologies about the delay. Had some health issues this end and also trying to finish up some work. Have been using the setup as is and it's actually not so bad. When I need the laptop screen, Arandr is there and it's up in seconds. 

To some of the questions. I created a shell script and tried both these commands some time ago.

```
sudo -u buckyball env DISPLAY=:0 /usr/bin/xrandr --output eDP --mode 1920x1080 --pos 1920x0 --rotate normal --output HDMI-A-0 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1-0 --off --output DP-1-1 --off

sudo -u me env DISPLAY=:0 /usr/bin/xrandr --auto
```

And then 'sudo chmod +x 00_screen' (the file where the script is) and reboot. Neither command made any diff. And this.

```
/etc/modprobe.d$ dir
alsa-base.conf			blacklist-modem.conf
amd64-microcode-blacklist.conf	blacklist-oss.conf
blacklist-ath_pci.conf		blacklist-rare-network.conf
blacklist.conf			dkms.conf
blacklist-firewire.conf		intel-microcode-blacklist.conf
blacklist-framebuffer.conf	iwlwifi.conf
```

... but no /etc/modprobe.d/blacklist-nouveau.conf.

---

### Post by #&amp;thj^% on 2023-07-02
> **Bucky Ball said:**
> 

... but no /etc/modprobe.d/blacklist-nouveau.conf.

Hope all is well, but i guess I should of said is create that file:
```

sudoedit  /etc/modprobe.d/blacklist-nouveau.conf
```
With this as the contents:
```
blacklist nouveau
options nouveau modeset=0
```
and a reboot will be needed.

---

### Post by Bucky Ball on 2023-07-04
Thanks, 1fallen. Tried it. No change.

One discovery I made and forgot to mention. When I move the mouse with the laptop lid down, it wakes the laptop and the monitor screen wakes up. Then, when I open the laptop lid, the laptop screen is on ! 

When I first discovered this, the screens were mirror image (a mirror of the laptop screen) when I opened the lid (whereas normal config is to have the primary screen on the monitor and the secondary screen on the laptop), but just a minute ago when I tried this and last time I tried this, it worked. The screens were actually configured as they should be; primary left, secondary right.

...

---

