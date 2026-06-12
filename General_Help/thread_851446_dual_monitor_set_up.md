---
title: "dual monitor set up"
date: 2008-07-06
forum: General Help
---

### Post by addernator123 on 2008-07-06
hi i want to put ubuntu on my computer but i need to know how to set up dual monitors on it, i have an nvidia geforce fx 5700 dual headed graphics card.

any help would be greatly appriciated
Adam

---

### Post by stich0602 on 2008-07-06
Dual monitors, I have found, are a pain. But maybe the standard way to configure will work for you.

0. Make sure you are all up to date, run "sudo apt-get -u upgrade" (no quotes).

1. Run "lspci | grep -i nvidia" (no quotes) in the terminal. Post the output here.

2. Go to System->Administration->Hardware Drivers and check the box to enable the restricted drivers for your nVidia card if the option is provided. 

3. Run "sudo apt-get install nvidia-xconfig nvidia-settings" (no quotes)

4. Run "sudo nvidia-settings" (no quotes). Click  "X Server Display Configuration" on the right to set up your monitors the way you wish. Check the "Enable Xinerama" box.

5. Once done, click the "Apply" button. Then click the "Save to X Configuration File" button. When prompted, **make sure you say yes to backup your "xorg.conf" file**. Make note of where the file is backed up to.

---

### Post by pupEOkami on 2008-07-19
wow holi-shi- the commands worked like a charm , after rebooting my system my 2 monitors showed up at the same resolution , only difference is my workspace doubled by 2 , and the environment on monitor 2 acts like a second Xserv,

thanks for the command settings tip . i am will moar than likely recommend this to anyone els with Nvidia cards, *but not sure how it works on SLI and multiple displays* 

props yo. !!

---

