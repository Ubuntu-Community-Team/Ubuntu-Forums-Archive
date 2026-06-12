---
title: "Sound stops working completely after playing music files"
date: 2008-05-08
forum: General Help
---

### Post by bg1256 on 2008-05-08
Before I say anything else, let me say I am not attempting to spam the forums. I made an original post here: [http://ubuntuforums.org/showthread.php?t=786777](http://ubuntuforums.org/showthread.php?t=786777)

However, the title no longer describes my problem effectively.

For some reason, my sound stops working completely in the middle of my session, and I only noticed it today after this morning's updates.

Here is the summary of my problem:

I boot up my computer, and sound is working properly. I fire up a music player (Exaile or Amarok), and music plays properly.

However, after I close the music player, my sound stops working completely. Video files don't play sound (in VLC or Movie Player), and I can't get sound working in any other application either.

The only way I can get it working is after a full reboot. This is Ubuntu Hardy after a fresh install and updates.

Help?

edit: I have discovered that Wine applications still have sound, namely Guild Wars.

edit2: Oddly, Exaile does not even show that the track is playing. I select play, and the progress bar just stands still at 00:00. This might suggest that it is a problem with Exaile rather than audio? But if that's the case, then why don't I have audio on video playback?

edit3: more information, I have an HDA intel built-in sound chip, which seems to be controlled by the alsamixer. I have run alsamixer and all looks to be normal as far as that goes. I've also opened system monitor, and it does not seem that either exaile or amarok is running, which leads me to believe that neither of those programs is causing the problem.

edit4: Firefox's sound works. I've tested several flash websites that produce sound, and they are fine. So, I now think that my sound problems are limited to music and video files. But why would that be the case?

---

### Post by hewhocutsdown on 2008-05-11
I second the issue. This is brutally difficult for me, as all flash videos are soundless and Quod Libet or any other media player works for a time, and then sites at 0:00 not playing. The only thing I have found to fix it is a reboot so far.

---

### Post by karthikkito on 2008-05-11
Seconded as well.  However, I did find that restarting X without performing a full reboot brought back the sound...

---

### Post by triple6 on 2009-03-25
Same problem here... p.s. I'm using ubuntu 8.10.

---

### Post by jocko on 2009-03-25
Are the applications that cause sound to stop by any chance set to use alsa directly?
In that case the problem is that you tie up the sound card with one application using direct hardware access through alsa, causing all other sound to fail (and pulseaudio to crash).
Restarting X will restart pulseaudio, which is why you get sound back until next time you try to use alsa. 

Next time sound stops, try to restart pulseaudio:
```
pulseaudio -k
pulseaudio -D
```("-k" terminates any running instance of pulseaudio, "-D" starts the pulseaudio daemon.)
If that doesn't help, then first reload alsa, then restart pulseaudio:
```
pulseaudio -k
sudo alsa force-reload
pulseaudio -D
```And:
Set *all* applications to use pulseaudio instead of alsa. pulseaudio is the *only* application that should have direct hardware access through alsa, everything else should be routed through pulseaudio.

---

