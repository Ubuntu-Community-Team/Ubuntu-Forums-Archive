---
title: "Why Ubunut is plagued with HDMI sound problems? Can't finx fix"
date: 2017-06-02
forum: General Help
---

### Post by gil80 on 2017-06-02
Hi,

I've been trying in the last 2 months to solve the No HDMI sound issue to no avail.
I now have the latest 17.04 ubuntu version.
I've tried almost every solution I could find in google, but nothing is working.
Mind you, when I use windows 10 with the same HDMI output, there are no issues.

This is Alienware M11xR3 laptop, powered by Nvidia GPU and intel iGPU.
I believe the HDMI output is controlled by Intel sound controller and not Nvidia.

I have the latest tested and recommended drivers for Nvidia, regardlessly.

I can only output sound via internal speakers or analogue output.
The HDMI output DOES display image when connected to my TV, but still no sound.
The sound option is not found under Pulse Audio or 'alsamixer' settings.

Can someone in this community help out please?

```

gil@gil-M11xR3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC665 Analog [ALC665 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gil@gil-M11xR3:~$ 


```

```

gil@gil-M11xR3:~$ sudo lspci -H1

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation QS67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev a1)
07:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
0d:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
13:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
13:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)


```

---

### Post by Bucky Ball on 2017-06-02
Have you looked in PulseAudio Volume Control at the 'Configuration' tab? 

There, you should see the first entry as a HDMI device. Next to profile, do you have the right HDMI device chosen from the drop-down list there? 

The second entry below the HDMI one, 'Built in audio', should have your analogue devices; generally 'Analogue Stereo Duplex'.

Have a look and make sure the HDMI setting in the first entry in 'Profile' is the correct one. If it is, then play an audio stream (get some music going or play Youtube clip; anything with sound). In PAVControl, go to 'Playback'. 

See the audio stream bouncing up and down? To the right above it, it is probably set to you Analogue Audio. Click there and in the drop-down menu, _*set the output device to the HDMI device you have assigned in the 'Configuration' tab*_.

Any luck?

---

### Post by qyot27 on 2017-06-02
Did you install and try to use kernel v4.11?  That's when HDMI sound for Intel's BayTrail SoCs landed - maybe it's relevant for any kind of HDMI sound over Intel chipsets.

---

### Post by gil80 on 2017-06-03
> **qyot27 said:**
> Did you install and try to use kernel v4.11?  That's when HDMI sound for Intel's BayTrail SoCs landed - maybe it's relevant for any kind of HDMI sound over Intel chipsets.

I don't know which kernel version I have, or how to upgrade it. I know I have the latest ubuntu version as mentioned in OP.


> **Bucky Ball said:**
> Have you looked in PulseAudio Volume Control at the 'Configuration' tab? 

There, you should see the first entry as a HDMI device. Next to profile, do you have the right HDMI device chosen from the drop-down list there? 

The second entry below the HDMI one, 'Built in audio', should have your analogue devices; generally 'Analogue Stereo Duplex'.

Have a look and make sure the HDMI setting in the first entry in 'Profile' is the correct one. If it is, then play an audio stream (get some music going or play Youtube clip; anything with sound). In PAVControl, go to 'Playback'. 

See the audio stream bouncing up and down? To the right above it, it is probably set to you Analogue Audio. Click there and in the drop-down menu, _*set the output device to the HDMI device you have assigned in the 'Configuration' tab*_.

Any luck?

Nope... I have no HDMI option to select from that menu.

---

### Post by LastDino on 2017-06-03
I've found that most people get through HDMI sound problems with TV with "pulsaudio -k" command

Detailed guide
[https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/](https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/)

What I do usually is

[LIST=1]
[*]Connect HDMI cable to TV and switch on the TV. 
[*]Run the below command on a console (It worked without sudo)

  ```
pulseaudio -k
``` 
[*]Open Sound settings, you should see "HDMI/Display Port" entry under Output tab. 
[/LIST]

---

### Post by qyot27 on 2017-06-03
> **gil80 said:**
> I don't know which kernel version I have, or how to upgrade it. I know I have the latest ubuntu version as mentioned in OP.
Then you don't.  17.04 ships with v4.10; 17.10 will ship with v4.12 so if v4.11 works for you now, the next release of Ubuntu (in October) will 'just work', without you needing to take any intervention.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.3/)

