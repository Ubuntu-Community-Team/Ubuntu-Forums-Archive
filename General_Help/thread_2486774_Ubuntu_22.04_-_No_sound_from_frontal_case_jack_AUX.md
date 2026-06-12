---
title: "Ubuntu 22.04 - No sound from frontal case jack AUX"
date: 2023-05-10
forum: General Help
---

### Post by ricciolino on 2023-05-10
I already see all similar post around the web without finding a working solution.
I am in this situation:

[LIST]
[*]Dual boot: **Windows 11 - Ubuntu 22.04** (audio works normal in Windows 11) 
[*]HW infos:
[LIST]
[*]MB: **MAG Z690 TOMAHAWK WIFI DDR4 (MS-7D32)** 
[*]CPU: **13th Gen Intel(R) Core(TM) i7-13700K** 
[*]GPU: **GeForce RTX 3080 Lite Hash Rate** 
[/LIST]
  
[*]Audio controller: 
[/LIST]

```

> lspci -v | grep -i audio
00:1f.3 Audio device: Intel Corporation Alder Lake-S HD Audio Controller (rev 11)
01:00.1 Audio device: NVIDIA Corporation GA102 High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. GA102 High Definition Audio Controller
```

[LIST]
[*]alsa-base.conf: 
[/LIST]

```
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
```

[LIST]
[*]alsamixer card images: see attachments (alsamixer_1.png,alsamixer_2.png,alsamixer_3.png) 
[/LIST]
 
[LIST]
[*]sound settings image (headphone from frontal case AUX jack are correctly detected, but no sound emitted): see attachments (settings_sound.png) 
[/LIST]
[B] 
I can't understand why rear AUX jack is working perfectly, if I attach my headphone to the rear jack, sound is emitted correctly, whilst frontal AUX jack it just looks dead (same frontal AUX jack that is working perfectly on Windows)[/B]
Someone know what is happening?

---

### Post by carlos-cardano on 2023-11-24
Yup. I've spent hours on this and I can't get it to work. Exact same issue. I have a Phanteks case and it's a new build. I checked on the [Linux Mint thread]("https://forums.linuxmint.com/viewtopic.php?t=317609") and it looks like people there have a similar issue. I'll be following this post carefully cuz there's gotta be a simple reason. We're just forced into digging deeper.

---

### Post by MAFoElffen on 2023-11-25
Please show the output of this, posted within CODE Tags:
```

LANG=C pacmd list-sinks | grep -e '-output-'

```

---

### Post by ricciolino on 2023-11-27
When the headphones are plugged in:
```

> LANG=C pacmd list-sinks | grep -e '-output-'
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: yes)
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: yes)
    active port: <analog-output-headphones>
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: yes)
    active port: <hdmi-output-1>

```




When they are not plugged:
```

> LANG=C pacmd list-sinks | grep -e '-output-'
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: yes)
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: yes)
    active port: <analog-output-headphones>
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: yes)
    active port: <hdmi-output-1>

```

---

### Post by ricciolino on 2023-11-27
I just added two attachments showing the output devices list when the headphones are attached and when they are not attached.

---

### Post by ricciolino on 2023-11-27
I also see this post

