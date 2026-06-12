---
title: "HP 762N with Kubuntu - No Sound on AC'97"
date: 2007-02-26
forum: General Help
---

### Post by crimp111 on 2007-02-26
Hi guys, I'm a semi-newb - I've setup Kubuntu succesfully on my old 380z Thinkpad and got sound working on it. Now I'm setting Kubuntu up on my HP 762n desktop and I can't get the sound working. The audio controller is a Realtek AC'97 device. I've checked user priviledges and audio is listed in my username, kmix has all the right areas un-muted, the correct driver (snd_intel8x0) is listed under lsmod, the sound system is enabled, and I've tried all of the device settings (Autodetect, OSS, ALSA etc). The speaker icon is not X'd out but I can't get any sound at all. Can anyone give me any pointers because I'm not sure where to go from here. I've also tried Fedora, PCLinux and SUSE and had the same problem on all of them. I've pasted a few items below. Thanks in advance for your help! 

lsmod

snd_intel8x0           33692  3
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm


lspci -v

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 5790
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at e000 [size=256]
        I/O ports at e400 [size=64]
        Memory at e0101000 (32-bit, non-prefetchable) [size=512]
        Memory at e0102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

BTW - would <available only to root> have anything to do with this.

---

### Post by cronholio on 2007-02-27
> would <available only to root> have anything to do with this.

No.

Google has many results for "82801DB ubuntu" and "82801DB linux". See [here]("http://www.ubuntux.org/no-sound-on-ubuntu-dapper") for example. I don't know that particular sound chip but I hope you will be able to find something that helps.

---

### Post by crimp111 on 2007-02-27
Thanks, I've googled til my google finger hurts! I can't seem to come up with an answer. Any ideas?
-Greg-

---

### Post by crimp111 on 2007-03-01
Anybody?

---

### Post by crimp111 on 2007-03-01
C'mon guys... I could get this kind of support from Microsoft! Please don't take offense, but isn't there someone out there who has an idea about how to help me track this down? Sorry about the MS comment, but the install is frustrating enough with out having to wait 2 days only to have someone tell me to go "Google" it. :confused: :mad:

---

### Post by cronholio on 2007-03-02
> I could get this kind of support from Microsoft!

You might want to refrain from these kind of comments in future. You pay for support by MS (by purchasing their very fine OS) and you can get paid support by Canonical too, so this is not a very good point.

> only to have someone tell me to go "Google" it.

Did you? "82801DB sound linux" returns 83,700 hits and it looks like there are many useful ones among them. I solved a lot of sound problems on a lot of different hardware by the very action of googling things. Nobody will go through all these results, pick out the one that will work for you and serve it to you on a plate.

On a sidenote, you can try to install the latest ALSA from source. It might help.

---

### Post by crimp111 on 2007-03-02
> **crimp111 said:**
> Thanks, I've googled til my google finger hurts! I can't seem to come up with an answer. Any ideas?
-Greg-

Already went through a LOT of the google results. Like I said before, I'm sorry about the rash comments, I just can't believe that no one seems to even want to even attempt to help. I've seen many, many posts on this forum that seem to get immediate attention, why does this one seem to be ignored? I will get down off of my soapbox now!

Anyway, I tried to install the latest stable release of ALSA from source, and I get the same problem. I even tried the beta version, no luck. 

I also tried installing the pnpbios tools to see if it would list the chip but after installing it didn't work. After scanning through dmesg I noticed that it had been disabled. Not sure why except that maybe there is no plug and play hardware on this box. ?? 

Everything seems to be in order, the hardware is detected, the driver is loaded, kmix is working and set to my hardware. It's as if something is muted but I've tried to mute and un-mute and set sliders in every combination I can think of. 

How can I tell if I have an irq conflict or something? I used pnpbios tools on my thinkpad 380z and it showed that IR and the audio chip were using the same irq setting, so I disabled the IR with pnpbios tools and it worked like a charm. 

Could someone maybe give me a few tips on how to trouble shoot this problem? 

