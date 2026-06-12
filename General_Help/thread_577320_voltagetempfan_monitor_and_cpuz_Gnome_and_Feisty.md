---
title: "voltage/temp/fan monitor and cpuz Gnome and Feisty"
date: 2007-10-16
forum: General Help
---

### Post by Hopworks on 2007-10-16
I was absolutely SHOCKED that motherboard monitor doesn't have a linux version. I did find a thread about another application **lm-sensors** at [http://ubuntuforums.org/showthread.php?t=2780]("http://ubuntuforums.org/showthread.php?t=2780").  Any thoughts on that software?

And the same shock for cpuz. No linux version, and I don't really want to run a virtual machine just to use it. Is there a good alternative?

Thanks!

Hop

---

### Post by JBAlaska on 2007-10-16
Don't be shocked...just grab GKrellM, lm-sensors and hdmon and don't look back lol

---

### Post by Hopworks on 2007-10-16
> **JBAlaska said:**
> Don't be shocked...just grab GKrellM, lm-sensors and hdmon and don't look back lolTHANKS!
A couple more questions...
I did a search for lm-sensors in add/remove applications, and turned up X Sensors, that reads data from THE lm-sensors. Is that all I need? And hdmon showed no hits at all.

As a new guy on the Linux scene, I'm fairly comfortable with apt-get install on an app, but not quite sure how to do an app that isn't found.

Thanks for any MORE help you can give me, and thanks for the quick response.

Hop

---

### Post by JBAlaska on 2007-10-16
Search synaptic package manager for "gkrellm", "hddtemp" and "lm-sensors"
Install gkrellm and any plugins you want, hddtemp and lm-sensors, then check this post to configure lm-sensors to work with your hardware;
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Or basically just do ```
sudo sensors-detect 
``` in a shell and follow the prompts.

Here's all the skins for GKrellM ```
http://www.muhri.net/gkrellm/
```

---

### Post by Hopworks on 2007-10-16
Thanks again for the response. I have been working that lm-sensor config thread while waiting for your reply, but hit a snag, telling me no sensors found when I enter 'sensors'. I'm sure I missed something. I'm really tired, and gonna hit the sack for a few hours. I'll go after it again over morning coffee. Aren't vacations grand? :cool:

I can't wait to get this right once and for all. Just takes me a few steps towards the land of Linux, and away from the Windows Metropolis. WOOT!

---

