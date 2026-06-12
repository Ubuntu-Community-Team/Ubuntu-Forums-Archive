---
title: "Dell Inspiron 15 7567 - Ubuntu and external monitor"
date: 2019-09-19
forum: General Help
---

### Post by xdeuiii on 2019-09-19
[COLOR=#1A1A1B][FONT=&quot]A few days ago I tried installing Ubuntu 18.04 on my Dell Inspiron 15 7567. Had to do a lot of hoops to even get it installed because of the way Ubuntu switches graphics in 18.04, or at least as far as I can understand as I'm not good at Linux. And Nautilus has this horrible circle thing when copying files instead of a progress bar in 18.04.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Then I found out my laptop is actually certified for Ubuntu 16.04. Fairly enough, it installed almost flawlessly compared to 18.04. It also has the old version of Nautilus which still has the progress bar. If I'm not wrong, I think I switched to proprietary NVIDIA drivers instead nouveau. PRIME switching works fine, just some little extra things had to be done for it to properly turn off the NVIDIA GPU when I'm on power saving (Intel profile).[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Here's my problem. Connecting an external monitor does not work unless I switch to performance mode because the HDMI port is wired to NVIDIA. As a result, I get horrible battery life when connecting an external monitor which makes sense since its on performance mode. Is there a way (or multiple ways for that matter) to get Windows like battery life or close when connecting an external monitor? I did try TLP and PowerTop, but on performance mode, doesn't make any difference.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I thought if it was certified for Ubuntu 16.04, it would be better optimised to use the NVIDIA card only slightly while being on Power Saving mode, but it seems it will only ever the NVIDIA GPU when on performance mode.[/FONT][/COLOR]

---

