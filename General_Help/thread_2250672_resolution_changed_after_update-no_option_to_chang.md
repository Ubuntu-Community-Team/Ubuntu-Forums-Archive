---
title: "resolution changed after update-no option to change it back"
date: 2014-10-30
forum: General Help
---

### Post by Ben_Cook on 2014-10-30
I installed the latest update for xubuntu yesterday.  When I turned on the computer this morning, my resolution was changed to a lower one and the option to change it back is gone. I look under display in the settings menu and it tells me 1024x768.  I am pretty sure there used to be a higher option I was using.  I have it hooked up to my TV via a VGA cable.  

    The only other thing I did yesterday was change my background to a picture of my own (as opposed to a pre-installed desktop).  BUT - that didn't make a difference in my resolution at the time.  It went to the lower resolution AFTER I restarted the computer.  When I installed the update earlier, it said changes would not take effect until after I restarted it, and when I did this morning my resolution was changed.  Any ideas?  I'm running Xubuntu 14.04.

---

### Post by Impavidus on 2014-10-30
You installed a kernel upgrade which broke your graphics driver. You can select "advanced options" in the grub menu and boot an older kernel. This may restore your resolution temporarily. This is exactly why the old kernel isn't uninstalled automatically.

As for a permanent solution, I don't know much about graphics drivers. But it may help if you post the model of your graphics card.

---

### Post by Ben_Cook on 2014-10-30
I am sorry if anyone spent time trying to answer my question.....I think my brain was non-functional before work this morning.  My VGA cord, oddly enough, was not plugged in securely.  Somehow it loosened.  As soon as I tightened it and restarted it I could change the resolution back :lolflag:

---

