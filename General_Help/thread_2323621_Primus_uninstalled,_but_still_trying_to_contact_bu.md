---
title: "Primus uninstalled, but still trying to contact bumbleed daemon"
date: 2016-05-06
forum: General Help
---

### Post by Nicholas_Williams on 2016-05-06
I've finally given up trying to sort this issue myself and have come seeking guidance.
  Originally I had bumblebee installed with the following  packages(bumblee bumblebee-nvidia primus nvidia-352). I was having issue  getting my steam install to work, so I un-installed everything and  reverted back to my iGPU. Now a few of my applications will not start, most notably skype. 
  
The error I get is:

```
primus: fatal: failed to connect to Bumblebee daemon: No such file or directory
```

I'm not sure why this is happening as I no longer have bumblebee  installed. Any help I can get with this would be very appriciated!


[SIZE=5]SOLVED!
[SIZE=3]I purged all of the nvidia packages on my system using the **"aptitude purge ~nnvidia"** command and then had to reinstall the 32bit libGL.so.1 library using the **"aptitude reinstall libgl1-mesa-glx-lts-vivid:i386".** A quick reboot later and all is well.

Thank you runrickus for taking an interest! You pointed me in the right direction.[/SIZE]
[/SIZE]

---

### Post by QDR06VV9 on 2016-05-06
What dose this report from the terminal.
```
apt-cache policy nvidia
```

---

### Post by Nicholas_Williams on 2016-05-07
The output from [B]apt-cache policy nvidia

[/B]```
nvidia:
  Installed: (none)
  Candidate: (none)
  Version table:


```

---

