---
title: "Sound/Audio Popping in Ubuntu 14.04 (video of problem)"
date: 2014-09-23
forum: General Help
---

### Post by Tim_Wernicke on 2014-09-23
When listening to audio (pandora internet radio, google music, local MP3s, youtube, etc.), I get a repeated popping/crackling sound. When I look at the sound settings while this is happening, I see "Headphone Output" rapidly appearing and then disappearing in the "Play Sound Through" section. The appearance and disappearance of "Headphone Output" coincides with the popping and crackling of the sound.

I am wondering if it has anything to do with the fact that my Nvidia card has built-in HDMI sound output that might be interfering with my onboard sound.

```

$ cat /proc/asound/cards 
0 [PCH ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7220000 irq 54
1 [NVidia ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 55
$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

```


Obviously blacklisting "snd_hda_intel" in /etc/modprobe.d/blacklist.conf won't work, because it then disables all sound (both onboard and nvidia are listed as snd_hda_intel).

I recorded a desktop session to show what the Sound Preferences window looks like while I'm experiencing the popping noise: [http://youtu.be/hw4HYpJKAZQ](http://youtu.be/hw4HYpJKAZQ)

I also filed a bug report for it here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1353013](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1353013)

But the bug report is almost two months old now and has received zero responses or attention.  Anyone else experience this?

---

### Post by Forbees on 2014-09-29
safe to assume that you don't have headphones plugged in when this is happening right? i've had headphone jacks go bad in the past, there could be a chance that even if there isn't one plugged in, the little pin that tells the computer one is might be damaged, but sounds unlikely... in my experience its the opposite - problems only when headphones are plugged in due to a bad port

i feel like the HDMI audio shouldn't be related, at least on my computers (14.04 and 12.04) i can't even try to use the HDMI output unless it's plugged in.

wish i had am answer for you but maybe someone will know how to disable the headphone jack? i feel like if you can do that it might help. it makes sense to me that you'd head a pop or crackle every time the computer has to switch from internal speakers to headphone output, so it really comes down to why does it think the headphone is being plugged in and removed?

---

### Post by pprspam on 2014-09-29
Bingo!

Wow.  I've been fumbling with this problem for a couple of months now.  Knee-deep in config files, blacklisting, tweaking.  All I had to do was plug in my headphones into the front panel jack instead of the back.  I haven't heard a single pop in an hour, and the "Sound Settings" menu isn't flickering.

What an incredibly simple yet elusive solution.  Thanks for the reply!  

I'd like to add that filing a bug report on launchpad gets you NOWHERE with the ubuntu dev community.  It's nothing but silence and darkness over there.  I know that it's mostly volunteers, but going months with zero response to bug reports just seems excessive.

Anyway, rant over.  Thanks again, Forbees.

---

### Post by costescuandrei on 2014-11-30
You saved me lots of trials. Thank you!
I have the exact same problem. It works normally just when something is plugged into the front jack...

I wonder if this is a hardware problem... I see meanwile more ppl. had the same problem in support system.

---

