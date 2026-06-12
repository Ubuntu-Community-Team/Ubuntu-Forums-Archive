---
title: "Why Can't I Run alsa-tools-gui?"
date: 2022-05-06
forum: General Help
---

### Post by Mark76 on 2022-05-06
I'm trying to fix a long running problem with pulseaudio/alsa not connecting to my laptop's onboard sound card, the Intel HDA Intel PCH.  One of the threads I looked at recommended using alsa tools but I can't even get it to run. ](*,):cry:

---

### Post by #&amp;thj^% on 2022-05-06
> **Mark76 said:**
> (*,):cry:
After installed, I could be wrong here but it should give more options in "alsamixer"
```
alsamixer --help
Usage: alsamixer [options]
Useful options:
  -h, --help              this help
  -c, --card=NUMBER       sound card number or id
  -D, --device=NAME       mixer device name
  -m, --mouse             enable mouse
  -M, --no-mouse          disable mouse
  -f, --config=FILE       configuration file
  -F, --no-config         do not load configuration file
  -V, --view=MODE         starting view mode: playback/capture/all
Debugging options:
  -g, --no-color          toggle using of colors
  -a, --abstraction=NAME  mixer abstraction level: none/basic

```
More info: [https://www.maketecheasier.com/alsa-utilities-manage-linux-audio-command-line/](https://www.maketecheasier.com/alsa-utilities-manage-linux-audio-command-line/)

---

### Post by Mark76 on 2022-05-06
Well, apparently alsa can't see my soundcard.

---

### Post by #&amp;thj^% on 2022-05-06
That's not good, but a start anyway.
what shows here:
```
inxi -A
Audio:
  Device-1: Intel 82801I HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-27-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```

---

### Post by Mark76 on 2022-05-06
This

> Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-27-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
mark@mark-laptop:~$ 


---

### Post by #&amp;thj^% on 2022-05-06
Interesting, PulseAudio is a layer between ALSA and sound applications, it won't work if ALSA does not work. 
what shows here: "lsmod | grep snd_hda_intel"

```
lsmod | grep snd_hda_intel
snd_hda_intel          61440  2
snd_intel_dspcfg       36864  1 snd_hda_intel
snd_hda_codec         188416  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core          122880  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_pcm               176128  11 snd_sof_amd_acp,snd_hda_codec_hdmi,snd_pci_acp6x,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_sof,snd_compress,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
snd                   135168  24 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi

```
and here: "lspci -nnk | grep -A2 Audio"
```

me on Fri May 06 at 12:20 PM in ~ branch: (HEAD) 
>> lspci -nnk | grep -A2 Audio
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10fa] (rev a1)
	Subsystem: NVIDIA Corporation Device [10de:10fa]
	Kernel driver in use: snd_hda_intel
--
04:00.5 Multimedia controller [0480]: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor [1022:15e2] (rev 01)
	Subsystem: Lenovo Device [17aa:381c]
	Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x, snd_sof_amd_renoir
04:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller [1022:15e3]
	Subsystem: Lenovo Device [17aa:381b]
	Kernel driver in use: snd_hda_intel


```
If you can see snd_hda_intel you may get lucky by adding, You need to add options **_snd-hda-intel model=generic _**at the end of the **_/etc/modprobe.d/alsa-base.conf_** file. Do not modify anything else in this file!

The easy way:
```
echo "options snd-hda-intel model=generic" | sudo tee -a /etc/modprobe.d/alsa-base.conf


```
Only run this command once because it adds this line each time you run it! If you want to modify it, open /etc/modprobe.d/alsa-base.conf as root with a text editor. Good Luck

---

### Post by Mark76 on 2022-05-06
First command

> snd_hda_intel          53248  1
snd_intel_dspcfg       28672  1 snd_hda_intel
snd_hda_codec         155648  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core          110592  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_pcm               139264  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd                   102400  11 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi

2nd command

> 00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
	Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family High Definition Audio Controller [103c:161c]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


---

### Post by #&amp;thj^% on 2022-05-06
> **Mark76 said:**
> First command



2nd command

Try that bottom line of code i mentioned, and reboot.
```
echo "options snd-hda-intel model=generic" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
After check in System Settings > Sound.

---

### Post by Mark76 on 2022-05-06
Well.  The good news is that I now have a working digital stereo HDMI output.  The bad news is I don't have anything HDMI and what I really need is the stereo analog duplex (output and input).

But at least something changed.

---

### Post by #&amp;thj^% on 2022-05-06
Ok we might need to open it a bit more:
```
echo "options snd-hda-intel dmic_detect=0" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
it shouldn't need to blacklist snd_soc_skl, but for this run we will
```
echo "blacklist snd_soc_skl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
yep another reboot

---

### Post by Mark76 on 2022-05-06
Hmm.  Still only have the Stereo Digital (HDMI) Output.

Odd.

---

### Post by #&amp;thj^% on 2022-05-06
have you tried kernel "linux-image-5.17.0-1003-oem/jammy 5.17.0-1003.3 amd64  Signed kernel image OEM"
EDIT: I forgot to ask if this is a dual boot with windows 10/11

---

### Post by Mark76 on 2022-05-06
How do I do that?

---

### Post by #&amp;thj^% on 2022-05-06
like:
```
sudo apt install linux-image-5.17.0-1003-oem
```
```
following additional packages will be installed:
  linux-modules-5.17.0-1003-oem
Suggested packages:
  fdutils linux-oem-5.17-tools linux-headers-5.17.0-1003-oem
The following NEW packages will be installed:
  linux-image-5.17.0-1003-oem linux-modules-5.17.0-1003-oem
```
you'll want the headers as well:
```
sudo apt install  sudo apt install fdutils linux-headers-5.17.0-1003-oem

```
reboot to that new kernel, any difference?

---

### Post by Mark76 on 2022-05-06
Nope.

Is it possible there's a problem with the hardware?

---

### Post by Mark76 on 2022-05-06
Nope.

Is it possible there's a problem with the hardware?

---

### Post by #&amp;thj^% on 2022-05-06
anything is possible, your card should have worked straight away>>OOTB
If you still have your live installer (USB) boot to that and Try Ubuntu not Install Ubuntu, and check if it works from that session.
that will help to know if it is a hardware issue.

---

### Post by Mark76 on 2022-05-06
I can confirm that I have the same problem when running a Ubuntu live session.

---

### Post by #&amp;thj^% on 2022-05-06
Sorry to hear that, I wish I had a magic bullet for that but I don't. :(

---

### Post by Mark76 on 2022-05-06
Do you have a circuit diagram of an HP EliteBook 8460P?

---

### Post by #&amp;thj^% on 2022-05-06
my friends at lab1 do: [https://www.laboneinside.com/hp-elitebook-8460p-6460b-schematic-diagram/](https://www.laboneinside.com/hp-elitebook-8460p-6460b-schematic-diagram/)

---

### Post by Mark76 on 2022-05-06
Cheers :D

---

### Post by Mark76 on 2022-05-07
Update.  So, on a whim I went into the BIOS and disabled and then reenabled Audio.  The result of which was that I lost sound completely for some reason,  Even over bluetooth, Luckily I managed to fix that by completely purging Alsa and PipeWire from the system but I'm now back to square one.  But it's no big loss and at least I can still listen to things over bluetooth.

Should I start a new thread "Pulseaudio Can't Connect To My Infel HDA PCH Soundcard"?

---

### Post by #&amp;thj^% on 2022-05-07
> **Mark76 said:**
> Update.  So, on a whim I went into the BIOS and disabled and then reenabled Audio.  The result of which was that I lost sound completely for some reason,  Even over bluetooth, Luckily I managed to fix that by completely purging Alsa and PipeWire from the system but I'm now back to square one.  But it's no big loss and at least I can still listen to things over bluetooth.

Should I start a new thread "Pulseaudio Can't Connect To My Infel HDA PCH Soundcard"?

No here is fine.
Mark76 This just seems so very odd, I have to admit I'm bit out of my normal here.
can you post this now:
```
LANG=C pactl info | grep '^Server Name'

```
The more I think about this, it really sounds like a bug,

---

### Post by Mark76 on 2022-05-07
Hey 1fallen.  Thanks for sticking around.   Output of command was 

> ANG=C pactl info | grep '^Server Name'
Server Name: pulseaudio


---

### Post by #&amp;thj^% on 2022-05-07
No problem. :)
Before I start let me be clear, your card should have worked OTB, no user intervention needed.
So i don't get you even more goofed up, have you tried with; pavucontrol?

```
apt policy pavucontrol
```
sometimes it just needs a nudge in the "configuration tab"
this is different from what ubuntu use's for volume control.

---

### Post by Mark76 on 2022-05-07
Output of that command was 
> apt policy pavucontrol
pavucontrol:
  Installed: 5.0-2
  Candidate: 5.0-2
  Version table:
 *** 5.0-2 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
        100 /var/lib/dpkg/status


The laptop I'm using Ubuntu on is a second hand EliteBook 8460P.

---

### Post by #&amp;thj^% on 2022-05-07
> **Mark76 said:**
> 
The laptop I'm using Ubuntu on is a second hand EliteBook 8460P.
Good to know, thanks.

Stabing in the dark now, the debian devs always push wireplumber: [https://wiki.debian.org/PipeWire#Bluetooth](https://wiki.debian.org/PipeWire#Bluetooth)
I use it some in testing things but not related to your issue.
```
sudo apt install wireplumber pipewire-media-session-
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libwireplumber-0.4-0 pipewire-pulse
The following packages will be REMOVED:
  pipewire-media-session
The following NEW packages will be installed:
  libwireplumber-0.4-0 pipewire-pulse wireplumber
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 312 kB of archives.
After this operation, 932 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 libwireplumber-0.4-0 amd64 0.4.8-4 [253 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 wireplumber amd64 0.4.8-4 [52.9 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 pipewire-pulse amd64 0.3.48-1ubuntu1 [6,604 B]
Fetched 312 kB in 1s (351 kB/s)      
Selecting previously unselected package libwireplumber-0.4-0:amd64.
(Reading database ... 198883 files and directories currently installed.)
Preparing to unpack .../libwireplumber-0.4-0_0.4.8-4_amd64.deb ...
Unpacking libwireplumber-0.4-0:amd64 (0.4.8-4) ...
dpkg: pipewire-media-session: dependency problems, but removing anyway as you re
quested:
 gnome-remote-desktop depends on pipewire-media-session | wireplumber; however:
  Package pipewire-media-session is to be removed.
  Package wireplumber is not installed.

(Reading database ... 198904 files and directories currently installed.)
Removing pipewire-media-session (0.4.1-2ubuntu1) ...
Selecting previously unselected package wireplumber.
(Reading database ... 198894 files and directories currently installed.)
Preparing to unpack .../wireplumber_0.4.8-4_amd64.deb ...
Unpacking wireplumber (0.4.8-4) ...
Selecting previously unselected package pipewire-pulse.
Preparing to unpack .../pipewire-pulse_0.3.48-1ubuntu1_amd64.deb ...
Unpacking pipewire-pulse (0.3.48-1ubuntu1) ...
Setting up libwireplumber-0.4-0:amd64 (0.4.8-4) ...
Setting up wireplumber (0.4.8-4) ...
Failed to preset unit, file /etc/systemd/user/pipewire-session-manager.service a
lready exists and is a symlink to /usr/lib/systemd/user/pipewire-media-session.s
ervice.
Created symlink /etc/systemd/user/pipewire.service.wants/wireplumber.service \u2192 /
usr/lib/systemd/user/wireplumber.service.
/usr/bin/deb-systemd-helper: error: systemctl preset failed on wireplumber.servi
ce: No such file or directory
Setting up pipewire-pulse (0.3.48-1ubuntu1) ...
Created symlink /etc/systemd/user/default.target.wants/pipewire-pulse.service \u2192 
/usr/lib/systemd/user/pipewire-pulse.service.
Created symlink /etc/systemd/user/sockets.target.wants/pipewire-pulse.socket \u2192 /
usr/lib/systemd/user/pipewire-pulse.socket.
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...
```
lets start it:
```

me@me-Standard-PC-Q35-ICH9-2009:~$ systemctl --user --now enable wireplumber.service
Created symlink /home/me/.config/systemd/user/pipewire-session-manager.service \u2192 /usr/lib/systemd/user/wireplumber.service.
Created symlink /home/me/.config/systemd/user/pipewire.service.wants/wireplumber.service \u2192 /usr/lib/systemd/user/wireplumber.service.
```

---

### Post by Mark76 on 2022-05-07
Okie doakie done that.  What happens now?

---

### Post by #&amp;thj^% on 2022-05-07
open pavucontrol, see if any settings allow the speakers

---

### Post by Mark76 on 2022-05-07
Done that and I'm afraid the answer is still no :(

---

### Post by #&amp;thj^% on 2022-05-07
If any of those chip-blocks received more than 19V it will take it out, and not to be pessimistic but it moves to the next block overloading that one etc, etc
My friend I'm just out of ideas now, maybe someone will come up with something, doubtful but maybe.

---

### Post by Mark76 on 2022-05-07
If it helps here's the output of lspci

> lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
**[COLOR="#0000FF"]00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)[/COLOR]**
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller (rev 04)
23:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
23:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
23:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
24:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
25:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)


---

### Post by #&amp;thj^% on 2022-05-07
The fact all that shows up in lspci, tells me something hardware related is at hand.

---

### Post by Mark76 on 2022-05-07
At least it shows up.  So we know it's not disconnected in some way.

---

### Post by #&amp;thj^% on 2022-05-07
If you have any  "phone jack" speakers or headphones, you could see if that would work.

---

### Post by Mark76 on 2022-05-07
The phones output definitely isn't working.

---

