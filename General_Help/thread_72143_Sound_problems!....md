---
title: "Sound problems!..."
date: 2005-10-05
forum: General Help
---

### Post by camp on 2005-10-05
Hi all!

Here we go again!... a question about the so loved sound problems! :D  I have looked at the various threads, and I haven't really found an answer to my problem.

I have sound, but!... there is always a freaking "BUT"! :mad: It very often dies on me. With that I mean... I use to be logged to Yahoo via Gaim. And I can sometimes receive messages, but no sound!? And then I can try again... and the sound plays that annoying little sound telling you that you got a new message. Even if the only thing/application running, is Gaim!?

I have noticed that my XMMS, has some problems with the sound too. Sometimes it just freezes... and after I killed it, it can take me a little while before XMMS starts to play the music without freezing again.

I think that I'm using OSS. Would love to skip it for ALSA. How can I do that? Or even better... is there anyone out there having the same problems? Got a solution for it?

Another annoying thing, that I think might be related to this. Is the fact that when I'm using say XMMS, listening to some groovy music and I get a Yahoo! message... it does not play it until I stop my groovy tunes! That's annoying! And I hate when people say... Windows does not have that kind of problem why must K/Ubuntu have them!? But in this case... it's true and I didn't have them on Fedora either. I DON'T want to go back to either of them! So any help is really appreciated.

Using Kubuntu Hoary, not that I think that has anything to do with it... My /etc/esound/esd.conf and /etc/asound.conf looks as they should according to various threads here.

Here comes some outputs:
root@gamer:~ # lspci |grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

root@gamer:~ # lsmod |grep snd
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm


All help is appreciated... otherwise, I will be out of friends... they are all getting pissed at me for not answering to their messages in time. ;) 

Thanks in advanced!
/JC

Edited some misspeled words! ;) Anybody that can actually give ME an built in dictionary!? :D

---

### Post by John.Michael.Kane on 2005-10-05
if you want alsa look here 
[http://www.ubuntuforums.org/showthread.php?t=44753&highlight=FIREFOX_DSP](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=FIREFOX_DSP)

---

### Post by camp on 2005-10-06
Thanks man!

This was exactly was I was looking for... I think that solved all the problems that I had... and even some I didn't knew I really had!

Have a nice day!
/JC

---

