---
title: "Totem can't play mp3"
date: 2006-07-14
forum: General Help
---

### Post by music_man on 2006-07-14
I am not enjoying this Totem media player. It can't play AVI (which is understandable) but it also can't play mp3 (?).

I have to download a codec for it? Mp3 is a common format, why on earth does it not come with inbuilt mp3 support?

---

### Post by aysiu on 2006-07-14
This explains everything (why it isn't included and how to install it):
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by music_man on 2006-07-14
To add mp3 support to GnomeBaker, install gstreamer0.8-mad and gstreamer0.8-misc. (?)

I clicked on the Gnomebaker URL and it wasn't there. Do I still get gstreamer0.8-mad and gstreamer0.8-misc (?)

Can I get that through the Synaptic package manager?

---

### Post by music_man on 2006-07-14
I got Beep media player. I just want something that works

---

### Post by aysiu on 2006-07-14
> **music_man said:**
> I got Beep media player. I just want something that works
Are you saying that Beep Media Player works for you and Totem doesn't? Or are you saying you desire a Linux distro that comes with MP3 playback?

If it's the latter, consider using Mepis, PCLinuxOS, or Blag. Those come with a lot of proprietary codecs.

---

### Post by Crosbie on 2006-07-15
Or just install and run [EasyUbuntu.]("http://easyubuntu.freecontrib.org/")

---

### Post by music_man on 2006-07-15
How can I set Beep to be my default media player please?

---

### Post by aysiu on 2006-07-16
> **music_man said:**
> How can I set Beep to be my default media player please?
Right-click an MP3.
Select **Properties**.
Select **Open With**.
Click on the dot next to Beep.
If Beep isn't there, add it.

---

### Post by mopar126 on 2006-11-02
Well, THANK YOU!!!! I am just getting the idea of this all. Music is VERY NEEDED! Now on to making games work(for another thread). Thank you, I'll learn this yet, LOL!

---

### Post by Polygon on 2006-11-02
you will most likely have to do this for all of the music file formats (ogg, wav, mp, whatever) but once you do it beep should be the default

---

### Post by squibbon on 2006-11-03
Tried installing gstreamer0.8-plugins which has a lot of dependencies but didn't solve the problem of not playing MP3s. What i did was i installed gstreamer0.10-fluendo-mp3 and it worked.

---

