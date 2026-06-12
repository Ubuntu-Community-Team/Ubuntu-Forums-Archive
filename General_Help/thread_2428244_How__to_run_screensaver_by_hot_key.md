---
title: "How  to run screensaver by hot key ?"
date: 2019-10-01
forum: General Help
---

### Post by petrogromovo on 2019-10-01
Hello!
Under my [COLOR=#000000]Kubuntu 18.04 [/COLOR]I have installed screensaver with default options and I want to know if there is a way to run
screensaver by hot key or by console command.

Thanks!

---

### Post by Xian on 2019-10-02
Does this command result in the desired action?

```
gnome-screensaver-command -a
```

---

### Post by petrogromovo on 2019-10-03
Thanks, but are there without locking and password entering after ?

---

### Post by Xian on 2019-10-03
You may need to install the xscreensaver suite to get this to work as described.

```
sudo apt-get install xscreensaver --install-suggests
```

Remove gnome-screensaver:

```
sudo apt-get remove gnome-screensaver
```

Run the xscreensaver program once from desktop menu to activate the needed modules. 
Here is also a good opportunity to choose your desired settings.

Once done then issue command:

```
xscreensaver-command -activate
```

---

