---
title: "Adobe Flash crash in 13.10"
date: 2013-10-25
forum: General Help
---

### Post by rafe101 on 2013-10-25
I'm having issues with both Chromium and Firefox locking up since upgrading to 13.10. Both are doing it whenever there is embedded video, but Chromium is having issues with no video present (e.g., reddit, facebook, etc.).

I ran firefox in a terminal and went to youtube to see what it says. This is the only message:

###!!! [Parent][RPCChannel] Error: Channel timeout: cannot send/recv

If I wait long enough, I will eventually get a message from firefox. In this situation it said that the adobe flash plugin crashed and that no report is available. I've tried reinstalling the flash plugin but it hasn't helped. Is anyone else having problems like this?

---

### Post by fcigoi on 2013-11-03
Same problem here.

I have tried all the suggested remedies I have found, to no avail.

---

### Post by benhill70 on 2013-11-04
Chrome is working for me, but Firefox 25 is crashing with 11.2.202.310 on Ubuntu 13.10.

I have tried reinstalling the flash plugin.

I'm also getting the same error as above.

###!!! [Parent][RPCChannel] Error: Channel timeout: cannot send/recv

Also tried:
Starting Firefox will all add ons disabled.

---

### Post by benhill70 on 2013-11-06
I fixed my problem, it was a problem with pulseaudio.

rm -r ./config/pulse
reboot

From this thread, I didn't not edit alsa-base.conf or the pam step.
[http://askubuntu.com/questions/290620/ubuntu-13-10-without-sound-in-flashvideos-at-firefox-chromiun](http://askubuntu.com/questions/290620/ubuntu-13-10-without-sound-in-flashvideos-at-firefox-chromiun)

---