[https://forum.manjaro.org/t/sound-from-speakers-no-sound-from-3-5mm-jack-audio/5343/28](https://forum.manjaro.org/t/sound-from-speakers-no-sound-from-3-5mm-jack-audio/5343/28)

I also tried adding

*```
*
*options snd-hda-intel model=headset-mode*[I]

```[/I]
[I]
to [/I]*```
*/etc/modprobe.d/alsa.conf*
```*

But this not works for me :(

---

### Post by donald187 on 2023-11-28
Since there doesn't seem to be any headway on this I'll add my experience from Debian 12 using the Backports kernel.

A year and  half ago I got a new computer.  Sometimes the rear port would not work.  It wouldn't cut in and out.  If it worked then it would keep working (playing a video for instance).  If it wasn't working it would continue to not work (again on a video for instance).  Just sometimes it would work and sometimes it wouldn't.  It worked on both Windows and Ubuntu.  The front panel jack worked fine on Debian as did sound over Bluetooth.

I later discovered that it would work consistently with kernel 5.15 (the first kernel version where my sound card was supported) but not consistently on 5.16 and later.  It seems to have been some kind of regression in the kernel.  Finally the 6.1 kernel solved the problem.  I seem to recall (but may be wrong) that Cirrus Logic, the maker of my sound card, put out a patch.

If you want to see my travails and read a bunch of attempts that didn't work here's the thread.

[https://forums.debian.net/viewtopic.php?t=152359](https://forums.debian.net/viewtopic.php?t=152359)

EDIT:  The reason it worked on Ubuntu was that Ubuntu was using the 5.15 kernel.  When it started using the 5.19 (?) kernel the back sound jack started having problems too.  But after a week or two the problems went away so I would assume that Ubuntu fixed the problem.

---

### Post by ricciolino on 2023-11-28
> **donald187 said:**
> Since there doesn't seem to be any headway on this I'll add my experience from Debian 12 using the Backports kernel.

A year and  half ago I got a new computer.  Sometimes the rear port would not work.  It wouldn't cut in and out.  If it worked then it would keep working (playing a video for instance).  If it wasn't working it would continue to not work (again on a video for instance).  Just sometimes it would work and sometimes it wouldn't.  It worked on both Windows and Ubuntu.  The front panel jack worked fine on Debian as did sound over Bluetooth.

I later discovered that it would work consistently with kernel 5.15 (the first kernel version where my sound card was supported) but not consistently on 5.16 and later.  It seems to have been some kind of regression in the kernel.  Finally the 6.1 kernel solved the problem.  I seem to recall (but may be wrong) that Cirrus Logic, the maker of my sound card, put out a patch.

If you want to see my travails and read a bunch of attempts that didn't work here's the thread.

[https://forums.debian.net/viewtopic.php?t=152359](https://forums.debian.net/viewtopic.php?t=152359)

EDIT:  The reason it worked on Ubuntu was that Ubuntu was using the 5.15 kernel.  When it started using the 5.19 (?) kernel the back sound jack started having problems too.  But after a week or two the problems went away so I would assume that Ubuntu fixed the problem.

Thanks for sharing your experience.
I just tried to switch to 6.2.0-37-generic kernel, but the issue persist for me.

---

### Post by ricciolino on 2023-11-28
I finally found the solution!!! :smile:
I just discovered the **MAG Z690 TOMAHAWK WIFI** needs an update version of [**alsa-ucm-conf**]("https://github.com/alsa-project/alsa-ucm-conf/tree/master") configuration file ([FONT=courier new]/usr/share/alsa/ucm2/USB-Audio/USB-Audio.conf[/FONT]).
Check the sound card USB device with:

```

> lsusb | grep -i audio
Bus 001 Device 003: ID 0db0:b202 Micro Star International USB Audio

```

In my case [FONT=courier new]0db0:b202[/FONT] certify the **MAG Z690 TOMAHAWK WIFI** is the device I have actually installed on my system.
Then execute the following commands in sequence:

```

sudo mv /usr/share/alsa/ucm /usr/share/alsa/ucm.bak
sudo mv /usr/share/alsa/ucm2 /usr/share/alsa/ucm2.bak
curl -L -o alsa-ucm-conf.tar.gz https://github.com/alsa-project/alsa-ucm-conf/archive/refs/heads/master.tar.gz
sudo tar xvzf alsa-ucm-conf.tar.gz -C /usr/share/alsa --strip-components=1 --wildcards "*/ucm" "*/ucm2"
rm alsa-ucm-conf.tar.gz

```

Then reboot and now you should have the front-chassis jack-AUX working as expected.

You can then check that the updated configuration file ([FONT=courier new]/usr/share/alsa/ucm2/USB-Audio/USB-Audio.conf[/FONT]) now supports the **MSI MAG Z690 Tomahawk Wifi** motherboard.

```

> cat /usr/share/alsa/ucm2/USB-Audio/USB-Audio.conf | grep 0db0:b202
        # 0db0:b202 MSI MAG Z690 Tomahawk Wifi

```

---

### Post by MAFoElffen on 2023-11-28
Happy you found that and it works for you.

---

### Post by ricciolino on 2023-12-07
Stopped working again :(

Don't know why...

Still this return correct...
```


> cat /usr/share/alsa/ucm2/USB-Audio/USB-Audio.conf | grep 0db0:b202
        # 0db0:b202 MSI MAG Z690 Tomahawk Wifi


```

I also tried to re-apply steps, but with no lucky...

What could be happened this time ?

---

### Post by ricciolino on 2023-12-07
I temporary solved this issue by applying following workaround (dirty solution).

Created systemd user service:

```

> cat $HOME/.config/systemd/user/front-headphones-switch-handler.service 
[Unit]
Description=Run front-headphones-switch-handler

[Service]
; Type=oneshot
Type=simple
ExecStart=/usr/local/bin/front-headphones-switch-handler
Restart=on-failure
RestartSec=5

[Install]
WantedBy=default.target

```

And bash script:

```

> cat /usr/local/bin/front-headphones-switch-handler
#!/bin/bash

TARGET_DEVICE="Headphones"

while true; do
    SINK_SELECTED_STATUS=`cat $HOME/.front-headphones-sink-selected-status`

    if [ `pactl list sinks short | grep $TARGET_DEVICE | wc -l` -lt 1 ]; then
        pacmd load-module module-alsa-sink sink_name=$TARGET_DEVICE sink_properties=device.description=$TARGET_DEVICE device=hw:Audio,1 control='PCM',1
        pactl set-default-sink alsa_output.usb-Generic_USB_Audio-00.analog-stereo 2>/dev/null
    fi

    are_front_headphones_attached=$(pacmd list-sinks | grep 'analog-output-headphones' | grep active | wc -l)
    if [ $are_front_headphones_attached -gt 0 ]; then
        if [ "$SINK_SELECTED_STATUS" == "FALSE" ]; then
            pactl set-default-sink "$TARGET_DEVICE" 2>/dev/null
            
            if [ $? -eq 0 ]; then
                echo TRUE > $HOME/.front-headphones-sink-selected-status
            else
                notify-send "front-headphones-switch-handler" "ERROR in setting front-headphones as output device"
            fi
        fi

    else
        is_speaker_already_default=$(pacmd list-sinks | grep 'analog-output-speaker' | grep active | wc -l)
        if [ $is_speaker_already_default -gt 0 ]; then
            if [ "$SINK_SELECTED_STATUS" == "FALSE" ]; then
                sleep 0.5
                continue
            fi
        fi

        pactl set-default-sink alsa_output.usb-Generic_USB_Audio-00.analog-stereo 2>/dev/null
        
        if [ $? -eq 0 ]; then
            echo FALSE > $HOME/.front-headphones-sink-selected-status
        else
            notify-send "front-headphones-switch-handler" "ERROR in setting speaker as output device"
        fi
    fi

    sleep 0.5
done

exit 0

```

So that each time I attach my headphones to the front AUX jack, the bash daemon detect them and it switches to new dedicated sink for redirecting the audio.

---

