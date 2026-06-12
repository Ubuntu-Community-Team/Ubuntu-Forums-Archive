---
title: "Display and sound problems with a new laptop and upgraded OS"
date: 2018-04-04
forum: General Help
---

### Post by lesliek2 on 2018-04-04
I switched to a newer laptop, an Asus X555UA, and also switched from Ubuntu version 14.04 to 16.04. I now have two problems.

1. I use an external monitor and would like the laptop's display to be off when I do. Each time I boot up attached to the external monitor, I have to go to Display under System Settings and change the configuration in order to turn off the laptop's display. Is there a way to make this change permanent?

2. If I plug in headphones, they're not recognised and sound continues to come through the laptop's internal speakers. In order to solve that problem, I created a launcher that opens pavucontrol at the output devices tab. I click on the launcher icon, then switch the port manually from speakers to "headphones (unplugged)", after which the headphones work and the internal speakers don't. I'd like to leave the headphones plugged in all the time and have the default to be that sound comes through them, but making the change using pavucontrol doesn't survive a reboot. Is there a way to make this change permanent?

Thank you for any assistance that you're able to give.

Leslie

---

### Post by dino99 on 2018-04-04
First run 'journalctl -b' to know about possible warnings/errors mainly about chipset/driver not found/recognized ...
Then you can also tell us about the DE used (gnome/kde/...)

---

### Post by lesliek2 on 2018-04-04
Thanks for taking the trouble to reply dino99.

Re DE used: when I run "gnome-shell --version", I get "GNOME Shell 3.18.5". (I hope that's what you were asking for.)

Re journalctl -b: I wasn't quite sure how to go through all the output of that command, so I ran instead "journalctl | grep error" and "journalctl | grep warning" and looked at the results of those. I found no errors or warnings that said anything about chipset/driver not found/recognised.

Thanks again,

Leslie

---

### Post by lesliek2 on 2018-04-09
Just in case this might help someone else, I report that I was able solve problem 2 by following the instructions here: [https://unix.stackexchange.com/questions/175930/change-default-port-for-pulseaudio-line-out-not-headphones](https://unix.stackexchange.com/questions/175930/change-default-port-for-pulseaudio-line-out-not-headphones).

As to problem 1, I wasn't able to solve it completely, but I created a custom application launcher with an icon for it on my top panel. When I click on it, it runs the command: xrandr --output <my laptop's screen, which is eDP1> --off. Although not automatic, that's a much easier way to turn off the laptop's screen when the external monitor is connected than I was using before.

Leslie

---

