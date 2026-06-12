---
title: "Can't find /etc/gdm/Init/Default file"
date: 2014-06-29
forum: General Help
---

### Post by RobRobinson on 2014-06-29
I am running Ubuntu 14.04 and I want to change the screen dimensions.  Instructions say to edit /etc/gdm/Init/Default using $gksudo gedit.  When I do that, a new, empty file comes up and when I go to save, I get a message that etc/gdm/Init/Default does not exist.  Help!

Thank you

Rob

---

### Post by deadflowr on 2014-06-29
You probably would need to install gdm for that to work 
Ubuntu now uses lightdm as the display manager.
But installing and switching to gdm is simple.
First install gdm
```
sudo apt-get install gdm
```
then to use it over lightdm run
```
sudo dpkg-reconfigure lightdm
```
select OK, and then highlight the gdm option, and I usually use the right arrow key to move to the OK button.
Upon the next reboot gdm will be the display manager.
As well, you should now have those files you didn't have before.

I don't know exactly what you're trying, but best of luck.

---

### Post by RobRobinson on 2014-06-29
Thanks to you, I was able to get in and edit the file.  Sadly, although i followed the directions of the tutorial, what I was trying to accomplish didn't work.

What I am trying to do is change the native screen dimension from 1024x768 to 1720x1080.

Thank you for your quick response.

Rob

---

