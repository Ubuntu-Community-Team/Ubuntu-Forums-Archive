---
title: "Running Ubuntu 12.04 Desktop in 'server' mode"
date: 2012-12-13
forum: General Help
---

### Post by chilisastry on 2012-12-13
I'd like to install the full Ubuntu 12.04 Desktop, but frequently I want run the computer in 'server' mode - ie, command line only.  Occasionally, I'd want to run the Desktop.

I'd rather not dual-boot between Desktop and Server editions.

If it is possible, or necessary, I'll install the Desktop and the Server on the same partition (to make sure all the necessary packages are present).

This is an old computer, with limited memory (384MB) so I don't want the Desktop running when I don't need it - which is most of the time.

---

### Post by dino99 on 2012-12-13
you probably know already how to boot the "desktop" without the graphic stuff: simply boot in recovery mode  :p

---

### Post by Cheesemill on 2012-12-13
384MB of RAM isn't enough to run Ubuntu Desktop, try installing [Lubuntu]("http://lubuntu.net/") instead as it has the lowest system requirements of any of the *buntus.

Once you have this installed you can run the following command so that the system always boots to a command line instead of a graphical login screen:
```
echo  "manual" | sudo tee -a /etc/init/lightdm.override
```
When you do need to use the desktop you can use the command:
```
startx
```

---

