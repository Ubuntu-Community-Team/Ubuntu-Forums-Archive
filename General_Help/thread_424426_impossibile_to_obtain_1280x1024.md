---
title: "impossibile to obtain 1280x1024"
date: 2007-04-26
forum: General Help
---

### Post by pennarello on 2007-04-26
hello. I use kubuntu from many time. Today i installed 7.04 (formatted previous 6.10) but i can' t select 1280x1024 with nvidia proprietary driver, desktop is always at 640x480

If i modify xorg.conf (put correct values for my monitor acer al732) and i reboot (to use 1280x1024), monitor goes black and on keyboard "CAPS LOCK", and SCROLL LOCK led flashing (goes on and after 1 sec turn off, and after 1 sec turn on etc). How can i solve?

If i use nv driver all was ok

i have 6800gt

---

### Post by pennarello on 2007-04-27
Ah monitor goes off after nvidia logo, and before login screen

---

### Post by dcstar on 2007-04-27
> **pennarello said:**
> Ah monitor goes off after nvidia logo, and before login screen

You probably don't have the correct NVIDIA driver installed now, do a forum search as there are many detailed posts addressing this sort of issue.

---

### Post by pennarello on 2007-04-27
> **dcstar said:**
> You probably don't have the correct NVIDIA driver installed now, do a forum search as there are many detailed posts addressing this sort of issue.

can you show me those posts? I have searched but i did not find those posts. Thank you very much

---

### Post by laidback on 2007-04-27
Other people seem to swear by the Envy program:-

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

worth a look and possibly a try.

---

### Post by pennarello on 2007-04-27
i tried with envy, but i have same problems

---

### Post by laidback on 2007-04-28
Could it be that there are lots of bits left from previous nVidia installation attempts, i.e. the system needs to be clean and back to nv state before Envy is installed. There is a remove on the Envy menu but no doubt you've tried it already.
This video issue really is a pain and despite gallant attempt by many problems still seem to occur. I have a 939 board where the on-board video flashes all the time, Envy has come closest to sorting it and did give me 3D, but I have now concluded that I need to try a new video card and come at the problem from a different angle.

---

### Post by Hairy_Palms on 2007-04-28
did you install from the repos or from nvidia website? if nvidia website then try changing your resolution using nvidia-settings.

---

### Post by kodoku on 2007-04-28
how about reconfiguring x from scratch?

> sudo dpkg-reconfigure xserver-xorg

---

### Post by konungursvia on 2007-04-28
> **kodoku said:**
> how about reconfiguring x from scratch?

+1 for this idea. There is more to it than including 1280X1024 in the screen section of xorg.conf

---

### Post by Cresho on 2007-04-28
I have a 6800 GT and it works fine.

first off, install correct drivers.

sudo apt-get install nvidia-glx nvidia-kernel-common

secondly,

sudo dpkg-reconfigure xserver-xorg

it will take you through the configuration.  you may want to use the space bar to include that particular resolution.  then after all configuration is done, reboot.

the only problem is run command "nvidia-settings" because when i bump up my settings to 16x aniso and antiali, my screen becomes unstable so use 8.  the other problem after reboot, the settings reset.  I think its a perm issue on my part so ill dig more on this.

glxgears to make sure it runs in terminal.

---

