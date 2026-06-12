---
title: "Can't Disable HDMI Sound Power Saving"
date: 2023-01-15
forum: General Help
---

### Post by nobody96 on 2023-01-15
Fresh ubuntu user here.

I have a monitor with built in speakers connected to GTX 1080 gpu via HDMI . I need the sounds to be played instantly because I ( should ) get important, short sound notifications. When the sound card power saving is on, the notification may "play", but it can't be heard, since it takes a second for the sound card to wake up and by the time it's ON, the sound is already finished "playing".
 I looked for solutions to no avail. Only config file in sys/module which has a power saving option is for intel sound cards ( which I turned to "0" just to be sure ). Nvidia settings panel doesn't have a power saving option. There is no option to change it in ubuntu sound settings either. I can't see it at least.

If there is a solution to this. Please advise. Thanks.

---

### Post by #&amp;thj^% on 2023-01-15
Not sure I can help, but will you show us this:
```
grep 10de /lib/udev/rules.d/*
```

---

### Post by nobody96 on 2023-01-15
/lib/udev/rules.d/71-nvidia.rules:SUBSYSTEM=="pci", ATTRS{vendor}=="0x10de", DRIVERS=="nvidia", TAG+="seat", TAG+="master-of-seat"
/lib/udev/rules.d/71-nvidia.rules:ACTION=="bind", SUBSYSTEM=="pci", ATTR{vendor}=="0x10de", ATTR{class}=="0x03[0-9]*", TEST=="power/control", ATTR{power/control}="auto"
/lib/udev/rules.d/71-nvidia.rules:ACTION=="add", SUBSYSTEM=="pci", ATTR{vendor}=="0x10de", ATTR{class}=="0x040300", TEST=="power/control", ATTR{power/control}="auto"
/lib/udev/rules.d/71-nvidia.rules:ACTION=="add", SUBSYSTEM=="pci", ATTR{vendor}=="0x10de", ATTR{class}=="0x0c0330", TEST=="power/control", ATTR{power/control}="auto"
/lib/udev/rules.d/71-nvidia.rules:ACTION=="add", SUBSYSTEM=="pci", ATTR{vendor}=="0x10de", ATTR{class}=="0x0c8000", TEST=="power/control", ATTR{power/control}="auto"

---

### Post by #&amp;thj^% on 2023-01-15
Oh brother, they have changed things here, I have a test for you to try if willing, this will have no harm to your system.
Try to add:
```
options snd_hda_intel power_save=0
```
To **"/etc/modprobe.d/modprobe.conf"**
You may also need to disable power saving for the audio card controller:
```
options snd_hda_intel power_save=0 power_save_controller=N
```
It's been a few years since I've used it, so keep us posted please...

---

### Post by nobody96 on 2023-01-15
I went to the specified folder. The file modprobe.conf was not present, so I made it.
I pasted what you recommended, in two lines, one under the other. Like that:

> options snd_hda_intel power_save=0
options snd_hda_intel power_save=0 power_save_controller=N

I saved it and then rebooted. The sound card still goes to sleep/power saving mode. So, sadly, it didn't help.

---

### Post by #&amp;thj^% on 2023-01-15
I wondered if it would still work due to this:
```
/lib/udev/rules.d/71-nvidia.rules:ACTION=="bind", SUBSYSTEM=="pci", ATTR{vendor}=="0x10de", ATTR{class}=="0x03[0-9]*", TEST=="power/control", ATTR**[COLOR="#FF0000"]{power/control}="auto"[/COLOR]**
```
Have you or can you now just remove that file.
```
sudo rm /etc/modprobe.d/modprobe.conf
```
One more to try this will get attention at boot via "/etc/default/grub"
Add this to set parameters for kernel modules:
```
snd_hda_intel power_save=0
```
If you need help with this just ask. ;)
I'm just being lazy today, to do this:
```
sudo nano /etc/default/grub
```
Add that to:
```
GRUB_CMDLINE_LINUX_DEFAULT="splash=silent resume=/dev/system/swap mitigations=auto**_ snd_hda_intel power_save=0 _**quiet security=apparmor nosimplefb=1"
```
Now update grub to the change:
```
 sudo update-grub
```
Reboot

---

### Post by nobody96 on 2023-01-15
I managed to remove modprobe.conf as root.

I added " snd_hda_intel power_save=0 " to grub . It looked like this:

> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
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

snd_hda_intel power_save=0

After reboot, still no improvement.

