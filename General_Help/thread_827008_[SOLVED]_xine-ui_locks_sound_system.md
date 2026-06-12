---
title: "[SOLVED] xine-ui locks sound system"
date: 2008-06-12
forum: General Help
---

### Post by 65 mustang on 2008-06-12
I use the xine-ui package to play DVD's and AVI movies.  In 8.04 once i play a movie in xine-ui it will lock the sound card.  So i can only get sound from it.  I dont get any sound from flash youtube videos in firefox or any other audio application after i play a movie in xine-ui.  The fix is to reboot.  Although once the sound is messed up when i try to reboot it will freeze when i select reboot from inside X.  I have to do a Ctrl+Alt+F1 and then reboot from there.

Does anyone else have this problem?  Could someone else try this and see if they have the same problem.  Im thinking about writing a bug and want to make sure its just not my hardware.

In all previous ubuntu releases i have not had a problem with this.  Guessing it relates to the pulseaudio change.

---

### Post by hesser on 2008-06-12
Follow that thread!
[http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio)

---

### Post by 65 mustang on 2008-06-12
That might fix it.  But do others have this problem?  I was going to write a bug so that everyone does not have to go through that procedure to get it to work.

---

### Post by 65 mustang on 2008-06-12
[https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/239508](https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/239508)

---

### Post by 65 mustang on 2008-06-12
Workaround:
This completely solved the problem on my system.
1) Open xine settings
2) Set configuration experience level to "Master of the known Universe"
3) Go to the audio tab and set the "audio driver to use" to "alsa" (mine was set to "auto" when i had the problems.
4) Restart and it should work and not blow up.

Also posed this here:
[https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/239508](https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/239508)

Hope we can get an upstream fix.

---

### Post by meistercobbman on 2008-06-12
I have a very similar problem: whenever I play audio with rhythmbox or amarok or movie player, my firefox sound stops working. I have to log out to fix the problem. It's very annoying, especially when trying to view youtube.

---

