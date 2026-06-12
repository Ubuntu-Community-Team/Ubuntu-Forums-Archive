---
title: "Issue booting with nVidia proprietary driver"
date: 2016-06-06
forum: General Help
---

### Post by adlerhn on 2016-06-06
I have a Dell XPS 15 (2013) laptop with Optimus graphics (Intel 4600 + nVidia GeForce GT 750M).

I can use the Nouveau driver just fine. It just seems a bit more unstable when I plug and unplug my external HDMI screen.

So, I usually use the proprietary driver from nVidia. The problem is that, since a few versions of the driver (about v. 346) onward, some of the versions work fine, but most of them fail to start. Whenever I update the driver, if it doesn't start, I have to uninstall the proprietary driver and go back to Nouveau until there is a new version.

I am not sure if the issue is in my system (currently running kernel 4.6.0-040600-generic, GNOME 3.20, Cinnamon 2.8.6), or if it is an issue of the nVidia driver.

Since my system moved to SystemD I am not too sure how to debug startup issues (which files to look at et al.).

Could anyone help me investigate why is the system not booting with some versions of the driver? Thanks.

---

### Post by SeijiSensei on 2016-06-06
Did you run "sudo nvidia-xconfig" after installing the driver? Give that a try.

---

### Post by adlerhn on 2016-06-06
Thanks for the tip. Yeah, I just tried that; no change.

---

### Post by ventrical on 2016-06-07
> **adlerhn said:**
> I have a Dell XPS 15 (2013) laptop with Optimus graphics (Intel 4600 + nVidia GeForce GT 750M).

I can use the Nouveau driver just fine. It just seems a bit more unstable when I plug and unplug my external HDMI screen.

So, I usually use the proprietary driver from nVidia. The problem is that, since a few versions of the driver (about v. 346) onward, some of the versions work fine, but most of them fail to start. Whenever I update the driver, if it doesn't start, I have to uninstall the proprietary driver and go back to Nouveau until there is a new version.

I am not sure if the issue is in my system (currently running kernel 4.6.0-040600-generic, GNOME 3.20, Cinnamon 2.8.6), or if it is an issue of the nVidia driver.


I was just going to say that. Try scaling back to k 4.4.0-23 or what have you.

regards..

---

### Post by adlerhn on 2016-06-07
> **ventrical said:**
> I was just going to say that. Try scaling back to k 4.4.0-23 or what have you.

Thanks for the suggestion. It works (so far) with 4.4.0-22.

Will keep an eye and if the issue comes back I will update this thread.

If you don't hear back from me, that is only good news (or lack of updated drivers).

---

### Post by adlerhn on 2016-07-05
Due to one program running really slow, yesterday I realised that I was not using the Nvidia card, but the Intel one.

So, switched the active graphics card, restarted, and the system does no longer boot correctly; it keeps retrying to initialise the graphics mode. Only after I uninstalled the proprietary driver did the system boot again (using the Nouveau driver, so faster than using the Intel card, but slower than in Windows).

Going back to kernel 4.4.0 may have only worked because I was actually not using the Nvidia card (which works perfectly in Windows).

I would love some assistance to be able to debug the issue.

---

### Post by Bashing-om on 2016-07-05
adlerhn; Hello;

> 
I would love some assistance to be able to debug the issue.


Bunches I do not know about the graphic's interfacing; but we can at least look at the basics and see if we can determine what is not going on here.

Back to the basics at square one;

What is the hardware we are working with :
```

lspci -k | grep -EA2 'VGA|3D'

```

What does the system think for installed modules ( drivers) :
```

dpkg -l | grep -i nvidia
lsmod | grep nvidia
sudo find / -name "NVIDIA-Linux-*"

```

And /// what is the state of the GUI (X) :
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log

