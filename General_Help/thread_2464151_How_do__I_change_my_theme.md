---
title: "How do  I change my theme"
date: 2021-06-25
forum: General Help
---

### Post by dora5 on 2021-06-25
I am having trouble changing my theme in Gnome in Ubuntu 18.04.

I downloaded a theme and extracted it in my downloads folder.   I opened Terminal and typed sudo nautilus and got Nautilus with root privileges.   I copied the folder with the theme's files into it into usr/share/themes.  I closed everything and opened gnome-tweaks and the new theme is not there.   

That is exactly what the instructions said to do. Here are the instructions.  [https://medium.com/the-techier/how-to-change-themes-in-ubuntu-20-10-2021-cce326076c73](https://medium.com/the-techier/how-to-change-themes-in-ubuntu-20-10-2021-cce326076c73)

I tried rebooting the computer, no change.

Here is where I got the theme from.  [COLOR=#292929][FONT=charter]* *[/FONT][/COLOR][https://www.gnome-look.org]("https://www.gnome-look.org/")

So what do I have to really do to install the theme?

Thanks!

---

### Post by dddman on 2021-06-25
That's too much work :)

Create a folder in your Home folder and call it [COLOR=#006400].themes[/COLOR]  No need for sudo, just put your themes there.  If you have icon packages create another folder and call it [COLOR=#008000].icons[/COLOR]

---

### Post by tea for one on 2021-06-25
When extracted, some themes have a master folder which, in turn, contains another set of folders e.g. different colour variations.

Can you provide the link to the exact theme?

```
edited@edited:/usr/share/themes$ ls
Adwaita       Default  HighContrast     Yaru       Yaru-light  Yaru-Red-dark
Adwaita-dark  Emacs    vimix-dark-ruby  Yaru-dark  Yaru-Red    Yaru-Red-light
```

The theme [COLOR="#0000FF"]vimix-dark-ruby[/COLOR] is an example.
It was originally contained in a master folder with 4/5 other colours

---

### Post by dddman on 2021-06-25
> **tea for one said:**
> Can you provide the link to the exact theme?
I can also try it in .themes

---

### Post by dora5 on 2021-06-25
Here is the contents of the folder Breeze-Chameleon Light in my themes folder.   

In which folder would I find the actual themes, if there are any?  It is a complex theme, you can select stuff.

Also, for those who said I don't have to use the themes folder for my themes, how would I get the system to recognize themes put elsewhere as themes?  That by itself doesn't make a lot of sense.

Actually it will suddenly only let me insert an image as a url to somewhere else online.    I know one SHOULD be able to post an image.   And when I try attachments it takes me to a list of things I've posted elsewhere on this forum long ago and then won't let me add to it.  

So the folders are actions, animations, applets, apps, categories, devices emblems, emotes, mimetypes places, preferences, status, 32.files (not a folder) 48.files, icon-theme.chage, index.theme, and make-symlinks.sh

Yours,
Dora

---

### Post by tea for one on 2021-06-25
Please supply exact link to the theme.

Is this it [https://www.gnome-look.org/p/1298508/](https://www.gnome-look.org/p/1298508/)?

Your description of the folders implies it is an icon theme not a gtk theme?

---

### Post by dora5 on 2021-06-25
Actually the reason why I wanted to change the screen only appears when a window takes up all the verticle space between dock and activities bar.   They turn dark.  Otherwise they're transparent like I want them.   Is that an issue with the theme?  Would a different theme keep it from happening?

---

### Post by dddman on 2021-06-25
Not working in .themes
[ATTACH=CONFIG]288727[/ATTACH]
[https://www.gnome-look.org/p/1311009/](https://www.gnome-look.org/p/1311009/)

---

### Post by tea for one on 2021-06-25
> **dddman said:**
> Not working in .themes
[ATTACH=CONFIG]288727[/ATTACH]
[https://www.gnome-look.org/p/1311009/](https://www.gnome-look.org/p/1311009/)

Is that not a KDE Plasma theme and you are using Gnome?

---

### Post by dddman on 2021-06-25
> **tea for one said:**
> Is that not a KDE Plasma theme and you are using Gnome?

Yep, my gnome does have a limited amount of QT on board but not going to cut it.

---

### Post by dddman on 2021-06-25
> **dora5 said:**
> Actually the reason why I wanted to change the screen only appears when a window takes up all the verticle space between dock and activities bar.   They turn dark.  Otherwise they're transparent like I want them.   Is that an issue with the theme?  Would a different theme keep it from happening?

Could you post a pic of this?  And what theme are you running?  It is possible to change default theme settings in your home folder ~/.config/gtk-3.0.gtk.css

As you mention, a different theme is usually a quick and easier fix.  It would be my preferred route.

---

