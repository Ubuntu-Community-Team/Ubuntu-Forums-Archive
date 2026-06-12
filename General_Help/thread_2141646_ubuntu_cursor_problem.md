---
title: "ubuntu cursor problem"
date: 2013-05-03
forum: General Help
---

### Post by oh6fse on 2013-05-03
My mousepointter changing it's size when i move it to desktop it size is 3-2 times bigger than normal but when i move it to   some programs it rezises to 24. i have tried dconf-editor but nothing happens even i reboot  

```
sudo update-alternatives --config x-cursor-theme
```
 just changes theme but not size

    ```
gsettings reset org.gnome.desktop.interface cursor-size
```
Don't do anything
 
This is what it says:


    ```
gsettings get org.gnome.desktop.interface cursor-size 
    24

```

This is a real problem i have so many grey hairs for this!


how i see it
[IMG]http://i.stack.imgur.com/IE0qA.jpg[/IMG]
how i see it part2
[IMG]http://i.stack.imgur.com/Qczv6.jpg[[/IMG]
screenshot
[IMG]http://i.stack.imgur.com/O2V8t.jpg[/IMG]
Ubuntu 12.04
2 monitors

ps.its ask ubuntu site because i didnt have reputation to post pics

---

### Post by oh6fse on 2013-05-07
bump

---

### Post by Impavidus on 2013-05-07
Which version do you use? The cursor size problem has been around for years and, although it's a serious accessability problem, nobody ever fixed it. I heard it should be fixed on 12.10 (I haven't tried, I use 12.04) and there are work-arounds for 12.04, but those are not ideal if multiple people use the same computer.

---

### Post by oh6fse on 2013-05-10
I'm using 12.04 64bit i tried 12.10 but cursor problem still exist

---

### Post by oh6fse on 2013-05-14
I sloved this problem installing kdm, kde and removing lightdm 
so i started using kde

---

### Post by Locus Kiesselbachi on 2013-05-15
Hello!

I am also looking a way to make cursor bigger.
I wonder is there some file you change number and cursor gets bigger? I dont care if cursor becomes pixelated.
Some advice is given [here]("http://askubuntu.com/questions/70942/how-can-i-change-mouse-cursor-size?rq=1") - it is not helping me.

Lubuntu 12.10 - cant find nowhere to change cursor size.

---