```

With the idea of purging the present drivers, and installing the recommended driver.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by adlerhn on 2016-07-07
Thanks for your response.

With the Nvidia proprietary driver uninstalled:

$ lspci -k | grep -EA2 'VGA|3D'
> 00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
	Subsystem: Dell 4th Gen Core Processor Integrated Graphics Controller
	Kernel driver in use: i915
--
02:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
	Subsystem: Dell GK107M [GeForce GT 750M]
	Kernel driver in use: nouveau

$ dpkg -l | grep -i nvidia
> ii  bbswitch-dkms                                     0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
rc  nvidia-367                                        367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA binary driver - version 367.27
rc  nvidia-opencl-icd-367                             367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                      0.8.2                                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                   367.18-0ubuntu0~gpu16.04.1                                  amd64        Tool for configuring the NVIDIA graphics driver

I have uninstalled those packages, just in case, and now the command returns empty.

$ lsmod | grep nvidia
$ sudo find / -name "NVIDIA-Linux-*"

These two return empty as well.

Xorg.0.log and gpu-manager.log with the nouveau driver installed: <deleted>

In this state (minus the nvidia packages I just uninstalled), I have installed the nvidia-367 package. After a restart, I get a text-mode black screen asking me to log in. Logging in and manually running startx does not boot the system (startx gets hung).

Xorg.0.log and gpu-manager.log with the nvidia driver installed (black screen on boot): <deleted>

---

### Post by Bashing-om on 2016-07-07
adlerhn; Sorry;

I run a minimal install on this my work station, I have no ready means in this install to cope with a zip file.
Maybe paste them here directly or in a pastebin site ??

Running the terminal command 'startx' is only applicable in certain Desktop Environments, Possible now that the ownership rights in your own /home are changed .
What returns:
```

ls -al /home/adlerhn

```
in respect to the .Xauthority and .ICEauthority files ; do you still own them ? Otherwise, you do not have the authority to start a GUI.

Maybe yes ?

---

### Post by adlerhn on 2016-07-08
.ICEauthority is owned by my own user, but .Xauthority is owned by root. Should I change that? Right now I am logging in fine (using nouveau, though).

The pastebins:

With nouveau:
[http://pastebin.com/FN7FXsFb](http://pastebin.com/FN7FXsFb)
[http://pastebin.com/iDuL5a8G](http://pastebin.com/iDuL5a8G)

With the nvidia driver:
[http://pastebin.com/KjcjsFA8](http://pastebin.com/KjcjsFA8)
[http://pastebin.com/HJ4miP47](http://pastebin.com/HJ4miP47)

---

### Post by Bashing-om on 2016-07-08
adlerhn; Well ..

Yeah ! You want .Xauthority as "You"
```

sudo chown USERNAME:USERNAME .Xauthority

