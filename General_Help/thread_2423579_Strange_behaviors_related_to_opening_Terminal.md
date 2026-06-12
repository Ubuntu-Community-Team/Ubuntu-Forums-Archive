---
title: "Strange behaviors related to opening Terminal"
date: 2019-07-25
forum: General Help
---

### Post by tyguy2 on 2019-07-25
Hello all,

I've been using an install of Ubuntu 16.04 for a while now. Recently I went to open Terminal, only to find it does not open. The computer simply loads for a few seconds, then nothing comes up. XTerm launches fine, however, any software installation programs do not launch or work. Software center launches but does not uninstall or install programs. The Software Update and Settings section in the System settings does not open, no matter how much I click on it. Essentially any program that relates to installing programs onto the computer does not function. I haven't done anything to change the OS, I just booted one day and none of these programs seem to launch. Does anyone have any idea as to what I could do?

Thanks!

---

### Post by again? on 2019-07-25
In xterm run...
```
gnome-terminal
sudo apt update
sudo apt upgrade
```
Errors??

---

