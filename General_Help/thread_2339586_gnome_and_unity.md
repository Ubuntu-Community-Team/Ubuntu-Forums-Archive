---
title: "gnome and unity"
date: 2016-10-10
forum: General Help
---

### Post by jgw on 2016-10-10
I was checking my startup programs and notice that one was "gnome software".  I am, I think, running with unity and am wondering if the 'gnome software' startup was correct.  (I am, obviously, confused as to what does what).   

As far as I can tell everything is running just fine - I was just wondering .................

Thank you......................

---

### Post by pauljw on 2016-10-10
Ubuntu Software Center has been replaced with Gnome Software in 16.04.  I hear there is still some work needed on it, I use and recommend synaptic for package management.

---

### Post by deadflowr on 2016-10-10
They moved from the software-center to gnome-software for the default package manager in 16.04.
They kept the name Ubuntu Software for it's launcher, so if you search for it in the dash with either gnome software or ubuntu software it'll show the same result.

gnome-software has an updater function that has a notification function as well.
So they set it to startup at login to connect to Ubuntu's dbus interface for those notifications.

Ubuntu 16.04 also still includes the old update manager (software updater)
So if you prefer to use only the old update manager (or if you prefer to update through apt-get commands)
then it is perfectly okay to disable the gnome-software setting in the startup applications.

Does that make sense?

---

### Post by jgw on 2016-10-11
thank you for the reply.  I have been trying to change my top bar to black (from grey) and was given 2 options to deal with.  The first was unity and the second was gnome.  I did the unity thing but that didn't change anything so I guess I will make a run at gnome.  My confusion lies in my apparent inability to determine just who is running my display, unity or gnome or both.

---

### Post by deadflowr on 2016-10-11
A couple of ways to find out quickly what you are running,

1)Unity keeps all the launchers on top of the desktop and Gnome's interface, gnome-shell, keeps all the launchers hidden or underneath the desktop so to speak, by default.

2)As far as the panel goes, an easy way to tell is where the location of the clock is.
Unity puts the clock in the right side, and Gnome's desktop interface, gnome-shell, puts it in the middle of the top panel.

3)Another way to find out what desktop is running is the command:
```
printenv | grep XDG_CURRENT_DESKTOP
```

---

### Post by CantankRus on 2016-10-11
In Ubuntu/unity, the panel appears to pick up it's colour from the gtk theme's dark_bg_color setting.
This is the case in 16.04 using the ambiance theme.

You can test this by creating a config @ **~/.config/gtk-3.0/gtk.css**
Using Ambiance, this config will overide the default theme settings.
eg I just added this line to the file....
```
@define-color dark_bg_color #EF00FF;
```

Then run the command "unity" to reload the panel.

The values used in gtk configs are continually changing so depending on the theme you are using results may vary.
Changing this color changes both panel and titlebar.
What theme are you using?

---

### Post by jgw on 2016-10-11
Thank you for the replies.  I can now change the bar colors with ease and know the difference between unity and gnome!  Its been a WONDERFUL day!!!!!!!!!!!!!!!

---