```

Having more than my share of difficulties making out what is going on here :

What is the reason that you have a testing kernel ( Linux Donald 4.6.0-040600-generic ) installed and booted ??
16.04's kernel is:
> 
xenial (kernel): Generic Linux kernel image 
4.4.0.28.30 [security]: amd64 i386 

What results when booting a 4.4 series kernel ?


In the Xorg log file that you say is booted with nouvea ... I see that Nvidia is loaded .. and for some unknown reason:
> 
  59.960] (II) NVIDIA(GPU-0): Deleting GPU-0

GPU-0 is the nvidia card; per:
> 
58.917] (II) NVIDIA(0): NVIDIA GPU GeForce GT 750M (GK107) at PCI:2:0:0 (GPU-0)


An inconsistent xorg.conf control file ?? Just do not know.

--------------------
And with the Nvidia driver loaded, we know we have a bad install per:
> 
Error: /usr/share/nvidia-prime/prime-quirks does not exist or is empty.

in the gpu-manager.log file.
We are looking at a complete purge and an attempted re-install of the 367 version driver. The question now is why is this present install failing ?

Again we have :
> 
59.960] (II) NVIDIA(GPU-0): Deleting GPU-0

Bad install ?? ... conflicts with installation of the driver ???

Backup 3 yards, punt
[INDENT][INDENT][INDENT]and try again
[/INDENT][/INDENT][/INDENT]

---

### Post by adlerhn on 2016-07-09
Hi, thanks again for your response.

> **Bashing-om said:**
> Yeah ! You want .Xauthority as "You"

Done.

> **Bashing-om said:**
> What is the reason that you have a testing kernel ( Linux Donald 4.6.0-040600-generic ) installed and booted ??
16.04's kernel is:
> 
xenial (kernel): Generic Linux kernel image
4.4.0.28.30 [security]: amd64 i386 

What results when booting a 4.4 series kernel ?

I did install kernel 4.6 because with the Nouveau driver, every time I plug or unplug my external external HDMI monitor, the system crashes. So, I wanted to check whether Nouveau in 4.6 fixed this (which it didn't). I did go back to 4.4 as per the suggestion by [http://ubuntuforums.org/member.php?u=1140838](http://ubuntuforums.org/member.php?u=1140838). uname confirms I am running 4.4:

> $ uname -a
Linux Donald 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Actually, looking deeper in that file I see it has not been updated in a month:

> [    58.786] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  7 00:05:02 2016

For some reason, this log file seems to have stopped updating. I just found out Xorg is writing logs now to a new location: ~/.local/share/xorg

I have reinstalled the nvidia driver and restarted. This time the system did boot fine! It seems like a lottery, though.

Strangely, at the end of .local/share/xorg/Xorg.0.log I see:

> [  3752.054] (EE) 
[  3752.054] (EE) Backtrace:
[  3752.055] (EE) 0: /usr/lib/xorg/Xorg (xorg_backtrace+0x4e) [0x55a971ca35ce]
[  3752.055] (EE) 1: /usr/lib/xorg/Xorg (0x55a971af1000+0x1b6959) [0x55a971ca7959]
[  3752.055] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7fda6a6ab000+0x354a0) [0x7fda6a6e04a0]
[  3752.055] (EE) 3: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fda6687f000+0x30d37) [0x7fda668afd37]
[  3752.055] (EE) 4: /usr/lib/xorg/Xorg (0x55a971af1000+0x134e57) [0x55a971c25e57]
[  3752.055] (EE) 5: /usr/lib/xorg/Xorg (0x55a971af1000+0x134f25) [0x55a971c25f25]
[  3752.055] (EE) 6: /usr/lib/xorg/Xorg (0x55a971af1000+0x135692) [0x55a971c26692]
[  3752.055] (EE) 7: /usr/lib/xorg/Xorg (0x55a971af1000+0x134243) [0x55a971c25243]
[  3752.055] (EE) 8: /usr/lib/xorg/Xorg (0x55a971af1000+0xe4918) [0x55a971bd5918]
[  3752.055] (EE) 9: /usr/lib/xorg/Xorg (0x55a971af1000+0x1325e4) [0x55a971c235e4]
[  3752.055] (EE) 10: /usr/lib/xorg/Xorg (0x55a971af1000+0x57d57) [0x55a971b48d57]
[  3752.055] (EE) 11: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf0) [0x7fda6a6cb830]
[  3752.055] (EE) 12: /usr/lib/xorg/Xorg (_start+0x29) [0x55a971b32f59]
[  3752.055] (EE) 
[  3752.055] (EE) Segmentation fault at address 0x20
[  3752.055] (EE) 
Fatal server error:
[  3752.055] (EE) Caught signal 11 (Segmentation fault). Server aborting
[  3752.055] (EE) 
[  3752.055] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

Will update this thread on the next driver update, when chances are it will stop working again.

---

### Post by Bashing-om on 2016-07-09
adlerhn; Welp'

Seems we are making progress !

OK, I do believe in your install with hybrid graphics, the control file /etc/X11/xorg.conf  is required .
What is presently in this file with Nvidia enabled :
```

cat /etc/X11/xorg.conf 

```
And as well, we want the graphic's controller installed:
so let's have a look at what is installed:
```

dpkg -l | grep -i nvidia
lsmod | grep nvidia

```

And as we have segmentation faults reported,
let's see what X reports:
```

cat /var/log/Xorg.0.log

```

And what is going on with the display:
```

cat .xsession-errors

