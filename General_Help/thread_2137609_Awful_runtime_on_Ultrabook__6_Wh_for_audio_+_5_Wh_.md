---
title: "Awful runtime on Ultrabook / 6 Wh for audio + 5 Wh for WiFi"
date: 2013-04-21
forum: General Help
---

### Post by arthoc on 2013-04-21
Hello,
I'm having some issues w. my Acer Timeline M5 14" Ultrabook, running Ubuntu 12.10: The battery runtime is approx. 2 hrs. - which apparently isn't suitable for an "Ultrabook" at all. ;)

Having PowerTop 3.1 installed I made out the main perpetrators:
[ATTACH=CONFIG]241616[/ATTACH][ATTACH=CONFIG]241617[/ATTACH]
As you can see, it's mostly the audio & WiFi that's going bananas here. Funny enough, I seem to have two audio-devices and displays, yet there's no external screen connected. The brightness is at 100% since I'm using an AC-adapter atm, ignore that value.

I've also installed bumblebee and it seems to be working:
$ optirun --status 
$ Bumblebee status:  Ready (3.1). X inactive. Discrete video card is off.

Neither Laptop-Mode-Tools nor jupiter have much of an effect.

Can anyone help me here? I'm somewhat desperate, since I cannot figure it out at all. :(

---

### Post by arthoc on 2013-04-30
I've recently updated to 13.04, hoping that the new kernel would be better of in terms of battery-saving... yeah. That was a bummer.

Doesn't have anyone a suggestion what's wrong here? WiFi and audio are consuming so much power, it's incredible. If you decide to use an external mouse (bluetooth or USB, both perform awfully) or turn up the brightness, you shouldn't forget your AC-adapter.

[ATTACH=CONFIG]242002[/ATTACH]

---

### Post by arthoc on 2013-05-02
Sorry for posting again, but I thought I might share all my tweaks with you guys... and maybe somebody offers better solutions.

1. The following disables the "acer-wmi" kernel-module which consumed about 1W. Has no effect on any hardware whatsoever (as far as I'm concerned, this is supposed to be a driver for the fn-shortcuts).
```
$ sudo gedit /etc/modprobe.d/blacklist.conf
# 05/02/13
# Battery saving settings from this point

# acer wmi
blacklist acer-wmi 
```

2. This disables the ethernet on startup. I use WiFi and don't really care about the cable. Should save about 3 - 4W. (you could also auto-mute your sound here by disabling pulseaudio or something)
```
$ sudo gedit /etc/rc.local
# 05/02/13
# Disable ethernet for battery-saving-reasons
sudo ifconfig eth0 down
```

3. Mute audio. There's probably a tweak for that, but the audio-driver consumes quite some power. I'll just listen to music on my iPhone, that's easier anyways. 

4. Turn down the display's brightness. Obviously a big tweak on any laptop, I suppose...

5. Disable any external USB-device. I dunno why, but my USB- or bluetooth-mouse as well as my USB-keyboard consume loads of battery...

This is the result:
[ATTACH=CONFIG]242086[/ATTACH]

---

