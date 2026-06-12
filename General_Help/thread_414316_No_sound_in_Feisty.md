---
title: "No sound in Feisty"
date: 2007-04-19
forum: General Help
---

### Post by IgnacioMiller on 2007-04-19
Hey all,

When I first installed Feisty I had no sound. I went into System>Preferences>Sound, and found the device that played sound for me, CA0106. There were for entries with the exact same name, the one that worked was the fourth one. I installed some packages related to music, and uninstalled some, and then when I went to go listen to a .ogg file I could not hear anything. I went back into the sound configuration applet and tested my CA0106, with no sound. I tested all available devices and all had no sound.

Disclaimer:
My speakers are plugged in
Alsamixer shows nothing muted
Speaker volume is turned up

Thanks for your help, I'm sure this forum is busy today of all days,
Ignacio

---

### Post by IgnacioMiller on 2007-04-19
By the way, I have a Soundblaster Live! 24 bit soundcard. It worked perfectly in Edgy.

---

### Post by IgnacioMiller on 2007-04-19
Resolved.

---

### Post by musicinmybrain on 2007-04-19
> **IgnacioMiller said:**
> Resolved.

If you don't mind posting how, it might be useful later when someone else searches the forum for the same problem.

---

### Post by Anaea on 2007-04-20
I too am having problems with sound in Feisty.  It worked fine in Dapper, so I know it ought to be able to work in Feisty.  I've gone through the sound troubleshooting document [here]("http://https://help.ubuntu.com/community/SoundTroubleshooting").

When I click on the panel volume controler I get:
```

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

The Sound section under administration>preferences craches when I try to test it at autodetect, and gives me the follow errors under other settings:```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
``````

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server
```

aplay -l gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v shows:
```
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

The driver for the ATI SB450 is snb-hda-intel. Modprobing did nothing.  I've done the reconfigure of the alsa-source from the tutorial both with and without module-assistant.  Both times it failed.

Functional wireless is more important to me than having sound, but I'd really like to have both ;).  Does anybody have any ideas?

---

### Post by Eremit on 2007-04-20
same here:

Alsa:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

ESD:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

But I can play mp3s and stuff as root. So it's a problem with access rights.
I made sure my user is in the audio group and that /dev/dsp has the proper group/rights but still no sound.

*edit* if I start esd as normal user I get:
```
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:rev50
```

**Solution**
[http://ubuntuforums.org/showthread.php?p=2415537](http://ubuntuforums.org/showthread.php?p=2415537)

---

### Post by Anaea on 2007-04-20
Double checked to make sure it isn't an issue with permissions.  running totem under sudo still gives me the same error as before, and my user account does have permission for sound services.  lspci -v changes a bit with sudo though:

```
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

```

I would try to use the solution linked to, but have dicsovered that I already don't have asoundrc or asoundrc.conf

I don't really have any experience with sound problems so I'm not sure what to try next.  Any ideas?

---

### Post by Anaea on 2007-04-20
I've created a new problem, though I'm honestly not sure how.  I should have everything set back to an untweaked state but the problem lingers.  

```
@Marduk:/usr/src$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

Alsamixer wasn't functioning properly before anyway, but now it's flat out not working.

---

### Post by jsully1 on 2007-04-21
This fixed it for me - everything that played sound after the initial login was crashing my computer.  All I had to do was follow the very helpful sound troubleshooter found here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

For some reason this also nuked GDM, so you need to do a
sudo apt-get install gdm
as well.

---

### Post by Anaea on 2007-04-21
That thread has the same troubleshooter I've been using and linked to in my first response.  I wind up with errors during the make stage of compiling the alsa-source.  I've posted about those particular problems [here]("http://ubuntuforums.org/showthread.php?t=415205"), but the errors I get during that stage are:
```

make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of &#8216;jiffies_to_msecs&#8217;
include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of &#8216;msecs_to_jiffies&#8217;
include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2
```

I've done some poking around looking for problems with jifffies_to_msecs.  Is this possibly just a bug in the kernel?  If so, I'm guessing I'll need to recompile with a different kernel; anybody got a handy tutorial for that tucked away somewhere?

Edit: Said tutorial is right [here]("http://ubuntuforums.org/showthread.php?t=311158&highlight=Master+Kernel+thread").  And it was updated this month even.

---

### Post by Monika on 2007-04-21
I've followed the intructions for uninstalling and then doing a clean install of the alsa packages and tried going through all the troubleshooting guidelines on the sound page (I did as much as I understood but everything seemed to be in order) and the skype fix (I have no such folders) and I still have no sound :(
I don't really know what I'm supposed to copy and paste to make it easier to diagnose the problem. I have an Audigy SoundBlaster card and it seems to have all the necessary drivers and modules installed. It worked fine in Edgy without any need for tinkering anything.

---

### Post by Tim Nakos on 2007-04-22
Yeah,
   I'm pretty new to Linux, but my dad has shown me how fedora core works so I've gotten okay with Ubuntu. I'm running a M-Audio 1010lt and i get that same weird error mes, so....I need help.

Thanks, Btw I am bad cause I'm unexperienced, I'm only 14.

---

### Post by djails on 2007-04-23
Anaea,
check my post for a solution to the ATI SB450 sound problem in feisty,and let me know if it works for you
[http://ubuntuforums.org/showthread.php?p=2515443#post2515443](http://ubuntuforums.org/showthread.php?p=2515443#post2515443)

---

### Post by Anaea on 2007-04-23
Looks like it ought to.  I'm going to have to run a quick uninstall to repair the damage I've done trying to fix the problem and try from there.  I'll let you know tonight.

Edit: Well, it helped, though it didn't clear everything up for me.  I'll post about it in the other thread.

Edit the second: Got it working.  How is in the other thread.

---

