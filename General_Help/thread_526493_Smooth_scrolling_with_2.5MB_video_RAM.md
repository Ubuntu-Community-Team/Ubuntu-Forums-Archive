---
title: "Smooth scrolling with 2.5MB video RAM?"
date: 2007-08-15
forum: General Help
---

### Post by Shardsofmetal on 2007-08-15
I have a ThinkPad 390X with a  NeoMagic MagicMedia 256AV video card with 2.5MB vRAM running Feisty. When scrolling in any application, firefox being the worst, scrolling is painfully slow. It scrolls down like 3 lines, then takes so long to rewrite the entire screen before scrolling down any more. I change my default depth to 16, and that made it a little faster. I was wondering if there is anything I can do to speed up scrolling. I would like to allow my default depth to be 24, but I can deal with 16. I didn't know if there was a way to use system ram in addition to video ram, or if that would even help. Any help would be greatly appreciated. 

Also, recently my mouse arrow started jumping around quite a bit. For example, when i was trying to place it in the text box to type the title to this topic, it kept jumping right over it. That is getting very annoying also. If anyone can help with this issue too, that would also be greatly appreciated. Thank you

---

### Post by dannyboy79 on 2007-08-15
there is a way to specify how much ram the system should share with the gfx card. you can set it through the sudo dpkg-reconfigure xserver-xorg Gconf wizard but other than that I am not sure what or where you would put in the xorg.conf. Back up your current xorg.conf first.
Also, I have an ancient Hitachi 266mhz Pentium MMX with 128mb ram and a 4gb Neomagic GFX card. I use Xubuntu Gutsy and dont have any issues with scrolling like do, I would suggest you try Xubuntu versus ubuntu. Otherwise not sure what else to tell you.

---

