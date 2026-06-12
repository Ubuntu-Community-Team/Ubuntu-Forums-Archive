---
title: "Cpu frequency Applet"
date: 2006-07-02
forum: General Help
---

### Post by adam.tropics on 2006-07-02
Ok, so I have p4-clockmod, cpufreq-ondemand, cpufreq-userspace, and cpufreqd up and running, and the applet displays correctly, and does seem to run....sort of. But the left click menu that used to work during Dapper development, no longer seems to work at  all. 

This is on Dapper, upto date, with Celeron M 1.5, it has 8 workable freqs, incl 1.5, but without this running properly, power consumtion is horrible!

---

### Post by adam.tropics on 2006-07-02
Got it! I am truly an idiot at times, and tend to ignore the simple things presuming the solution will be more complex. It is just a screwy default permissions setup....
```

 sudo chmod +s /usr/bin/cpufreq-selector
```

fixed it...

---

