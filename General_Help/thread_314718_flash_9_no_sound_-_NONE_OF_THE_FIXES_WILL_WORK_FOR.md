---
title: "flash 9 no sound - NONE OF THE FIXES WILL WORK FOR ME!"
date: 2006-12-08
forum: General Help
---

### Post by lopzided on 2006-12-08
i have tried and tried and i CANNOT get sound out of flash 9!

i have installed alsa-oss, changed to "aoss" in firefoxrc, i've downloaded the new beta and replaced EVERY instance of libflashplayer.so on my system with the new one, i've changed my sound system to be alsa...and still no luck!

when i had flash 7, sound worked fine, but the sync was always way off.  recently i did a full reinstall using edgy 6.10 with flash 9.

PLEASE HELP!  thanks in advance!

---

### Post by partsdale on 2006-12-08
I always use Automatix to get Flash installed. Have you tried that? It's pretty simple to use and has worked every time I have used it.

Good Luck

---

### Post by lopzided on 2006-12-08
> **partsdale said:**
> I always use Automatix to get Flash installed. Have you tried that? It's pretty simple to use and has worked every time I have used it.

Good Luck

yup.  tried automatix, no luck.  the video works fine, but no sound whatsoever. :(

---

### Post by partsdale on 2006-12-08
Unfortunately, that was the best advice I had for you... I know there was a period several weeks back where everyone was having trouble with Flash, but all those posts seem to have slowed down. There must be a fix that works out there but I bet you have about 500 posts on this specific problem to try and read through to find the one that works... just remind yourself how good it will feel when you get it working..

---

### Post by lopzided on 2006-12-08
okay, i hope this is a clue that might resolve my problem...

when i run firefox from console and watch a flash movie, i get these errors in the console :

```
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
```

it goes on and on like that...so much that i couldn't even scroll up to capture it all...

any clue what all that means?  how to fix it?

---

### Post by lopzided on 2006-12-09
bump

---

### Post by jocko on 2006-12-09
what soundcard do you have? Which driver does it use?

---

### Post by lopzided on 2006-12-09
from lspci :

02:07.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)

and from cat /proc/asound/modules

 0 snd_ens1370

---

### Post by riven0 on 2006-12-09
You may have already done this, but just to be certain; did you try completely uninstalling flash 9 and then following [this howto]("http://www.ubuntuforums.org/showthread.php?t=279990&highlight=flash+9")? That was the only way I could get flash 9 to install without problems.

---

### Post by lopzided on 2006-12-10
> **riven0 said:**
> You may have already done this, but just to be certain; did you try completely uninstalling flash 9 and then following [this howto]("http://www.ubuntuforums.org/showthread.php?t=279990&highlight=flash+9")? That was the only way I could get flash 9 to install without problems.

i just tried that, with the same results : video works fine, still no sound.  could it be possible that my sound card is too old to work with flash or something?

---

### Post by riven0 on 2006-12-10
One last thing to try. Paste these commands in the terminal, one at a time:
> 
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

> sudo mkdir -p /tmp/.esd/

> sudo touch /tmp/.esd/socket

---

### Post by lopzided on 2006-12-12
that didn't work either...still have perfect video, no sound at all.  :(

still getting these errors in console
```
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings

```

there's more, just too long to paste...
any other suggestions?

---

### Post by lopzided on 2006-12-13
bump

---

### Post by cully on 2006-12-17
I'm having a similar issue.  No sound in flash at all.  However, my ALSA sound doesn't work anywhere in KDE.  Apparently Flash 9 doesn't support OSS (that's what I read somewhere).

Any solution found yet?

---

### Post by cully on 2006-12-17
I got it working.  I'm not sure if it was getting ALSA to work in the rest of KDE or what, but it works.  I ended up setting FIREFOX_DSP="arts" in firefoxrc.  I did this because 'man firefox' says:

FIREFOX_DSP - configures the /dev/dsp wrapper to use.  Accepted  values  are  "auto",  "arts",  "esd"  or  "none" (default).   Do not use this feature to select "auto" or "esd" as this will involve using "esddsp" which is known to be buggy and to make Firefox unstable.

