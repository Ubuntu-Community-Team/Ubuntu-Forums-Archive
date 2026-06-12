---
title: "Feisty Sound Trouble"
date: 2007-04-22
forum: General Help
---

### Post by Valdrone on 2007-04-22
Alright. In past versions of Ubuntu, I've been able to work my sound perfectly. That's why I've decided to use Ubuntu over Sabayon and a few others. Now all of my sound is goofing.

Right now I'm using a USB headset. In the sound preferences, I can hear the test beep only when I select the USB audio driver. I selected USB Audio, just like I did in previous releases. However, now when I try to play the login or logout sounds, nothing happens. Games don't have sound, nor does Amarok.

So, I decided to try my speakers, which are hooked up to my PCI sound card (SoundBlaster Live).
ALSA still doesn't work. Only the ES1371 drivers work, but they still don't let me hear sound in games or in Amarok or in anything else.

So, what can I do to help correct this problem?

---

### Post by NoTiG on 2007-04-22
Well i am the same way. i have a set of Logitech USB headphones. They work in edgy. In feisty now i don't get sounds when i try to play the start up, log out ones.. or any of the system sounds. Flash or games don't work etc.

but i have the USB audio selected in the sound setup screen and the test beeps work. I have the same problem.

bump

---

### Post by Valdrone on 2007-04-22
I actually have the same headset as you.

Why did I click the update button....Why!?

*bump*

---

### Post by Selmer79 on 2007-04-23
(I was about to post in my own thread when I remembered to "Search The Forum" ;))

I have a SoundBlaster Live! 24-bit External soundcard and it's acting up after I installed 7.04..

I had 6.10 (AMD64) installed earlier and my "card" worked perfect, but after completely formating down my computer and re-installing XP, Vista and Ubuntu (i386 this time) it's only kinda working..

The problem is that the card is properly detected in the hardware-list under Administration, the SPDIF-port in the box lights up, but the "On"-light is off. Running TOTEM I get "could not initiate sound-server" but there's absolutely no hint of anything NOT running fine when I boot..

