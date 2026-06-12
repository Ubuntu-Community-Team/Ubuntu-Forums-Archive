---
title: "Using the termial to untar and install tar.gz: Error:"
date: 2013-05-08
forum: General Help
---

### Post by UltimateCat on 2013-05-08
Hi:

I'm trying to use the terminal to untar this tar.gz (Theme) that I downloaded; however I'm getting this error that I don't understand:
This file is sitting on my Desktop: 

```
ultimatecat@:~$ tar -zxvf 77221-GDM-MagicBook.tar.gz
tar (child): 77221-GDM-MagicBook.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
ultimatecat@:~$ 



```

Really is on my Desktop so not sure why terminal says: No such file of directory....clearly; it's there-:confused:

```
ultimatecat@ultimatecat-MS-7501:~$ cd Desktop
ultimatecat@ultimatecat-MS-7501:~/Desktop$ ls
77221-GDM-MagicBook.tar.gz  Practice scan~
ultimatecat@ultimatecat-MS-7501:~/Desktop$ 



```

What's this all about?

---

### Post by Habitual on 2013-05-08
I sometimes get this in another distro, but I usually have to run "tar" "***F***irst letter <tab> and let the shell 'find' it.

---

### Post by schragge on 2013-05-08
Try ```
tar -xvf [COLOR=red]~/Desktop/[/COLOR]77221-GDM-MagicBook.tar.gz
```

---

### Post by UltimateCat on 2013-05-08
Schragge:

Thank you!
```
ultimatecat@ultimatecat-MS-7501:~$ tar -xvf ~/Desktop/77221-GDM-MagicBook.tar.gzmagic-book/
magic-book/background.jpg
magic-book/option.png
magic-book/session.png
magic-book/screenshot.jpg
magic-book/disconnect.png
magic-book/magicbook.xml
magic-book/GdmGreeterTheme.desktop
magic-book/system.png
ultimatecat@ultimatecat-MS-7501:~$ ./configure
bash: ./configure: No such file or directory
ultimatecat@ultimatecat-MS-7501:~$ 



```

Now what's wrong?
Thought configure would be next, than make && make install :confused:

---

### Post by steeldriver on 2013-05-08
You can see from the tar output in your window

```

magic-book/background.jpg
magic-book/option.png
magic-book/session.png
magic-book/screenshot.jpg
magic-book/disconnect.png
magic-book/magicbook.xml
magic-book/GdmGreeterTheme.desktop
magic-book/system.png

```

that there is no file called 'configure' (in fact, the ./configure - make - make install sequence only applies to distributions in source code form - and not always then). To install themes you usually just need to untar them into (or untar wherever and then move them into) the appropriate themes directory - usually either /usr/share/themes (for everyone), or ~/.themes or ~/.local/share/themes (for personal themes). The theme files also need to be appropriate for the desktop session you are running.

---

### Post by UltimateCat on 2013-05-09
> To install themes you usually just need to untar them

Thank you! I wasn't aware of that. Thought they required configuring and other practices--

So if I understand you correctly; that Magic Book should already be where it's suppose to be and I should be able to set it now?

---

### Post by schragge on 2013-05-09
Most probably no. You unpacked it into folder *magic-book* in your home directory. I doubt your desktop environment can find it there unless it explicitly configured to search for themes directly in your home directory. Move it to one of locations suggested by **steeldriver** above.

[highlight]Edit[/highlight]
What you downloaded looks like a GDM theme. Recent Ubuntu releases by default use [uwiki]LightDM[/uwiki] instead. Are you sure this theme is suitable for your system? Anyway, a background image for LightDM can be specified in file */etc/lightdm/lightdm-gtk-greeter.conf* in form
```
background=[COLOR=#FF0000]/home/utimatecat/magic-book/[/COLOR]background.jpg
``` Replace [COLOR=#FF0000]/home/ultimatecat/magic-book/[/COLOR] with the full path to the image.

---

### Post by UltimateCat on 2013-05-09
Your right it is in my Home directory and attempting to put it in my themes folder failed.
The system would not allow me to cut and paste that file nore drag nor drop into the themes folder.

Perhaps this is not the correct "theme" for my distribution--

My new OS allows me 2 to 4 different types of DE and I tend to stay with Gnome or Gnome 3-

> Ubuntu releases by default use [LightDM]("http://wiki.ubuntu.com/LightDM") instead

Thank you for telling me that. That makes a considerable difference!

---

### Post by UltimateCat on 2013-05-11
It is now clear how to un-tar ; Thank You-
I'll look into "Light Dm' not GDM in the future for desktop themes-

---