I also had to set my sound to ALSA in KDE sound config (System Setting -> Sound and Multimedia -> Hardware)

---

### Post by lopzided on 2006-12-29
> **cully said:**
> I got it working.  I'm not sure if it was getting ALSA to work in the rest of KDE or what, but it works.  I ended up setting FIREFOX_DSP="arts" in firefoxrc.  I did this because 'man firefox' says:

FIREFOX_DSP - configures the /dev/dsp wrapper to use.  Accepted  values  are  "auto",  "arts",  "esd"  or  "none" (default).   Do not use this feature to select "auto" or "esd" as this will involve using "esddsp" which is known to be buggy and to make Firefox unstable.

I also had to set my sound to ALSA in KDE sound config (System Setting -> Sound and Multimedia -> Hardware)

ok, just tried that....i still get no sound, and the same errors in console : 

```
ALSA lib pcm_direct.c:187:(make_local_socket) socket failed: Too many open files
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:187:(make_local_socket) socket failed: Too many open files
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card
```

i even tried installing a new sound card...i didn't think it would help, but gave it a shot...same problem...

help!

---

### Post by lopzided on 2006-12-29
interestingly enough, i don't get any sound if i play a flash movie in IE through wine, either ([http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)) .....

---

### Post by lopzided on 2007-01-03
ok, i'm at the point to where i'll PAY someone to help with this problem!

PLEASE!

---

### Post by riven0 on 2007-01-03
This probably won't help at all, but as a last resort, did you try reinstalling alsa?

> sudo apt-get install --reinstall alsa

---

### Post by lopzided on 2007-01-03
thank you for your reply....but no, that didn't help.


as a side note, i get sound if i play an .swf file through a standalone flash player such as gnash or klash.

---

### Post by lopzided on 2007-01-08
ok, so gnash and klash both have sound, but both are so buggy....gnash's sound loses sync (like badly)...as in, it keeps playing sound even though the movie has stopped...klash plays everything at warp speed!

so i downloaded the flash 9 beta 2 standalone player....it plays great, but no sound...however, no errors in console either!

i am so confused!  please, if anyone has any ideas, i'm ready to try anything!

EDIT: the only error i get in console while watching a flash movie in firefox (after doing a lot of updating and such) is this:

> ALSA lib pcm_direct.c:1123:(snd_pcm_direct_open_secondary_client) unable to open hardware

---

