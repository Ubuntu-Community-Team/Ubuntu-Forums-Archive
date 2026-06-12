---
title: "No sound with Ubuntu 22.04.2 LTS on Asus Zenbook UX582L"
date: 2023-07-04
forum: General Help
---

### Post by ubuuseraa on 2023-07-04
[COLOR=#232629][FONT=-apple-system]I installed Ubuntu 22.04.2 LTS on my new Asus Zenbook (single install not dual-boot) No sound comes out from the speakers, or the headphones jack (while in Windows sound is ok).[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I previously tried with Kali-Linux and it didn't work either. For several days I browsed similar "no sound questions", but it didn't work out. So now I freshly re-installed ubuntu 22.04.2, updated it, and installed pavucontrol, and inxi only for a fresh start.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Hoping someone can help I put some useful information below.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Thanks,


[/FONT][/COLOR] [COLOR=#232629][FONT=-apple-system]LINUX username 5.19.0-46-generic #47~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Jun 21 15:35:31 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]alsamixer[/FONT][/COLOR]
| Card: HDA Intel PCH
&#9474; Chip: Realtek ALC294
&#9474; View: Playback 
&#9474; Item: Master

[COLOR=#232629][FONT=-apple-system]Everything is on, "OO", Auto-Mute is disabled
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]inxi -SMAG
[/FONT][/COLOR]
System:
  Host: Username Kernel: 5.19.0-46-generic x86_64
    bits: 64 Desktop: GNOME 42.5
    Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: ASUSTeK
    product: ZenBook Pro Duo UX582LR_UX582LR v: 1.0
    serial: <superuser required>
  Mobo: ASUSTeK model: UX582LR v: 1.0
    serial: <superuser required> UEFI: American Megatrends
    v: UX582LR.305 date: 12/30/2021
Graphics:
  Device-1: Intel CometLake-H GT2 [UHD Graphics]
    driver: i915 v: kernel
  Device-2: NVIDIA GA104M [GeForce RTX 3070 Mobile / Max-Q] driver: nvidia v: 535.54.03
  Device-3: USB C Video Adaptor type: USB driver: N/A
  Device-4: IMC Networks USB2.0 HD UVC WebCam type: USB
    driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa
    gpu: i915 resolution: 1: 3840x1100~60Hz
    2: 1680x1050~60Hz 3: 3840x2160~60Hz
  OpenGL:
    renderer: NVIDIA GeForce RTX 3070 Laptop GPU/PCIe/SSE2
    v: 4.6.0 NVIDIA 535.54.03
Audio:
  Device-1: Intel Comet Lake PCH cAVS driver: snd_hda_intel
  Device-2: NVIDIA GA104 High Definition Audio
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.19.0-46-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

[COLOR=#232629][FONT=-apple-system]pavucontrol
[/FONT][/COLOR]
Output devices: Built-in Audio Analog Stereo
Port: Speakers (on which I can see the audio bar moving when playing a youtube video)
Configuration: Analog Stereo Duplex/Analog Stereo Output (same thing)
 
[COLOR=#232629][FONT=-apple-system]cat /etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]

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
options snd-hda-intel model=asus-zenbook
[COLOR=#232629][FONT=-apple-system]alsa-info (scanned alsa-info) ---[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][URL="http://alsa-project.org/db/?f=76a4508f951d475f28e92f6e5f1bf5f211d420aa"]http://alsa-project.org/db/?f=76a4508f951d475f28e92f6e5f1bf5f211d420aa
[/URL][/FONT][/COLOR]

---

### Post by Xian on 2023-07-04
Hard to pin down. You might review here for ideas:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1850439/comments/170](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1850439/comments/170)

---

### Post by ubuuseraa on 2023-07-11
not helped i tried that methods and nothing is working and also i tried these but no luck [https://askubuntu.com/questions/1476088/no-sound-with-ubuntu-22-04-2-lts-on-asus-zenbook-ux582l](https://askubuntu.com/questions/1476088/no-sound-with-ubuntu-22-04-2-lts-on-asus-zenbook-ux582l)

---

### Post by ubuuseraa on 2023-07-11
Never Mind i just fixed it by updating the kernal to 6.4.3 generic and reboot after reboot just updated the ubuntu

---

### Post by neodiz on 2023-08-10
I have same laptop, but its not work.

---

### Post by sienile on 2023-08-12
> **ubuuseraa said:**
> Never Mind i just fixed it by updating the kernal to 6.4.3 generic and reboot after reboot just updated the ubuntu
How did you manage to get that installed? Highest kernel version I see in the repos is 6.2.0.26.26.

---

### Post by kneboo on 2024-01-08
[link to topic]("https://phoenixnap.com/kb/how-to-update-kernel-ubuntu")  There is a way called Mainline that can help you to install yet tested kernels)

---

