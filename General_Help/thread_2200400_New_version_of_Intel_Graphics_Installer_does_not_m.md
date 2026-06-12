---
title: "New version of Intel Graphics Installer does not make flash work on web browsers"
date: 2014-01-19
forum: General Help
---

### Post by pavelexpertov on 2014-01-19
Hello, I have upgraded my lubuntu to 13.10, because there is a new version of linux Intel graphics installer and I hoped it would solve the problem with flash. However, it dod not solve. I have a Dell Optiplex gx 270 with Pentium 4 processor and I think I have intergrated gpu, but I am not sure. Does anyone have a solutioin to this problem? Thanks

---

### Post by ajgreeny on 2014-01-19
What exactly is your problem with flash?  Does it not work at all?  Does it only just about work successfully, but not in fullscreen?

More info please, and also give us details of your hardware; exactly what cpu, as a P4 could be a lot of different speeds; how much ram, what graphic card or chip?

If you're not sure about some of the hardware use command ```
sudo lshw -html > hw.html
``` and then open the **hw.html** file it makes in your web-browser, firefox or chromium.

---

### Post by pavelexpertov on 2014-01-19
Hello thank  you for reply. Flash content do work, because they play animation and sound, but the images are distorted that the content is not usable and watchable. For example, when I go to watch a video on youtube, image of the video and its controls are distorted and I can not click on any buttons including play or volume controls. However, the video is playing and sound is coming out on external speakers. Furthermore, when I go to a maths revision website, which is based wholly on flash, flash content is distorted and I can not see anything properly. That happens on both webbrowsers: firefox and chromium. Also I installed adobe flash plugins by installing ubuntu-restricted-extras packages and they used to work before I upgraded to 13.10.

My hardware spec:
Computer: dell optiplex gx270
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz, 32 bit. (one core)
RAM: 1GB.
Graphic chip: 82865G Integrated Graphics Controller (description: VGA compatible controller)

After I ran commandsudo lshw -html > hw.html, 
I looked through the list to give information on what above. When I read through list I found one part of information 
that describes System peripheral called 82865G/PE/P Processor to I/O Memory Interface. This info stood out by having 
a different background and red text font colour. Here is a full information list about this:

 
[TABLE="class: node-unclaimed, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]generic
[/TD]
[/TR]
                [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]System peripheral[/TD]
[/TR]
              [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]82865G/PE/P Processor to I/O Memory Interface[/TD]
[/TR]
              [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Intel Corporation[/TD]
[/TR]
              [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]6
[/TD]
[/TR]
              [TR]
[TD="class: first"]bus info: [/TD]
[TD="class: second"]pci@0000:00:06.0
[/TD]
[/TR]
              [TR]
[TD="class: first"]version: [/TD]
[TD="class: second"]02[/TD]
[/TR]
              [TR]
[TD="class: first"]width: [/TD]
[TD="class: second"]32 bits[/TD]
[/TR]
              [TR]
[TD="class: first"]clock: [/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
              [TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
              [TR]
[TD="class: first"]resources:
[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] memory
[/TD]
[TD]:[/TD]
[TD]fecf0000-fecf0fff
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 
I assumed that the drivers for intel's intgrated graphics chip was the problem, because the installer managed to solve the problem in 13.04. if you would like to get more info of my computer, just ask. THanks

---

