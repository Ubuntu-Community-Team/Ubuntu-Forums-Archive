---
title: "How do I install software in 17.10"
date: 2017-11-05
forum: General Help
---

### Post by rplantz on 2017-11-05
Most of the software I need to install (e.g., texlive, gnuplot, git, etc., etc.) is not available through "Ubuntu Software." Synaptic no longer works in 17.10 without using a hack that opens a security risk. I can use apt-get, but I like the "history" that Synaptic maintains. And when I look at the official Ubuntu help, it doesn't even tell how to install software. So, what't the officially approved way to install software on 17.10?

---

### Post by deadflowr on 2017-11-05
synaptic will run fine (normal) if you log out of the current session and into Ubuntu on Xorg at the login screen (click the cog icon the appears below the password field)
The hack is only if your insistent to run wayland for everything you do.

---

### Post by rplantz on 2017-11-06
Thank you, deadflowr. I decided to use apt-get, which required me to hone my skills a bit (a good thing).

I had previously used the xhost xi:localuser:root hack to allow me to run synaptic. My system crashed big time while I was installing things with synaptic. I had to reinstall 17.10. I have no idea if the crash was caused by my use of synaptic, but superstition encouraged me to become more familiar with apt-get and use that instead. Been doing this stuff since the early 60s, and the command line still feels "safer" to me.

---

### Post by monkeybrain20122 on 2017-11-07
> **rplantz said:**
> Thank you, deadflowr. I decided to use apt-get, which required me to hone my skills a bit (a good thing).


Not sure what "skills" you are talking about. The only "skill" you need to use apt (no longer apt-get) is to know the exact names of the packages, which is pretty trivial but also can be frustrating if you don't, unless you mean typing skill. :)

---

### Post by rplantz on 2017-11-07
I suppose "knowledge" would be a better word than "skill." I'm learning more about using the various options of apt. My typing skill is already pretty good. I learned touch typing over sixty years ago. Now I have difficulty entering text on small touch screens.

---

