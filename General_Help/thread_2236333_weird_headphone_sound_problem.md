---
title: "weird headphone sound problem"
date: 2014-07-26
forum: General Help
---

### Post by skar2 on 2014-07-26
Hi all,

I'm having this strange problem on kubuntu 14.04. Well I've had this issue only in Linux distros (all Ubuntu based) installed on my laptop. I tried a couple before settling with kubuntu. I have Bose noise cancellation headphones. When i'm about to play a video/sound file I get this huge air puff sort of sound that is obviously uncomfortable. This happens on startup/shutdown as well. Even system sounds will produce this issue. However, when the sound is playing, things are perfect, no issues at all. When there is no sound playing I also get this interference type of sound. It's hard to describe, but like the sound you get when your about to loose a radio connection. Again it happens periodically. One time it is off, and then up again. I'm 100% sure, its not a hardware issue. I had no problems with Windows. I've used these headphones on several other systems with no problem (well they were all windows). I tried the regular headphones and on that too the problem persisted, but it wasnt as amplified to casue great annoyance or discomfort. Any help would be appreciated.

Karan

---

### Post by Jesse_Campton on 2014-07-26
Wireless? Sounds to me, like your headset is powering up and your getting a burst of power. If your headset is wireless, you could be getting the interference from another wireless signal..

---

### Post by skar2 on 2014-07-26
Nope. It's wired. Like I said I'm 100% certain its not a hardware issue. Have had no problems whatsoever on Windows.

skar

---

### Post by Yellow Pasque on 2014-07-26
What model is the laptop? It sounds like audio chip is making the noise when waking up from power save.
```
Power-Saving
~~~~~~~~~~~~
The power-saving is a kind of auto-suspend of the device.  When the
device is inactive for a certain time, the device is automatically
turned off to save the power.  The time to go down is specified via
`power_save` module option, and this option can be changed dynamically
via sysfs.

The power-saving won't work when the analog loopback is enabled on
some codecs.  Make sure that you mute all unneeded signal routes when
you want the power-saving.

The power-saving feature might cause audible click noises at each
power-down/up depending on the device.  Some of them might be
solvable, but some are hard, I'm afraid.  Some distros such as
openSUSE enables the power-saving feature automatically when the power
cable is unplugged.  Thus, if you hear noises, suspect first the
power-saving.  See /sys/module/snd_hda_intel/parameters/power_save to
check the current value.  If it's non-zero, the feature is turned on.
```

---

### Post by skar2 on 2014-07-27
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar327594_14.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=327594") 				 				 					 						 	[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")

It's an Acer Aspire V5-573-9491 with nVIDIA geforce 720 M

---

