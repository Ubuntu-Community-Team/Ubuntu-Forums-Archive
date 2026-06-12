---
title: "Command line mode to desktop mode"
date: 2007-12-15
forum: General Help
---

### Post by camcorderdoctor on 2007-12-15
Is there a way to go to desktop mode from command line mode - I downloaded the alternative cd by mistake - I don't know a lot about linux and was hoping I could get to the desktop function from the command line. please help - sorry if this is a stupid question.

---

### Post by taurus on 2007-12-15
What happens if you type

```
startx
```
If you get an error message about command not found, it means that you have a server version.  Therefore, you need to install Gnome window manager by

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by camcorderdoctor on 2007-12-15
thank you - i will try that.

---

