---
title: "Sound disappears in 8.04. help!"
date: 2008-06-11
forum: General Help
---

### Post by yuv656 on 2008-06-11
Yesterday I installed 8.04, and my sound worked fine.

When I booted today, suddenly I have no sound card installed.

```
conrad@conrad-desktop:~$ aplay -l
aplay: device_list:205: no soundcards found...

```

```

conrad@conrad-desktop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

I have an Intel dragontail peak motherboard with onboard sound.

The only changes I've made was to:
- Install gnome media keys script in amarok
- Install flash plugin for mozilla

Any help would be appreciated.

[IMG]http://www.chweb.net/downloads/Untitled.jpg[/IMG]

[IMG]http://www.chweb.net/downloads/Amarok.jpg[/IMG]

---

### Post by yuv656 on 2008-06-11
bump

---

### Post by yuv656 on 2008-06-11
I fixed the recognition of my sound card using advice from here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/)

The problem is that now ALSA is playing all sound through my pc speaker. Any ideas? Please, I'm going mad here. I have troubleshooting this for 4 hours straight.

---

### Post by alxlabs on 2008-06-11
> **yuv656 said:**
> I fixed the recognition of my sound card using advice from here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/)

The problem is that now ALSA is playing all sound through my pc speaker. Any ideas? Please, I'm going mad here. I have troubleshooting this for 4 hours straight.

Welcome to the club :) I have

```

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

I had problems with everyhting - skype, games run thru wine, multimedia playback - it worked evry other time or didn't work or worked thru speaker. I figured out that combination as per attached file works fine. Try it by pressing "test" buttons

---

### Post by yuv656 on 2008-06-11
Thanks for the reply.

I don't have the **Intel HDA (alsa mixer)** option at Default Mixer, only three options related to the pc speaker.

---

