---
title: "[SOLVED] USB headset World of Warcraft"
date: 2008-01-02
forum: General Help
---

### Post by thunderdan on 2008-01-02
This is my first post, please forgive me for anything I do wrong.

I have gotten World of Warcraft running, and I have my Logitech USB headset kind of working. I can get the sound to come through, but I can't get the microphone to work for in-game voice chat. I'm using the ALSA in wine. That's the only way I could get the sound to come through. Does anyone have a USB headset completely working in World of Warcraft? Could you please give me step-by-step instructions for me?

Thanks,

Thunder Dan

---

### Post by thunderdan on 2008-01-04
A little more info on my problem, to which I have not found a solution yet:

In WoW, under my sound options, I can choose to playback voicechat on either "dmix:1" which makes the sound come through my USB headset, or I can choose "ADC Capture/Standard PCM Playback" which makes the sound come through my speakers. However, for talking, the only option available is "ADC Capture/Standard PCM Playback."

So I think I need to get "dmix:1" available under the talking options. That leads me to this:

In Ubuntu, under sound preferences, I have all devices set to "USB Audio." One thing that happens, though, is when I click the test button for sound capture, I get the following error message:

> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

But I also am able to hear myself talking through the microphone while it performs the test.

I suspect that this is the area where my problem lies. I eagerly await your advice.

Thanks,
Thunder Dan

---

### Post by thunderdan on 2008-01-04
Also, I can go to alsamixer and hear myself through the microphone on my USB headset. Just an extra little note, there.

Anyone who has any ideas at all, I surely would appreciate hearing from you.

Thanks,
Thunder Dan

---

### Post by thunderdan on 2008-01-07
I am adding another note, hoping someone will enlighten me, but also as a documentation for myself.

When I run the Wine configuration, On the tree for the ALSA Driver, there is "Wave Out Devices" and "Wave In Devices." On Wave Out, there is "ADC Capture/Standard PCM Playback" and also "dmix:1." These options are also listed in the sound options for World of Warcraft. Then on Wave In, the only option listed is the ADC Capture/Standard PCM Playback. And accordingly, that is the only option listed for voice input on WoW.

SO! I think I'm getting closer. If you are having the same kind of problem I'm having, please let me know so I will know I'm not alone.

Thanks,
Thunder Dan

---

### Post by Dojan5 on 2008-01-07
Do the headset work for the system sounds?

---

### Post by thunderdan on 2008-01-07
> **Dojan5 said:**
> Do the headset work for the system sounds?

My system sounds do not go through my USB headset. For example, if I receive an email, the computer's internal speaker plays a beep, but no sound comes through the USB headset. However, if I play a CD, the sound does come through the headset. Also, WoW plays through my headset. Yet I still remain unable to speak to my teammates through my microphone in WoW.

---

### Post by Dojan5 on 2008-01-07
Hmm, im no expert, but, what happens if you set the sound capture to something else... Under sound preferences i mean...
Else you can look and see if you can find anything useful in this topic: [http://ubuntuforums.org/archive/index.php/t-517655.html]("http://ubuntuforums.org/archive/index.php/t-517655.html")

---

### Post by thunderdan on 2008-01-07
I tried all the options available and nothing changed. I am still unable to get "dmix:1" to show up in Wine configuration or under the voice capture in WoW.

---

### Post by thunderdan on 2008-01-07
The solution to my problem was perhaps the most simple one. I did not realize that I did not have the latest version of Wine. Ubuntu had installed 0.9.46 through the package manager. When I updated to the latest version of Wine (0.9.52 as of this post), I was able to use the OSS driver instead of ALSA, and I was able to hear sound in WoW. Previously, I had not been able to use the OSS driver. So then I checked the voicechat options in Wow, and under the previous option, there were two blank entries. I clicked on the first blank entry, and ran the test in the voicechat panel. I was pleased to hear my own voice played back to me. I tested it with another person listening on the other end, and they could hear me loud and clear.

So lesson learned: Think about simple solutions first.

Thanks,
Thunder Dan

---

