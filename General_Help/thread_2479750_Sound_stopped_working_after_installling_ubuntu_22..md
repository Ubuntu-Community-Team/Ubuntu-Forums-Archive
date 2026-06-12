---
title: "Sound stopped working after installling ubuntu 22.04 / No audio showing Dummy Output"
date: 2022-10-05
forum: General Help
---

### Post by mkelmi on 2022-10-05
[COLOR=#232629][FONT=-apple-system][COLOR=var(--black-200)  !important][FONT=inherit][CENTER][COLOR=var(--black-500)  !important][FONT=inherit][INDENT][/FONT][/COLOR][/CENTER][/INDENT]
[/FONT][/COLOR]
[/FONT][/COLOR]
**I Am new user Kindly need your help , Ubuntu to 22.04 audio is not working. In the setting, the audio option has only [Dummy Output]("https://i.stack.imgur.com/2fp4r.png") and the test fails. [webcam]("https://i.stack.imgur.com/yKGr1.png") and the touchscreen is not working too.**[COLOR=#232629][FONT=-apple-system][COLOR=var(--black-200)  !important][FONT=inherit][CENTER][COLOR=var(--black-500)  !important][FONT=inherit][INDENT]
[/FONT][/COLOR][/CENTER][/INDENT]
[/FONT][/COLOR]
[/FONT][/COLOR]

Details of my laptop:-

Brand       :- XENIA Xe LIFESTYLE ULTRABOOK
Processor   :- 11th Gen Intel® Core™ i7-1165G7 
Graphics    :- Integrated Intel® Iris® Xe Graphics

---

### Post by TheFu on 2022-10-05
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

The exact audio chips will need to be known and supported with a kernel driver. If there isn't a driver available, it will not work.  Sometimes less used chips don't have any Linux support ... or bleeding edge hardware.  OTOH, if the chips do have support, perhaps we can convince the correct driver to load.  But the first step is to follow those 2 links to gather more information.

The following command
```
$ lspci -vk |perl -lne 'print if /Audio/ .. /^[\w]*$/'
```
will hopefully get what the kernel knows about the audio subsystem. It isn't the prettiest, but should always work.  Showing multiple audio devices is common. I see the motherboard audio and the GPU audio on my system.  For analog output, the motherboard is what I choose. For audio over HDMI, the GPU audio is what gets selected.  On my system, these are manual choices. I don't like surprise changes, but many people want the audio to follow which 3.5mm jack was just connected. That's possible too .... after the drivers are figured out.

---

### Post by mkelmi on 2022-10-05
[COLOR=#202124][FONT=Roboto]Thank you for your fast respond. I had followed the steps on the two links above still no luck.
[/FONT][/COLOR]


```


00:1f.3 Multimedia audio controller: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20)
    DeviceName: Onboard - Sound
    Subsystem: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller
    Flags: bus master, fast devsel, latency 32, IRQ 187, IOMMU group 16
    Memory at 603e1e0000 (64-bit, non-prefetchable) [size=16K]
    Memory at 603e000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: sof-audio-pci-intel-tgl
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl



```[COLOR=#202124][FONT=Roboto]



[/FONT][/COLOR]Kernel Version [COLOR=#202124][FONT=Roboto]
[/FONT][/COLOR]```
   5.15.0-48-generic      
```
[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: sofhdadsp [sof-hda-dsp], device 1: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 2: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

[COLOR=#202124][FONT=Roboto]Please let me know if you I can provide any information which can help .I appreciate your support . Thank you very much.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2022-10-05
could you also show this please:
```
apt policy firmware-sof-signed
```
These cards and alike are having a tough time on Jammy.

---

### Post by TheFu on 2022-10-05
That aplay output says you can only use HDMI for audio.  No analog speakers or headphones.  Do you have the HDMI port connected to a monitor/TV with speakers?  Is the audio output in a format supported by the TV/monitor?  For example, my monitor with speakers only supports PCM output, not DD or DD+ or high-end audio. That means if the source material is Dobly-whatever, I have to convert it to PCM to hear it.

If you have a 3.5mm headphone jack, it doesn't seem that the driver for the motherboard is installed at all.

---

### Post by mkelmi on 2022-10-05
```


firmware-sof-signed:
  Installed: 2.0-1ubuntu3
  Candidate: 2.0-1ubuntu3
  Version table:
 *** 2.0-1ubuntu3 500
        500 http://ae.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://ae.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages
        100 /var/lib/dpkg/status
     2.0-1ubuntu2 500
        500 http://ae.archive.ubuntu.com/ubuntu jammy/restricted amd64 Packages
        500 http://ae.archive.ubuntu.com/ubuntu jammy/restricted i386 Packages



```

---

### Post by mkelmi on 2022-10-05
Yes i do have HDMI but its not connected to anything .true I had tried to use [COLOR=#000000]3.5mm headphone jack,[/COLOR] also it was not working .i apologize for not being helpful with my information this is my first time using ubuntu .

---

### Post by TheFu on 2022-10-06
> **mkelmi said:**
> Yes i do have HDMI but its not connected to anything .true I had tried to use [COLOR=#000000]3.5mm headphone jack,[/COLOR] also it was not working .i apologize for not being helpful with my information this is my first time using ubuntu .

There isn't an audio card/chip recognized with drivers loaded to support the analog 3.5mm headphone jack.  Only the HDMI connection has a recognized driver based on the output above.

In short, you need to find, install, and setup the driver for the other audio chip in the system. It won't work before that is accomplished.  In theory, intel audio drivers should "just work" and that has been my experience, thought I don't have any new Intel computers to really know. Also, I'm not running 22.04 on any real desktop for a number of reasons (not audio related).

[https://askubuntu.com/questions/1243369/sound-card-not-detected-ubuntu-20-04-sof-audio-pci](https://askubuntu.com/questions/1243369/sound-card-not-detected-ubuntu-20-04-sof-audio-pci) says that the SOF driver selected by the installer (it was a 20.04 question) wasn't working, so they blacklisted it.  There are a number of ways to accomplish it The solution at that link makes it a grub boot option.  I'd probably just add a line to the /etc/modprobe.d/blacklist.local   file myself to list the specific driver, 
```
blacklist snd_sof_pci_intel_tgl
```
Use 'sudoedit' to change system files. It is the safest way.

After the change is made, reboot.  If that doesn't work, comment out that line and you've lost nothing but the time to reboot. Seems worth a shot to me.

---

### Post by mkelmi on 2022-10-07
> **TheFu said:**
> There isn't an audio card/chip recognized with drivers loaded to support the analog 3.5mm headphone jack.  Only the HDMI connection has a recognized driver based on the output above.

In short, you need to find, install, and setup the driver for the other audio chip in the system. It won't work before that is accomplished.  In theory, intel audio drivers should "just work" and that has been my experience, thought I don't have any new Intel computers to really know. Also, I'm not running 22.04 on any real desktop for a number of reasons (not audio related).

[https://askubuntu.com/questions/1243369/sound-card-not-detected-ubuntu-20-04-sof-audio-pci](https://askubuntu.com/questions/1243369/sound-card-not-detected-ubuntu-20-04-sof-audio-pci) says that the SOF driver selected by the installer (it was a 20.04 question) wasn't working, so they blacklisted it.  There are a number of ways to accomplish it The solution at that link makes it a grub boot option.  I'd probably just add a line to the /etc/modprobe.d/blacklist.local   file myself to list the specific driver, 
```
blacklist snd_sof_pci_intel_tgl
```
Use 'sudoedit' to change system files. It is the safest way.

After the change is made, reboot.  If that doesn't work, comment out that line and you've lost nothing but the time to reboot. Seems worth a shot to me. 
 
after doing what you mention plus the link above. Dummy output changed to HDMI /DisplayPort built in audio but no sound.

---

### Post by TheFu on 2022-10-07
Also, you need to check the list of audio devices with that lspci command again, after the blacklist.
If there isn't any analog out chip shown, then it isn't useful trying to use the 3.5mm analog plug.

Once the analog ports/drivers are seen by the drivers, use the 'pavucontrol' tool - start at the far right tab and work left - to setup the settings for inputs and outputs. This is a complex thing, especially when there are multiple choices.  While you learn, it is best to disable all but the single speaker/plug you want to actually use.

And always check that mute is disabled.  That gets people, including me, all the time.

But ... until the correct driver for the chip is working, none of this is useful at all. There won't be any sound without it.

---

### Post by mkelmi on 2022-10-07
> **TheFu said:**
> Also, you need to check the list of audio devices with that lspci command again, after the blacklist.
If there isn't any analog out chip shown, then it isn't useful trying to use the 3.5mm analog plug.

Once the analog ports/drivers are seen by the drivers, use the 'pavucontrol' tool - start at the far right tab and work left - to setup the settings for inputs and outputs. This is a complex thing, especially when there are multiple choices.  While you learn, it is best to disable all but the single speaker/plug you want to actually use.

And always check that mute is disabled.  That gets people, including me, all the time.
But ... until the correct driver for the chip is working, none of this is useful at all. There won't be any sound without it.



lspci
```



 00:00.0 Host bridge: Intel Corporation 11th Gen Core Processor Host Bridge/DRAM Registers (rev 01)00:02.0 VGA compatible controller: Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics] (rev 01)
00:04.0 Signal processing controller: Intel Corporation TigerLake-LP Dynamic Tuning Processor Participant (rev 01)
00:05.0 Multimedia controller: Intel Corporation Device 9a19 (rev 01)
00:06.0 PCI bridge: Intel Corporation 11th Gen Core Processor PCIe Controller (rev 01)
00:07.0 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #0 (rev 01)
00:07.2 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #2 (rev 01)
00:08.0 System peripheral: Intel Corporation GNA Scoring Accelerator module (rev 01)
00:0a.0 Signal processing controller: Intel Corporation Tigerlake Telemetry Aggregator Driver (rev 01)
00:0d.0 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 USB Controller (rev 01)
00:0d.2 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #0 (rev 01)
00:0d.3 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #1 (rev 01)
00:10.0 Serial bus controller: Intel Corporation Device a0d8 (rev 20)
00:10.6 Digitizer Pen: Intel Corporation Device a0d0 (rev 20)
00:12.0 Serial controller: Intel Corporation Tiger Lake-LP Integrated Sensor Hub (rev 20)
00:14.0 USB controller: Intel Corporation Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller (rev 20)
00:14.2 RAM memory: Intel Corporation Tiger Lake-LP Shared SRAM (rev 20)
00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201 (rev 20)
00:15.0 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 (rev 20)
00:15.2 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #2 (rev 20)
00:15.3 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #3 (rev 20)
00:16.0 Communication controller: Intel Corporation Tiger Lake-LP Management Engine Interface (rev 20)
00:1f.0 ISA bridge: Intel Corporation Tiger Lake-LP LPC Controller (rev 20)
00:1f.3 Multimedia audio controller: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20)
00:1f.4 SMBus: Intel Corporation Tiger Lake-LP SMBus Controller (rev 20)
00:1f.5 Serial bus controller: Intel Corporation Tiger Lake-LP SPI Controller (rev 20)
01:00.0 Non-Volatile memory controller: ADATA Technology Co., Ltd. Device 5350 (rev 01)



```
This what showing .

I Have also installed pavucontrol . Still no luck:sad::sad::sad::sad::sad:

---

### Post by mkelmi on 2022-10-07
> **TheFu said:**
> Also, you need to check the list of audio devices with that lspci command again, after the blacklist.
If there isn't any analog out chip shown, then it isn't useful trying to use the 3.5mm analog plug.

Once the analog ports/drivers are seen by the drivers, use the 'pavucontrol' tool - start at the far right tab and work left - to setup the settings for inputs and outputs. This is a complex thing, especially when there are multiple choices.  While you learn, it is best to disable all but the single speaker/plug you want to actually use.

And always check that mute is disabled.  That gets people, including me, all the time.

But ... until the correct driver for the chip is working, none of this is useful at all. There won't be any sound without it.



  [COLOR=#000000]lspci[/COLOR]

```

00:00.0 Host bridge: Intel Corporation 11th Gen Core Processor Host Bridge/DRAM Registers (rev 01)
00:02.0 VGA compatible controller: Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics] (rev 01)
00:04.0 Signal processing controller: Intel Corporation TigerLake-LP Dynamic Tuning Processor Participant (rev 01)
00:05.0 Multimedia controller: Intel Corporation Device 9a19 (rev 01)
00:06.0 PCI bridge: Intel Corporation 11th Gen Core Processor PCIe Controller (rev 01)
00:07.0 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #0 (rev 01)
00:07.2 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #2 (rev 01)
00:08.0 System peripheral: Intel Corporation GNA Scoring Accelerator module (rev 01)
00:0a.0 Signal processing controller: Intel Corporation Tigerlake Telemetry Aggregator Driver (rev 01)
00:0d.0 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 USB Controller (rev 01)
00:0d.2 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #0 (rev 01)
00:0d.3 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #1 (rev 01)
00:10.0 Serial bus controller: Intel Corporation Device a0d8 (rev 20)
00:10.6 Digitizer Pen: Intel Corporation Device a0d0 (rev 20)
00:12.0 Serial controller: Intel Corporation Tiger Lake-LP Integrated Sensor Hub (rev 20)
00:14.0 USB controller: Intel Corporation Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller (rev 20)
00:14.2 RAM memory: Intel Corporation Tiger Lake-LP Shared SRAM (rev 20)
00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201 (rev 20)
00:15.0 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 (rev 20)
00:15.2 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #2 (rev 20)
00:15.3 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #3 (rev 20)
00:16.0 Communication controller: Intel Corporation Tiger Lake-LP Management Engine Interface (rev 20)
00:1f.0 ISA bridge: Intel Corporation Tiger Lake-LP LPC Controller (rev 20)
00:1f.3 Multimedia audio controller: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20)
00:1f.4 SMBus: Intel Corporation Tiger Lake-LP SMBus Controller (rev 20)
00:1f.5 Serial bus controller: Intel Corporation Tiger Lake-LP SPI Controller (rev 20)
01:00.0 Non-Volatile memory controller: ADATA Technology Co., Ltd. Device 5350 (rev 01)



```



[COLOR=#000000][FONT=Ubuntubeta]This what showing .[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]I Have also installed pavucontrol . Still no luck[/FONT][/COLOR]:sad:

---

### Post by TheFu on 2022-10-07
The lspci command to use is in post #2 above and you'll need to review the output to see if there is any analog devices or not.
The 'aplay' command used before (not some random aplay command) is a good way to see devices, if the driver is loaded.

---

### Post by feveal on 2023-03-06
I also did a clean installation of Kubuntu 22.04 and the HDMI card was not detected. I did this twice with the same result. I tried all possible methods and that I was finding on the web. None worked.
In the end I decided to reinstall Kubuntu 20.04 from zero, in this versión I configured the sound outputs (20.04 detected all outputs) Then I upgraded to version 22.04 and now everything works.

---

### Post by ctrlcctrlv2 on 2023-03-08
Hello all.

First, sorry, but I fixed this on Arch Linux, so it won't be exactly the same on Ubuntu, but all of it's applicable. I think I'm one of the first with this hardware to figure it out so **both** audio playback and the mic work.

You *must* install the SOF firmware. Either from Ubuntu's repositories if it's there, or <https://github.com/thesofproject/sof-bin>.


```
Audio:
  Device-1: Intel vendor: Matsushita driver: N/A bus-ID: 00:05.0
  Device-2: Intel Tiger Lake-LP Smart Sound Audio vendor: Matsushita
    driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3
  Sound API: ALSA v: k6.2.2-zen1-1-zen running: yes
  Sound Server-1: PulseAudio v: 16.1 running: yes
  Sound Server-2: PipeWire v: 0.3.66 running: yes
```

Then, make sure you did *not* put something like dmic_detect=0 in your kernel parameters. No special kernel parameters are needed on my machine.

Proof: 

[https://files.catbox.moe/1hfe0p.png](https://files.catbox.moe/1hfe0p.png)
[URL="https://files.catbox.moe/8megyg.png"]https://files.catbox.moe/8megyg.png
[/URL]

---