According to this [https://docs.kernel.org/sound/designs/powersave.html](https://docs.kernel.org/sound/designs/powersave.html) There are other devices other than intel that have this power saving setting.I can locate snd_hda_intel  in > /sys/module/
 Correct me if I'm wrong, but shouldn't a config be here? > /sys/module/snd_hda_codec_hdmi/parameters

There are config files there, but I don't know what they are for. > enable_acomp , enable_all_pins , enable_silent_stream, static_hdmi_pcm

---

### Post by nobody96 on 2023-01-15
I saw your edit. Seems like my grub looks different to what you pasted. Should I still edit it the way you wrote?

---

### Post by #&amp;thj^% on 2023-01-15
> **nobody96 said:**
> I managed to remove modprobe.conf as root.

I added " snd_hda_intel power_save=0 " to grub . It looked like this:



After reboot, still no improvement.

I wouldn't have expected that to work, please re-read my  previous post, I edited it due to my laziness.
> **nobody96 said:**
> 

According to this [https://docs.kernel.org/sound/designs/powersave.html](https://docs.kernel.org/sound/designs/powersave.html) There are other devices other than intel that have this power saving setting.I can locate snd_hda_intel  in 
 Correct me if I'm wrong, but shouldn't a config be here? 

There are config files there, but I don't know what they are for.
Best to leave those be as is...;)
FTR I just used it in my system and works as expected on my end.
```
Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.pci-0000_01_00.1.hdmi-stereo
         1. Audio/Source  alsa_input.pci-0000_06_00.6.analog-stereo


```
```
 Streams:
        77. Strawberry                                                  
             79. output_FL       > SAMSUNG:playback_FL	[active]
             81. output_FR       > SAMSUNG:playback_FR	[active]


```

---

### Post by nobody96 on 2023-01-15
My grub file now looks like this

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash=silent resume=/dev/system/swap mitigations=auto snd_hda_intel power_save=0 quiet security=apparmor nosimplefb=1"
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

I updated grub in terminal using the command and rebooted.
 Still no improvement.

I went to snd_hda_intel to check the parameter file for power saving, and it turned to "1" for some reason. I manually changed it to 0 before.

---

### Post by #&amp;thj^% on 2023-01-15
I seem to have over estimated here:
Your original grub file looked like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
The change should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash snd_hda_intel power_save=0"
```
Nothing else there>>> but what I show in the above^^^^
update grub and reboot

---

### Post by nobody96 on 2023-01-15
That's what I meant by your grub looking different. My said quiet splash. Well, I pasted your first version and rebooted and it didn't break anything. It just booted for 30 seconds.

I changed the grub again. Updated grub in terminal and rebooted. No improvement. I checked again and snd_hda_intel power saving still turned ( itself? ) to "1".

---

### Post by #&amp;thj^% on 2023-01-15
Have you made changes to any sound related settings prior to this thread?
Some realtek cards have rules of their own, not good for a user.
Lets check what you are working with:
```
inxi -A
```
NOTE: this is a sample of mine _only_.
```
Audio:
  Device-1: NVIDIA driver: snd_hda_intel
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound API: ALSA v: k6.1.4-1-default running: yes
  Sound Server-1: PipeWire v: 0.3.64 running: yes


```

---

### Post by nobody96 on 2023-01-15
I only changed and_hda_intel power saving to 0 manually. And attempted to make a service file which would loop a "silent" sound to keep the sound card from sleeping ( didn't work, apparently ).

> Audio:
  Device-1: NVIDIA GP104 High Definition Audio driver: snd_hda_intel
  Device-2: AMD Family 17h HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.19.0-29-generic running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes

words,words,words ( min num characters for posting )

---

### Post by #&amp;thj^% on 2023-01-15
> **nobody96 said:**
> words,words,words ( min num characters for posting )

:lolflag:
I run in a different circle, bleeds over to user forums..
OK Plainly worded now.
I still need to know, Have you made changes to any sound related settings prior to this thread?

---

### Post by nobody96 on 2023-01-15
I only changed and_hda_intel power saving to 0 manually. And attempted  to make a service file which would loop a "silent" sound to keep the  sound card from sleeping ( didn't work, apparently ).

---

### Post by #&amp;thj^% on 2023-01-15
> **nobody96 said:**
> I only changed and_hda_intel power saving to 0 manually. And attempted to make a service file which would loop a "silent" sound to keep the sound card from sleeping ( didn't work, apparently ).

It's only a guess on my part, but that could be the differences between yours and my findings.

---

### Post by nobody96 on 2023-01-15
The service file was only an autostart for a sound looping. Nothing more to it. The .service file isn't even there anymore. 
 
sys/module/snd_hda_intel/parameters/power_save changes value to "1" after reboot, and power_save_controller changes value to "Y" .

I don't know if that's important, but I do have a realtek sound card. Shouldn't it appear on > inxi -A ?

There is a > snd_hda_codec_realtek folder in > /sys/module/

Under > /sys/module/snd_hda_codec_realtek/drivers/hdaudio:snd_hda_codec_realtek/hdaudioC1D0 there is a "chip_name" file, it says "ALC1220"

---

### Post by #&amp;thj^% on 2023-01-15
> **nobody96 said:**
> 
There is a  folder in 

Under  there is a "chip_name" file, it says "ALC1220"

Bingo there it is....
It should show as realtek in a perfect world, some vendors just do things different.
I'm not sure how to advise you now.
Don't kill the messenger:
> Reltek HD-audio drivers _have the automatic power-saving mode_. This feature is enabled via Kconfig CONFIG_SND_AC97_POWER_SAVE and CONFIG_SND_HDA_POWER_SAVE options, respectively.

With the automatic power-saving, the driver turns off the codec power appropriately when no operation is required. When no applications use the device and/or no analog loopback is set, the power disablement is done fully or partially.** It&#8217;ll save a certain power consumption, thus good for laptops (even for desktops)**.

---

### Post by nobody96 on 2023-01-16
Well, this sucks.
I wonder who was the person that thought that was a good idea.
Thanks for trying.

Perhaps, someone here can tell me how to make a working, looping dummy silent sound process that autoruns on boot and keeps the sound card from going to sleep. The one I found somewhere else didn't work for some reason. I wanted to paste what was in it exactly but I can't to find the source.

---

### Post by #&amp;thj^% on 2023-01-16
I just now noticed this was your first post here in UF, and as luck would have it, you ended up with me. :(
Welcome to the forums, I hope I did not leave a bad taste for your first post.

---

