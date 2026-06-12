---
title: "I installed Ubuntu, but I don't have sound!"
date: 2007-10-02
forum: General Help
---

### Post by mathgirl on 2007-10-02
:confused:  i dont know what to do!  everything else works great!  please help!

---

### Post by Tyke91 on 2007-10-02
please post the output of this command

```
aplay -l
```

---

### Post by mathgirl on 2007-10-03
It says
```

$ aplay -l
aplay: device_list:221: no soundcards found...

```
Thanks for helping!:)

---

### Post by mali2297 on 2007-10-03
Next, post the output of
```

lspci -v | grep -A 5 Audio

```

This link might also help you:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by mathgirl on 2007-10-04
Okay, that one says
```

$ lspci -v | grep -A 5 Audio
0000:00:0f.3 Multimedia audio controller: Advanced Micro Devices [AMD]: Unknown device 2093 (rev 01)
        Subsystem: Advanced Micro Devices [AMD]: Unknown device 2093
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
        I/O ports at d400 [size=128]

0000:00:0f.4 USB Controller: Advanced Micro Devices [AMD]: Unknown device 2094 (rev 02) (prog-if 10 [OHCI])

```
Thanks again!:-k

---

### Post by mali2297 on 2007-10-04
Do you have any other OS (like Windows) installed on the same computer? Does sound work with that OS?

Do you know the full name of your sound card? Ubuntu seems to have some difficulties recognizing it.

---

### Post by mathgirl on 2007-10-05
I don't have any other OS installed on it now, but it used to have Gentoo Linux on it and sound worked then.  I don't know the name of the soundcard, but my system is an all-in-one type thing.  Thanks for helping!:)

---

### Post by mali2297 on 2007-10-05
You can try reinstalling the alsa utilities:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop

```

Reboot, then check
```

aplay -l
lspci -v | grep -A 5 Audio

```
Any change?

---

### Post by mathgirl on 2007-10-11
I asked the guy who built my computer what my soundcard was and he said
> The audio codec is Wolfson WM9715L connected by AC97 to AMD CS5536 companion chip.

Would that help anybody help me?:confused:
Thanks for any help you can provide!:)

---

### Post by mali2297 on 2007-10-11
I found this at [alsa-project]("http://www.alsa-project.org/"):

> 
 Changelog between 1.0.11rc2 and 1.0.11rc3 releases

    * alsa-driver 

 + Sound Core
   - Improved handling of temp files
   - configure: fix kernel version test in RTC check
   - Fix configure for 2.6.15-git
   - PCM midlevel & PCM OSS - make procfs & OSS plugin code optional
   - Remove superfluous quotes
   - Add mutex.h wrapper
   - Add description of als300
   - release 1.0.11rc3
 + ALSA Core
   - Fix compile on 2.6.15 without CONFIG_PM_LEGACY
   - Regenerate the patch
   - Regenerated the patch
   - **Added AMD cs5536 audio**
   - PCM midlevel & PCM OSS - make procfs & OSS plugin code optional
   - fix snd_info_entry_ioctl_old wrapper compilation
   - Add mutex.h wrapper
 + ALSA sequencer
   - Update patch
 + ALSA<-OSS emulation
   - Regenerated the patch
 + Generic drivers
   - Replace semaphore with mutex
 + Memalloc module
   - Fix patch
 + Opti9xx drivers
   - Replace semaphore with mutex
 + snddevices script
   - Remove bashism from snddevices


The version of alsa-driver in Ubuntu 7.04 is 1.0.13 so your card should be supported.

---

### Post by mathgirl on 2007-10-11
But I don't have Ubuntu 7.04, I have Ubuntu 6.06.1  I'll try to reinstall the alsa utilities like you said before.  Thanks so much.  I hope it works![-o<

---

### Post by mali2297 on 2007-10-11
> **mathgirl said:**
> But I don't have Ubuntu 7.04, I have Ubuntu 6.06.1  I'll try to reinstall the alsa utilities like you said before.  Thanks so much.  I hope it works![-o<

OK, that explains it. Dapper's version of the alsa-driver is < 1.0.11. I think the best solution would be to install Ubuntu 7.10 when it is released next week. If you for some reason don't want to do that, I guess you could fetch the latest source from [alsa-project]("http://www.alsa-project.org/main/index.php/Main_Page") and compile it yourself.

---

### Post by mathgirl on 2007-10-12
7 never installed correctly.  That's why I went with 6.06.  I have a pretty weird computer, so I thought it would be a better idea to go with "Long Term Support".  I'm going to embark on the adventure of compiling and installing ALSA from scratch using [http://alsa.opensrc.org/index.php/Quick_Install]("http://alsa.opensrc.org/index.php/Quick_Install")

If anybody has any Ubuntu specific advice, I'm all ears!:grin:  Thanks for getting me this far! :biggrin:

---

### Post by mali2297 on 2007-10-12
From the [link]("https://help.ubuntu.com/community/SoundTroubleshooting") I gave in a previous post:

> 
Using drivers from alsa-project

update I now recommend using the stable version 1.0.12 

The alsa-project route is very similar to the alsa-source route without the module-assistant. First you would have to get the alsa-driver tar from alsa-project then pretty much do configure, make and make install again. However, I do recommend that you make a specific directory when you compile something from source. Remember the name of your soundcard driver and use it in place of the blue text below. 
mkdir src
cd src
mkdir alsa
cd alsa
sudo apt-get install build-essential linux-headers-$(uname -r)
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12.tar.bz2
tar -xvjf alsa-driver-1.0.12.tar.bz2
cd alsa-driver-1.0.12
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes
sudo make
sudo make install

If you get no errors from doing the above then you have successfully compiled alsa-drivers from source. Resume this guide from General Help step 4.


> 7 never installed correctly. That's why I went with 6.06. I have a pretty weird computer, so I thought it would be a better idea to go with "Long Term Support".

Even tough Dapper has Long Term Support, it doesn't necessarily mean it is more stable. If it isn't too much hassle for you, you should try Gutsy Gibbon when it is released. Usually things work better with each release (but it is not a promise).

---

### Post by Achetar on 2007-10-12
When I upgraded to Ubuntu v. 7.04, my sound stopped working. I got it working again by right-clicking on the Volume Applet (on the bar at the top) and selecting "Open volume control" and then Adjusting the PMC slider up and that fixed it!

---

### Post by mathgirl on 2007-10-13
I compiled the alsa drivers, utils, and oss by following the instructions at [http://alsa.opensrc.org/index.php/Quick_Install]("http://alsa.opensrc.org/index.php/Quick_Install")
very carefully.  Now when I run mpg123 on a file I get
```
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such deviceALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
ALSA snd_pcm_open error: No such device
/bin/sh: /usr/bin/esd: No such file or directory
Can't find a suitable libao driver. (Is device in use?)

