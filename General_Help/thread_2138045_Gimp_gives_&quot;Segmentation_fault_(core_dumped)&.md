---
title: "Gimp gives &quot;Segmentation fault (core dumped)&quot; on Hybrid graphics"
date: 2013-04-22
forum: General Help
---

### Post by lachoneus on 2013-04-22
First, thanks for advance for any help.  It is much apprieciated.

Specs:
HP Envy 15-3033cl
Core i7-2670QM 2.20GHz
[COLOR=#000000][FONT=HPSimplified]Radeon HD 7690M switchable graphics with 1024MB GDDR5
Kubuntu 12.10
Kernel Linux 3.5.0-27-generic

This problem is easy to reproduce for my system.

Fresh Kubuntu install
Manually install Catalyst 13.1 driver (every version of catalyst, I have experienced the same bug.)
Install Gimp from this PPA "[/FONT][/COLOR]ppa: otto-kesselgulasch/gimp"
run gimp from either the console or menu

Here's the kicker, my system has hybrid graphics.  The ATI radeon chipset, listed above, and an intel chipset. When I have my system switched to the Radeon card, gimp works great, but when I switch over to the intel, I get this error when I try running Gimp through Konsole "Segmentation fault (core dumped)".  Nothing else prints in the console and the program does not start. 

I assume that this has something to do with graphics, opengl, or something.  I have no idea where to start debugging though.

 I know I could stick with the radeon card, and I have for over a year now, but I would really like to get some extra time out of my battery by running the intel chipset.

Also, Gimp seems to be the only program that I use that experiences this problem.

---