Any help? (I'm semi-n00b with Linux, so if you need something, tell me what and I''ll do my best to get it for you.)

---

### Post by Selmer79 on 2007-04-23
Only common points I've seen  so far in this thread are USB-based sound-devices under Feisty Fawn...

---

### Post by Bashed on 2007-04-23
[B]Creative SB Live 24 bit external sound also does not work for me.


[/B]

---

### Post by PleaseEnjoyThis on 2007-04-23
I have the same mic as all of you, but I never had sound working on my linux being that I am very new.  This is driving me nuts!

---

### Post by Bashed on 2007-04-25
No one by now?

---

### Post by Selmer79 on 2007-04-25
Yeah, kinda sad that nobody has responded with a solution.. :(
Hopefully someone is atleast looking into the issue.

---

### Post by ingomueller.net on 2007-04-26
Hi!

Please post the output of the command "aplay -l". This is a list of physical sound devices the sound server ALSA sees. If your card is in the list, it should be recognized correctly. You can test, whether the card itself works with the following command. It produces sound on one channel after the other.

```
speaker-test -t wav -c <x> -D plughw:<y>
```

where <x> is the number of channels of your sound card and <y> the number of the card in the list. If you have only one card installed, the card number is most likely 0, so it would look like this: "-D plughw:0". If you have a 6 channel sound card and "-c 6" doesn't work, try other numbers instead of 6. The "-t wav" option makes a female voice say the according channel names instead of just producing white noise.

If the speaker-test is successfull, i.e. you hear the voice in all of your channels, your sound card is installed correctly and the remaining problem is only a matter of configuration. If the speaker-test doesn't produce any sound, you either did something wrong or the support of your card in the installed ALSA version is broken.

Also some links might help:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://alsa.opensrc.org/](http://alsa.opensrc.org/)
[http://alsa.opensrc.org/ALSA_resources](http://alsa.opensrc.org/ALSA_resources)
[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix)

Greets, Ingo

---

### Post by Bashed on 2007-04-28
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

```
~$ speaker-test -t wav -c 5 -D plughw:1

speaker-test 1.0.13

Playback device is plughw:1
Stream parameters are 48000Hz, S16_LE, 5 channels
WAV file(s)
speaker-test: pcm_params.c:187: snd_pcm_hw_param_get_min: Assertion `!snd_interval_empty(i)' failed.
Aborted (core dumped)

```

```
~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0180000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: fast devsel
        Memory at 8c000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at d01c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c8000000-c9ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000c1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: ca000000-cbffffff
        Prefetchable memory behind bridge: 00000000c2000000-00000000c3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: cc000000-cdffffff
        Prefetchable memory behind bridge: 00000000c4000000-00000000c5ffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: ce000000-cfffffff
        Prefetchable memory behind bridge: 00000000c6000000-00000000c7ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at d03c4000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d03c4400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1050
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at cc000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 90000000-93fff000
        I/O window 0: 00006400-000064ff
        I/O window 1: 00006800-000068ff
        16-bit legacy interface ports at 0001

0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at d0006000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 6000 [size=64]
        Capabilities: <access denied>

```

---

### Post by ingomueller.net on 2007-04-28
> **TalkJesus said:**
> ```
~$ speaker-test -t wav -c 5 -D plughw:1
```

Hi!

Did you try other "-c" values than 5? I guess that the SBlive card is an 5.1 card, so the value should be 6 (=5+1). If you did try other values, but the error persists, something seems broken with the support of your hardware. Maybe installing ALSA 1.0.14rc3 manually helps... The following wiki page is the best guide I know about installing ALSA:

[http://alsa.opensrc.org/Quick_Install](http://alsa.opensrc.org/Quick_Install)

Regards, Ingo

---

### Post by Bashed on 2007-04-28
This is crazy. All of a sudden my card is not detected???

chad@Secured:~$ speaker-test -t wav -c 6 -D plughw:1

speaker-test 1.0.13

Playback device is plughw:1
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm_hw.c:1351_snd_pcm_hw_open) Invalid value for card
Playback open error: -19,No such device

[1]+  Stopped                 speaker-test -t wav -c 6 -D plughw:1

chad@Secured:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by dagrump on 2007-04-28
Well, I could totally looking at the wrong approach here but I would try to disable on board sound support first.  I know I had to disable on board support but I can't remember the hardware issue. I've messed with  breaking so many things, I think I'd installed a old sound card in an existing & was trying get it to work. Anyway try disabling on board sound in your bios.

---

### Post by Selmer79 on 2007-04-28
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
That's all the info I get out of that command.. I was kinda expecting my soundcard to be listed as item 0 since it's the only card I have (the on-board card is disabled in BIOS).

```
~$ speaker-test -t wav -c 2 -D plughw:2
``` plays sound in the two front channels, but after each "announcement" I get some really horrible noise (NOT white-noise)...

---

### Post by Bashed on 2007-04-28
I got my card recognized again after a reboot, but I hear nothing at all.

chad@Secured:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


chad@Secured:~$ speaker-test -t wav -c 6 -D plughw:1

speaker-test 1.0.13

Playback device is plughw:1
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 87381
Period size range from 48 to 43690
Using max buffer size 87380
Periods = 4
was set period_size = 21845
was set buffer_size = 87380
 0 - Front Left
 4 - Center

---

### Post by ingomueller.net on 2007-04-29
Hi!

> **Selmer79 said:**
> ```
[CODE]~$ speaker-test -t wav -c 2 -D plughw:2
``` plays sound in the two front channels, but after each "announcement" I get some really horrible noise (NOT white-noise)...

The fact that this command only plays sound on two channels is absolutely normal because that's what it's supposed to do! Notice the "-c 2" part, which tells the speaker-test program to test only two channels. Use "-c 6" to run a full 5.1 surround test. I don't know what's about the "horrible noise", though...

> **TalkJesus said:**
> ```
chad@Secured:~$ speaker-test -t wav -c 6 -D plughw:1

speaker-test 1.0.13

Playback device is plughw:1
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 87381
Period size range from 48 to 43690
Using max buffer size 87380
Periods = 4
was set period_size = 21845
was set buffer_size = 87380
 0 - Front Left
 4 - Center
```

This looks as it should work... Just to be sure in case you didn't do it: please check with "alsamixer" in a console that all channels are unmuted and not set to very low levels. Especially look for channels called "Surround", "Rear" or similar.

Another two general tips: (1) If the "-D plughw:<X>" doesn't work, you can also try "-D surround51:<X>" (only for 5.1 cards, it's "surround40" for 4.0 cards, "surround71" for 7.1 cards etc). (2) Alway play with the mixer settings (with alsamixer). Sometimes cards only produce sound when the mixer level is set to 100%, in rare cases they even only work if the are muted (!).

I hope this helps... Regards, Ingo

---

### Post by Selmer79 on 2007-04-29
> **ingomueller.net said:**
> The fact that this command only plays sound on two channels is absolutely normal because that's what it's supposed to do! Notice the "-c 2" part, which tells the speaker-test program to test only two channels. Use "-c 6" to run a full 5.1 surround test. I don't know what's about the "horrible noise", though...
I re-tested now using "-t sine" and "-t pink" instead of "-t wav" and it worked fine.. No nasty noise..

Then I re-ran it with "-t wav" and the noise was back.. It changes every time I re-run the test (some times it sounded like the sound you get when plugging a guitar into an amp, sometimes it sounded like a groan etc).

Anyways, the base system is working, just not in GNOME...

---

### Post by LDRoamer on 2007-04-29
I doubt this will help you but the sound on my machine was broken by Feisty as well. I have an old laptop that uses the ESS 1869 chip and it worked perfectly under Edgy. The card shows up but it won't work except to emit a terrible screeching sound. However it also is apparent that Feisty has introduced some sort of a hardware conflict. My machine is very slow loading the desktop. However if I comment out the sound card driver it works perfectly. Dmesg shows a bunch of DSP errors and it shows something like 
"unable to grap 0x220".  0x220 is one of the ports my sound chip uses. If I go into the bios and change the port to 0x240 I get "unable to grap 0x240".  It seems as if something is broken.

---

### Post by Boodah on 2007-05-05
I got my USB Headphones to work on Fiesty after following instructions below

See OLEOLEOLE's post here ... [http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

HowTo make ALSA (sound) work after upgrading to Fesity 7.04!
It doesnt seem to be a bug, but just a new/updated configuration file.

What you need to do, is to backup your old config files (if you have any):
```
cd ~
mv .asoundrc .asoundrc.bak
mv .asoundrc.asoundconf .asoundrc.asoundconf.bak

```
Then you run:
```
asoundconf list
```

You should see "Headset" in the list.

```
asoundconf set-default-card Headset
```

asoundconf should now have created two new configuration files in your home folder. You can check it by this 
command:
```
ls ~/.asoundrc*
```

This should display the files you backed up, including the new ones, and you can also check if the configuration file is empty or not, do this command:
```
cat ~/.asoundrc.asoundconf
```

Then you should get some output, and also see that your soundcard have been selected as default.

Restart any application using sound devices, and it should work. If not, try a simple reboot (should be unecessary).

This worked for me after installing Fiesty clean. I had no initial conf files but now I have them and I have great sound through my USB Headphones.
Big thanks to OLEOLEOLE (wonder if he's a Man Utd fan? LOL)

---

### Post by julupanter on 2007-05-05
SO
MUCH
THANKS!!!


Now my External SB Live 24-bit is working, but only the front speakers....

---

### Post by Selmer79 on 2007-05-05
That fix sorted my problems too..

---

