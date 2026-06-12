---
title: "Ubuntu Studio 16.04 LTS Choppy Mouse and Laggy Keyboard Response"
date: 2018-01-29
forum: General Help
---

### Post by matthanley on 2018-01-29
**Short Version**
About a week ago, my computer started responding very slowly to input of any kind. The cursor movement is choppy and delayed, and if I type at a normal speed, a lot of characters are missed. This happens even at the login screen after a reboot, so it doesn't appear to matter whether applications are running or not. I'm pretty convinced that it's related to a recent software update, possibly to Xorg.

[Obligatory link to relevant xkcd comic]("http://xkcd.com/963")
[IMG]https://imgs.xkcd.com/comics/x11.png[/IMG]

I run Ubuntu Studio 16.04 LTS. I don't have any other OSes installed. My computer hardware is about 7 years old. My processor is an AMD Athlon II X4 635 2.9GHz, I have 4GB of RAM.

**Director's cut**
Some time last week, my wife was browsing the internet with Chrome (not Chromium) and the computer semi-froze. The mouse would move in the choppy manner described above, but the web page wouldn't scroll and no input was accepted. At the time, I was also logged in (but not active), and I may have had FreeCAD open at the time. I had to use the reset button to restart the computer. It was after this that the laggy input started. When booting the installed OS, this problem is present 100% of the time, but when booting from the installation/live DVD, the problem doesn't exist.

Based on the age of the computer, I assumed I either had a failing hard drive or a problem with memory. I noted in system monitor that my swap utilization was always 0%, so I started looking there. (I learned a few things about crypttab in the process). However, fsck and badblocks found no problems with any of my partitions, including swap, and 18 hours of memory testing found no issues with the memory.

Ultimately, I figured the easiest thing to do would be a fresh install, so I did that. Backed up /home, re-installed everything, including reformatting all partitions (except /home). At first, the fresh install worked fine. The only packages I added aside from the default install were google-chrome-stable and freecad-daily. Both seemed to be working fine.

Next, I installed updates from Software Center, and on the first boot up after this, the problem was back. This is why I think it's related to an update. I tried removing freecad-daily and google-chrome-stable, but it made no difference. I opened a terminal window and ran top, and when I started moving the mouse, Xorg jumped to the top of the list. When I stopped moving the mouse, it fell way back down. Everything else seemed pretty normal. My processor and memory utilization are both fairly low. My swap usage still reports as 0%, I assume that's related to cryptswap.

I'm out of ideas now. Anyone seen this, or know what update this might be related to?

---

### Post by cruzer001 on 2018-01-29
May be the kernel.

At boot (grub) go to advance options and run the previous (original) kernel.

---

### Post by matthanley on 2018-01-31
Thanks, cruzer, that seems to have been it.

When booting kernel v4.13.0-32-lowlatency, it seems to be related to some process that's running in the background or the load on resources (RAM, I guess?) because if either freecad-daily or freecad-stable was installed, the problem is there *even if FreeCAD isn't running or hasn't been started*. When FreeCAD isn't installed (i.e. apt-get remove, apt-get purge, apt autoremove, reboot, do the hokey pokey), the problem comes up if I have, say, three browser tabs open or anything going on that uses any decent amount of resources. For any given boot, once the problem comes up, it stays there, even if I close everything.

But on your advice, I booted v4.8.0-36-lowlatency, and the issue hasn't come back. I'll keep an eye on it for a few days to see if it comes up again, but it looks like there's some interaction between the 4.13 kernel and some library that's needed by FreeCAD.

---

