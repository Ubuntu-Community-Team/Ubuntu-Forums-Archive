---
title: "Mousepointer won't move"
date: 2013-11-28
forum: General Help
---

### Post by kdrejer on 2013-11-28
Hi everynow and then when i close the lid on my laptop and it goes to standby, when I open it at and login to Xubuntu again, the mousepointer won't react to my movements, instead every movement I make it thinks that I am scrolling. It occurs about every 10 times being on standby.

---

### Post by varunendra on 2013-12-01
When this happens, open a terminal (Ctrl-Alt-T) and try this set of commands -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```
If this doesn't help, please post back the outputs of -
```
xinput
synclient
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

