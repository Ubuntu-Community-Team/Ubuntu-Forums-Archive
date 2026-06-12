---
title: "changing graphics settings often breaks GUI"
date: 2016-11-28
forum: General Help
---

### Post by caleb87 on 2016-11-28
I've been using Ubuntu forever on my laptop, and decided to wipe Windows 10 for Ubuntu on my desktop. So far, I regret it :( Changing the Display settings can break the GUI. 

I'm running dual 4k monitors with dual GTX 760s with SLI adapter (though I don't think the drivers have SLI enabled). The Nouveau driver Ubuntu chose to use would cause the cursor to disappear and it couldn't run 4k fast. I used Software & Updates > Additional Drivers > NVIDIA 375.20 (latest) to install the NVIDIA driver; I also tried several earlier versions and they all have the same issues. 


I've narrowed down that using any settings under Settings > Displays will likely cause the GUI to break. After changing "Scale for menu and title bars" the screen adjusts perfectly without clicking Apply, but once I click "Apply", my screens went black. After 60 seconds, I forced the PC off and returned to the screenshot. In the attached image, clicks don't register where the cursor is; clicks are about 3-5 inches away.

[ATTACH=CONFIG]272438[/ATTACH]


If I alter NVIDIA settings, this hasn't happened yet... though sometimes one screen will go blank. 


I'd like to know if this is probably an NVIDIA issue or a Ubuntu issue, and if there are known ways to fix this.

---

