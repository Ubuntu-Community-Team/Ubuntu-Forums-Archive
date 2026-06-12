---
title: "Installing themes on Ubuntu Mate 16.04"
date: 2017-11-25
forum: General Help
---

### Post by MZ250Supa5 on 2017-11-25
I've been trying to change the appearance of my desktop, and wanted install the Equilux theme on my computer. [https://www.gnome-look.org/p/1182169/](https://www.gnome-look.org/p/1182169/) I followed the directions, and then placed the extracted theme folder in /usr/share/themes and then rebooted, and then went and looked for the theme in Appearance.  Couldn't find the theme there, so tried clicking the Install button, and navigated to /usr/share/themes and found the Equilux folder and then clicked the Open button on the dialogue window, which did nothing as it detected nothing in any folder I clicked Open for.  I noticed that there were a lot of other themes in that folder too, most of which also did not appear in the Appearance configuration window. I'm now at a complete loss, as this should be something very easy.

---

### Post by RobGoss on 2017-11-26
Hello MZ250Supa5, You must first** extract** the **tar** file and place the extracted file within the theme folder, you will need to have root access to copy the contents and move them to the theme folder 

You can run this command to gain root access;

```
 gksu nautilus 
```

You will be prompted to enter your password

---

### Post by MZ250Supa5 on 2017-11-26
Thanks Rob, but I've already done that. As I explained in my initial post, I've placed the theme in /usr/share/themes, therefore I had to be root to do that.   What I don't get is how I now can't install the theme on my computer. I've done a pretty extensive web search looking for solutions to my problem, but so far have come up with nothing other than old solutions that are no longer valid.

---

### Post by Dennis N on 2017-11-26
To have the theme appear in the Appearance Preferences window (see screen shot) the theme folder must contain a file name **index.theme** with a specific structure, as shown in following example for Menta theme (I omitted the Comment entries here):

```

[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Menta
Comment=
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Menta
MetacityTheme=Menta
IconTheme=menta
CursorTheme=mate

```

The themes set up this way are called **Gnome Metathemes**. The gtk theme, metacity theme, icon theme, and cursor theme to use with it all can be specified here. 
Reference page about Gnome Metathemes: [https://people.gnome.org/~shaunm/admin-guide/themes-17.html](https://people.gnome.org/~shaunm/admin-guide/themes-17.html)

You can edit your theme's **index.theme** file to fit these requirements, then it will show up in Appearance Preferences.

---

### Post by MZ250Supa5 on 2017-11-27
Thanks Dennis. I've made some progress, and I am seeing an entry in the Appearance window now, but the icon for the theme has a question mark on it, and when I select the theme I get a warning telling me that the appearance won't be as desired, as, apparently, the theme isn't installed!  This is after I've put the index.theme file in the desired theme folder too!  By the way, I hadn't realised that the index.theme file is totally invisible, even when 'show hidden files' is selected, which makes it doubly a pain to work with, even though using a terminal works well enough for moving it around and opening it in Pluma when it needs editing.

I actually find it completely amazing that changing a theme should be as involved as this, as it's something that I would have thought that someone would have created an easy way to do it.  The reference to the wiki was as usual, clear as mud, and about as useful as a chocolate teapot, but at least I was able to deduce from it that the index.theme file needed to go into the actual theme folder, and not just the .themes folder.

*Update, some 10 mins later...*

Slowly realised that it has to be an individual theme folder, i.e.  specific theme folder. In my case the Equilux theme folder contained both Equilux and Equilux-compact, so I needed to put just the Equilux folder into the themes folder in /usr/share. This is nowhere made specific. Once this is done, the theme will show up in the Appearance window, as each theme folder contains it's own index.theme file, which is, after all, visible, but is merely a text file named after the theme, and has no reference to index.theme in the filename. In retrospect this is very easy indeed, and even though it might seem "obvious" that subfolders with the themes in them need to be taken out of the main folder they come in, and be placed individually into the themes folder. 

Sometimes us humans are a bit like computers, and also need to be told exactly what to do, step by step!

---

### Post by Dennis N on 2017-11-27
Glad to hear you figured it out. I will mention something else that is a bit surprising: In my attached image of post #4, there is a theme called "Zukitwo-Paper", which is a name I just made up. All it is is an index.theme file in a folder. That is, the theme folder doesn't need to contain any of the actual components it specifies!

Contents of Zukitwo-Paper - one file only.
```
dmn@Sydney:/usr/share/themes/Zukitwo-Paper$ ls
index.theme

```
Contents of index.theme
```
dmn@Sydney:/usr/share/themes/Zukitwo-Paper$ cat index.theme
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Zukitwo-Paper
Comment=Zukitwo with Paper Icons
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Zukitwo
CursorTheme=FlatbedCursors.White.Large
IconTheme=Paper
MetacityTheme=Zukitwo-Dark
```

All the theme folders named in the "X-GNOME-Metatheme" section should exist in standard locations for themes and icon themes. That is, GtkTheme to use is in the "Zukitwo" folder (/usr/share/themes/Zukitwo). Icon theme to use is in the "Paper" folder (/usr/share/icons/Paper).The OS will find and use them.

Note: This metatheme concept is as far as I know, only used in the ancient Gnome 2 and its descendant, MATE.

---

