---
title: "Gnome wont load"
date: 2013-02-26
forum: General Help
---

### Post by Bradley129 on 2013-02-26
Hello all I've used unity till today well I decided why not try that little foot icon gnome lol well I grew very fond of it with it themes and such I loved it I wppliead a few themes added a few plugins nothing bit edited one thing in compwiz the opacity that's all now when I restarted MY computer the login screen came up as usual and I login everything is working good except GNOME never loads! It just sits there with my wallpaper and the mouse icon but I can press the power button and I can log out I can go into unity and it works fine! So any way to get my gnome back I miss it. Please help I have found no solutions through my searching and reinstalling isn't really a options becoise I have over 100gb of data I've save on ubuntu. Please help. Also if it help I'm on Ubuntu  12.04.2 LTS and gnome 3.4

---

### Post by meteorrock on 2013-02-26
Try to follow this guide here. I replaced unity with gnome 3+ using this guide. I will post it in here for you also. Here is the link.  [http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html](http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html)

Do not forget to update your apt-get in the terminal first while loading and changing your desktop for ubuntu, it will use code updated in the apt-get for your desktop also. Any time you want to change your desktop use this command here, lot of these guides assume linux users know this already.

```
sudo apt-get update
```

This link here shows you how to totally purge gnome 3, you might need to purge that desktop and start over from scratch. These instructions in both of these links are kind of lengthy so make sure to check over these links. Use number 6 answer in there for a complete purge. Make sure you run the sudo apt-get update after purging.   =) [http://askubuntu.com/questions/65200/remove-gnome-shell-completely-after-installing-it](http://askubuntu.com/questions/65200/remove-gnome-shell-completely-after-installing-it)

After purging your defective gnome 3+ desktop for ubuntu, follow those instructions in the first link, update your apt-get and start over and see if that gets you on track. Follow each line of code in your terminal carefully without missing any steps in that first link. Just drag and drop that code in your terminal is what I do. :)

~~~~~~~~~~~~~~~~~~````````

Reinstalling your desktop will not damage your data, I updated mine with over 1 TB of music files and purged it before reinstall. Just do not use SU in your terminal.

---

### Post by Bradley129 on 2013-02-26
Ah you seem to know your stuff hey would this method work instead? [http://ubuntuforums.org/showthread.php?t=1429582](http://ubuntuforums.org/showthread.php?t=1429582) its a lot easier and all I want to do is just reinstall gnome 3.4 to get it back in working order thanks in advance

---

### Post by Bradley129 on 2013-02-26
OK well after many attempts I booted back into gone to see what was causing the problem it turned out to be my theme I switched back to the android  4.0 ICS theme and there we go good as new I suggest that everyone does not download the zucini theme if there on 3.4

---

