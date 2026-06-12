---
title: "Update = Sound problems"
date: 2008-06-21
forum: General Help
---

### Post by Az_135r on 2008-06-21
Well ive been happily running ubuntu for the past 6 months or so now, up until now, where recently things just start to fall apart (running hardy)

i'll focus on the sound issues as these are my main concerns. Im running ubuntu on both my laptop Dell X1, and the Desktop (MSI K8N Neo Platinum, nforce 3, using onboard sound)

the sound has been functioning properly, both on the laptop, during the gutsy install and early hardy installs, however now the sound is complete rubbish... from both the laptop and desktop, the desktop being far worse

to sum up the output (using both analogue and spdif), it sounds like music is playing in a large hall, echoey. But it also sounds like the channels are mixed up and all sorts.

_what ive tried in the past._
all sorts of asound.conf configs
using pulse audio with various tweaks etc
using alsa
using analogue
using spdif
various packages, incl the 5.1 recoding (which i actually quite liked, but being experimental its quite unstable)

then i gave up... I tested the sound output using a gutsy live cd.. and what do you know.. perfect.

so i decide to revert back to gutsy (i386 aswell). great it works... but then sudo apt-get update + upgrade and bam... i have screwed up sound again

where do i go from now?

one thing to mention, sound drivers seem to be updated as theres many more options availble in alsa mixer than in comparison to fresh intall alsa mixer


(+ been having lots of problems with nvidia drivers and tgz file system restores with hardy as well ](*,) )


```
-@Az-Desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
aarondjajasaputra@Az-Desktop:~$ 
```

---

### Post by VMC on 2008-06-21
What does "System-Preferences-Sound" detect?

Also "lsmod|grep snd" should match the same as above.

Any errors in "dmesg" ?

---

### Post by Az_135r on 2008-06-21
> **VMC said:**
> What does "System-Preferences-Sound" detect?

Also "lsmod|grep snd" should match the same as above.

Any errors in "dmesg" ?

hi vmc, thanks for the reply

funny thing is, i would tell you... but ubuntu now hangs at ```
* running local boot scripts 
``` ](*,)

i remember the last thing i was working on was installing the newest alsa packages, thats pretty much it

i'll reinstall... again (lucky i made desktop set up script! :))

---

### Post by Az_135r on 2008-06-21
hopefully this might shed some light, or at least explain a little of whats occurring (on both installs, currently gusty)

if i play something like this
[http://users.skynet.be/fa046054/home/P22/track06.mp3](http://users.skynet.be/fa046054/home/P22/track06.mp3)
the sound is fine

as soon as a play a video, mp3 etc... the sound is extremely quiet & distorted

---

### Post by Zorael on 2008-06-21
Many have similar issues. Some don't get sound out of one speaker. Some still get sound out of their speakers even with their headphones connected. It's the new ALSA drivers. You *may* be able to fix these things by passing certain options to your sound chipset driver. Don't get your hopes up, though.

It seems to me that you should be running the snd_intel8x0 driver, but to make sure, enter this command.
```
$ lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 **module=snd_intel8x0**
```
If it doesn't say snd_intel8x0 there, stop here, rest is irrelevant. If it *does* say snd_intel8x0, then there are some tweaks you could add to your /etc/modprobe.d/alsa-base file to - hopefully - make it work. You just open that file up in a text editor with superuser permissions (such as by running '**gksu gedit /etc/modprobe.d/alsa-base**' in Gnome or '**kdesu kate /etc/modprobe.d/alsa-base**' in Kubuntu), and add a line to the end that looks akin to the following.
```
options snd-intel8x0 <*option1=setting1 option2=setting2 option3=setting3 ...>*
```


Now, as for your list of available options:
```
  Module snd-intel8x0
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, MCP04, CK804
				 CK8, **CK8S**, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    **ac97_clock**	  - AC'97 codec clock base (0 = auto-detect)
    **ac97_quirk**    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    **buggy_irq**     - Enable workaround for buggy interrupts on some
                    motherboards [I](default yes on nForce chips,
		    otherwise off)[/I]
    **buggy_semaphore** - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    **spdif_aclink**  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)

    This module supports one chip and autoprobe.

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

    Joystick/MIDI ports are not supported by this driver.  If your
    motherboard has these devices, use the ns558 or snd-mpu401
    modules, respectively.

    The power-management is supported.
```
```
AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - **default**	Don't override the default setting
    - **none**	Disable the quirk
    - **hp_only**	Bind Master and Headphone controls as a single control
    - **swap_hp**	Swap headphone and master controls
    - **swap_surround**  Swap master and surround controls
    - **ad_sharing**  For AD1985, turn on OMS bit and use headphone
    - **alc_jack**	For ALC65x, turn on the jack sense mode
    - **inv_eapd**	Inverted EAPD implementation
    - **mute_led**	Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.
```
Reading through the descriptions, I don't see anything that immediately describes your problem, but then I'm not sure what issues "buggy semaphores" can cause. From here on, it's a matter of trial and error. An example would be:
```
options snd-intel8x0 buggy_semaphore=true ac97_quirk=inv_eapd
```
To apply the settings, you'd need to restart the module (driver). I think this requires a full system restart; trying to manually remove the module says it's "in use". To try, do this.
```
$ sudo /etc/init.d/alsa-base stop
$ sudo rmmod snd-intel8x0 && sudo modprobe snd-intel8x0
$ sudo /etc/init.d/alsa-base start
```
It'll likely spout the following.
```
ERROR: Module snd_intel8x0 is in use
```



[SIZE="4"]**If all else fails**[/SIZE], such as if/when you succumb to insanity from restarting endlessly with no success, you could try OSS v4. See Hardy installation instructions here: [http://www.uluga.ubuntuforums.org/showthread.php?t=780961&highlight=oss4](http://www.uluga.ubuntuforums.org/showthread.php?t=780961&highlight=oss4). It uses its own drivers, so any ALSA-specific issues you might have would be just that; ALSA-specific.

---

### Post by Az_135r on 2008-06-24
Zorael - sorry for not getting back sooner, thanks for your reply, appreciate it

had all sorts of hardware problems this week, WD Raptor died, CDRW's playing up etc

anyway, ive had no joy with alsa yet, but i havent had time to really have a go. i notice that the snd_intel8x0 driver supports both my desktop and laptop chips (ck8s + ICH6), so you never know i might be able to fix both :)

i did try oss4, which actually i was quite pleasantly surprised :) no spdif though, and rythmbox wouldn't have it, but im sure thats fixable... definately a project im going to keep an eye on

for me, no sound = 1 step back..... but the new release of Codeweavers Crossover office = 2 steps forward!! :)   so im happy for the moment

---

