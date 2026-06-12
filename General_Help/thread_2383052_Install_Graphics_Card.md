---
title: "Install Graphics Card"
date: 2018-01-20
forum: General Help
---

### Post by neutronforrest on 2018-01-20
Dear Forum,

I have a headless unit running a recent version of Ubuntu (16.04) that is my primary server.  I am using X11 to start a xserver so I can remote into the unit.  I have a few questions.  I am unable to recall how the X11 session starts.  It must do it automatically when the system reboots.  I don't see any information in the files in /etc/X11 where it performs this activity.  My second question is my motherboard has a cpu (and I assume a gpu) built together.  When I went to install the graphics card and remote into the headless unit the screen was frozen.  I am assuming the newly installed graphics card is interfering with either the X11 session or the builtin gpu (or both).  My goal is to just install the gpu and not use the graphics portion of the card.  Any help would be greatly appreciated.

Regards,
CJ

---

### Post by gordintoronto on 2018-01-21
Many computers have no built-in GPU. What graphics card did you try to install?

Run these two commands:
cd Desktop
sudo lshw -html > config.htm

Copy config.htm to a flash drive and carry it to a computer where you can see the details.

---

