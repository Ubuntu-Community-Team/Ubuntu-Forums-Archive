---
title: "Set default &quot;Open With...&quot; to Terminal"
date: 2016-07-02
forum: General Help
---

### Post by drew123301 on 2016-07-02
I have a few applications that need to be opened up with terminal in order to run correctly, but when I access the "Open With..." menu in the Right-Click options, Terminal doesn't appear. I don't want to have to take a bunch of extra steps just to run a few applications. Does anyone know how to set Terminal as default?

---

### Post by mc4man on 2016-07-02
You should mention what is the nature of your apps, ie. what are you r. clicking on. A binary, shell script, .desktop ?

---

### Post by ajgreeny on 2016-07-02
You can probably do this with a .desktop file that makes sure the executable is opened in whatever is set as your default terminal but as mc4man says it would be better if we knew what this application is.

Here's one I used in the past for alsamixer.
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Exec=alsamixer
Name=Alsamixer
Icon=/path/to/alsamixer.png

```

---

### Post by drew123301 on 2016-07-02
They're shell scripts.

---

### Post by mc4man on 2016-07-02
> **drew123301 said:**
> They're shell scripts.

then just create a whatever.desktop on the Desktop or wherever you want to keep it. You can use the posted above .desktop as a template. 

The Name= line will be what is displayed for your launcher, can be anything you like. Keep the actual file name of the .desktop file simple (no spaces) & unique.
The Icon= line can be left blank or if you have an icon you like then use full path to icon in the line. An icon makes the launcher nicer than some generic one if line is left blank.
The Exec= line should be full path to the script unless the script is in a bin folder in your PATH, in that case it could simply be Exec=scriptname

After creating then right click on the .desktop file > Properties > Permissions. Enable the Execute: box, ex. in screen. Then just d. click on the launcher you created to open your script in a terminal.

---

### Post by mc4man on 2016-07-02
Another option vs. creating a launcher  (.desktop), would be to set executable files to either ask or launch. (- default is to display
For launch (run),  then the script would have to handle  running the app in a terminal. 
For ask you'd be given the choice to run in terminal, display, or run
Setting is in dconf-editor, see screen, scr. 2 is what ask produces on a d. click on executable file

---

### Post by efflandt on 2016-07-03
Note that for any scripts, you should create a bin directory in your home directory (mkdir ~/bin), put them in that directory, and give the scripts execute permission. Then once you log out of X and log back in, that bin will be in your default $PATH to automatically run by name (if launched from a terminal or desktop launcher) without requiring a path.

But I always thought the default when you double click on a proper script anywhere with execute permission was as ***mc4man*** mentions, where it asks if you want to run or display the script.

---

### Post by mc4man on 2016-07-03
> **efflandt said:**
> 
But I always thought the default when you double click on a proper script anywhere with execute permission was as ***mc4man*** mentions, where it asks if you want to run or display the script.
It always used to, the current default in a gnome or ubuntu session is to display. (gnome devs change

You could stick your scripts in ~/bin & if desired create symlinks elsewhere, for ex. on the Desktop. So with prior example of script named testrun - 
ln -s  /home/doug/bin/testrun   /home/doug/Desktop/trun
(- in the properties of the link  clicking on the icon will allow setting an icon of choice

---

