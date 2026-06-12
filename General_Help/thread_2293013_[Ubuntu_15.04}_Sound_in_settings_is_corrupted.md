---
title: "[Ubuntu 15.04} Sound in settings is corrupted"
date: 2015-09-01
forum: General Help
---

### Post by aziz07 on 2015-09-01
Hi,

I have lost sound after installing some equalizers but now, even after removing them, my sound is still not working. Sound in settings shows nothing and has graphical glitches such as transparency. How do I repair it? I tried to reinstall pulse audio but no results.

thanks

---

### Post by NathanRodriguez on 2015-09-01
You can check the bottom layer ALSA too.

---

### Post by aziz07 on 2015-09-01
Thanks, how do I check for that?

---

### Post by Geoffrey_Arndt on 2015-09-02
Basically, you would open a terminal window (ctrl+alt+T) and type in alsamixer.

To understand the layout and adjustment settings, here's a video that goes over the most common tweaks.

Just remember, a code of "00" means sound is on, while "MM" means the sound is off (aka muted).

The video is 5 years old and run in Linux Mint, but the adjustments also apply to Ubuntu . . . alsamixer hasn't changed much over the years.

[https://www.youtube.com/watch?v=wWmXG-e6yzI](https://www.youtube.com/watch?v=wWmXG-e6yzI)

---

### Post by aziz07 on 2015-09-03
The thing is that my sound icon in top right is not appearing anymore. Alsamixer shows 00 for speaker etc In sound settings, there's nothing in devices and its transparent like the screenshot I attached.

[http://imgur.com/F70qBNP]("http://imgur.com/F70qBNP")

[IMG]http://imgur.com/F70qBNP[/IMG]

---

### Post by aziz07 on 2015-09-04
Ok, even the about window of ubuntu is also transparent like the sound one. It has a gnome icon insntead of Ubuntu. There is also 2 printer settings icons in settings. How do I fix these without reinstalling from scratch?
Can I just remove and reinstall Unity or it will it won't boot after?

thanks

---

### Post by aziz07 on 2015-09-04
UPDATE: I removed and reinstalled Unity from software center and it fixed corrupted GUI files. Ubuntu shows up in about tab and sound settings are displayed correctly now. There is no more duplicate printer settings. I have not reboot yet to see if sound works. Will report later but it should work as login sound was always present with this issue, except that sound wasn't working after logging in.

Hope this helps others as there is no need to reinstall Ubuntu from scratch.

---

### Post by aziz07 on 2015-09-04
Ok, sound icon shows up now after reboot but still no sound device detected in settings... Its a realtek HD with Intel if that helps...
Sound level in alsamixer always default to 55 after altering it.

---

