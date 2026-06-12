---
title: "ubuntu 18.04 gnome top bar clock font size increase"
date: 2019-01-17
forum: General Help
---

### Post by lance bermudez on 2019-01-17
I have ubuntu 18.04 gnome desktop. On the top bar is the clock but the font is small how can I make it bigger. I have gnome tweeks installed and making the fonts bigger there does not make the clock fonts any bigger.

[https://www.omgubuntu.co.uk/2017/04/change-gnome-shell-font](https://www.omgubuntu.co.uk/2017/04/change-gnome-shell-font)

sudo gedit /usr/share/themes/Arc/gnome-shell/gnome-shell.css 

change 9pt to the size you want
```

stage {
  font-family: Futura Bk bt, Cantarell, Sans-Serif;
  font-size: 9pt;
  color: #5c616c; }

stage {
  font-family: Futura Bk bt, Cantarell, Sans-Serif;
  font-size: 14pt;
  color: #5c616c; }

```

---

### Post by howefield on 2019-01-17
You could try creating a file called gnome-shell.css and placing it in ~/.themes/CustomFontTheme/gnome-shell

The contents of the gnome-shell.css would look something like the following..

```
stage {
 font-family: Ubuntu;
 font-size: 9pt;
 color: #fdf498; }
```

obviously that is just an example, change the font, size and colour to suit what you want.

You may need to install the gnome shell extension "User Themes"

---

### Post by #&amp;thj^% on 2019-01-17
See if this helps: [https://www.modmy.com/how-change-font-gnomes-top-bar](https://www.modmy.com/how-change-font-gnomes-top-bar)
Ninja'd by howefield ;)

---

