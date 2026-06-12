---
title: "Anyone know how to change this GTK color (part of this window) (picture included)"
date: 2008-07-01
forum: General Help
---

### Post by AaronMT on 2008-07-01
I'm speaking of the gray background color in the update window "Downloading Package Files", it's the only window part of the theme I'm running that has that deep dark gray background. Any help appreciated. 

Click to view image

[http://www.uploderx.net/dphrag/Screenshot745.png](http://www.uploderx.net/dphrag/Screenshot745.png)


_Solved_

---

### Post by soccerboy on 2008-07-01
If you go into System>Preferences>Appearance.  Then click customize on your theme, you can change the background window color in the color tab.

---

### Post by damis648 on 2008-07-01
That is different because that synaptic window is being run as root. I suppose you could change the GTK theme for root and it would work...

PS Do not put such big photos in context! Use the attachment tool!

---

### Post by AaronMT on 2008-07-01
How would one change the GTK theme for root? Login as root and change it under appearance?

---

### Post by AaronMT on 2008-07-01
Solved.


```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

### Post by NilsE on 2008-07-01
If the theme you are using does not allow color changes then you will have to edit the gtkrc file in /usr/share/themes/ThemeName for the theme and find the entry for the box.  Off hand I don't remember which one it is but you can experiment with changing the 6 hex digits for any that sound by name like the popup box. Probably something like menu or window background.

---

### Post by damis648 on 2008-07-01
> **AaronMT said:**
> Solved.


```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

Ah, good idea. Create a symlink to your themes! I never thought of that... I will have to do that.

---

