---
title: "Xubuntu 16.10.Not running the sound through the headphones.Need help.ENG screenshots"
date: 2016-12-10
forum: General Help
---

### Post by tola90 on 2016-12-10
This is what is displayed in Alsamixer and Pulseaudio(screen shots)
The problem with "headphon" channel. No volume slider all the way, although the channel itself is enabled.
The sound is nothing more did not check. Headphones work. At the previous system worked

[URL="http://i.imgur.com/0I09HFc.png"]
  [/URL][URL="http://i.imgur.com/gyFTZ8W.png"]
  [IMG]http://imgur.com/gyFTZ8Wl.png[/IMG]
[/URL]

[URL="http://i.imgur.com/E4jczOP.png"]
[/URL][URL="http://i.imgur.com/3EaDfuK.png"]
  [IMG]http://imgur.com/3EaDfuKl.png[/IMG]
[/URL]

---

### Post by RobGoss on 2016-12-10
I think that would be a good idea to convert those screen shots in to English you might get better help that way

---

### Post by tola90 on 2016-12-11
> **RobGoss said:**
> I think that would be a good idea to convert those screen shots in to English you might get better help that way

Ready

---

### Post by Yellow Pasque on 2016-12-11
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Geoffrey_Arndt on 2016-12-12
Did you try what is shown in this video? . . . . also, unmute the far right setting (can always reverse that if needed):

[https://www.youtube.com/watch?v=wWmXG-e6yzI](https://www.youtube.com/watch?v=wWmXG-e6yzI)

---

### Post by RobGoss on 2016-12-12
I would recommend making sure the levels for the Alsamixer is at the highest levels, I had a issue with sound on one of my machines and this was the fix for it

Have you also checked to make sure nothing is muted?

---

### Post by tola90 on 2016-12-12
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Here is information on ALSA.
[http://www.alsa-project.org/db/?f=89ab11e99363f747a48640dd57eb43490d4e490b](http://www.alsa-project.org/db/?f=89ab11e99363f747a48640dd57eb43490d4e490b)

> **Geoffrey_Arndt said:**
> Did you try what is shown in this video? .  . . . also, unmute the far right setting (can always reverse that if  needed):

[https://www.youtube.com/watch?v=wWmXG-e6yzI](https://www.youtube.com/watch?v=wWmXG-e6yzI)


**unmute the far right setting **(can always reverse that if needed) - what is it? And how to do it?

I do not quite understand what was proposed to do in this video. (Except  I do not have sound). But if there it is on / off channel using M  characters, then I did it. Another try to read my other answers in this  post.

> **RobGoss said:**
> I would recommend making sure the levels for the Alsamixer is at the highest levels, I had a issue with sound on one of my machines and this was the fix for it
Have you also checked to make sure nothing is muted?

I tried to do it, did not help.The problem is that the channel "headfon" [COLOR=#ff0000]**[SIZE=4]_no _[/SIZE]**[/COLOR][COLOR=#ff0000]**[SIZE=4]_volume slider_[/SIZE]**[/COLOR]. So I can not adjust the volume there. Although the channel can be activated and deactivated by means of the letter M.

---

### Post by Yellow Pasque on 2016-12-12
Oh no, not an AC97 sound chip :(

About the only suggestions I have are trying your headphones in different jacks and trying a quirk: [https://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#2125](https://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#2125)
```
echo "options snd-intel8x0 ac97_quirk=hp_only" | sudo tee /etc/modprobe.d/ac97.conf
```
If it does not work after reboot, undo the change:
```
sudo rm /etc/modprobe.d/ac97.conf
```

> **tola90 said:**
> The problem is that the channel "headfon" no volume slider. So I can not adjust the volume there. Although the channel can be activated and deactivated by means of the letter M.

The problem is that you have no headphone mixer setting at all.  The channel you are toggling in your screenshot is the "headphone jack sense" (the setting that controls whether the speaker is muted when the headphones are plugged in). It is not supposed to have a volume slider..

---

### Post by tola90 on 2016-12-12
> **Temüjin said:**
> Oh no, not an AC97 sound chip :(

About the only suggestions I have are trying your headphones in different jacks and trying a quirk: [https://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#2125](https://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#2125)
```
echo "options snd-intel8x0 ac97_quirk=hp_only" | sudo tee /etc/modprobe.d/ac97.conf
```
If it does not work after reboot, undo the change:
```
sudo rm /etc/modprobe.d/ac97.conf
```


 used the codes. Did not help.

So the problem is not in the channel ...
I'm, like, seen screenshots, where the channel "Headphone" volume slider was ...

---

### Post by tola90 on 2016-12-13
up

---

### Post by Yellow Pasque on 2016-12-13
The only other suggestion I have is changing this setting to 4ch or 6ch and trying to plug the headphones into different jacks:
```
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
```

> I'm, like, seen screenshots, where the channel "Headphone" volume slider was ... 
Once again, you are misunderstanding. This is what you have highlighted in the screenshot:
```
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
```

---

### Post by tola90 on 2016-12-16
> **Temüjin said:**
> The only other suggestion I have is changing this setting to 4ch or 6ch and trying to plug the headphones into different jacks:
```
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
```


don't work..

---