I've tried everything in this thread also: [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by crimp111 on 2007-03-02
Why would alsaconf say "Command not found"?

---

### Post by cronholio on 2007-03-02
> I've seen many, many posts on this forum that seem to get immediate attention, why does this one seem to be ignored?

If a thread gets a lot of attention it means it's a problem shared by many people. If hardly anyone else has the same sound chip as you do, this is is not the case. And there are also many other threads that go unanswered (sad but true).

Often, sound problems can be solved by tweaking an ALSA option for your card. These are the possible options for yours:

>   Module snd-intel8x0
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, MCP04, CK804
				 CK8, CK8S, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)


AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - default	Don't override the default setting
    - none	Disable the quirk
    - hp_only	Bind Master and Headphone controls as a single control
    - swap_hp	Swap headphone and master controls
    - swap_surround  Swap master and surround controls
    - ad_sharing  For AD1985, turn on OMS bit and use headphone
    - alc_jack	For ALC65x, turn on the jack sense mode
    - inv_eapd	Inverted EAPD implementation
    - mute_led	Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.

Try enabling them one by one, reboot after each change and see if it works. Also check the ALSA mixer after each reboot. New settings may show up.

To enable one option, put it in /etc/modprobe.d/alsa-base like this:

```
options snd-intel8x0 ac97_quirk=inv_eapd
```

If nothing seems to help, the only thing left for you to do is to file a bug on the ALSA website.

---

### Post by crimp111 on 2007-03-05
:( Tried all options, no sound love. 

Any other ideas?

I have a tv card in my setup which has a bt878 chip. I'm going to pull it out and reinstall. If this doesn't work, I'll file a bug report.

Thanks for your help and sorry about the attitude.:)

---

### Post by crimp111 on 2007-03-05
Tried the reinstall, still no audio. It works in XP, any other ideas before I file a bug report?
Thanks.

---

### Post by vasko on 2007-03-19
Don't rush with bug reports. Most likely it is something you are doing wrong. No offense but in 99.99% of the cases whenever I considered a bug report it was behind-the-monitor problem (me :) ).

I have AC'97 as well on Intel Gigabyte MB with chipset Intel865PE. Kind of old but it still works perfectly.

I installed Xubuntu - no sound. For instance when you play a mp3 in the XMMS player there are no errors/warnings, the equalizers jump up`n`down but no sound...

I went through installing the latest ALSA drivers/utils/libs & etc, playing with the alsamixer volume and whatever you can think of but none helped. Then I decided to do a much more simple thing - try the head-phones jack. My case has two jacks on the front part that are connected via cables to the Line-in / Mic of the sound card, thus leaving the Line-out jack open. My 2+1 is connected to it. So I decided to plug the head-phones to the front jack and there was sound :) 

It seems volume/channel control issue because the old driver is the same as the new one and this card is kind of old and it is being supported for quite some time. 
If there is a way to test this - try it. Also Xubuntu did not have any problems on HP zv5000 laptop (but it is with ATI snd card). 

Also try checking those links they may help you:
[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29"]
**Ubuntu Forums SND problem**[/URL]  - if you go here and decide to recompile
the drivers make sure to use:

sudo ./configure --with-cards=intel8x0
instead of 
sudo ./configure --with-cards=hda-intel

Also [**ALSA**]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0") have a pretty nice docs as well. Just remember to enter sudo 
before  ./configure, make, make install otherwise it won't work.

And don't rush into this ! Before that make sure that the sound is not getting out of a place you don't expect :) Hope this can help

---

### Post by vasko on 2007-03-19
Done. Now there is sound through the 2+1 :)
The answer is in alsamixer. Just played with the settings and after getting out some terrible noise I found the correct settings.

Surround => Shared 
Mic Scale => Mic1
IEC 958 => PCM
Channel => 4 (it did not work for 2)

I hope this can help you.

---

### Post by pureblood on 2007-04-10
This workaround might work but it is not a solution:
[http://ubuntuforums.org/showthread.php?p=2430827#post2430827](http://ubuntuforums.org/showthread.php?p=2430827#post2430827)

---

