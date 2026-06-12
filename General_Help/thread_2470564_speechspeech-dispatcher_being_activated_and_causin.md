---
title: "speech/speech-dispatcher being activated and causing distorted audio by firefox"
date: 2022-01-04
forum: General Help
---

### Post by slaytanicprion on 2022-01-04
...on certain websites. I will also be going to the Firefox forums with this. I was running the latest long term version of Firefox that didn't update itself (v.79 that came with Ubuntu Mate 20.04.2 on installation, I know the real ESR is v.78 but they behaved the same). Updating finally (ESNI is now unsupported by Cloudflare, so the only thing holding me back recently went away so I updated it).

When I visit websites such as soundcloud or a TTS robot website I use sometimes instead of reading huge paragraphs (too bad my pay version of Foxit Phantom Reader with a still-good license can't be installed, well maybe it would work with CrossOver, but the version I own is likely outdated by now (v.17), I mention it because WINE doesn't like Foxit Phantom Reader and the remaining time on my license (got a 3 year license in 2018, but I got rid of win7 in mid 2020 so this is now a linux/ubuntu we desktop) is being unused. It had unparalleled TTS with many many voices.

So when I visit the TTS robot website, I have to play around with NoScript to get rid of the sudden static noise coming out of my speakers. If I don't, anything I paste in there will come out with annoying trebelly distortion as well as the words being read twice (or echo). Soundcloud will only do the same if I start a track. The only solution to put an end to it is opening terminal and typing ```
sudo pkill -f speech 
```and the distortion and noise mess will stop and will stop coming out normally. This issue has been following me ever since some time into Ubuntu MATE 18.04.x (not at the start of it all). 

What's happening here? Is this a known Firefox bug? I updated 26 versions up and the problem remains, it seems more like the OS is causing speech/speech-dispatcher to open up like this. 

BTW, the mic on my desktop (usb, external obviously) is not connected when not used, and the input line is on Mute anyways on my sound card, so it can't be related to that. Although, I remember, but am not sure that I sometimes had to do this when I plug in the mic I have, or my guitar (I have this amp emulator program, with the correct jack, I can plug it to my sound card, been doing that since year 2000 with a neat program I won't advertise here), sometimes I had to kill speech or speech-dispatcher when the mic was plugged in at first and turned on (it has an on/off mute mode switch), after that I would turn it back on and things would be fine. But I haven't used my PC mic since 6 months+ so that might not be that important.

Have a great day, especially those who aren't on paid vacation still today like I am [IMG]https://cdn.frankerfacez.com/emoticon/262458/1[/IMG]

---

### Post by slaytanicprion on 2022-01-04
Using 20.04.2 LTS btw. I'm surprised nobody has an idea what is happening. I'll provide every log data one can request.

---

### Post by slaytanicprion on 2022-01-12
It's been like 3 threads I made about issues (big or small) where I didn't get any help at all...are u guys conspiring not to help me? &#129300; Just kidding. There's still one that demands much attention if you at my profile that did get a lot of replies, but when I got the exact screengrabs (the issue I have isn't logged at all, when installing new kernels...doesn't prevent the new kernels from working and being installed, but I get that same line on boot about init 1 something something mkinitramfs-update permission denied and being told some file is preventing it, the file only has one line in it, that's an either or line, the resume.save file which is at NO right now or such, which looks like changing whats there to another setting would fix that other annoying error I get.  BTW, I've updated enough that I'm now on 20.04.3 for what its worth.

---

### Post by drumone on 2022-03-03
I'm having the same issue. For me, it is intermittent. I have noticed that it seems to happen when I open a second tab in Firefox that requires audio. For example, I'm working on an online degree and some of my coursework requires me to watch videos. While I'm reading my class material I listen to streaming music (SiriusXM or Pandora). When I stop the streaming music and play the video the audio becomes distorted. It's tinny with static and an echo. I used your kill command and it worked! I haven't tried another browser yet, but that's my next option for troubleshooting.

---

