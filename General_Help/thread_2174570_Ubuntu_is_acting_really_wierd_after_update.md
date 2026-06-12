---
title: "Ubuntu is acting really wierd after update"
date: 2013-09-15
forum: General Help
---

### Post by andreas8 on 2013-09-15
Hi!

I installed GTK3 the other day and then i updated and upgraded my system. I never had any problems with it before but now it's just acting bananas.

The login screen wont show my background I selected (tried it several times, but nothing happens), when i have logged in, the login box shows on my wallpaper. I cant change the wallpaper or the menu bar color (which i had done before).

The whole system is freezing when im minimizing firefox,banshee etc.. the whole system is really slow right now.

Any idea how to fix this? 

Appreciate all the help I can get.

Cheers / Andreas

---

### Post by ibjsb4 on 2013-09-15
I think you already have the answer, GTK3.  How did you install it?

---

### Post by grahammechanical on 2013-09-15
I am wondering exactly what was installed. It is my understanding that GTK+3 is a development tool kit. I think that Ubuntu already has certain libraries related to GTK+3 installed. Was this a theme that was installed?

Regards.

---

### Post by andreas8 on 2013-09-15
[**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120"); I installed through the terminal.

[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"): I think it was the "Conky" theme and one more but cant remember which one.

Is there a way to remove the GTK3 from the system and see if that fixes the problem?!

---

### Post by ibjsb4 on 2013-09-15
Conky is not a theme, conky is a system monitor.  From where did you download, what terminal command did you use?

---

### Post by andreas8 on 2013-09-15
I think it was from [http://www.ubuntuthemes.org/](http://www.ubuntuthemes.org/)

Think it was this one: gsettings set org.gnome.desktop.interface gtk-theme 'Ice-Cream-GTK'^C

Is there a way to get rid of it? cause my desktop is just a big mess now

---

### Post by ibjsb4 on 2013-09-15
Guessing isn't going to cut it.  Hopefully you can open a terminal and let us have a look at what themes you have installed.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
ls /usr/share/themes
```

And please post the output.

---

### Post by andreas8 on 2013-09-15
AgingGorilla  Bright      Default  HighContrast  Mist      Redmond
Ambiance      Clearlooks  Emacs    Industrial    Radiance  Simple
Atlanta       Crux        Esco     Metabox       Raleigh   ThinIce

---

### Post by ibjsb4 on 2013-09-15
There is a couple there that I don't recognize, but I do not run unity so its probably ok.  Whats in "icons"?

```
ls /usr/share/icons
```

And I think you have a hidden folder in your home folder called .themes, not sure though.

Have you tried just changing themes?  Open up "System Settings" and go to "Appearance" and try changing it.

---

### Post by andreas8 on 2013-09-15
default    hicolor              locolor           ubuntu-mono-light
DMZ-Black  HighContrast         LoginIcons        unity-icon-theme
DMZ-White  HighContrastInverse  LowContrast       unity-webapps-applications
gnome      Humanity             redglass          whiteglass
handhelds  Humanity-Dark        ubuntu-mono-dark



Yeah ive tried changing theme and it works, but the issues are the same. cant change wallpaper and its really slow sometimes

---

### Post by Frogs Hair on 2013-09-15
> [COLOR=#000000]AgingGorilla Bright Default HighContrast Mist Redmond[/COLOR]
[COLOR=#000000]Ambiance Clearlooks Emacs Industrial Radiance Simple[/COLOR]
[COLOR=#000000]Atlanta Crux Esco Metabox Raleigh ThinIce[/COLOR]

These are all default themes and window borders except the high/low contrast and ambiance/radiance. There will be .themes folder in home hidden folders if created by the user or an installation script. There are some installation scripts from wget that create the folder.

---

### Post by andreas8 on 2013-09-18
I noticed that my screen/colors are wierd while watching movies aswell..

Might be something wrong with my graphic card or drivers?!

---

### Post by ibjsb4 on 2013-09-18
What about what Frogs Hair suggested.  Do you have a .themes folder in your home directory?

Open up your file manager (nautilus) to Home, then press **Ctrl + H** and look for a .themes folder.

---

### Post by andreas8 on 2013-09-25
Well..I tried to reinstall ubuntu.. but it's worse now. I get the login screen. then it stays that way. Can't do anything except for when I press ctrl+alt+del I can choose to logout. But that´s it.

(So now I can't get to the home folder to see if theres a .themes folder)

Really need some help with this since I need some documents for work.

---

### Post by andreas8 on 2013-09-25
I looked at the home folder now throu ext2explore on Windows.. and all thats in that folder is "a new hope"..

---

