---
title: "Improve bluetooth headset audio quality"
date: 2018-01-30
forum: General Help
---

### Post by jacopastorius82 on 2018-01-30
I noticed that the there is a audio quality loss in playing files via bluetooth with bluetooth headset. I can compare that quality playing the same file in windows with the same software (VLC), which is much more superior and in xubuntu appears to be a much metallic and seems to be hearing a 6kbps mp3 file. Is there something i can do to improve the listening experience? Tried other software like parole and same issue

---

### Post by Holger_Gehrke on 2018-01-30
There are two modes for Bluetooth audio transmission: HSP/HFP (Headset Profile/Hands Free Profile) and A2DP (Advanced Audio Distribution Profile). The former is for telephony and produces a sound quality (barely) acceptable for that purpose. The latter is meant for actually enjoying what you hear ;). 

If the problem is that your headset is seen as a HSP/HFP device, then depending on a lot of factors you might be able to switch your device to A2DP either in the pulse-audio mixer on the tab "Configuration"  or with the Bluetooth applet (Click on the applet, choose devices, right click on the headset, "Audio Profile") . On my system a cheap Bluetooth speaker can handle both but I have to try multiple times before the change 'takes', while a slightly more expensive (but still not top-dollar - or rather euro ...) headset comes up as a2dp on it's own and trying to change to low quality makes audio output hang ...

If the device is already set to A2DP but the quality is still not as good as in Windows, then there's not much that can be done. The sound server gets PCM data from the app and sends it to the Bluetooth stack which encodes it as SBC (low-complexity sub band coding, the default codec for Bluetooth A2DP; a sound sink may implement other codecs, but only SBC is always guaranteed to be available) and sends it to the headset. To avoid the double decoding and encoding (format X to pcm, pcm to sbc) the (player-) Application, sound server, Bluetooth stack and device would have to be much closer integrated and "tell" each other what formats they can handle. With the kind of legal mine field codec support can be, I'm not holding my breath waiting for that ...

Holger

---

### Post by jacopastorius82 on 2018-01-31
thank for your reply, the issue was just what you're saying but i had trouble setting the headset to A2DP. I found a workaround with this script

```
wget https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae/archive/d698974910bbb7d016ec0ad08c1bf41b4b524364.zip[CODE]
```[/CODE]

---

