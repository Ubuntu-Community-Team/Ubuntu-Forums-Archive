---
title: "Stuck in login loop and with very low performance after installing packages"
date: 2017-12-15
forum: General Help
---

### Post by Oinos on 2017-12-15
I have a fresh installation of ubuntu 16.04; initially it worked fine, but then I wanted a 3d program to recognise my gpu, so I ran ```
sudo apt-get install nvidia-cuda-toolkit nvidia-modprobe
```. Sometime later I wanted to watch a downloaded video, but when I ran it, I was prompted to install a long list of codecs, so I did. Lastly, I installed some profiling programs, like indicator-multiload. After all of this I rebooted the computer and got those two issues.

How can I figure out which package is the faulty one? For the record, the gpu is gtx.

---

### Post by Oinos on 2017-12-17
Update: I've narrowed down the possible reasons:

1. It's likely not lightdm; tried replacing it with gdm, but upon rebooting I got no login screen, just mostly black one with occasional blinking of some console messages. Barely got back to the ctrl+alt+f1 console to restore lightdm.
2. It's likely not the nvidia drivers. Removing them leads to the login screen not being displayed; instead I get a 'No monitor, etc. found...' message. I've installed nvidia-387 through the *drivers autoinstall *command.

3. This leaves the video codecs&other stuff, that was install automatically - I'm not even sure if they were only video codecs. How do I revert those?

What other reason could there be for this behaviour?



Here's what xsession errors say:
```
Xlib: extension "GLX" missing on display ":0"
Xlib: extension "GLX" missing on display ":0"
openConnection: connect: No such file or directory
cannot connect to britty at :0
```
Then various processes killed by TERM signal

---

