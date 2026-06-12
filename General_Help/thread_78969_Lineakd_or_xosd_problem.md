---
title: "Lineakd or xosd problem"
date: 2005-10-19
forum: General Help
---

### Post by Ysanne on 2005-10-19
Hi, I've just upgraded from Hoary to Breezy, and lineakd is not working anymore. It crashes with a segmentation fault. Running lineakd with "-v", it says the segmentation fault occurs when it's "Initializing Plugin: xosd". 

My LCTElite keyboard used to work with Hoary, I even had a working klineakconfig to configure it, so my config file should be ok. (I tried a newly created empty config file as well, and got the same.) 

I have reinstalled xosd, lineakd and its plugins, didn't help any. 
Any suggestions or ideas how to solve this? 
Anna

---

### Post by ajkeys on 2005-10-26
I started with a fresh install of ubuntu 5.10 and then installed the kubuntu and xubuntu packages. I use XFCE the most and have the same problem. I found out that if you uninstall the xosd plugin lineakd then works fine. Then after downloading the xosd plugin from the lineakd website I extracted it and read the readme and at the bottom it said, that if the font the xosd plugin is suppose to use is not installed xosd would segmentation fault then causing lineakd to segmentation fault. The question I have is how to specify a different font in lineakd.conf (which has to be specified in "x format") or how to install the specific font(-adobe-helvetica-bold-r-normal-*-*-240-*-*-p-*-*-*). Tried to google the x format or how to get that font, but couldn't find anything. Maybe this will help to solve the problem. Also I am using the amd64 edition. Thanks.

---

