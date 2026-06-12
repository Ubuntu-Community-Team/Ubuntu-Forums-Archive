---
title: "Changing Firefox Flash addon"
date: 2008-05-04
forum: General Help
---

### Post by Handonam on 2008-05-04
Hey there, i just started using ubuntu, so i'm a bit new at this. Please bare with me.

The first time i started using flash, i went to check out some youtube videos.  I clicked on the addon space that appears when you first encounter a flash player embedded on a page.  A popup box came up with 3 items (which i don't remember), so i instinctively clicked on the first thing i saw.  Now, everytime i go on youtube, i see a big grey ring with a play button in the middle.  I don't want that to appear when i start seeing flash embedded objects.  This applies to flash banners and flash oriented websites as well.


Any idea how to change it to the other flash handler, or at least something to bypass the ring?  



also a side note, anything speed tips to make youtube videos run smoother on compiz-fusion?

---

### Post by Handonam on 2008-05-06
can someone please help me?  I need to get another flash plugin instead of this one i'm using (which i have no idea what it is)

---

### Post by Handonam on 2008-05-06
Anyone???

---

### Post by stalemateman on 2008-05-06
Go to this thread "http://ubuntuforums.org/showthread.php?t=766683" and read through it. Part 2/5 is especially important, and it should help you fix your problem.

---

### Post by Handonam on 2008-05-06
i went through it and it still doesn't work.

i can't even find the plugin.dat. also renamed the flash files in firefox folder by adding .bkp to them

---

### Post by Handonam on 2008-05-06
bump

---

### Post by Handonam on 2008-05-07
i like the lack of support here.

---

### Post by ironclaw on 2008-05-07
The Flash plugin that was installed must be Swfdec from your description of the default paused playback.

You can uninstall swfdec-mozilla on Synaptic or by:
```
sudo apt-get remove swfdec-mozilla
```

Then Firefox should prompt you again to install a plugin when you visit a page with Flash content.

Using the proprietary Adobe Flash plugin should run faster than Swfdec and Gnash, I think.

---

### Post by Handonam on 2008-05-07
> **ironclaw said:**
> The Flash plugin that was installed must be Swfdec from your description of the default paused playback.

You can uninstall swfdec-mozilla on Synaptic or by:
```
sudo apt-get remove swfdec-mozilla
```

Then Firefox should prompt you again to install a plugin when you visit a page with Flash content.

Using the proprietary Adobe Flash plugin should run faster than Swfdec and Gnash, I think.

Awesome! That did the trick

thanks ironclaw!  feels so smooth now

---

