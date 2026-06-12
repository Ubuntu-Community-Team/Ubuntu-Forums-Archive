---
title: "HDMI no audio"
date: 2022-07-16
forum: General Help
---

### Post by jgw on 2022-07-16
My sound settings is "HDMI/DisplayPort Built-in-Audio" and that was arrived at automatically. There are no other options, tried a test and nothing. If I have the picture I have to have the sound (they are both in the same cable!) I am missing something here I think.

```
downstairs:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. AMD RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300]
02:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)

```

Any thoughts on this is helpful.

---

### Post by #&amp;thj^% on 2022-07-16
Try this please, In `pavucontrol' go to the last tab "Configuration" and set the Built-in Audio to off. This should force the OS to RS780 HDMI profile.

---

### Post by jgw on 2022-07-16
I am trying things.  I went here:[https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/](https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/)

I changed RS780 HDMI Audio [Radeon 3000/3100 / hd 3200/3300) to
digital stereo (HDMI) output (unplugged) (unavailable) and Built in Audio to 
Analog Stereo Duplex (unplugged) (unavailable)

This didn't change any system sound settings.  I also still can't get sound when trying to test speakers.  I can, however, get sound out of kodi!  I went to see how they had the sound there and I couldn't copy it as it was a moving target and look to be over 100 character song!

I just quit  PulseAudio Volume Control and the sound to kodi still held.  Inside my system sound settings the sound is still at "HDMI/DisplayPort Built-in-Audio" and there is no sound when trying to test the speakers.  I have to figure out how to change the built in audio thing and replace it.  Don't know how to change it.  I am going to leave it alone, for now.

---

### Post by #&amp;thj^% on 2022-07-16
You need to disable the onboard sound for this test to work. (See screenshot)
Also helpful if the Nvidia driver is installed.
Please run the [system-info script ]("https://github.com/UbuntuForums/system-info")and post the link here.

---

### Post by jgw on 2022-07-16
Thanks for the reply.

I rebooted my machine and kodi lost sound (system never had it).  I have now run as you suggested.  Without the second one there was sound but it was blobby and made no sense so I need the second to do the job.  I changed that to Analog Sterio Input (unplugged)(unavailable) and now kodi has sound again. and the top is digital stereo (HDMI) output (unplugged)(unavailable) .

My problem is that I can't figure out how to transfer this to the system settings so that will have too.  When I bring up the system sound the output device is empty.  If I click on it I get HDMI/?Display Port/Built in audio.  Pulse Audio, without configuration has HDMI/DisplayPort(unplugged).  I don't understand the (unplugged)(unavailable) stuff.

---

### Post by #&amp;thj^% on 2022-07-16
Still waiting for the link from the script I've shown.
I need that to minimize guessing.

---

### Post by jgw on 2022-07-16
I think I ran it with:
   Width: 64 bits
    Capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        family=To Be Filled By O.E.M.
        sku=To Be Filled By O.E.M.
        uuid=6028BE27-8EFE-D511-BF80-2C56DC769C21

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends Inc.
Bios Version:        2101   
Bios Release:        8.15
Board Vendor:        ASUSTeK Computer INC.
Board Name:          M5A78L-M/USB3
Board Version:       Rev X.0x
Board Serial:        151158035903226
Board Asset Tag:     To Be Filled By O.E.M.

Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
   --- SecureBoot Status from 'mokutil':
        This would check / have checked if SecureBoot was enabled or not, 
        and checks if the system BIOS was UEFI or Lagacy only BIOS, 
        but package mokutil was not installed. If you would like to check
        this information, please install 'mokutil' and rerun script.

---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:          7.5Gi       3.3Gi       123Mi        65Mi       4.1Gi       3.8Gi
Swap:         2.0Gi       106Mi       1.9Gi

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet 192.168.0.37/24 brd 192.168.0.255 scope global dynamic noprefixroute enp4s0
    inet6 fe80::8290:78d5:9467:e394/64 scope link noprefixroute 
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1419 qdisc fq_codel state UNKNOWN group default qlen 500
    inet 10.18.11.5/24 scope global tun0
    inet6 fe80::7a57:a6d:55b6:952f/64 scope link stable-privacy 

:
From there it took off.  It asked me if I wanted to send it someplace, I assumed it was what you wanted.  I have no idea what happened after that.  

Thoughts?

---

### Post by #&amp;thj^% on 2022-07-16
:lolflag: You crack me up jgw, it just wouldn't be the same without you my friend. 
Just run it until your past the Main Complaint: Problem Description:  and then press "q" it will go through a process and then ask if you want to upload it to pastebin, reply yes, and copy the URL it gives you back here to save space.

---

### Post by jgw on 2022-07-16
Ok, I did it again.  I stopped and pressed 'q' when I started getting red lines telling me something.  Hope its better this time!

---

### Post by #&amp;thj^% on 2022-07-16
Was there a link shown?

---

### Post by jgw on 2022-07-16
The link to the pastebin is saved in: '/home/greg/system-info-link.log'

View at: [https://termbin.com/6h0n](https://termbin.com/6h0n)

Its strange I used pastebin for years.  Then, when I wanted it I forgot the name.  I checked, I still had an account there.  (I tend to forget things after a year or two (sometimes a half hour ago))

---

### Post by #&amp;thj^% on 2022-07-16
Still going through it, but I forgot to ask for this:
```
lspci -v | grep -i audio
ls -ld /proc/asound/cards
cat /proc/asound/devices
```
Is this Machine a new-ish build?
> **jgw said:**
>  (I tend to forget things after a year or two (sometimes a half hour ago))
I'm right there with you..:)

---

### Post by jgw on 2022-07-16
This is a machine I have had for about 5 years or so.  It works well.  I have had so many messes lately that I think I trashed two machines.  When I get stuff running again I'll fix them.  My problem started when one of them wouldn't start.  I think I now know what was happening but I trashed it.  

Anyway.......

greg@greg-downstairs:~$ lspci -v | grep -i audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300]
	Subsystem: ASUSTeK Computer Inc. RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300]
greg@greg-downstairs:~$ 
greg@greg-downstairs:~$ ls -ld /proc/asound/cards
-r--r--r-- 1 root root 0 Jul 16 14:39 /proc/asound/cards
greg@greg-downstairs:~$ 
greg@greg-downstairs:~$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 1- 3]: digital audio playback
  3: [ 1- 0]: hardware dependent
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 3]: digital audio playback
  7: [ 0- 0]: hardware dependent
  8: [ 1]   : control
  9: [ 0]   : control
 33:        : timer
greg@greg-downstairs:~$

---

### Post by jgw on 2022-07-17
ifallen, hope you haven't given up on me!

I thought I would take a look at the manual.  It seems that I have a SPDIF_02 HDMI port .  Its also got a push button on it but I have no idea what its for (researching)   Should also mention that I no longer have any sound on kodi (just stopped in the middle of a movie).  . I turned it on today and checked to see if anything changed (it hasn't)  Oh,  except for the picture settings is for 1920x1080 but the picture still fills a 65" screen.  It usually goes up but its all magic.

---

### Post by #&amp;thj^% on 2022-07-17
No I don't give up on anyone.
This is an old bug come back to haunt your card: [https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg6031340.html](https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg6031340.html)
But I suspect the problem was the way Ubuntu loaded pulseaudio on 20.04
Please run this first:
```
pactl load-module module-detect&
```
That will reload the detection libraries and restart pulseaudio.
Now check sound.

This I'd try to avoid, so only try this if the above fails.
I remember I modified /etc/pulse/daemon.conf like this from my notes:
```
sudo nano /etc/pulse/daemon.conf
```
At the bottom I added:
```

