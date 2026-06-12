---
title: "Lubuntu 18.04 - how can I test microphone?"
date: 2020-12-25
forum: General Help
---

### Post by 2CV67 on 2020-12-25
Hi!
I have Lubuntu 18.04LTS running on an old Eeepc Netbook.
I am having a lot of trouble trying to join Zoom meetings, mainly no sound heard by others or very bad sound.
Is there some way, independant of Zoom, I could check the function & settings of the built-in microphone(s)?

I found lots of information on microphone testing in Ubuntu, but nothing for Lubuntu.
There doesn't seem to be anything under "Sound Settings"...

Thanks for any suggestions!

---

### Post by guiverc on 2020-12-25
I've only done it via other programs (*and haven't done that in years either on an eeepc*).  The program `cheese` comes to mind, but it may not have been the program I used.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by grahammechanical on 2020-12-25
I do not have Lubuntu installed. I use Ubuntu + Gnome shell. But I also have LXDE Linux installed. And if the user interface is similar to the LXQt of Lubuntu then this link might be useful

[https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html](https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html)

You need to find the menu that allows you to open the volume mixer or the PulseAudio control panel. Under the Input Devices tab there should be a slider that lets you increase the sound level going into the computer through the microphone. There should also be a bar that moves across and back as the microphone detects sound. That will give you an indication that the microphone is working.

Regards

---

### Post by HermanAB on 2020-12-25
You can also go Olde Skool and test the audio with sox, rec and play.

$ rec filename
$ play filename

---

### Post by 2CV67 on 2020-12-28
Thanks for all those suggestions!

In the meantime, I had found several sites for testing microphones on-line & they all showed some activity (wiggly line) when speaking to the microphone.
So it seemed to be at least connected & working to some extent.

I then installed Cheese (had bever heard of it - thanks for that) and that allowed me to record & replay a short session with the webcam & microphone.
That showed that the microphone was working quite reasonably.
The only snag seems to be an irritating level of background noise - maybe the netbook cooling fan?

Have not yet found any way of improving that condition, or of finding why Zoom users don't hear me...

Thanks again!

---

### Post by guiverc on 2020-12-28
Headset with microphone maybe is helpful. Older pcs with *spinning rust* drives contain moving parts which can cause vibration (unlike modern SSDs), generate more heat (meaning fan too) etc.  By using external microphone you've at least made the pc further away, and you're likely closer to the mic  (and maybe get a better microphone too).

I just booted my eeepc using Lubuntu 18.04.5* (live)*, added `cheese` to record a quick test, which was played in `vlc` (also added/installed) and speaker was okay, volume however was very low, and yeah there is/was what could be described as background noise.. 

With my eeepc just sitting there on, I hear a buzzing (whine maybe) sound from electronics... I'd expect that to be picked up by microphone, however a quick play and it looked like it's just the box itself (eg. reboot and hit ESC to select boot device but let it sit there, and I can detect noise then too, before any OS has loaded with nothing yet loaded; firmware only active).  Maybe it is the fan, but it's part of the machine so I doubt much can be done about it.

---

### Post by 2CV67 on 2021-02-08
I left this subject for a while but am now trying again.
I am still at the same place - nobody else can hear me.

Before joining a meeting, I can, of course, opt to "Test Speaker & Microphone" which I have tried many times.
One thing I forgot to mention & which may be significant, is that, although there is a "Test Speaker" button, there is no "Test Mic" button for me...
Is this a clue?

Thanks!

---

