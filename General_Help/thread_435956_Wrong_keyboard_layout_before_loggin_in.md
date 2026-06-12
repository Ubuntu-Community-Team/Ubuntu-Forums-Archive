---
title: "Wrong keyboard layout before loggin in"
date: 2007-05-07
forum: General Help
---

### Post by bvanaerde on 2007-05-07
This is quite weird, and only happened after my Feisty installation:
I installed Feisty, and set my keyboard layout to "Belgium" (basically it's an "azerty" keyboard)

At the login screen (when powering up  my laptop), I always have a querty keyboard.
But... after loggin in, it is "azerty" again.

Is this just some startup script that starts too late?

---

### Post by Dekunuts on 2007-05-07
as far as I know, the login screen uses the xorg.conf settings and after that, the gnome configuration is loaded. this would mean that your keyboard is qwerty in the x config and azerty in gnome. 

You can go through the setup to configure X, which includes your keyboard, by doing sudo dpkg-reconfigure xserver-xorg . In case you have never done this before, you might encounter some things you don't understand very well, so be careful. Maybe there are other people who know of a more stylish way to change keyboard settings in the xorg.conf file. Hopelijk helpt dat u :)

---

### Post by bvanaerde on 2007-05-07
ahh, another Belgian... what a small world :)

Anyway, thanks for the advice, I will surely check it out.
I have reconfigured xorg before, so that's not really a problem. I'm going to check the xorg.conf file first though...

edit: it seems the keyboard layout in my xorg.conf was set to "us".
I have changed it to "nl_BE", and now everything's working fine :)

Thanks for the help!

---

