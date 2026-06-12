---
title: "Stupid error message"
date: 2007-04-04
forum: General Help
---

### Post by vladimiroane on 2007-04-04
I am running Feisty on a Fujitsu Simens v3205 and each time I install something I get this nasty error: 

E: linux-restricted-modules-2.6.20-13-generic: subprocess post-installation script returned error exit status 1

Any idea what happens and how I can get rid of it?

---

### Post by acormack on 2007-04-04
if you open a system console window and type 

sudo tail -f /var/log/syslog

Then try installing something do you get any more detailed errors appearing?

---

### Post by thelinuxguy on 2007-04-04
> **vladimiroane said:**
> I am running Feisty on a Fujitsu Simens v3205 and each time I install something I get this nasty error: 
E: linux-restricted-modules-2.6.20-13-generic: subprocess post-installation script returned error exit status 1
Any idea what happens and how I can get rid of it?

The installation/configuration of that particular package had encountered an error. Now whenever you try to install anything, the post-installation script gets executed and that script is generating the error.
For getting rid of the error message, dismiss the dialog that shows the above error and expand the terminal panel in the "Changes applied" window. The terminal output will have the name of the file (typically in /var/lib/dpkg/info on Edgy) that caused the error and the line number. Commenting out that line should stop the error message from being shown the next time.

However, [COLOR="Red"]just getting rid of the error message may not be a good idea[/COLOR] since the original problem remains. And since the package that you have mentioned is a critical one, maybe you should spend some time to get rid of the error and not just the message.

---

### Post by vladimiroane on 2007-04-04
Getting rid of the problem is the thing to do.... but how? I am not Linux expert. 

> if you open a system console window and type

sudo tail -f /var/log/syslog

Then try installing something do you get any more detailed errors appearing?

Did that. Nothing more detailed.

---

### Post by thelinuxguy on 2007-04-04
> **vladimiroane said:**
> Getting rid of the problem is the thing to do.... but how? I am not Linux expert. 

Could you post the contents of or attach a screenshot of the terminal panel in the "Changes applied" window?

---

### Post by vladimiroane on 2007-04-04
[Here it is.]("http://www.vladimiroane.com/Screenshot.png")

---

### Post by thelinuxguy on 2007-04-05
Does the file/folder /lib/modules/2.6.20-13-generic/modules.ofmap.temp exist?
If it does, are you able to rename it to /lib/modules/2.6.20-13-generic/modules.ofmap (using sudo)?
```

sudo mv /lib/modules/2.6.20-13-generic/modules.ofmap.temp /lib/modules/2.6.20-13-generic/modules.ofmap

```
If not then are you able to rename it after booting into recovery mode?


And what kernel are you running?
```
uname -r
```

---

### Post by vladimiroane on 2007-04-09
Moving didn't work either way. Kernel is 2.6.20-13-generic.

Other suggestions?

Many thanks for your help so far. I appreciate it a lot.

---

