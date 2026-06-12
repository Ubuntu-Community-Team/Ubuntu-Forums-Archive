---
title: "Unity/Sidebar question"
date: 2013-09-14
forum: General Help
---

### Post by sebastian-finke-ca on 2013-09-14
Hi,

I have been using Linux now (on-off) for the last 5 years. Started with Ubuntu but when Unity came out it really put me off. What I specifically didn't like was the sidebar thing (not exactly what Unity all entails but that's a different question). Since then I have played around with many, many distros. A lot I liked but none seem to have that all-round 'everything works' factor of Ubuntu. My question: is it possible to deactivate the sidebar? If not, is it customizable i.e. use own links/icons? Not looking for how-to's but rather just interested in whether or not it can be done.

Any and all feedback appreciated. :)

---

### Post by Bashing-om on 2013-09-14
sebastian-finke-ca; Hi !
Though I can appreciate the future that is unity .. I too prefer a simpler desk top. I am pleased with the simplicity and configureability of xfce4.
Many report a pleasing experience with  gnome-shell. To install gnome-shell on 12.04 is as easy as:
```

sudo apt-get install gnome-shell

```
reboot and at the login, click the icon in the upper right of the login box and choose it !

[INDENT][INDENT]different strokes for different folks, it is all in ubuntu
[/INDENT][/INDENT]

---

### Post by stinkeye on 2013-09-14
> **sebastian-finke-ca said:**
> Hi,

I have been using Linux now (on-off) for the last 5 years. Started with Ubuntu but when Unity came out it really put me off. What I specifically didn't like was the sidebar thing (not exactly what Unity all entails but that's a different question). Since then I have played around with many, many distros. A lot I liked but none seem to have that all-round 'everything works' factor of Ubuntu. My question: is it possible to deactivate the sidebar? If not, is it customizable i.e. use own links/icons? Not looking for how-to's but rather just interested in whether or not it can be done.

Any and all feedback appreciated. :)

You can't really deactivate the launcher without loosing the unity panel and dash as well but you can hide it.
You can create your own launchers with custom icons for the launcher/sidebar. They are just .desktop files 
which can be dropped on the launcher/sidebar.
It's also very simple to create your own quicklists in the .desktop file.

---

### Post by CeejRab on 2013-09-14
Hello There, Sebastian-Finke-ca,

All the above comments are true, yet i do have another method which ive used myself. I also have tried many many distros and fell back to ubuntu for its my first love of linux, everything combines in ubuntu to make such a wonderful OS that really contends with windows 7 (my ex OS) and others, 

The panel on the left with the icons is called the unity launcher, i wouldnt reccomend actuallly turning it off because that caused me some issues. I used the following method and it was easily reversible without making and intense changes to my system:

1. Download Docky from the ubuntu software center. Its free, fast, and uninstalls easily if youre dissatisfied with it by using the following command (without quotes) "sudo apt-get unintsall docky"
2. Once docky is set up the way you like it, you can go to system settings and click apprearance. From here you can click behavior and choose to autohide the launcher, also make the sensitivity the lowest possible by sliding the bar all the way to the left. This will make it very very unlikely for the launcher to pop out from the side unless you fiercely shove your mouse toward that side of the screen.

This method worked great for me as docky is easily removed and your unity launcher is still there. I always try to keep the main OS components accesible in case third party or secondary packages fail me. After all, the developers of the OS know more than we do! 

PS: docky makes it feel like a Mac. If you set the menu bar to radiance theme and use a Mac wallpaper and have docky all set up, people will think you have a Mac OS on a PC!

Hope this helps, Happy Ubuntu-ing,

-Christian

---