Download the *.deb files you need (amd64 most likely, i386 if you're using 32-bit Ubuntu) and install them.  You may need to run *sudo update-grub2* afterward.  Then restart the computer and select the v4.11 kernel from the GRUB list - you may need to go into the 'Advanced options for Ubuntu' menu item to see them.  After logging in, check if the kernel is the correct one:
```
uname -a
```
And then check if PulseAudio can find your HDMI device like you were doing before.


It's also possible to use the third-party tool [Ukuu](https://launchpad.net/ukuu) to avoid having to download the debs yourself:
```
sudo add-apt-repository ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install ukuu
```
Tell Ukuu to download the kernel list:
```
sudo ukuu --check
```
Then parse out the right install name for the kernel:
```
 sudo ukuu --list | grep "v4.11"
```
Which should provide the list of proper names in the left column of the results: v4.11, v4.11.3, etc.  You'll use this to install like so:
```
sudo ukuu --install v4.11
```

---

### Post by gil80 on 2017-06-04
> **qyot27 said:**
> Then you don't.  17.04 ships with v4.10; 17.10 will ship with v4.12 so if v4.11 works for you now, the next release of Ubuntu (in October) will 'just work', without you needing to take any intervention.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.3/)

Download the *.deb files you need (amd64 most likely, i386 if you're using 32-bit Ubuntu) and install them.  You may need to run *sudo update-grub2* afterward.  Then restart the computer and select the v4.11 kernel from the GRUB list - you may need to go into the 'Advanced options for Ubuntu' menu item to see them.  After logging in, check if the kernel is the correct one:
```
uname -a
```
And then check if PulseAudio can find your HDMI device like you were doing before.


It's also possible to use the third-party tool [Ukuu]("https://launchpad.net/ukuu") to avoid having to download the debs yourself:
```
sudo add-apt-repository ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install ukuu
```
Tell Ukuu to download the kernel list:
```
sudo ukuu --check
```
Then parse out the right install name for the kernel:
```
 sudo ukuu --list | grep "v4.11"
```
Which should provide the list of proper names in the left column of the results: v4.11, v4.11.3, etc.  You'll use this to install like so:
```
sudo ukuu --install v4.11
```


Hi.

I can't install it with the commands you kindly provided. I get the following:

```
Need to get 4,059 kB/73.6 MB of archives.
After this operation, 17.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Ign:1 http://au.archive.ubuntu.com/ubuntu zesty/main amd64 aptitude-common all 0.8.3-1ubuntu4
Err:2 http://au.archive.ubuntu.com/ubuntu zesty/main amd64 libcwidget3v5 amd64 0.5.17-4ubuntu2
  403  Forbidden
Err:3 http://au.archive.ubuntu.com/ubuntu zesty/main amd64 aptitude amd64 0.8.3-1ubuntu4
  403  Forbidden
Err:4 http://au.archive.ubuntu.com/ubuntu zesty/main amd64 libc-ares2 amd64 1.12.0-1
  403  Forbidden
Err:5 http://au.archive.ubuntu.com/ubuntu zesty/universe amd64 aria2 amd64 1.30.0-2
  403  Forbidden
Err:1 http://au.archive.ubuntu.com/ubuntu zesty/main i386 aptitude-common all 0.8.3-1ubuntu4
  403  Forbidden
Get:6 http://ppa.launchpad.net/teejee2008/ppa/ubuntu zesty/main amd64 ukuu amd64 17.2.3~77~ubuntu17.04.1 [217 kB]
Fetched 217 kB in 3s (63.9 kB/s)                    
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude-common_0.8.3-1ubuntu4_all.deb  403  Forbidden
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/cwidget/libcwidget3v5_0.5.17-4ubuntu2_amd64.deb  403  Forbidden
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude_0.8.3-1ubuntu4_amd64.deb  403  Forbidden
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/c/c-ares/libc-ares2_1.12.0-1_amd64.deb  403  Forbidden
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/a/aria2/aria2_1.30.0-2_amd64.deb  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

and in the link for downloading the newer kernel, there are several flavors. which should I choose for the amd64

---

### Post by gil80 on 2017-06-04
I downloaded the generic amd64 kernel installed it and booted using this kernel.
it's worse now. hdmi doesn't output image.
Afterwards I installed a kernel header file... not sure what I'm doing here...

---

