---
title: "Ubuntu GNOME font error"
date: 2016-11-16
forum: General Help
---

### Post by TBK on 2016-11-16
screenshot: [https://drive.google.com/open?id=0B0YPxoTYHWAZMmNjVHM2TWwtUnc](https://drive.google.com/open?id=0B0YPxoTYHWAZMmNjVHM2TWwtUnc)
I got this error on Ubuntu GNOME 16.04 64bit after do some things, and I don't know how to fix this. Help me!

---

### Post by QIII on 2016-11-16
Hello!

What were the "some things" that you did?

---

### Post by TBK on 2016-11-16
```
sudo apt install git
sudo apt install python-pip
pip install --user powerline-status 
pip install --upgrade pip
```

Then installing font: I downloaded PowerlineSymbols.otf and 10-powerline-symbols.conf then moved PowerlineSymbols.otf into /usr/share/fonts/ and 10-powerline-symbols.conf into /ect/fonts/conf.d/

```
sudo fc-cache -f -v
```

then I tried to reinstall this font: deleting 10-powerline-symbols.conf insize /ect/fonts/conf.d/ and run this cmd
```
sudo fc-cache -f -v
```

Next
```
sudo apt install powerline python3-powerline
sed -i '1i term screen-256color' ~/.screenrc[SIZE=3][FONT=arial][COLOR=#404040]
[/COLOR][/FONT][/SIZE]
```

and I saw "sed: can't read /home/juno_okyo/.screenrc: No such file or directory", then I reboot and got this error :(

---

