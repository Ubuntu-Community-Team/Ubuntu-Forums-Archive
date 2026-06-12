---
title: "Hoary sound worked, then broke!"
date: 2005-08-18
forum: General Help
---

### Post by zwalkert on 2005-08-18
Can someone with knowledge of sound please help me?  I've gone through every thread in the ubuntu forum I could find about sound problems, and am still hearing nothing.  I installed Ubuntu the other day and after getting alsa installed, I was able to listen to CDs and audio files.  Then I allowed ubuntu to update a bunch of packages(too many to list).  Today I rebooted and have no sound.  Nothing.  Nada.  the sound device is an Intel AC97 built onto my motherboard, so it should be easy, right?  Here's my lsmod | grep snd:
snd_intel8x0           29984  0 
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0 
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

here is my relevant lspci output:

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

Alsa packages:
 # dpkg -l | grep alsa
ri  alsa-base      1.0.8-4ubuntu4 ALSA driver configuration files
ii  alsa-oss       1.0.7-1        ALSA OSS-compatibility application wrapper
ii  alsa-utils     1.0.8-1ubuntu1 ALSA utilities
ii  libesd-alsa0   0.2.35-2ubuntu Enlightened Sound Daemon (ALSA) - Shared lib
#

I have tried every asound.conf configuration listed in these forums but none of those did anything - a couple of them crashed alsa - so I just deleted /etc/asound.conf because it was working just fine yesterday without one. Kernel version is 2.6.10-5-386

/etc/libao.conf:
default_driver=alsa


esd is not running, alsa is started.  I can't even hear anything if I cat a file into > /dev/dsp.  Before you ask, yes, I have looked at my mixer about a billion times and I'm dang sure that my speakers are connected and on.   
 :confused: 

Now I can't even listen to an audio CD. (Yes, yesterday I installed the cable from the drive to the sound input)

Help?

---

### Post by audax321 on 2005-08-18
I had this problem on my laptop (also with AC97 integrated sound) and I fixed it by using beep media player.

My problem was that the sound card was detected, but I couldn't get sound. So, I installed beep media player (should be available in universe, package is called beep-media-player). Then when it starts up, in the middle of the player it should say something about 'disabled' or 'no sound' or something similar. Just click that and it should re-enable the sound. Next, reboot the computer so your alsa settings and everything get saved and then you can go ahead and uninstall beep media player.

I didn't really set out to fix the sound like this, just something I noticed when I started beep. Anybody know what beep does to re-enable the sound? Let me know if it works out for you.

---

### Post by zwalkert on 2005-08-18
Hmm, the beep-media-player didn't say anything about disabled or 'off' - I went through and selected the alsa connector in the preferences but still no sound.  Thanks, though

---

### Post by audax321 on 2005-08-18
Well that sucks :(  I probably can't help you much more since I really haven't dealt with alsa before. Good luck.


btw:

this is where it said disabled in beep (right where the volume bar should have been):

[IMG]http://www.dieburnbot.com/Screenshot-BMP.png[/IMG]

---

### Post by Apostata on 2005-10-11
[QUOTE=zwalkert]Hmm, the beep-media-player didn't say anything about disabled or 'off' - I went through and selected the alsa connector in the preferences but still no sound.  Thanks, though[/QUOTE]

This is what I did - and this may not be a fix but a workaround:

1.  Open Kmix
2.  Switch tabs to 'input'.
3.  Pull down all of the fader switches, except for Wave and CD.

Does this have any effect?

Matt

---

