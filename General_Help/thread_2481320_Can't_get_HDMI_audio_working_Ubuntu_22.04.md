---
title: "Can't get HDMI audio working Ubuntu 22.04"
date: 2022-11-25
forum: General Help
---

### Post by dwstix86 on 2022-11-25
Hi I have a Radeon RX Vega connected via HDMI to my Sony TV, but cannot get any audio working. I'm running Ubuntu 22.04. I've tried editing grub and adding the intel_iommu=on,etc line in and restarted, no change. The audio settings seem to have the correct output device, radeon HDMI (there are only 2 to choose from the other is the SPDIF which is not selected). Please advise!

Thanks.

---

### Post by MAFoElffen on 2022-11-25
Have you ran
```

alsamixer

```
...and ensured that it is not muted?

That is often overlooked there.

---

### Post by dwstix86 on 2022-11-26
None of the outputs are muted in alsamixer, but none of them are showing hdmi as an output? Only spdif

---

### Post by MAFoElffen on 2022-11-26
If you run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") in detailed mode by appending a "-d" startup option... It will run in detailed mode and supply you with a very detailed sound/audio section of the report.

Select the upload option and post the URL of the pastebin so we can look and see what is going on.

---

### Post by dwstix86 on 2022-11-26
Link to log file: [https://termbin.com/xhh0](https://termbin.com/xhh0)

Thanks for your time, much appreciated

---

### Post by MAFoElffen on 2022-11-27
I am seeing all the HDMI sound devices shown...

Ensure that when you go to Settings > Ouput > Output Device... That it is set to "Digital Output ()S/PDIF). 

If that is set and there is still no sound, then I see you Linux Boot Line set to "quiet splash". Open file /etc/default/grub, with sudo permissions and change the line
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

```
Save. Exit. Then in terminal
```

sudo update-grub

```

If either of those does not work, then please post the output of 
```

pactl list short sinks

```

---

### Post by dwstix86 on 2022-11-27
My audio output gives me to options: "HDMI / Display port 6 - Vega 10 HDMI audio" and "digital output SPDIF", the sound doesn't work with either one.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291309&stc=1[/IMG]

---

### Post by dwstix86 on 2022-11-27
I changed the grub line, still no audio no matter which output device i select. 

I tried pactl, the audio initially shows as "suspended" so i tried killall and then the HDMI shows as "idle" but once i start playing a media file, it shows as "running" but no audio!

=*(***

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291310&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291311&stc=1[/IMG]

---

### Post by dwstix86 on 2022-11-27
i thought maaayyybe it was those dbus error messages so I did sudo apt install dbus-x11 which got rid of the error messages....but alas no audio. =*(***

---

### Post by dwstix86 on 2022-11-29
Any suggestions? Were you able to view the attachments ok?

---

### Post by MAFoElffen on 2022-11-30
Try this
```

pactl set-card-profile 0 alsa_output.pci-0000_29_00.1.hdmi-stereo-extra5

```
That tells it to set it to that profile, unmuted.

if that does work, but it changes each time you log in, then: Activites > Startup Applications > Add ... Add that commamd. That would reset it each time you logged in.

If it still doesn't work, then
```

sudo apt install -y pavucontrol
pavucontrol

```
Set device. Ensure it is not muted. Test by reseting the volume to full... Should hear it while resetting the volumes.

---

### Post by dwstix86 on 2022-11-30
I tried both methods, still no luck! This is so weird. The pactl command says the device is invalid. I already have pavucontrol, I set it to the correct device and turned the volume all the way up, nothing!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291331&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291332&stc=1[/IMG]

---

### Post by MAFoElffen on 2022-11-30
That doesn't make sense. The list show sinks is ID'ing with that, but not being able to set it. Then the Volume Level widget is showing it, but nothing coming out. What the heck?

This is a mystery. Is there any other devices showing in the Volume Level widget to test for sound?

---

### Post by dwstix86 on 2022-11-30
I know! I even copied and pasted the text to make sure there weren't any typos... Tried unplugging HDMI, plugging back in, nothing. The only other audio output device is the SPDIF digital ouput but there's nothing connected to that, and no volume either.r.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291336&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291337&stc=1[/IMG]

---

### Post by dwstix86 on 2022-11-30
Should I try reinstalling Ubuntu?

---

### Post by dwstix86 on 2022-11-30
I thought maybe it was the Radeon drivers but I already reinstalled the latest version

---

### Post by MAFoElffen on 2022-12-01
Let me ask a friend about it...

---

### Post by dwstix86 on 2022-12-01
Ok thanks!

---

### Post by #&amp;thj^% on 2022-12-05
Sorry work has gobbled all my time as of late.
If your still around and unsolved, please  show this:
```
cat /etc/default/grub
### And
cat /proc/asound/cards

```
Mine is a bit different than your model IE:
 ```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd1000000 irq 94
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xd1540000 irq 95
 2 [Dock           ]: USB-Audio - UOEOS Laptop Dock
                      DisplayLink UOEOS Laptop Dock at usb-0000:06:00.4-1.2.1, super speed

```

---

### Post by ajgreeny on 2022-12-05
It may also be worth opening pulseaudio-volume-control if it's installed (if not install it with **sudo apt install pavucontrol** then have a look in the right hand tab, Configuration, of that where it should show several HDMI options, all assuming that you have an HDMI port of course.

Mine shows two profile options in dropdown boxes, one for **Analogue Stereo Duplex** and the other for **Digital Stereo (HDMI) Output**

It is possible that the Digital one may be set to Off instead of one of the needed HDMI options.

See screenshot of my **pavucontrol** window.

---

### Post by dwstix86 on 2022-12-05
Pavucontrol shows everything correctly set. Screenshots attached. Thanks for all your help.

---

### Post by #&amp;thj^% on 2022-12-05
Will you please try turning this setting to off>>>Setting Digital Stereo (IEC958) Output to Off 
Now check your HDMI

---

### Post by dwstix86 on 2022-12-05
You&#8217;re not gonna believe this but I fixed it&#8230; if I set my refresh rate for my display to 30hz, the audio works. But if I set it any higher, for example, 60hz like I had it on, no audio&#8230;huh??

---

### Post by MAFoElffen on 2022-12-05
Dang. LOL. Now I have one more question to ask people... :grin:

---

### Post by ajgreeny on 2022-12-06
Great news! Strange solution, but I'm glad you found it!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by dwstix86 on 2022-12-06
Do you know why this worked or what happened?

---

### Post by #&amp;thj^% on 2022-12-06
> **dwstix86 said:**
> Do you know why this worked or what happened?

I'm  glad you asked,  This might be best documented in the PipeWire FAQ, so that it's documented somewhere that I frequent and brief HDMI (and possibly DisplayPort) audio drop-outs/cuts may be caused by the PCI-E link switching between signalling generations IE:
```
inxi -Alsa -j
Audio:
  Device-1: NVIDIA driver: snd_hda_intel v: kernel pcie: bus-ID: 4-1.2.1:4
    chip-ID: 17e9:4307 gen: 1 speed: 2.5 GT/s class-ID: 0a00 lanes: 8
    serial: 4307293310436 link-max: gen: 3 speed: 8 GT/s lanes: 16
    bus-ID: 01:00.1 chip-ID: 10de:10fa class-ID: 0403
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor vendor: Lenovo driver: N/A
    alternate: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x,
    snd_acp_pci, snd_rpl_pci_acp6x, snd_sof_amd_renoir pcie: gen: 4
    speed: 16 GT/s lanes: 16 bus-ID: 06:00.5 chip-ID: 1022:15e2 class-ID: 0480
  Device-3: AMD Family 17h/19h HD Audio vendor: Lenovo driver: snd_hda_intel
    v: kernel pcie: gen: 4 speed: 16 GT/s lanes: 16 bus-ID: 06:00.6
    chip-ID: 1022:15e3 class-ID: 0403
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound API: ALSA v: k6.0.10-1-default running: yes
  Sound Server-1: PulseAudio v: 16.1 running: no
  Sound Server-2: PipeWire v: 0.3.61 running: yes
Swap:
  Kernel: swappiness: 60 (default) cache-pressure: 100 (default)
  ID-1: swap-1 type: partition size: 7.63 GiB used: 232 MiB (3.0%)
    priority: -2 dev: /dev/dm-1 maj-min: 254:1 mapped: system-swap label: N/A
Sensors:
  System Temperatures: cpu: 48.6 C mobo: N/A gpu: nvidia temp: 37 C
  Fan Speeds (RPM): N/A


```

And Lastly I have Nvidia in the works on mine so on some OS's Arch based and Debian based I'll have to set forcing power saving mode by driver setting. I'm adding "**nvidia-smi --lock-memory-clocks / --reset-memory-clock**s" to my TV on/off button script :)  Fedora and openSUSE was a good to go for sound. (With this on Nvidia Driver** param nosimplefb=1**)


Try using** ibt=off**

---

### Post by dwstix86 on 2022-12-06
I&#8217;m going to be honest&#8230;I have no idea what you just said lol. But a quick google search shows only nvidia uses ibt? I&#8217;m running amd cpu and gpu

---

### Post by #&amp;thj^% on 2022-12-06
> **dwstix86 said:**
> I’m going to be honest…I have no idea what you just said lol. But a quick google search shows only nvidia uses ibt? I’m running amd cpu and gpu

LOL, that's why I don't try to explain in general forums, older experienced user's pick up on the gist of it..
But while I have you will you try with your sound running, now change your refresh rate. It might stutter for a second but should still play sound.

---

### Post by dwstix86 on 2022-12-06
When I switch to 60 the audio completely stops, resumes choppily when I switch back to 30 snd smoothed out snd becomes normal audio after about 5-10s

---

### Post by #&amp;thj^% on 2022-12-06
Ok, I did notice something from the system-info script
What shows with:
```
apt policy amdgpu-install
```
As you can see I also have a AMD Radeon&#8482; Graphics, but I don't recall ever having to install the driver.

---

### Post by MAFoElffen on 2022-12-07
'amd-gpu' is now part of kernel... Like Intel graphics drivers are. AMD opensource'd it and provides to Linux kernel.

---

### Post by #&amp;thj^% on 2022-12-07
> **MAFoElffen said:**
> 'amd-gpu' is now part of kernel... Like Intel graphics drivers are. AMD opensource'd it and provides to Linux kernel.

+1 The other Driver the OP has "may" have something to do with the sound Oddities they are now facing.

---

