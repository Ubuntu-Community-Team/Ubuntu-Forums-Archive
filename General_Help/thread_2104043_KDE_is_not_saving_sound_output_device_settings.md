---
title: "KDE is not saving sound output device settings"
date: 2013-01-11
forum: General Help
---

### Post by cafejunkie on 2013-01-11
Hello Everyone!

I'm baffled on this one. In gnome/unity, I could go to sound preferences and change my output device from my soundcard where my speakers are plugged in to my USB headset and it worked perfectly.

I attempted the same thing in Kubuntu just now (I set the kmix master channel to the USB headset) and then I went into the phonon settings and for all audio playback I set it to prefer the USB headset. I hit the test button and could hear sound through the headset. Perfect!

But, when I play audio through any program it still uses the speakers and not the headset. So, I went into "Audio Hardware Setup" and saw it's set to use the soundcard. So I changed that to my USB headset, hit apply and closed it. Then I played some music and the same issue. 
When I opened up the audio hardware setup settings again, it had reverted back to using the soundcard w/ the speakers.

I've searched and tried about everything I could think of and I just can't get it to work. Does anyone have any ideas or have experienced this problem? (Perhaps there's a different way I can configure the output device?) Thank You!

*EDIT*
I installed pavucontrol and that was able to successfully switch the outputs, but using that method applications have weird behavior (example clementine crashes as soon as audio starts to play, while amarok recognized the device changed and works fine). So if there's a method to switch the outputs without using pavucontrol and using KDE's built in phonon instead that would be awesome

---

