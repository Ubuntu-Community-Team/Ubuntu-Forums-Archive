---
title: "Launching openssh..."
date: 2007-01-30
forum: General Help
---

### Post by Mygly on 2007-01-30
Hey everyone, I'm pretty new to linux and i'm trying to launch open ssh but for some reason can seem to do it. It's not in the applications menu so I looked around for it and found what was said to be an executable for it and tried to open that but nothing happens when I try to open it. Like I said i'm fairly new to linux so try to go easy on me. I would like to have and ftp program and openssh to use. Thank you in advance for any help you may be able to give me.

---

### Post by taurus on 2007-01-30
Applications -> Accessories -> Terminal
```
ssh -l **username** IP_of_the_site_you_want_to_connect_to
```
(Replace the **username** with your actual login name and the IP adress of the site.)

---

### Post by houstonbofh on 2007-01-30
The command above with a -X (ie: ssh -Xl username IP_of_the_site ) will allow you to run X applications locally.

---

### Post by Mygly on 2007-01-30
I'm so new to linux I don't know what an X application is, although I have seen that phrase a lot lately. Does it have something to do with GUI apps?

---

### Post by houstonbofh on 2007-02-07
Everything to do with it.  X-Windows is the graphical interface for Unix.  X-Windows applications (X Apps for short) are the GUI applications.

---

