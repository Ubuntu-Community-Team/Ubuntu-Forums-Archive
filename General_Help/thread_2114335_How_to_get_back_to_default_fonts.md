---
title: "How to get back to default fonts ?"
date: 2013-02-09
forum: General Help
---

### Post by sinaphysics on 2013-02-09
I encountered by a Farsi language font, And I installed them to use in Libreoffice. Unfortunately It wasn't enough Ok in Libreoffice. Beside that the Firefox, Chrome, Opera and some other software don't look ok. I think the package of TTF files which I installed have made this. Please give me some guides to how to get back to previous situation ?

---

### Post by schragge on 2013-02-10
If the font pack you installed came packaged as .deb then simply uninstall that package ```
sudo apt-get remove *package*
```. If you don't remember the name of the package that installed the font, first try to find it out with
```
dpkg -S '**[COLOR=green]nastaliq[/COLOR]**.ttf'
``` Put the name of your font instead of *[COLOR=green]nastaliq[/COLOR]*.

Otherwise, we need to know in more detail how and where you did install the font.

---

### Post by ibjsb4 on 2013-02-10
Your fonts are located in /usr/share/fonts.

For me, I can pick a font, right click on it, go to "open with font viewer" and then install.

You are probably running Unity.  I understand the package "MyUnity" has the capability of changing fonts.

---

### Post by schragge on 2013-02-10
> **ibjsb4 said:**
> Your fonts are located in /usr/share/fonts.Well, I wouldn't be so sure. */etc/fonts/fonts.conf* on my system contains
```

        <dir>/usr/share/fonts</dir>
        <dir>/usr/X11R6/lib/X11/fonts</dir> <dir>/usr/local/share/fonts</dir>
        <dir>~/.fonts</dir>

```and I have a bunch of fonts installed in *~/.fonts*.

---

### Post by ibjsb4 on 2013-02-10
*~/.fonts*, I have no such file so I guess this is either Unity or Libreoffice which I do not have installed and can't help you.

Good luck

---

### Post by lovevn on 2013-02-10
> **ibjsb4 said:**
> *~/.fonts*, I have no such file so I guess this is either Unity or Libreoffice which I do not have installed and can't help you.

Good luck
Oh, you should enter Home, and choose View -> show hidden files, then you can see .fonts :D

---

### Post by ibjsb4 on 2013-02-10
> **lovevn said:**
> Oh, you should enter Home, and choose View -> show hidden files, then you can see .fonts :D

I prefer **Ctrl + H**

---

### Post by sinaphysics on 2013-02-10
To explain more, I installed the fonts by double clicking on TTF file and then by choosing install button. Actually I didn't install any fonts by "deb" package. And for some ttf files I add them to "./fonts" folder and for resetting, I remove that Folder :D 
So you think there is some special trick works for me ?
In addition how can I detect which fonts dominates the web page I'm watching through Firefox ?

---

### Post by sinaphysics on 2013-02-10
I know that the Arial is the font used by firefox. I want to remove this font. But I can't find the location. In addition I've installed Font manager and unfortunately it couldn't find too.

---

### Post by sinaphysics on 2013-02-11
I find the problem. By installing by double click on ttf files I realize that the files is copied in this folder " /home/sina/.local/share/fonts ". And I find the path by installing "Fontmatrix" app. You can even deactive files through this app.

---