```

Looking for that hint
[INDENT][INDENT]where the failure is
[/INDENT][/INDENT]

---

### Post by adlerhn on 2016-07-11
Thanks! You have already helped me a lot.

> **Bashing-om said:**
> What is presently in this file with Nvidia enabled :
Code:

cat /etc/X11/xorg.conf

[http://pastebin.com/pGTbYGQm](http://pastebin.com/pGTbYGQm)

> **Bashing-om said:**
> And as well, we want the graphic's controller installed:
so let's have a look at what is installed:
Code:

dpkg -l | grep -i nvidia

```
ii  bbswitch-dkms                                     0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-367                                      367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA CUDA runtime library
ii  nvidia-367                                        367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA binary driver - version 367.27
ii  nvidia-opencl-icd-367                             367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                      0.8.2                                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                   367.18-0ubuntu0~gpu16.04.1                                  amd64        Tool for configuring the NVIDIA graphics driver
```

> **Bashing-om said:**
> lsmod | grep nvidia

```
nvidia_uvm            630784  0
nvidia_drm             45056  2
nvidia_modeset        765952  1 nvidia_drm
drm_kms_helper        147456  2 i915,nvidia_drm
nvidia              11075584  116 nvidia_modeset,nvidia_uvm
drm                   360448  17 i915,drm_kms_helper,nvidia_drm
```

> **Bashing-om said:**
> And as we have segmentation faults reported,
let's see what X reports:
Code:

cat /var/log/Xorg.0.log

/var/log/Xorg.0.log is empty, though ~/.local/share/xorg/Xorg.0.log is [http://pastebin.com/JPYv3HTM](http://pastebin.com/JPYv3HTM)

> **Bashing-om said:**
> And what is going on with the display:
Code:

cat .xsession-errors

[http://pastebin.com/8qwpVQjd](http://pastebin.com/8qwpVQjd)

---

### Post by Bashing-om on 2016-07-11
adlerhn; Hummm ...

I am not real happy with the control file " xorg.conf" May consider making an edit . It is in my mind - presently this thought is but a place holder . As I also entertain generating a new file.

This is the biggy:
> 
[    79.351] (EE) Failed to load module "nvidia" (module does not exist, 0)

Huh ... why ? the driver is installed (ii  nvidia-367) ! So why does the system not find it ??
Why oh Why is there no /var/log/Xorg.0.log !! Please verify:
```

ls -al /var/log/Xorg.0.log

```
As if this file is not generated, then we have a deep deep underlying problem that in all likely hood is over my pay grade.

And then there is Goggle and FaceBook !
Both are causing the system to scream and holler in pain. 32 bit apps ? As Google has dropped all support for 32 bit apps. I have no idea how FaceBook interfaces. How tough is it to remove the interface(s) all together and get this system updated ?

[INDENT][INDENT]getting the deeper now
[/INDENT][/INDENT]

---

### Post by mc4man on 2016-07-11
Are you saying you're using the nvidia drivers now?  There is no indication in your Xorg.0 log that you are
Some items from the Xorg log - 
You're using vt 2  - why? (indicated with (++)
As far as video driver no config files are being used (indicated with (**), so your xorg.conf exists via nvidia-prime but isn't used
In 16.04 SNA is not used for intel display when using nvidia drivers via nvidia-prime, modesetting instead. This is reflected in your xorg.conf but not in your Xorg.0.log so again not on nvidia via nvidia-prime

What does inxi -b show for Graphics:

I've pretty much the same HW here, using nvidia via nvidia-prime is pretty straightforward, - snippet
> $ inxi -b
CPU:       Quad core Intel Core i7-4700MQ (-HT-MCP-) speed/max: 2400/3400 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 755M]
           Display Server: X.Org 1.18.3 drivers: nvidia,intel Resolution: 1920x1080@59.91hz
           GLX Renderer: GeForce GT 755M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 358.16

Also of curiosity is your supposed use of 'nouveau'. (apparently). By default in ubuntu it's either nvidia drivers or intel, nouveau is not an option for nvidia mobile optimus gpu setups. Did you install nvidia blob from nvidia?

---

### Post by adlerhn on 2016-07-11
> Why oh Why is there no /var/log/Xorg.0.log !! Please verify:
Code:

ls -al /var/log/Xorg.0.log

As if this file is not generated, then we have a deep deep underlying problem that in all likely hood is over my pay grade.

```
$ ls -al /var/log/Xorg.0.log
ls: cannot access '/var/log/Xorg.0.log': No such file or directory
```

The log file is only being written at ~/.local/share/xorg/Xorg.0.log

> Are you saying you're using the nvidia drivers now? There is no indication in your Xorg.0 log that you are

I do think I am now using the nvidia drivers due to the performance being much higher now than before, and the "NVIDIA X Server Settings" applet now showing all the options, including "NVIDIA Driver Version: 367.27", all monitors, etc.

> You're using vt 2 - why? (indicated with (++)

No idea; I never changed that. Where is that configured? Is that a bad thing?

> What does inxi -b show for Graphics:

```
$ inxi -b
System:    Host: Donald Kernel: 4.4.0-28-generic x86_64 (64 bit)
           Desktop: Cinnamon 3.0.6  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Dell model: XPS 15 9530 v: A09
           Bios: Dell v: A09 date: 07/30/2015