### Post by lee797 on 2007-01-10
If you are using kde have you tried the aoss fix in gnome?  It seems a bit extreme, but you could install gnome and try flashplayer in firefox there.  
howto here: [http://psychocats.net/ubuntu/gnome](http://psychocats.net/ubuntu/gnome) . I had sound probs but "aoss" fix worked after I removed and reinstalled flashplayer 9 in gnome. Don't know if this will help, but you never know.

---

### Post by lopzided on 2007-01-11
> **lee797 said:**
> If you are using kde have you tried the aoss fix in gnome?  It seems a bit extreme, but you could install gnome and try flashplayer in firefox there.  
howto here: [http://psychocats.net/ubuntu/gnome](http://psychocats.net/ubuntu/gnome) . I had sound probs but "aoss" fix worked after I removed and reinstalled flashplayer 9 in gnome. Don't know if this will help, but you never know.

i've switched to gnome, reinstalled everything, same error.  

it's something to do with this error message...and if i'm not mistaken, i think it has to do with the drivers for my soundcard

```
ALSA lib pcm_direct.c:1123snd_pcm_direct_open_secondary_c lient) unable to open hardware
```

google is failing me...and nobody in the forums knows, nor on IRC, nor on lq....i must be the only person in the world with this problem!

as extra information, here's my sound card info from lspci : 02:07.0 Multimedia audio controller: Creative Labs SB Audigy LS

and as extra info on it, it's a sound blaster live! 24 bit

---

### Post by jamespi on 2007-01-14
you're not alone, i have exactly the same problem.
i doubt it's your soundcard as you've changed it over and my soundcard is

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)


and that doesnt work either.

i think its something to do with the fact linux has umpteen different sound subsystems and every application seems to have issues with at least some of them. i really think Ubuntu need to settle on ONE SOUND SUBSYSTEM in feisty+1. i know KDE has arts as it's official sound subsystem, so maybe they should ship with arts on Kubuntu and whatever's the best out of ASLA OSS and ESD for gnome.

personally i've given up trying to get flash sound to work - i'm just going to hope it's fixed in feisty.

---

### Post by wesley_of_course on 2007-01-14
Would this help ?

alsaconf utility [http://www.linuxjournal.com/node/8234/print](http://www.linuxjournal.com/node/8234/print)

---

### Post by lopzided on 2007-01-14
i've actually fixed it...sad how i had to do it though...

formatted.  reinstalled ubuntu.  followed the ubuntuguide for edgy on how to install flash, but let flash update itself after that to 9 through the adept update reminder.

works great now...wish i knew what was the problem...

---

### Post by vigleik on 2007-01-18
I wish you knew what the problem was too, because I'm having the exact same problem. No sound with flash 9, though I had sound with flash 7, no error messages when starting from console (well, one, but it looks unrelated), and none of the fixes will work. I think reinstalling is a bit drastic though, but maybe I'll install Herd 2 or something on a separate partition to see if that helps.

---

### Post by meanmrmustard on 2007-01-18
> **lopzided said:**
> okay, i hope this is a clue that might resolve my problem...

when i run firefox from console and watch a flash movie, i get these errors in the console :

{code snipped}

it goes on and on like that...so much that i couldn't even scroll up to capture it all...

any clue what all that means?  how to fix it?

Just a shot in the dark but it looks like your system can't find the sound card.

I just found that disabling my onboard sound allowed flash video sites to see my PCI card and now I have sound.

Hope it works for you.

---

### Post by Tmi on 2007-01-18
You guys aren't alone. I'm having the exact same problem.
Reinstalling feels a bit drastic, even though I keep everything important on other drives/computers, but still.

A friend recommended to try installing opera and see if flash worked there since it did for him. Haven't had the time to try it yet myself though.

At the moment I use my laptop with XP if I really need to watch something on Youtube or similar.

---

### Post by atlfalcons866 on 2007-01-19
i dont have sound ether:(  could it be bug in flash? this my soundcard

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

---

### Post by shimme01 on 2007-01-20
> **riven0 said:**
> One last thing to try. Paste these commands in the terminal, one at a time:

I tried riven0's commands seemingly without success, but then I decided to reboot linux.
I got sound for a second then it stopped again. Not sure if the reboot or the commands gave me sound.

I am using flash 9 on MEPIS.

Thanks.

---

### Post by paszczak on 2007-01-20
Yeah, 2hours and the solution is...so easy that i can't belive ;-)
So, i have the newest flash 9 from ([http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW))
And...i'v tried the solution [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760)
but it not helped.
So...finally i've found some post about system setting. So try this (gnome) System>Prefences>Sound and set your default sound card. For me that was the second VIA 8237, and you know wat? I HAVE SOUND IN FLASH!
Try it and tell me if it works!
Ps.I set the /etc/firefox/firefoxrc to use aoss.

---

### Post by ghostdog on 2007-01-27
I am having the same issue on Kubuntu 6.10, but after I created "/etc/asound.conf" with following entries:

```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}
```

This is to do software sound mixing for multiple sound, I shut off artsd also. Will follow up if solved

---

### Post by ghostdog on 2007-01-27
Yup, just as I thought, it is a problem with setting your system with "multisound". Looks like flash 9 does not like to share.

I moved "asound.conf" to "asound.conf.OLD" and flash 9 is working again, without any other sound working (of course).

---

### Post by nickwilton on 2007-01-27
I tried the solution on this site...and the fix works :D :
[http://motls.blogspot.com/2007/01/adobe-flash-9-for-linux-sound.html]("http://motls.blogspot.com/2007/01/adobe-flash-9-for-linux-sound.html")

However, I'm back to the old flash problem where flash 9 blocks the soundcard...and the ol' FIREFOX_DSP="aoss" fix doesn't work anymore. At least sound now works on Flash 9. :confused: 

:) :) :) :)