; default-sample-format = s24le
; default-sample-rate = 192000
```
This is just a dirty hack, but let us know if there is any improvment.

---

### Post by jgw on 2022-07-17
$ pactl load-module module-detect&amp;
[1] 10629
$ 27
[1]+  Done                    pactl load-module module-detect
$ 

Nothing happened (I can continue if you say to)

I have been messing around.  I went to my denon receiver and they had setups for this.  
[https://manuals.denon.com/avrs530bt/na/en/GFNFSYtgugzsae.php](https://manuals.denon.com/avrs530bt/na/en/GFNFSYtgugzsae.php)
[https://manuals.denon.com/avrs530bt/na/en/UJDCSYuhvkdmdm.php#UJDCMLctoidyqm](https://manuals.denon.com/avrs530bt/na/en/UJDCSYuhvkdmdm.php#UJDCMLctoidyqm)
[https://manuals.denon.com/avrs530bt/na/en/GFNFSYwysioymk.php#OKNRMLwqwdyzwn](https://manuals.denon.com/avrs530bt/na/en/GFNFSYwysioymk.php#OKNRMLwqwdyzwn)

I have assumed that my tv has acr (still looking) but that's the way its setup and it works.  

My system sound now gives me two options.  
built in audio analog stereo
HDMI  / display/port - built in audio

The top one is changing every now and then for no reason
The volume control thing is running and the two profiles have changed for no reason
the top one now has about 3 choices and the lower has a pile of choices

Currently:
digital surround 5.1 (HDMI) output 
analog sterio output
both end with: (unplugged)(unavailable)

Oh, I took a look at /etc/pulse/daemon.conf  Your changes weren't there.  Want me to put them there, or send you a copy of what I have)

---

### Post by #&amp;thj^% on 2022-07-17
> **jgw said:**
> 
Oh, I took a look at /etc/pulse/daemon.conf  Your changes weren't there.  Want me to put them there, or send you a copy of what I have)

That might be a good Idea, it's hard for me to understand all your self changes though, 
You might just be working against my suggestions.
If you would like, I'll wait for you to make all your self changes, then come back when the smoke settles.

---

### Post by jgw on 2022-07-17
I haven't been making changes except in some of the denon stuff and very few there as they don't seem to make any difference.  The sound stuff in system settings is a complete mystery as I haven't changed that either.  Its currently "built in audio analog stereo.  I suspect the analog thing might be a wrong thing. I also suspect that comes from the pavucontrol thing.   The first is built in audio analog stereo - built in audio the other is hdmi / display/port - built in audio (settings)   I think this changes if the pavucontrol changes. 

I will stop and wait.  I have no sound!  (last whine)

---

### Post by jgw on 2022-07-17
It dawns on me that it might be of interest that I also have regular tv also connected via the denon reciever.  When I switch (with denon) to the regular tv I use the same hdmi cable to drive both the computer and the regular tv.  The difference is that the regular tv has sound and the computer does not.  Always wondered abut that one.  I have plugged the computer into the dvd/bluray, the other option is media.  I doubt that it makes any difference but I thought you should know.  I also think its strange that hardinfo tells me that HDA-Intel-HDA ATI HDMI controls my audio but I seem to be using Radeon.  Anyway I have changed NOTHING!

---

### Post by jgw on 2022-07-17
I thought I would take a look at the manual.  It seems that I have a SPDIF_02 HDMI port .  Its also got a push button on it but I have no idea what its for (researching)   Should also mention that I no longer have any sound on kodi (just stopped in the middle of a movie).  . I turned it on today and checked to see if anything changed (it hasn't)  Oh,  except for the picture settings is for 1920x1080 but the picture still fills a 65" screen.  It usually goes up but its all magic. I never did figure out with the button on the hdmi port does.

---

### Post by jgw on 2022-07-18
1fallen

You have gone away?

---

### Post by jgw on 2022-07-18
just wondering what happened to you as I haven't heard from you for a while.   Glad to know you're still there!  Oh, I now have another disaster and have posted it this morning.

---

### Post by jgw on 2022-07-19
I now have audio.  It remains mysterious.  The output system sound is blank (nothing!)  if I put anything there it turns off the sound.  When I turned it on, this morning it had no sound!  I went to pavucontrol and in configuration the first line was RS780 HDMI (Audio (Radeon 300/3100/HD 3200/3300) and the Profile was empty.  I inserted Digital Stereo (HDMI) Output (unplugged)(unavailable)

I have tried other profiles, this is the one that works!

Under Built-in Audio Profile was Analog Stereo input (unplugged)(unavailable) I tried others, this is the one that works. 

I have two things connected to my denon receiver.  The first is my TV and the second is my computer.  The TV connection has always been dandy with no problems.  The computer, however was getting the video but not the sound.  Both connections are hdmi cables.  
 

My problem is how to fix this stuff so that it works between boots.  Don't know how to make that so.  The system sound to is another problem.  Its also pretty obvious that even the settings that work are a bit odd.

Oh, When I run kodi the sound setting for the Audio Output Device can be anything - makes no difference.  I should also mention that I still get the sound (when I can) even though the system settings can have everything shut down for its sound.  That, I think, means that I am not hearing ANY system sound when I hear stuff!

Here is some info on my audio system:

```

greg@greg-computer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: VT1708S Digital [VT1708S Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
Subdevices: 0/1
Subdevice #0: subdevice #0
greg@greg-computer:~$

reg@greg-computer:~$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
Flags: bus master, slow devsel, latency 64, IRQ 16, NUMA node 0
Memory at fe7f4000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel

--
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300]
Subsystem: ASUSTeK Computer Inc. RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300]
Flags: bus master, fast devsel, latency 0, IRQ 19, NUMA node 0
Memory at fe9e8000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel

02:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
greg@greg-computer:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. AMD RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300]
02:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
greg@greg-computer:~$ 
```

---

### Post by jgw on 2022-07-20
Thank you all for the replies. 

 am going to mark this as solved and start another not so complicated long.

---

