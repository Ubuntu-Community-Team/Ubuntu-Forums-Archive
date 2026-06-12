---
title: "Help! Chrome is broken!!"
date: 2017-02-21
forum: General Help
---

### Post by jsc12345 on 2017-02-21
Please Help! Today, Chrome stopped loading images properly. Then, it started telling me that DNS servers on some of my favourite site are non-existent. And now, Ubuntu doesn't recognise it as a program on the system. (In fact, it doesn't recognize any google apps as being on the system! I've had to resort to Firefox! Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by RobGoss on 2017-02-21
This is a first time I've head this issue have you tried Uninstalling Google Chrome and reinstalling it to see if that fixes this issue

---

### Post by jsc12345 on 2017-02-21
> **RobGoss said:**
> This is a first time I've head this issue have you tried Uninstalling Google Chrome and reinstalling it to see if that fixes this issue

Already did. But you know Ubuntu. If you get rid of something then install it again, it dosen'tknow the difference. A clean install is impossible

---

### Post by howefield on 2017-02-21
Uninstalling won't make any difference unless you also remove the hidden folders/files in your ~/ folder.

Using Chromium here so that means /home/$USER/.cache/chromium and /home/$USER/.config/chromium

The chrome folders are probably called google-chrome or something similar but the path is the same.

---

### Post by dragonfly41 on 2017-02-21
32bit or 64bit?

If 32bit Chrome may possibly not work now since 32bit is not supported.. 

You could try clearing the cache or Ctrl+F5.

---

### Post by jsc12345 on 2017-02-22
Okay, now I have my images back, but now Chrome (and Chromium) can't find productforums.google.com servers and others. The problem is temporarily fixed if I restart the machine.

---

### Post by speedwell68 on 2017-02-22
> **jsc12345 said:**
> Okay, now I have my images back, but now Chrome (and Chromium) can't find productforums.google.com servers and others. The problem is temporarily fixed if I restart the machine.

Try removing the folders specified above and try again.

---

