---
title: "How to get different wallpapers on different workspaces"
date: 2008-05-10
forum: General Help
---

### Post by anuban on 2008-05-10
I have written a blog post with pictures and steps to bring different wallpapers on different workspaces.  Check it out and drop your comments on the post.  Your feedback and suggestion to further enhance the customization will be highly appreciated.  You might be already doing the same with little different steps.  But I thought of putting together some simple bulleted points so that the newbies can also customize their Ubuntu experience.
Here is the link:
[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)

Thanks
Anurag Bansal

---

### Post by klange on 2008-05-10
Just thought I'd pop in to mention a few things:
1. For Gutsy, there are patches to Nautilus 2.20 to make it render icons over a clear background, but not for Nautilus 2.22. Blame the GNOME devs for making massive changes to libeel.
2. We (Compiz) no longer support the Cube background drawing, and it has been removed in the git version.
3. We've thrown our support over a newly rewritten Wallpaper plugin, which works even if you don't use the cube.

---

### Post by anuban on 2008-05-10
Thanks for the info...

---

### Post by Gonzalo_VC on 2008-05-11
> **anuban said:**
> I have written a blog post with pictures and steps to bring different wallpapers on different workspaces. ...
[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)
Thanks
Anurag Bansal

[COLOR="Navy"]Nice. But... what about doing it without this A.W.N.? Where in Gnome can we set to use different desktop wallpapers?
THANKS![/COLOR]

---

### Post by loganp82 on 2008-05-11
thanks i was wondering if this was possible :)

---

### Post by anuban on 2008-05-11
You can do that without AWN because AWN is only a dock.
But you lose any shortcut on desktop.  That;s why AWN...
Without AWN you will have different wallpapers on different workspaces but will lose all desktop functionalities.  You can go to Places>Desktop to browse for Desktop though.

Thanks
Anurag

---

### Post by motin on 2008-08-17
A rough gnome applet that enables different wallpapers + icon for each workspace is found here: [http://ubuntuforums.org/showthread.php?p=5600774#post5600774](http://ubuntuforums.org/showthread.php?p=5600774#post5600774)

If you only want the different wallpapers, I guess you could comment out the parts that changes the icons:
```
        os.popen('gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false')
        os.popen('gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true')
```
and
```
      os.popen('xdg-user-dirs-update --set DESKTOP %s' %self.current_desktop)
```

Remember: the applet is alpha quality - so be prepared for side effects.

---

### Post by dr_psikick on 2008-08-18
going to try this. Thanks

---

### Post by Stan_1936 on 2008-08-18
> **WindowsSucks said:**
> ...We (Compiz) no longer support **the Cube background drawing**, and it has been remove....

By that do you mean the **Skydome**?

---

### Post by timz84 on 2008-08-18
Here is a wallpaper I made, similar to the one that ubuntu edgy one. Maybe someone might like to use it.

[IMG]http://i33.photobucket.com/albums/d53/timz84/UbuntuRain.jpg[/IMG]

and wide

[IMG]http://i33.photobucket.com/albums/d53/timz84/UbuntuRain1440x900.jpg[/IMG]

---

### Post by ArtF10 on 2008-08-18
Looks nice.  You should start your own thread with the wallpapers you've made.

---

### Post by Gooseman240 on 2009-02-23
> **anuban said:**
> I have written a blog post with pictures and steps to bring different wallpapers on different workspaces.  Check it out and drop your comments on the post.  Your feedback and suggestion to further enhance the customization will be highly appreciated.  You might be already doing the same with little different steps.  But I thought of putting together some simple bulleted points so that the newbies can also customize their Ubuntu experience.
Here is the link:
[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)

Thanks
Anurag Bansal

Absolutely great material dood, still learning, but love the power of Ubuntu, it has not let me down yet!!

---

