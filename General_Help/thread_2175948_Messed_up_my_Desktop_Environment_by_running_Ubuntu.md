---
title: "Messed up my Desktop Environment by running Ubuntu Tweak janitor"
date: 2013-09-22
forum: General Help
---

### Post by nitinsatish on 2013-09-22
I had upgraded my PC from ubuntu 12.04 to 13.04 (through 12.10). The system booted fine, but I felt it was a bit slow. So I ran Ubuntu Tweak janitor clearing old packages, config files and kernels. It also told me few packages are no longer required and I cleared them as well.


But after this reboot, I am getting "The system is running in low-graphics mode" error. I tried removing and re-installing nvidia-current, nvidia-settings and xorg packages. But its still the same. I tried putting xorg.failsafe configuration also.


I guess Ubuntu Tweak has removed some config or package required. Can I someway re-install entire Display+drivers stack ? Any other packages i need to try re-install/reconfigure ?

---

### Post by TheFu on 2013-09-22
Why not just restored from the pre-upgrade backup?

---

### Post by ibjsb4 on 2013-09-22
Ubuntu Tweak janitor is known to be over zelous when removing packages.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Ubuntu+Tweak+janitor&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Ubuntu+Tweak+janitor&sa=Search&cof=FORID:9)

For system cleaning I use Bleachbit, it does not have this problem.

[https://apps.ubuntu.com/cat/applications/raring/bleachbit/](https://apps.ubuntu.com/cat/applications/raring/bleachbit/)

---

