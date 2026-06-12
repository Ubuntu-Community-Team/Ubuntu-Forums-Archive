---
title: "ubuntu 18.04 system hangs/freezes because of pulesaudio and alsa issues"
date: 2020-07-25
forum: General Help
---

### Post by stephenlin on 2020-07-25
I've installed ubuntu 18.04 for while, and the OS system keeps have that temporarily hang/freeze issues once in a while. It happens probably every two or three days.  

I found that this hang up issues only happens when I watch stream videos on the internet. Sometimes it's just the sound suddenly go breaking when playing stream videos. and that can be easily fixed by the command:

sudo killall pulseaudio 

However, sometimes the situation will be worse and causing the sound skipping and the whole system just hangs/freezes terribly.  I've checked the system logs and it shows below messages: 

[ATTACH=CONFIG]286536[/ATTACH]

I believe it is the audio issues that is causing the system hang up. However after google the issues I still cannot find the answer to solve this problem. 

I've also installed libcanberra-gtk-moudle: amd64 after google the info provided by the system log couple weeks ago (kind forget exactly what the log said at that time but google told me that it was something related to sound issues).   

I also have all following libcanberra packages installed in my system:  
 
libcanberra-gtk0:amd64
 libcanberra-gtk3-0:amd64
libcanberra-gtk3-moudle:amd64  
libcanberra-pulse:amd64
libcanberra0:amd64
[ATTACH=CONFIG]286537[/ATTACH]

Does anyone know how to fix this system hang/freeze issues??  

Thanks

---

### Post by kc1di on 2020-07-25
Please go to a terminal a type this command and post the output here:```
lshw -C video
```

---

### Post by stephenlin on 2020-07-25
> **kc1di said:**
> Please go to a terminal a type this command and post the output here:```
lshw -C video
```

Thanks for the reply, and the output is shown below:

[ATTACH=CONFIG]286540[/ATTACH]

---

