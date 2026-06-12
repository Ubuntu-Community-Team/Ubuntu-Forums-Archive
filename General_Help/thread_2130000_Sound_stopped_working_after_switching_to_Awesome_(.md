---
title: "Sound stopped working after switching to Awesome (unrelated, likely)"
date: 2013-03-28
forum: General Help
---

### Post by GermanMafia on 2013-03-28
So I tried out awesome wm the other day, switching from Unity. Everything was working great, but then it froze, hard. I restarted it (held the power button down on my desktop), and it took forever to boot up. It sat at a blinking cursor for about 3 minutes, and I figured it was dead or something, so I restarted it again. 

When it comes back up, it sits at the same blinking cursor for a while. The display driver boots up, it increases the resolution and mirrors to both monitors. 

It sits for a little bit longer, but then it starts yelling commands like "udevd killed /sbin/perfmon PCI device" and "udevd killed /sbin/perfmon USB device". I know this is going to be bad from this point...

It takes about 10 minutes to boot the whole system up - it sits and sits, until it realizes that something won't respond (at least that's my hunch). Then it goes forward. It sits on the Ubuntu login screen for a long time too, the password box is unselectable, and it takes about 3 minutes for it to do something with that.

So I get my computer booted up into Unity, no sound plays. Logout, back to awesome, no sound. Restart, no sound (still takes a while, although it does't say that stuff about udevd and perfmon now, at least not visibly). Getting a little frustrated, I see that rm -r ~/.pulse* can help for hard resets, remove those, restart, no dice. 

I try to update stuff - dpkg --configure -a or whatever, it actually found some pulseaudio stuff, but after a restart, it didn't work.

I try to update the kernel, nope.

I was on Ubuntu 12.04.2, try upgrading to 12.10, nope. Nothing.

My sound card is found by lspci, but not by alsa. I'm not sure what the heck is going on. :(

uname -r
3.5.0-27-generic

cat /etc/issue 
Ubuntu 12.10 \n \l

aplay -l 
aplay: device_list:252: no soundcards found...

lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at f3ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0

And alsa config used to be in /etc/perfmon.d/alsa-***, but that seems to have moved in 12.10

Any help would be great!

---

### Post by GermanMafia on 2013-03-28
Okay, I was pretty close with my estimates! It does take about 10 minutes for my computer to boot. I tried to edit the boot options to not be quiet so I could get a better idea of what was going on, but for some reason it didn't work.

[Here's my bootup from bootchart]("http://i1.minus.com/ibcc2kRcpjHNci.png") (note: very large image). This is a pretty handy tool - I found out it was waiting to mount some non-existent network shares (that's what mountall was trying to do I think).

So I know next to nothing about the Linux boot process, is modprobe supposed to take up that much time in the boot process?

Also, I found the file that I thought moved. For some reason I was looking for perfmon, when I wanted to find modprobe. Here's what it says -

> cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=generic




As far as other fixes go - I tried [this one ]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS") but it didn't work. I still get "dummy output" as the only option under the sound settings.

---

