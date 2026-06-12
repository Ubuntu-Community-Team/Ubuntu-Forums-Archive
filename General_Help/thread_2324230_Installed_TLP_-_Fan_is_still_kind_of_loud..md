---
title: "Installed TLP - Fan is still kind of loud."
date: 2016-05-12
forum: General Help
---

### Post by Convexus on 2016-05-12
Hey, so I'd like to lower the fan speed on the laptop. TLP definitely improved my battery life, but my fan is still pretty loud. It's like running high performance mode in Windows. How can I set it to the equivalent of balanced or power save mode that's found in Windows?

---

### Post by speartip on 2016-05-12
What graphics card do you have installed?
Often installing the proprietary graphics drivers resolves this kind of problem.

---

### Post by Convexus on 2016-05-12
It's an Intel HD 4000. Can I find this driver in the repo?

---

### Post by speartip on 2016-05-16
> **Convexus said:**
> It's an Intel HD 4000. Can I find this driver in the repo?
Shouldn't be an issue then. I'm running a similar integrated graphics card. My fan speed is exactly the same on Windows 10 as on Ubuntu.
Intel graphics are usually supported out of the box, without the need for additional drivers.
It might be an idea to install the lm-sensors package.
Then run the command "sensors" in a terminal, to see exactly what your fan speeds are.

---

### Post by Linuxisfast on 2016-05-16
I have no heat issue on my ThinkPad X220, battery life and noise is same as Windows 7 it came with. What I would suggest is to check your BIOS for updates and also make sure your fan setting is either quiet or adaptive.

---

