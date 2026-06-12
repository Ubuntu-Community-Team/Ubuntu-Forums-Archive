---
title: "CpuFreq-set indicator"
date: 2014-09-15
forum: General Help
---

### Post by bariscolaker on 2014-09-15
hello guys, sorry for my noob question but im newbee on linux.

i was looking for changing cpu governers and setting frequencies for my xubuntu 14.04.01 to save battery and heating problems.

i used lots of commands and downloads via command prompt. accually i found what i want, but i dont know how i did :(

i wrote some codes for indicator like windows but it didnot change anything at that time

lastly i changed "rc.local" like this "cpufreq-set -r -u 1200000 cpufreq-set -r -g powersave" to start like this and it works well

after restarting pc i saw indicator in panel but idk which command did this. i need proper utils and indicator command

can u help me find codes?? cause i would like to save it



update: after a few restarts and using programs i realize that cpu automaticaly changed to ondemand, can i fix this?

---

### Post by SBMN7 on 2014-09-15
have you checked BIOS setting ?

---

### Post by Doug S on 2014-09-15
Hi and welcome to Ubuntu forums,

There is a script that runs at startup. It waits 60 seconds and then sets the governor to ondemand. You can make changes there, perhaps keep a backup of the script first.
The file is /etc/init.d/ondemand.

---