CPU:       Quad core Intel Core i7-4702HQ (-HT-MCP-) speed/max: 3005/3200 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 750M]
           Display Server: X.Org 1.18.3 driver: N/A
           Resolution: 3200x1800@59.98hz
           GLX Renderer: GeForce GT 750M/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 367.27
Network:   Card: Intel Wireless 7260 driver: iwlwifi
Drives:    HDD Total Size: 1262.3GB (82.3% used)
Info:      Processes: 305 Uptime: 3:23 Memory: 3172.2/15950.7MB
           Client: Shell (bash) inxi: 2.2.35
```

"driver: N/A"... What would that mean? The GLX Version looks fine though.

> Also of curiosity is your supposed use of 'nouveau'. (apparently). By default in ubuntu it's either nvidia drivers or intel, nouveau is not an option for nvidia mobile optimus gpu setups. Did you install nvidia blob from nvidia?

I currently have installed the nvidia-367 package from the PPA-graphics-drivers. For some time I could not get any version of the proprietary driver to install, so I added the PPA to try with the newest version.

---

### Post by mc4man on 2016-07-11
> **adlerhn said:**
> 
I do think I am now using the nvidia drivers due to the performance being much higher now than before, and the "NVIDIA X Server Settings" applet now showing all the options, including "NVIDIA Driver Version: 367.27", all monitors, etc.



No idea; I never changed that. Where is that configured? Is that a bad thing?



```
$ inxi -b
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 750M]
           Display Server: X.Org 1.18.3 driver: N/A
           Resolution: 3200x1800@59.98hz
           [COLOR="#0000CD"]GLX Renderer: GeForce GT 750M/PCIe/SSE2[/COLOR]
           GLX Version: 4.5.0 NVIDIA 367.27
```

"driver: N/A"... What would that mean? The GLX Version looks fine though.


Yeah, you're using the nvidia drivers, blue indicates that. (with optimus Intel always handles the display, when using nvidia it's the renderer. At least when using the laptop display, not sure if hdmi is connected to Intel or nvidia gpu.. maybe I'll try that later here.

Why the N/A, no clue though something about your install is slightly off the rails so to speak. Maybe using an external display is a factor here??
  It's weird that xorg.conf isn't being used, can't figure that either. What may be interesting is to delete that log & reboot. Then see if the new log is any different. Possibly also do so without an ext. display connected ..

In any  event if things are working ok for now it may be better to let sleeping dogs lie. My experience with 16.04 has shown it's not that hard to get to where nvidia drivers don't work at all, just black screen. On the machine I have similar to yours it became impossible to get it right, I did a fresh install the other day & then all was well again. (- that 'bad' install went back to Feb.

Edit: you may want to ck. if root owns anything in your Home dir., at normal terminal prompt - 
```
ls -lA -R |grep root
```

---

### Post by adlerhn on 2016-07-12
Yeah, things seem to be working fine for now, probably due to the cleanup we did. Thanks a lot everyone.

---

### Post by Bashing-om on 2016-07-13
adlerhn; Great :

as :
> 
Yeah, things seem to be working fine for now,

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And it is onward and upward
[INDENT][INDENT][INDENT]bigger and better things
[/INDENT][/INDENT][/INDENT]

---

