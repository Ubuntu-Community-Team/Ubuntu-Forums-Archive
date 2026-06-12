---
title: "[SOLVED] Multiple displays on one monitor (4 desktops showing up at once)"
date: 2008-03-08
forum: General Help
---

### Post by EckoAK on 2008-03-08
Hey, I just installed ubuntu on my main machine, and I'm having an issue with my NVidia graphics card. I finally managed to get the damn driver to install, after sort-of figuring out how to not load in X server (what the hell NVidia, what the hell). Now I'm having this issue where I see four desktops on one monitor. The mouse can go across all of them, but all 4 display the same thing. Basically I'm getting an image that is 4 inches wide and 10 inches tall repeating across my screen four times horizontally. It distorts the text so much that I can't read anything. I think I'm going to have to edit this in command line, but I can't find any other instances of this, and the NVidia website doesn't offer anything that mentions this. I think it has something to do with a setting being set to "display 4 monitors" or something, and it's just outputting them all into 1.

help?

---

### Post by .nedberg on 2008-03-08
To get your X server to display correctly you can run```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and restart X (ctrl+alt+backspace).

Did you install the Nvidia driver from nvidia.com or with the restricted driver manager?

I would recomend you use the restricted driver manager. You will get an older driver, but one that is tested to work with Ubuntu.

---

### Post by EckoAK on 2008-03-08
Thank you!! It worked!! So simple :) I believe I am using the restricted driver manager. any way to check?

Edit: Nevermind, figured it out. Using RDM driver now

---

