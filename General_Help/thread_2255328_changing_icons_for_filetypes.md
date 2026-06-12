---
title: "changing icons for filetypes"
date: 2014-12-04
forum: General Help
---

### Post by jeff106 on 2014-12-04
Ive searched around and none of the solutions I have found are working for me. I want to change the default text file icon, specifically for .txt files and .py files. It seems like a simple tast but I just can't get it to work. 

I've done

```
grep 'py' /etc/mime.types
``` (and the same with 'txt')

I've then replaced the /usr/share/icons/gnome/scalable/mimetypes/ files with the following two svg files...

```
text-x-generic.svg
text-x-python.png
```

I've tried putting in all sorts of different sizes, extensions, names, etc and nothing works. Every time I have also logged out and then logged back in to see if the changes have taken effect and they have not. Can anyone help me get these changed. The default textfile icons just drive me nuts with their blandness.

---

### Post by vasa1 on 2014-12-04
>  I've then replaced the /usr/share/icons/gnome/scalable/mimetypes
But which icon theme are you using?

---

### Post by jeff106 on 2014-12-04
was using ubuntu-mono-dark I guess that was pretty obvious, trying it now...

---

### Post by vasa1 on 2014-12-04
> **jeff106 said:**
> ... I guess that was pretty obvious ...
Not to me :(

---

### Post by jeff106 on 2014-12-04
anyway, I couldn't get it to work even when I switched the icon theme. It also doesnt reflect my changes when I switch it to the gnome icone theme :( any more ideas? or am I just getting something not quite right in the process?

---

### Post by jeff106 on 2014-12-04
> **vasa1 said:**
> Not to me :(

sorry I don't want you to misunderstand me. I meant it should have been obvious to me that I was copying the files to the wrong place :)

---

### Post by vasa1 on 2014-12-04
> **jeff106 said:**
> anyway, I couldn't get it to work even when I switched the icon theme. It also doesnt reflect my changes when I switch it to the gnome icone theme :( any more ideas? or am I just getting something not quite right in the process?
Okay, can you change any other icons other than those for .txt or .py?

You'll need to do it for each icon size. On my system, Lubuntu, the icons for mimetypes are here:
```
06:57 PM /usr/share/icons/lubuntu/mimes $ ls
16  22  24  48
06:57 PM /usr/share/icons/lubuntu/mimes $ 

```As you can see, there are four sizes and depending on where the icon is to be displayed (panel, file manager, desktop, application switcher, etc), a particular size is chosen.

---

### Post by vasa1 on 2014-12-04
For practical reasons --- I like to mess with my icons --- I have my icons in ~/.icons so I don't need to sudo. Plus that way I leave the system icons intact in case I ever want to revert to them.

---

### Post by jeff106 on 2014-12-04
couple questions...

if you put them in ~/.icons (you mean home folder, right) do you have to change any paths to tell the desktop manager to look there?

second, in my ubuntu-mono-dar folder there is only the sizes 16 22 24 and they only have an icon or two in them by default. Does this sound right? i'll try adding what I want for now.

BTW, do they have to be in svg format?

UPDATE:

I managed to get the icons to update, but the only file sizes available are 16,22,24 so the icons are too small. I tried adding a 48 folder and then changing the theme file via gedit to add 48 to mimes in every place I saw but that didn't work.

Also, the command:
```

sudo gtk-update-icon-cache /usr/share/icons/ubuntu-mono-dark/

```

needs a location, so one must add the directory where the icon cache to be updated is.

---

### Post by vasa1 on 2014-12-04
> **jeff106 said:**
> couple questions...

if you put them in ~/.icons (you mean home folder, right) do you have to change any paths to tell the desktop manager to look there?
Yes, that means your home folder. No, you just have to point to that icon theme. If you're using Ubuntu, you may need something like Ubuntu Tweak to change themes.
> **jeff106 said:**
> second, in my ubuntu-mono-dar folder there is only the sizes 16 22 24 and they only have an icon or two in them by default. Does this sound right? i'll try adding what I want for now.

BTW, do they have to be in svg format?I haven't used Ubuntu recently and can't help with that. I seem to remember that ubuntu-mono uses png and not svg. I like svg because it's easy to mess with.

---

### Post by jeff106 on 2014-12-04
so weird, after exploring the problem further and playing around with diferen icon themes I am so confused. 

First of all, the icons I want to change are the ones that show in file explorer. These happen to be different from ones that show in the unity launcher. For that matter I can't find these icons anywhere. Ive searched through my icon theme and other icon themes everywhere. They just seem to be missing. 

Can anyone enlighten me here?

---

### Post by jeff106 on 2014-12-04
I am so confused, the icons are different in unity launcher and in the file manager, anyone know why this is and where the different.  sources are?

---

### Post by jeff106 on 2014-12-05
ok I have isolated my problem a little bit. I know how to change the icon files and I have done that with no success, I have changed other icons without trouble. 

I have include a picture here to show you that the system thinks it should be using the blue icon, but it is in fact using the system icon that gets used for plain text files. Its interesting that a .pyc file will use the correct icon, but that  is considered application-x-python and not text-x-python. It is only the text-x-python files and like you see here text-x-html files that are somehow not getting the icons. Everything else in the system shows the proper icon, like in the unity launcher...

[IMG]http://i59.tinypic.com/zn7d4i.png[/IMG]
[IMG]http://i58.tinypic.com/2nw3hxx.png[/IMG]

---

