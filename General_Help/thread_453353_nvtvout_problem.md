---
title: "nvtvout problem"
date: 2007-05-24
forum: General Help
---

### Post by Russty of Oz on 2007-05-24
I posted this on the multimedia and video section but have had no replies, so either the right people are not reading it or no one has any idea what I am talking about.:(  So this is what I had in the other section:

"I have a NVidia Geforce 6200 turbocache video card in my computer but when I try to use nvtv out, it says "No supported video card found" Under NVidia X server settings it shows the video card with driver 1.0-9755"
 
I have a DVB-T card installed and it is working well with Kaffeine, but it is just that nvtvout will not work at all.  So what could be going wrong?
 
 Russty.

---

### Post by Russty of Oz on 2007-05-26
Well, it seems no one knows anything about it. :(  

Could it be that I have to install something else as well?  

I am getting tired of having to switch back to windows just to recorded something every time.  There is not much point recording in Ubuntu if I can't get it out to my TV to watch.  This is about the only thing now that is keeping me switching between systems.

Russty

---

### Post by puterboy on 2007-06-09
I seem to have a solution. I'm using a 6600gt on ubuntu 6.06 amd64

First off, i didn't use nvtv. i used envy, which configured all my settings for me. maybe it's cheating, but whatever.....after it installed the packages and stuff i needed, nvtv STILL wouldn't work, despite finally seeing the NVIDIA splash screen. so I went into 

Applications>System Tools>NVIDIA X Server Settings

I went to the X Server Display Configuration, clicked on my TV (which it had never detected before), and configured it (I put my screen to the right of screen 0, my PC monitor. I couldn't apply settings, so I saved it and restarted. It didn't work after restarting my X Server (Ctrl+Alt+Shift+Backspace). I found that the file didn't have the correct permissions, so i used

sudo chmod a+rwx /etc/X11/xorg.conf

to let me write it. I couldn't seem to keep any settings by overwriting the file, so I had to save the xorg.conf from the settings panel on my desktop, open both, and paste over the contents of the old file with the new one. worked like a charm. i'm so newbish, but it works now. any questions, feel free to PM me, i'll try to help as much as I can.

Also, after every reboot of the X server, you need to reconfigure your TV setting in the panel, because if it didn't work, it'll overwrite the settings to where your TV is disabled.

Hope it works!!!

---

