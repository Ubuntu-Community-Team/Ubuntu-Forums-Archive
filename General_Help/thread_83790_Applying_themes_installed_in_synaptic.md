---
title: "Applying themes installed in synaptic?"
date: 2005-10-29
forum: General Help
---

### Post by eyebrowman92 on 2005-10-29
ive installed a desired theme for the ubuntu breezy 5.10 gnome desktop, but i dont know how to apply it. Can some help me?

---

### Post by matva on 2005-10-29
try doing gnome-theme-manager in console. that should bring up theme manager where you can select your installed theme. you may have to hit theme details to see what you installed.  
system->pref->themes works too

---

### Post by Strangerdave on 2005-10-29
If you have installed a theme you should just select it from the panel that you see.

For instance, I went to system->Preferences->Theme and up comes up the theme manager (same if you followed the previous post and typed gnome-theme-manager into a terminal).  There I have a choice of installing a theme.  This is what you should have done.  Once it is installed, it should show up as a selection in the left frame.

-SD-

---

### Post by eyebrowman92 on 2005-10-29
ive tried but nothing but the default themes come up. how did you go about installing and applying themes?

---

### Post by matva on 2005-10-29
go to [http://gnome-look.org](http://gnome-look.org), download a theme, and drag it into the theme manager.

---

### Post by eyebrowman92 on 2005-10-29
ok so through firefox i downloaded it to my desktop and dragged it over to the theme window and it said the file format was invalid. i tried extracting it to my desktop then dragging that into the window. it said the same thing.

---

### Post by Strangerdave on 2005-10-29
Alternatively, go to System->Preferences->Theme, then on the right side is "Install New Theme".  Click on it, then find where you downloaded the new theme, select it and click "Ok" and you should see it.

What type of theme are you trying to apply?

If it is not a metacity theme then it might not work.  

-SD-

---

### Post by munkymonkjr on 2005-10-30
its sorta off topic, but you might wanna go ahead and install gnome-art

```
sudo apt-get install gnome-art
```

very usefull proggy :)

---

### Post by angrykeyboarder on 2005-10-30
[quote=eyebrowman92]ok so through firefox i downloaded it to my desktop and dragged it over to the theme window and it said the file format was invalid. i tried extracting it to my desktop then dragging that into the window. it said the same thing.[/quote]

Just for the heck of it, go to [http://art.gnome.org](http://art.gnome.org) and try the same thing.  The themes there tend to be of better quality (packaging wise).  I'm not dissing gnome-look.org.  Some of the best themes I have are from there, I'm just making a suggestion to test your setup.  It sounds to me like you might have a problem of some sort.  Unfortunatly I have no clue as to what it could be.

---

### Post by dcstar on 2005-10-30
[QUOTE=eyebrowman92]ive installed a desired theme for the ubuntu breezy 5.10 gnome desktop, but i dont know how to apply it. Can some help me?[/QUOTE]

Be warned that some of us have found that our old 5.04 themes have not worked 100% with Breezy.

I had to go back to using a "standard" theme because the Volume Control Icon was only 1 pixel wide in the theme (Nuvola) that I used previously.

I hope someone updates gnome-themes-extras soon.........

---

### Post by eyebrowman92 on 2005-11-10
ive found how to do it. i just saved it to a folder and pressed add a theme on the thing then uploaded the saved file. i think thats how i did it.

---

### Post by VitaminG on 2005-11-11
If the pakcage won't install, the files in it probably have the wrong permissions. Themes should have 775 permisions, but some people forget to check that when they compress it. If you really want the theme, you'll have to change the permissions on all the folders and files, then repackage it and try installing it again.

---

