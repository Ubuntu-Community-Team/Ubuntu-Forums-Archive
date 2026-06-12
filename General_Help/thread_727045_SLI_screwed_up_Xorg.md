---
title: "SLI screwed up Xorg"
date: 2008-03-17
forum: General Help
---

### Post by cheesecake.llama on 2008-03-17
Hi, I am running Ubuntu 7.10 and it was a clean install, and everything booted up the first time just fine. I had two 8800gt's connected and everything worked. It worked for about a week and then i figured out that I had to manually turn on SLI so, i read a guide that said to use nvidia-config or something like that and to change the SLI command on that to "On" "Off" "Auto" "AFR" or "SFR" I selected AFR and restarted xserver and then i got a blank screen. I can go into the text mode with CTRL + ALT + F1 and did nvidia-config again and tried to turn it to SFR, On, Off, and Auto and restarted the xserver after each of these but nothing is working and i'm new to ubuntu so i don't really know what to do. Please help guys. Oh and by the way, I am using the latest nvidia drivers installed by ENVY. :confused: :confused: :confused:

---

### Post by DoctorMO on 2008-03-17
Can you post the error messages reported by xorg in /var/log/Xorg.0.log (or just attach the file) otherwise we can't help you fix the problem.

---

