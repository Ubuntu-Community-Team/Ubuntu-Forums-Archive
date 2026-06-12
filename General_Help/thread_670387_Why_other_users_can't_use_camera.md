---
title: "Why other users can't use camera?"
date: 2008-01-17
forum: General Help
---

### Post by danpre on 2008-01-17
Hi,

I have video camera.
It works with my user (this is a user which installed ubuntu system and installed a camera).
I can use Skype2beta with video.

There are two more local users on this computer.
When they start Skype2beta - it says: No camera detected

What I need to do to let others use a camera?

DANIeL

Ubuntu Gutsy Gibon 7.10
Gnome
Camera: Creative Live Vista IM
camera installed with this HOWTO:
[http://forum.skype.com/index.php?showtopic=100897&st=59#](http://forum.skype.com/index.php?showtopic=100897&st=59#)

---

### Post by danpre on 2008-01-17
> **danpre said:**
> Hi,

I have video camera.
It works with my user (this is a user which installed ubuntu system and installed a camera).
I can use Skype2beta with video.

There are two more local users on this computer.
When they start Skype2beta - it says: No camera detected

What I need to do to let others use a camera?

DANIeL

Ubuntu Gutsy Gibon 7.10
Gnome
Camera: Creative Live Vista IM
camera installed with this HOWTO:
[http://forum.skype.com/index.php?showtopic=100897&st=59#](http://forum.skype.com/index.php?showtopic=100897&st=59#)

Well...
I will answer to myself:
[http://ubuntuforums.org/showthread.php?t=408448&highlight=webcam+users](http://ubuntuforums.org/showthread.php?t=408448&highlight=webcam+users)

:)

---

### Post by sisco311 on 2008-01-17
the command to add a user to video group is: 
```
sudo usermod -a -G video **username**
```

---

