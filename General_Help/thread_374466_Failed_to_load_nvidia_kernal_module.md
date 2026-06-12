---
title: "Failed to load nvidia kernal module"
date: 2007-03-02
forum: General Help
---

### Post by Yellowbelly on 2007-03-02
[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=nvidia+kernal+module](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=nvidia+kernal+module)

That link is the latest nvidia driver install that I've been using. I followed the instructions step by step and I think it causes some problems. I first installed this driver on my first ubuntu install and everything went great until I tried to install Beryl. Beryl worked great until I restarted and I got a blue/white error screen that says it failed to load the nvidia kernal gui thing. I thought fair enough, beryl is to blame since it's buggy. Some guy was having the same problem I was so he uninstalled beryl from recovery but it didn't fix it. I thought that strange but I figured you would have to set the window manager back to Metacity but I didn't know how to do that, so I reformatted my ubuntu partition and started all over with a fresh new install. 

I installed these drivers again and it worked well (although this time i didn't get the nvidia splash screen at start up but everything else in the xorg.conf file check out fine and the new menu for nvidia drivers was up and running and functional. I was even able to restart a few times and it worked but once I turned on my computer and tried to run ubuntu, BAM! The same exact blue/white error message came up because it failed to load the nividia kernal. This time Beryl had nothing to do with it since I didn't think about touching it. The only thing that I thought could be the problem was when I changed the input numbers on the mouse so I can have more buttons to use while browsing and stuff. I guess this could change the xorg file enough to where it can't read "nvidia"? I dunno. I'm going to try to change it back to "4 5" under mouse buttons and if that doesn't work, change drivers from "nvidia" to "nv". I'll be back with a report.

---

### Post by brazzmonkey on 2007-03-02
i don't know if this is related in any way, but check this : [http://www.ubuntuforums.org/showthread.php?t=374061&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=374061&highlight=nvidia)

---

### Post by Yellowbelly on 2007-03-02
K, I changed the numbers under input devices and sure enough it didn't do anything. Changed the recognized driver to "nv" from nvidia so there's a problem with drivers somewhere.

Yeah that thread does help but I don't know what envy is and how to run it. If I decided to run beryl again, would it mess this up?

---

### Post by brazzmonkey on 2007-03-02
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
use at your own risk ! (worked for me, and needed since kernel-2.6.17-11-generic).

---

### Post by Yellowbelly on 2007-03-02
Thanks. It worked great. Would it still work if I decided to give Beryl another try or would I have to play around with this again?

Is it even a good idea to touch beryl/compiz?

---

### Post by brazzmonkey on 2007-03-03
there's nothing wrong to give it a try... i have beryl-svn installed from 3v1no's repos, but i still find it not ready fot day-to-day use... you don't risk much in trying beryl imho...

---

