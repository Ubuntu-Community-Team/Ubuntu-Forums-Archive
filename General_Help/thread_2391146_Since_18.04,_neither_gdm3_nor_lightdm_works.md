---
title: "Since 18.04, neither gdm3 nor lightdm works"
date: 2018-05-06
forum: General Help
---

### Post by gen2fdp8 on 2018-05-06
Hello 

After the update to 18.04, gdm3 was stuck on "started gnome display manager" so after looking on internet I tried a lot of things : repair packages with recovery mode, same, and then reinstall gdm3 with a console  (Ctrl+alt+F2). After that the login screen appeared but I had to enter 2 times my password to.. have then a black screen. And now after some reboot, each time I enter the password, that ignores it and go back to the login screen again : [[IMG]https://image.noelshack.com/minis/2018/18/7/1525607498-img-0658.png[/IMG]]("http://image.noelshack.com/fichiers/2018/18/7/1525607498-img-0658.jpg")

I tried to install lightdm and to start it directly (sudo lightdm) or to "boot" with :  (sudo dkgp-reconfigure lightdm and then reboot) but all I obtain from lightdm is.. a black screen with a white promt: [[IMG]https://image.noelshack.com/minis/2018/18/7/1525607504-img-0664.png[/IMG]]("http://image.noelshack.com/fichiers/2018/18/7/1525607504-img-0664.jpg")

When I try to do startx from a console : [[IMG]https://image.noelshack.com/minis/2018/18/7/1525607503-sanazs-titare.png[/IMG]]("http://image.noelshack.com/fichiers/2018/18/7/1525607503-sanazs-titare.png") + [[IMG]https://image.noelshack.com/minis/2018/18/7/1525607500-img-0657.png[/IMG]]("http://image.noelshack.com/fichiers/2018/18/7/1525607500-img-0657.jpg")


What should I do ?

---

### Post by gen2fdp8 on 2018-05-06
Fixed by installing nvidia drivers (sudo apt-get install nvidia-352) if someone interested..

---

