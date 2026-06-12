---
title: "Need help making  minecraft .desktop icon"
date: 2021-08-11
forum: General Help
---

### Post by snype9lives on 2021-08-11
the "solutions" dont work at all for me

---

### Post by QIII on 2021-08-11
Which "solutions" don't work?

---

### Post by snype9lives on 2021-08-12
pastiing a code into text editor and making it a .desktop

---

### Post by QIII on 2021-08-12
"A code"?  This is not a video game, so video game vernacular is not appropriate.  You may have pasted a "command" or two.  What was the file?  Where was it?  How was it invoked?

Could you try to be a tiny bit less parsimonious with the information you provide? I've never been any good at mind reading.

---

### Post by snype9lives on 2021-08-12
dont be a smartass, I meant a script

---

### Post by QIII on 2021-08-12
And the script's contents?

---

### Post by T6&amp;sfpER35% on 2021-08-12
lol

---

### Post by snype9lives on 2021-08-12
#!/usr/bin/env xdg-open [Desktop Entry] Version=1.0 Type=Application Terminal=false Exec=/home/charles/Downloads/minecraft
 Name=Minecraft Comment=Icon=/home/charles/Downloads/mine.png

---

### Post by T6&amp;sfpER35% on 2021-08-12
are you trying to make an icon on your desktop pointing to minecraft?
or do you already have the desktop icon on the desktop but you want to modify it to an icon you like ?

---

### Post by deadflowr on 2021-08-12
What happens when you paste the Exec line into a terminal
(note only the file path part not the whole Exec= part)
```
/home/charles/Downloads/minecraft
```

---

### Post by dragonfly41 on 2021-08-12
When creating/editing .desktop files
run this command

sudo locate .desktop | grep applications

and you see many examples in /usr/share/applications/
also in /snap/   and elsewhere.

At least this is where I place my custom desktop files.

[P.S.] don't know why the Reply to Forum went to sleep .. multiple posts .. sorry.

---

### Post by dragonfly41 on 2021-08-12
removed

---

### Post by dragonfly41 on 2021-08-12
removed

---

