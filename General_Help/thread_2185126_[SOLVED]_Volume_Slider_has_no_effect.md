---
title: "[SOLVED] Volume Slider has no effect"
date: 2013-11-01
forum: General Help
---

### Post by kevinkendall.6 on 2013-11-01
Hi there, 

Lubuntu is my first linux distro I've used. Enjoying it! Considering putting it on my main PC! 

My only issue is the volume slider. Any app that is opened which has independent volume controls can have the levels adjusted i.e Spotify, Browser etc. My issue is the volume slider in the bottom right has no effect on any volume. When I choose to look at the settings I'm given 'Alsamixer'. To the best of my knowledge I've got everything turned up full that can be turned up. I've also tried changing between default and the soundcard it lists and the problem persists. 

Any help much appreciated! 

Thanks

EDIT: 

In the terminal I ran 
```
sudo apt-get pulseaudio
```
then
```
sudo apt-get pavucontrol
```
Once installed I then did 
```
sudo reboot
```

Upon rebooting I opened spotify and the volume slider is working as intended!

---

