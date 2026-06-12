---
title: "Pulseaudio is BROKEN!"
date: 2008-06-24
forum: General Help
---

### Post by damis648 on 2008-06-24
I have been somewhat ignoring this for sometime now... it has been a few weeks and I have switched back to ALSA. Now I want pulseaudio back, so I need help fixing it. I have searched many threads through many forums, but I cannot seem to fix pulseaudio. At first when running a test via the sound settings, it would give me an error ( I do not remember it). Now I have installed the "Device Choose" app, and have configured the local server to "Add virtual output device for simultaneous output on all local sound cards" and selected my sound server and sink (simultaneous) but the sound still does not work via pulseaudio. Through this madness I did get OSS to work through through some bizarre way, however. Anyway, now when I run the pulseaudio sound test in sound preferences i get the bar swinging back and forth with no error, but also not sound. Help??

**UPDATE**: I just reinstalled Ubuntu... after a few days of smooth sailing PulseAudio screwed up again. I had completely no sound for a few boots and then it came back. The issue now is I longer have audio input. Mics do not work at all. Any help?

---

### Post by sdennie on 2008-06-24
Have you seen this thread?  It seems to have a lot of good info on pulse audio: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by damis648 on 2008-06-24
> There are three possible results:

   1. The application plays audio and lists an entry in PulseAudio Volume Control.
   2. The application plays audio and does not list an entry in PulseAudio Volume Control.
   3. The application fails to play audio and does not list an entry in PulseAudio Volume Control.

Unfortunately none of those are my problem.

Is a reinstall in order? That would not be the worst thing, as I do need to clean up my system;.

---

### Post by damis648 on 2008-06-24
Any other suggestions? I am on the verge of a reinstall because i have an application that i would like to use pulseaudio for.

---

### Post by Nexusx6 on 2008-06-24
I've posted the steps I took to get PA working for me in Kubuntu on my blog, it might work for you too. Everything should work just the same for Ubuntu as well, except for the start-up script.

Let me know if it works out, or if you have any questions:
[http://nexsjournal.blogspot.com/](http://nexsjournal.blogspot.com/)

---

### Post by BlueSkyNIS on 2008-06-24
There is a possibility they will change PA version in 8.04.1 release expected in July.

Luckily, this will be the case and a solution for many audio problems. :popcorn:

---

### Post by damis648 on 2008-06-25
> **BlueSkyNIS said:**
> There is a possibility they will change PA version in 8.04.1 release expected in July.

Luckily, this will be the case and a solution for many audio problems. :popcorn:

I already have it, it is in the pre-release repos. I am cleaning up my system and reinstalling anyway so I will close this discussion I guess. I am removing Windows so wish me luck!

---

### Post by damis648 on 2008-06-30
Bump on the update?

---

