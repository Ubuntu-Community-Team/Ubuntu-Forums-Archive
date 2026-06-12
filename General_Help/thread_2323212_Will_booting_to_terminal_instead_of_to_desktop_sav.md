---
title: "Will booting to terminal instead of to desktop save CPU usage?"
date: 2016-05-03
forum: General Help
---

### Post by Justin_Schwaitzber on 2016-05-03
Hello there!

I have an AWS EC2 instance running a Ubuntu AMI. It did not come with a GUI Desktop interface installed, so I installed one. I was monitoring the CPU usage and noticed that it was particularly high. I decided to have it automatically boot to the terminal, and then if I need a desktop I would type startx. **Note: I do indeed want a GUI that I can access sometimes.**

Does this make sense? Will this help with my CPU usage? Is there a better solution to my problem?



Thank you for your help,

Justin

---

### Post by DuckHook on 2016-05-03
GUIs use lots of resources (and increase attack surface) which is why they are not used in Linux-based servers. Depending on the resources of the base machine, a GUI could use lots of CPU, especially in things like AWS or any cloud setting where the graphics may have to be rendered in software.

You can decrease CPU intensity by installing the lightest DEs.  Stay away from Ubuntu/Kubuntu. Stick with any of L/X/ubuntu/-Mate.

---