```

I was so happy when the installation went okay.  What's going on?:confused:
Thanks again for everybody being so helpful!  :)

---

### Post by mali2297 on 2007-10-14
Did you reboot?

Post the output of
```

aplay -l
lspci -v | grep -A 5 Audio

```

---

### Post by mathgirl on 2007-10-14
D'oh.  Now I've rebooted, I get more promising errors.;)  But at least the sound card is known.

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audio [CS5535 Audio], device 0: CS5535 Audio [CS5535 Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ lspci -v | grep -A 5 Audio
$

```

In the installation instructions for the ALSA driver, I had problems with a few of the instructions.  Namely
[Step 4]("http://alsa.opensrc.org/index.php/Quick_Install#4._Loading_the_ALSA_modules")

After I've installed everything, I type in the cryptic ```
sudo mod-probe
``` commands, but the paragraph after it is confusing.  It tells me to do two different conflicting things with directories "to make module loading permanent".  Then it gives a text-file starting with ```
 # alsa/soundblaster live module settings
``` but doesn't tell me where to put the file.  It also says to look up my card in the "ALSA matrix" which I couldn't find.

Anywho, when I type the mysterious mod-probe commands in by hand, I get one step closer.  Now I get this error:
```

$ mpg123 02.wav
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!

Playing MPEG stream from 02.wav ...
MPEG 1.0 layer I, 14 kbit/s, 44100 Hz stereo
ALSA: underrun, at least 0ms.
mpg123: layer3.c:2633: mad_layer_III: Assertion `stream->md_len + md_len - si.main_data_begin <= (511 + 2048 + 8)' failed.
Abort

```

Thank you so much for getting me this far.  This is *way* further than I ever thought I'd get when I started!  :mrgreen:

---

### Post by mathgirl on 2007-10-14
Nevermind!  IT WORKS!\\:D/

I decided to reinstall gdm while I waited for advice on how to fix ALSA, and when it reinstalled, it configured ALSA somehow.  When I restarted and heard the drum-beats, I nearly fell out of my chair!

Thank you so much!  I now have a functioning computer!!!!!!:KS:KS:KS

---

### Post by mathgirl on 2007-10-14
How do I register this problem as _solved_?  'Cause that's what it is! :)

---

### Post by mali2297 on 2007-10-14
> **mathgirl said:**
> How do I register this problem as _solved_?  'Cause that's what it is! :)

Go to your first post and click the Edit entry in the corner, I think that will give you an option to mark it as _solved_.

May the Ubuntu be with you.:-)

---

### Post by mathgirl on 2007-10-14
The ubuntu is strong with this one.

I didn't see any way to mark it as solved, so I changed the subject to ... [Solved!]

Thanks again!:)

---

