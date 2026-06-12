---
title: "How do I Manually Change Desktop Background?"
date: 2013-11-21
forum: General Help
---

### Post by nzk13 on 2013-11-21
Hello, all. I'm wondering if there is a text file somewhere that tells ubuntu what my Desktop background image is? If there is, where is it, and how can I change it? I'm thinking of creating a program which alternates them every day or so. Thank you for your time:)

---

### Post by stinkeye on 2013-11-21
```
gsettings set org.gnome.desktop.background picture-uri "file://[COLOR="#696969"]<path to pic>[/COLOR]"
```

eg ```
gsettings set org.gnome.desktop.background picture-uri "file:///home/glen/Pictures/wallpaper/coffee.jpeg"
```

If you want an application that will do it for you take a look at [**_[COLOR="#B22222"]Variety[/COLOR]_**]("http://peterlevi.com/variety/")

---

### Post by nzk13 on 2013-11-22
Thanks, stinkeye! I had already figured out how to do it by changing my /home/Firefox_wallpaper.png file, but I didn't know how to do it like this, through the terminal. And thank you doubly for suggesting Variety. It seems like something I'd enjoy.

---

### Post by Bucky Ball on 2013-11-22
In the Desktop Background settings window you can set it to use a list of images instead of one image if you want to.

---

