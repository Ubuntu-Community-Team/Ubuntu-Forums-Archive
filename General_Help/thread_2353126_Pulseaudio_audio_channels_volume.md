---
title: "Pulseaudio audio channels volume"
date: 2017-02-19
forum: General Help
---

### Post by cyphaw on 2017-02-19
Hello,

I have an issue I wasn't able to solve through good old googling and searching, so I'm here asking for some help.

In short, I currently have a 7.1 capable sound card, but only have stereo headphones. When I put my card in stereo mode, I can only control the volume of the front panel jack. I need pulseaudio to control the volume of all the jacks (or at least the Front Left/Right jack on the back of my card).


Now with more details:

I currently have a 7.1 capable sound card (Asus xonar dsx / CMI8788), which works very well, and which is plugged to my front panel audio.
Thus I have 5 output jacks and 10 audio channels :
[LIST]
[*]4 jacks/8 channels on the back of the card: Front Left/Right, Rear Left/Right, Side Left/Right, Center, Woofer
[*]1 jack/2 channels on the front panel: Headphones Left/Right (which output the same audio as Front Left/Right)
[/LIST]
I correctly get the different audio channels on the different output jacks, and when I change the volume through my media key or pavucontrol's volume slider or the sound applet volume slider, the volume change on all the jacks, the 4 from the back and the front panel one.

Here is a screenshot of alsamixer (my soundcard, on the left) and alsamixer -Dpulse (on the right).
When I change volume through pavucontrol, nothing happens on the left, but the volume of all the channels change on the right:
[IMG]https://i.imgur.com/C43mS17.png[/IMG]


But since I have only stereo speakers and headphones, if I want to hear all the sounds of content with more than two audio channels, I need to downmix the channels to stereo.

No problem, I go in pavucontrol -> configuration, and change my card from "Analog Surround 7.1 Output + Analog Stereo Input "to "Analog Stereo Duplex". Now all 5 jacks output the same downmixed to stereo audio, which is what I want. But now, when I change the volume with pavucontrol, only the volume of the front panel jack changes. I cannot change the audio of the back jacks unless I go in alsamixer and change it there.

Here is a another screenshot of alsamixer (my soundcard, on the left) and alsamixer -Dpulse (on the right) in this configuration.
When I change volume through pavucontrol, this time, the volume of the Headphones channel (front panel) on the left and the channel on the right change in the same way:

[IMG]https://i.imgur.com/KN8yQ9q.png[/IMG]

What I need is that when my card is in stereo mode, for pulseaudio to control the volume of all alsa channels, like it does when it is in 7.1 mode.

I couldn't find anything yet, so any help is appreciated. Thanks in advance.

---

