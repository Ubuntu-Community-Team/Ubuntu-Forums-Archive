---
title: "ubuntu doesnt load up"
date: 2012-11-06
forum: General Help
---

### Post by aninona on 2012-11-06
hi there
When I turn on the pc it loads up and ubuntu loads as well as in the image below, but after that screen nothing is seen, all black. 

What should I do? Thanks!!

[[IMG]http://img43.imageshack.us/img43/4538/06112012882.jpg[/IMG]](http://img43.imageshack.us/img43/4538/06112012882.jpg/)

---

### Post by grahammechanical on 2012-11-06
If I was you I would take notice of the message that says

> Starting GNHstep distributed object mapper

The next two lines tell you what to do. You could try selecting Recovery mode from the Grub menu. I find that sometimes I can get to a desktop by selecting Resume.

But if not you need to get to a root prompt. That too is an option on the Recovery menu but I have found that the file system is mounted as read only. My solution is to -

first select low resolution mode, then back out of it back to the menu and then select Root prompt at which you should now find that the filse system is read/write mounted and you can use apt-get to install what is missing.

Regards.

---

