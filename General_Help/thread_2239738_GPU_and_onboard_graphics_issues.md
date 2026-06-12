---
title: "GPU and onboard graphics issues"
date: 2014-08-15
forum: General Help
---

### Post by ben-nabity on 2014-08-15
I have my computer set up to dual boot with Windows 7 and Ubuntu 14.04 LTS. My BIOS are set up to enable Multi Display with my onboard intel graphics and my nVidia 8400GS to use all 3 of my screens, with my primary display as Auto (I have changed this to NVIDIA in my troubleshooting attempts). When I boot into Ubuntu I have a few issues. I understand that I am unable to use both graphics cards because of the lack of support, but I want to be able to use the nVidia 8400GS gpu without unplugging my onboard vga. I have changed the bios primary boot to every option available, but no matter what the BIOS is configured to it always boots Ubuntu to my single onboard screen. 

Is there a way for me to keep everything plugged in (my computer is hidden) and be able to boot ubuntu to my NVIDIA card?

Just to clarify my question. Ubuntu runs just fine on my NVIDIA graphics  card as long as my onboard gpu is not plugged in. This means there is  no driver issues that I am aware of. The issue is in which gpu is chosen  as default for my Ubuntu OS. With the nvidia card chosen as primary in  the BIOS the ubuntu boot screen uses it when loading but switches over  to the onboard for log in. Is there a way to make it stay with the  nvidia graphics?

---

### Post by ben-nabity on 2014-08-20
Any ideas?

---

### Post by OneOldFish on 2014-08-25
did you ever solve this ? im having the same problem. i know ubuntu can see my onboard gpu because when i boot up the splash is on the 2 screens that are on the on board gpu then after it boots in i can use the 2 sreens that are on the gtx780. when i go to display it only has the 2 screens that are on the gtx780. i remember when this was as simple as adding text to the xorg.conf but now it rewrites xorg.conf on boot WTF.

---

### Post by ben-nabity on 2014-08-28
I have not been able to solve this problem yet but it sounds like your problem is slightly different than mine. My issue is the OS not using or even allowing me to use my graphics card after I log in. Your issue is with the supporting software for your gpu but this is common because, from what I read, Only one company can be used at a time with Ubuntu because there is no Multi-screen support for them like in Windows. I simply want to use my screens plugged in to my graphics card without having to unplug the screen from my onboard gpu, which it defaults to for some reason and I can find a way to change that.

---

