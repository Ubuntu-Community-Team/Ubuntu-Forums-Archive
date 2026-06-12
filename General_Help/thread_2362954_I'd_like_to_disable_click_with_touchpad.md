---
title: "I'd like to disable click with touchpad"
date: 2017-06-04
forum: General Help
---

### Post by josefranw on 2017-06-04
Hello, dear friends. I'm a new user to Lubuntu (I had used Ubuntu and Ubuntu Mate before) and there's a configuration I always do when I install a new system and it is to disable the clicking option of the touch pad. I want to click with the physical buttons not the pad. How can I disable it? Thanks.

---

### Post by Hadaka on 2017-06-04
Hi have you tried, from the command line...ctrl/alt/t..

                                           [TABLE]
[TR]
[TD="class: votecell"]

[/TD]
[TD="class: answercell"]      You can use gsettings: 
 

  ```
gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click true
```  
  Which enables tap to click. 
  ```
gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click false
```
  Will disable it.  This is the same as changing it in System Settings.
     
[/TD]
[/TR]
[/TABLE]
#Ref.. [https://askubuntu.com/questions/403113/how-do-you-enable-tap-to-click-via-command-line-with-xmodmap](https://askubuntu.com/questions/403113/how-do-you-enable-tap-to-click-via-command-line-with-xmodmap)
#Ans 4..

---

### Post by josefranw on 2017-06-04
I just did and it does not work.

---

### Post by Hadaka on 2017-06-04
Hi, not having Lubuntu I cannot verify if this will help or not.
"the link is for double click,but it still may lead you to an answer"
see if you have the .gtkrc file with..
```
ls -al .gtkrc*
```
if you do have the file, cat it and see if there is an entry for "touchpad"
and change the value there.
#Ref..  [https://ubuntuforums.org/showthread.php?t=1920761&highlight=double+click](https://ubuntuforums.org/showthread.php?t=1920761&highlight=double+click)
Good Luck.

---

### Post by josefranw on 2017-06-04
Something I did must have worked because, after a reboot of the system, I discovered the feature had been disabled. Unfortunately, it also disable scrolling and now I can-t scroll up or down the pages using the pad... I guess we can't have everything in life?  But it all used to work perfectly in other Ubuntu flavors, why not here?

---

### Post by josefranw on 2017-06-04
I finally found a solution: by installing touchpad-indicator I was able to deactivate the tap-to-click option while keeping the scrolling and other features active.

---

### Post by Hadaka on 2017-06-04
Glad you found a solution !
Please take the time to mark your thread solved.
From your thread, click Thread Tools, then Solved.
This will help others when searching.
Thanks.

---

