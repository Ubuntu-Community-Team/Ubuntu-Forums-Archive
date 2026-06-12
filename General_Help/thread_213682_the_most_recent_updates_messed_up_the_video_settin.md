---
title: "the most recent updates messed up the video settings."
date: 2006-07-11
forum: General Help
---

### Post by Cyraxzz on 2006-07-11
I am not sure of the name of the update was that may have caused this, there where about 8-9 updates listed on the update manager list, i did not go over the list.

Anyway, when it was finsihed installing the updates it required a reboot which i allowed it to, the first thing that I noticed was that the log-in menu was under it's average speed, and the second thing that i noticed was all the lag when i viewed video files in full-screen, the general computer speed was just far under it's normal speed. I thought it was most likely the video settings that was causing this effect, so i went over the "xorg.conf" file, and no driver was on default, originally "fgrlx" was put on default. 

Later i did this command:

```
sudo dpgk-reconfigure xserver-xorg
```

to set the "fglrx" driver to the default driver, and this had no effect. The next thing that came to mind was executing this command: 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

it updates the xorg.conf file for recent alterations, it's recommended for updating the Xserver. Video files now function ordinarily but not the desktop/windows itself and video games

Games now display error messages in the terminal saying that i am using the "vesa software".

---

### Post by Somenoob on 2006-07-11
I experienced the same thing with this morning's updates, but the updates i recived also effected other fields of the computer.

However, you could probably solve this problem by editing the xorg.conf file, by adding/modify this 

```
Driver		"fgrlx"
```

For some reason it changed my graphics driver as well.

---

### Post by yopnono on 2006-07-11
[http://ubuntuforums.org/showthread.php?t=213420](http://ubuntuforums.org/showthread.php?t=213420)

---

