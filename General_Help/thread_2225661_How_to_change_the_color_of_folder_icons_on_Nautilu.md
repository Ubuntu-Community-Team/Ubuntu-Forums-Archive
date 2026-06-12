---
title: "How to change the color of folder icons on Nautilus?"
date: 2014-05-22
forum: General Help
---

### Post by acutbal on 2014-05-22
Hello!!

I would know if it's possible to change the color of folder icons on Nautilus. I mean all folder icons at the same time, not one by one or selected folders as, for example, Folder Color does ([https://launchpad.net/folder-color](https://launchpad.net/folder-color)). I would use the default ubuntu-theme with blue folders, I like very much the Humanity icons:

[http://gnome-look.org/content/show.php/Humanity+Colors+Icon+Theme?content=148933](http://gnome-look.org/content/show.php/Humanity+Colors+Icon+Theme?content=148933)

I suppose that it should modify some kind of index.theme file or something similar, I don't know.

Thank you very much!!

---

### Post by slickymaster on 2014-05-22
There’s a small extension for Nautilus that can do that.```
sudo add-apt-repository ppa:costales/folder-color
sudo apt-get update
sudo apt-get install folder-color
```Once installed, restart Nautilus via:```
nautilus -q
```

---

### Post by acutbal on 2014-05-22
> **slickymaster said:**
> There’s a small extension for Nautilus that can do that.```
sudo add-apt-repository ppa:costales/folder-color
sudo apt-get update
sudo apt-get install folder-color
```Once installed, restart Nautilus via:```
nautilus -q
```

Thanks for your help, but this is not what I want. I already know this application, it only changes the color from selected folders. 

I want to change the entire folders color without changing the defult ubuntu icon theme.

I apologize for my English.

Regards!! &#128513;

---

### Post by Claus7 on 2014-08-31
Hello,

I have not find a definite solution to your issue, yet I suppose that this procedure here is close to what you are seeking, since you like Humanity like themes.
[http://www.webupd8.org/2014/06/humanity-colors-icon-theme-now.html](http://www.webupd8.org/2014/06/humanity-colors-icon-theme-now.html)

Regards!

---

### Post by acutbal on 2014-09-02
> **Claus7 said:**
> Hello,

I have not find a definite solution to your issue, yet I suppose that this procedure here is close to what you are seeking, since you like Humanity like themes.
[http://www.webupd8.org/2014/06/humanity-colors-icon-theme-now.html](http://www.webupd8.org/2014/06/humanity-colors-icon-theme-now.html)

Regards!


Thanks for your response, finally I decided to go with Faience theme + Elementary Xfce icons, also a nice mix.

Best regards!! :D

---

