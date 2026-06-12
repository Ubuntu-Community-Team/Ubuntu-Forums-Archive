---
title: "How do you know which additional driver to install?"
date: 2015-05-27
forum: General Help
---

### Post by cwblanch on 2015-05-27
Hey,

I've finally gotten Ubuntu 14.04 installed on my Win 8 laptop. 

I'm now doing all the updates and everything, I've gotten to the additional drivers and I have multiple options, I have no idea which to install or anything.

I'll include a screenshot so I don't have to describe it all.

It says I'm using the recommended driver, but would there be a reason, like graphics performance, for changing it?

Thanks!

---

### Post by nerdtron on 2015-05-27
where's is you screenshot?  And what model of your graphics card?
 
I think the recommended driver is the default included on the kernel, and I think it's the open source version. One reason to install the proprietary drivers is to increase graphics performance (say for gaming). But if you're happy with the performance of the current display drivers, it's not a requirement to install the proprietary ones. Some users reported screen tearing when installing the proprietary drivers.

---

### Post by kryten35 on 2015-05-27
If you have an nVidia card, its the one right at the top      binary driver (proprietary tested)

---

### Post by cwblanch on 2015-05-27
Sorry about that, I'm not sure why the screenshot didn't add[ATTACH=CONFIG]262252[/ATTACH]
And it's an AMD.

---

### Post by grahammechanical on 2015-05-27
When we install we are asked if we want to install third party software at the same time. If we tick that box we will get a proprietary video driver. It is usually the safest driver. Additional Drivers will offer us a selection of 5 drivers. Sometimes we change video drivers and do not notice any difference in performance. That is the way of things.

Generally we accept that a proprietary video driver is better than the open source video driver because it comes from the manufacturer of the video adapter who has better knowledge of his hardware than do the open source video driver developers. We usually get a choice between a newer and an older proprietary driver and 2 sub choices - tested and updates. I think that "tested" does not get updates. Whereas, "updates" will be updated from time to time. "Tested" carries less risk. Experiment. See what works better. You might not notice any difference. I don't.

Some of us are also offered the option of installing a processor microcode driver from the manufacturer of the CPU. This driver runs during the loading of the OS and it is a method of changing the way the CPU works without needing to flash the BIOS. It is a safer option. Additional Drivers offers me this option. I have installed the intel-microcode driver and to tell you the truth it must be doing something but I cannot tell the difference. 

Regards.

---