---

### Post by themeone on 2007-01-30
I've also got the es1370 soundcard, and I'm afraid I've given up with Flash 9, uninstalled it, and manually reverted to Flash 7, so it won't get updated again.

It's not an ideal solution, but I figure slightly out of sync sound on most flash video with Flash 7 is better than complete silence with Flash 9.

---

### Post by ghostdog on 2007-02-02
You might want to try to "compile it" with OSS support (I think I read that on a previous page of this thread).

[http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux](http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux)

```
 cc -shared -O2 -Wall -Werror -licuuc -lssl flashsupport.c -o libflashsupport.so
 ldd libflashplayer.so 
 sudo cp libflashplayer.so /usr/lib

```

Hope this helps.

---

### Post by CPtAJ on 2007-02-03
I haven't read through this entire thread yet but I had a very similar problem (Terminal error output and everything). It happened because I was using a PCI sound card but also had an integrated one activated. When I disactivated the integrated one at BIOS, the errors came. The problem was flash somehow using the integrated card as a default.

The fix is this: Use the asoundconf utility...
```
asoundconf list
asoundconf set-default-card <card name>
```

Replace the <card name> with the right card out of the ones shown by the list command. It should make everything in ubuntu go to that sound card first.

Hope that helps some of you...

---

### Post by themeone on 2007-04-02
Well, I finally got Flash 9 to work with the ES1370 soundcard.

I created the following file in /etc/asound.conf
```

pcm.!default {
    type plug
    slave.pcm "dmixer"
}
pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 8192
        rate 44100
    }
    bindings {
        0 0
        1 1
    }
}

ctl.dmixer {
    type hw
    card 0
}
```

and then I changed the file /etc/libao.conf to the following:

```
default_driver=alsa10
```

previously it was default_driver=alsa09

I do not understand alsa sufficiently to know why any of this worked, but I hope it might help someone else.  It worked in both Dapper and Edgy.

---

### Post by delmore on 2007-04-11
alsa09 = ALSA version 0.9

alsa10 = ALSA version 1.0

Did you find this fix via ArchLinux wiki?  
[http://wiki.archlinux.org/index.php/Allow_multiple_programs_to_play_sound_at_once](http://wiki.archlinux.org/index.php/Allow_multiple_programs_to_play_sound_at_once)

---

### Post by jiminycricket on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/109485](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/109485) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can't get flash to work either.  I have two soundcards, and flash attempts to play through my bad onboard sound card.  However, I can't get it to play through my Soundblaster live card, which I chose in GNOME.

If Adobe had used gstreamer instead of ALSA directly, I wouldn't have had this problem because it would have respected my GNOME sound preferences.

In this blog by the guy who you can see arguments for and against using ALSA: [http://blogs.adobe.com/penguin.swf/2006/07/api_review.html](http://blogs.adobe.com/penguin.swf/2006/07/api_review.html)

Also report Flash bugs to Adobe following this link: [http://blogs.adobe.com/penguin.swf/2007/01/building_a_better_bug_report.html](http://blogs.adobe.com/penguin.swf/2007/01/building_a_better_bug_report.html)

---

### Post by jiminycricket on 2007-04-26
.

---

### Post by rajaf on 2008-04-15
> **CPtAJ said:**
> I haven't read through this entire thread yet but I had a very similar problem (Terminal error output and everything). It happened because I was using a PCI sound card but also had an integrated one activated. When I disactivated the integrated one at BIOS, the errors came. The problem was flash somehow using the integrated card as a default.

The fix is this: Use the asoundconf utility...
```
asoundconf list
asoundconf set-default-card <card name>
```

Replace the <card name> with the right card out of the ones shown by the list command. It should make everything in ubuntu go to that sound card first.

Hope that helps some of you...

This worked for me from the start... thanks.

Ooops... this was april 2007... sorry for digging up old threads...

---

### Post by boogz on 2008-04-29
Sorry to resurrect an old thread just thought I'd mention I had the exact same problem, a simple:

"sudo alsa reload" 

should fix it! - this is if and only if sound is missing from youtube (sound should be working everywhere else) :)

---

