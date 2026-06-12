---
title: "General problems with Lenovo Y510p"
date: 2014-11-29
forum: General Help
---

### Post by Mu57ard on 2014-11-29
Hello. I recently switched from Windows to Ubuntu 14.04. My computer is draining the battery like crazy and runs very slow when just using the battery -- this did not happen with Windows. The only real mod I have made since installing Ubuntu has been to modify /etc/default/grub and /etc/modprobe.d/blacklist.conf as i was having problems dimming the screen. (I used a solution I found online). It also runs very very slow and even crashes when I connect it through HDMI to my TV (even when laptop is plugged in).

I am still new to Ubuntu, so I am not entirely sure what logs you may need in order to help me. I greatly appreciate your help.

---

### Post by dsc1596 on 2014-11-29
Hey Mu57ard, great looking laptop by the way. While I don't have any experience with that model, from what you said it sounds like it might be related to a video driver issue. Have you checked "System Settings-->Software and Updates-->Additional Drivers" for any available proprietary drivers? That's usually the first thing I do after a fresh install, since you get better graphics performance that way. Also, you may try using "TLP" to improve battery life. Go [here]("http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html") for a write up on this, find #8, laptop tweaks. Just a thought, but is it possible Ubuntu 14.10 would have better support for this machine, since it is so new?

---

### Post by oldfred on 2014-11-29
Not sure if any of these are similar enough models to have solutions to issues:

       Some Lenovo comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

The nVidia driver does use a lot more power. Often users just set system to use Intel interal video for improved battery life.


 lenovo W520 with dual video, use Intel boot parameters to boot
[http://askubuntu.com/questions/498161/boot-up-problem-14-04-grub-swap-nvidia-with-pictures/500852#500852](http://askubuntu.com/questions/498161/boot-up-problem-14-04-grub-swap-nvidia-with-pictures/500852#500852)

---

### Post by Mu57ard on 2014-11-29
> **dsc1596 said:**
> Hey Mu57ard, great looking laptop by the way. While I don't have any experience with that model, from what you said it sounds like it might be related to a video driver issue. Have you checked "System Settings-->Software and Updates-->Additional Drivers" for any available proprietary drivers? That's usually the first thing I do after a fresh install, since you get better graphics performance that way. Also, you may try using "TLP" to improve battery life. Go [here]("http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html") for a write up on this, find #8, laptop tweaks. Just a thought, but is it possible Ubuntu 14.10 would have better support for this machine, since it is so new?

I have done these two tweaks and my battery life seems to have improved somewhat -- not nearly as good as it's supposed to be. I appreciate your help very much!

---

