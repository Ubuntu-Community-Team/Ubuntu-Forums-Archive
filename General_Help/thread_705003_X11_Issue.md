---
title: "X11 Issue?"
date: 2008-02-22
forum: General Help
---

### Post by Cynic4l on 2008-02-22
I have been recently running Ubuntu 7.10 without any issue until today when I changed a few appearance settings along with some updates that I installed without reviewing them. For some reason my desktop looks like this:

[http://img521.imageshack.us/img521/3267/dscn1055fw8.jpg](http://img521.imageshack.us/img521/3267/dscn1055fw8.jpg)

Anyone have any ideas how to revert this back to normal? I have faced this issue several times before, and the only way I fixed it myself was by reformatting and reinstalling linux (which I want to completely avoid this time). Any help is appreciated.

---

### Post by dieselpower on 2008-02-22
You have the resolution set too high. Get the specs for your monitor from the internet and the "ctrl+alt+F2" to get to a usable term, then run "sudo dpkg-reconfigure xserver-xorg". let it autodetect all but keyboard and mouse, and at the end choose advanced and put in the correct values for you hardware. After that's done, run "sudo /etc/init.d/kdm restart"

---

### Post by soldats on 2008-02-22
well instead id suggest doing "sudo dpkg-reconfigure -phigh xserver-xorg" as this will auto create a "working" xorg file without the possibility of maybe missing a crucial configuration.. then log in and out.

---

