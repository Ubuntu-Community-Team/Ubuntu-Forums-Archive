---
title: "Incorrect Nvidia Driver = Resolution Disconfigured"
date: 2014-06-08
forum: General Help
---

### Post by Bubblegut on 2014-06-08
I was having problems with my graphics drivers so I went to Nvidia and downloaded a driver that matched my AMD Catalyst driver specifications. I used tty1 to do this and everything seemed fine but it told me that I was installing the incorrect driver for my system (even though I made sure to download the correct one). So, I decided to to continue the install and it gave me another error before installation that the pre install script had failed. At this point I was ready to see what happened so I allowed the install to complete. Restarting my system, my resolution is zoomed in and after logging in I get this:
[ATTACH=CONFIG]253836[/ATTACH]
Would uninstalling the driver fix the issue at hand?
My system is Ubuntu 12.04 LTS and my graphics driver *was (something like) *AMD Radeon RV710 [Radeon HD 4550]
please help...

---

### Post by Bubblegut on 2014-06-08
UPDATE

I uninstalled Nvidia and now I am missing parts of my GUI. I have no dash sidebar nor can I close/minimize windows. I've tried resetting Unity but it is not an issue with that...

---

### Post by deadflowr on 2014-06-08
[s]Uninstalling the driver? Sure.[/s]

But the real question is why go to nvidia to get an amd driver?
If the card is amd, then you need amd drivers, nvidia drivers won't do anything.

Aside from that, though, AMD has stopped support for your card, so no driver you try to download will work with the current versions of Xserver used by Ubuntu.
You'll have to rely on the open-source radeon driver.

---

### Post by Bubblegut on 2014-06-09
Okay, I managed to find a solution to my question in this thread [here]("http://askubuntu.com/questions/215016/unity-doesnt-appear-after-installing-nvidia-drivers")
As for why I am trying to install Nvidia, it was a solution to my first thread [Steam: glxChooseVisual Failed]("http://ubuntuforums.org/showthread.php?t=2228135")
It seemed sound, and if I were to have (potentially) installed the correct driver Steam may have worked. When I tried to run Steam with the Nvidia driver, it gave me an error like "GLX is not using direct rendering" which led me to believe that If the rendering/resolution had been stable it would have ran, and resolved my initial issue.

---

### Post by Bubblegut on 2014-06-09
Issue Resolved.
TL;DR Uninstalled Nvidia, Installed correct AMD driver.

---

