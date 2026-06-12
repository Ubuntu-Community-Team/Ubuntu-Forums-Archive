---
title: "How do I make this my panel icon??"
date: 2007-07-20
forum: General Help
---

### Post by herbster on 2007-07-20
[http://gnome-look.org/content/show.php/Ninja+Ubuntu+logo?content=62635](http://gnome-look.org/content/show.php/Ninja+Ubuntu+logo?content=62635)

I just love that, and I am really at a loss to figuring out how to change my gnome panel icon. It's currently the standard orange Ubuntu logo. Now, when I have installed a few different icon themes to try them out, it changed to the golden gnome foot, which I also really liked, but didn't want to keep the entire icon theme (I am currently using Buuf).

I have tried the changing of the start-here.png icon in icons/gnome/scalable and tango and human, but it doesn't change. I'm really at a loss, and would love to make this tiny alteration.

Any help appreciated, TIA!

---

### Post by Di@blo on 2007-07-20
dude, you need to read more carefully...On the link you provided, the second comment:

> It tries to replace /home/you/.icons/gnome/scalable/places/start-here.svg

---

### Post by herbster on 2007-07-20
> **Di@blo said:**
> dude, you need to read more carefully...On the link you provided, the second comment:

That was posted just recently after I asked (you'll notice it's me in that link that asks), but thanks!

EDIT: And I just tried it, does not work. It's a .png replacing an .svg but even after converting it it doesn't do it :(

---

### Post by Astro96 on 2007-07-20
I had to resize the image to be 22x22 (I've attached mine).  Then I put that icon into /usr/share/icons/Human/22x22/places/ as start-here.png.  That alone, did not change my image, however.  I also had to delete (I moved it) /usr/share/icons/Human/icon-theme.cache.  With that done, I cycled my theme and the new pretty icon was there.

It seemed prudent to recreate the cache so I ran
```
sudo gtk-update-icon-cache /usr/share/icons/Human/
```

Andy

---

### Post by strabes on 2007-07-20
I wrote a blog post about this a long time ago. I don't know if it still works or not. Anyway here's the link: [http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/](http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/)

---

### Post by herbster on 2007-07-21
Well I am at a total loss now. I have just gone through all start-here.png's and .svg's in /usr/share/icons/gnome, Tango and Human, changing all of them and my panel has not changed still, hehe. I only have Buuf in my ~/.icons, so it's not there.

I changed the icon in each folder using sudo nautilus, then that command Astro96 gave to flush the icon cache, then even doing killall gnome-panel. I've even logged out and back in, the orange bugger's still there on my panel :(

:?  ????

---

### Post by Astro96 on 2007-07-21
It is working for me so it is possible!  Don't give up hope!

To clarify, I ran the command in my previous post after the icon had already changed.  To make mine change I had to delete the cache, replace the icon, and cycle my icon theme.  Mine was the in 22x22 folder so make sure you hit that one.

Beyond that... not sure where to go if it still doesn't work for you.

Good luck!
Andy

---

### Post by herbster on 2007-07-22
Okay, how do you delete the icon cache? Your command updates it I think, so maybe I'm missing that step.

And I just noticed that in the main menu, if I click on System, where it says "About Ubuntu," that icon has indeed changed to the new one! So at least one of 'em did, haha ;)

Still gotta get this main menu sucker done though...

---

### Post by Astro96 on 2007-07-22
I deleted it by running nautilus as root: "sudo nautilus".  That's usually not such a great idea because you can accidentally mess some things up, but it lets you poke around a bunch of directories easily.  You just have to be careful that you don't move the wrong file and forget about it.

Another, probably easier way is just to move it to a backup with the command line:
```
sudo mv /usr/share/icons/Human/icon-theme.cache /usr/share/icons/Human/icon-theme.cache.backup
```

- Andy

---

### Post by herbster on 2007-07-25
Okay, well I ran into a guide on a blog that instructed using the gconf-editor method of going to apps > panel  and looking for "menu-bar" in object_type, and checking "use custom icon." I did it even though I had tried this method before and it didn't work, and to my amazement my main menu icon has finally changed! :D

---

### Post by notwen on 2007-07-25
Sweet icon indeed !

---

### Post by shane2peru on 2007-07-28
> **herbster said:**
> Okay, well I ran into a guide on a blog that instructed using the gconf-editor method of going to apps > panel  and looking for "menu-bar" in object_type, and checking "use custom icon." I did it even though I had tried this method before and it didn't work, and to my amazement my main menu icon has finally changed! :D

Herbster,

Do you mind posting that link to that blog so that I can look at those instructions?  I would like to do this too, and would like to read through them.  Thanks.

Shane

---

### Post by Jim Danner on 2007-08-03
It's strange how we have all installed the same Ubuntu (7.04 for most of us, I'm sure) and still one method works for one user and another one works for someone else.

For example, the most described method on this forum is to open the Configuration Editor (gconf-editor), navigate to /apps/panel/objects, find a subkey for which *object_type*=menu-object, check its *use_custom_icon* checkbox and set the variable  *custom_icon* equal to the path of the image file.

This doesn't work for me, because I don't have any subkey for which *object_type*=menu-object. There is one with *object_type*=menu-bar, but the procedure doesn't work with that.

I also tried methods described on several other forum posts, with no luck. Only on this one did they get the crucial point right: the image must already be 22x22 pixels. It isn't automatically resized as GNOME does in many other situations.

The procedure that worked, in the end, was the one described in bits and pieces in the posts above:
[LIST=1]
[*]Save a 22x22 pixel .png icon as /usr/share/icons/Human/22x22/places/start-here.png (or replace Human with the name of the icon theme you're currently using - this isn't necessarily the same as the general theme you're using; see Theme Preferences).
[*]Empty the icons cache: rename or remove /usr/share/icons/Human/icon-theme.cache (again, use the right icon theme).
[*]Rebuild the icons cache by typing *sudo gtk-update-icon-cache /usr/share/icons/Human/*
[*]Rebuild the screen panels by typing *killall gnome-panel*
[/LIST]
This worked for me, but nothing else did!

---

### Post by zoroko on 2007-08-08
NONE... of the above has worked for me... im clueless..

---

### Post by Jim Danner on 2007-08-08
Is your panel size 24? (right-click somewhere on it and select Properties). If that's different, you might need to try replacing an icon of different size. Finally, this whole procedure seems to work for Gnome 2.18 in particular (see in the menu System... About GNOME), and only if you put the icon in the folder of the right "icon theme" (see the Theme Preferences, click Customize, click Icons).

You might still try [this one]("http://ubuntuforums.org/showthread.php?t=498890"), including the first and second post. This is actually the most elegant method, because it keeps your customization in your Home folder. But it didn't seem to work for me (I got only as far as the procedure described in the first post, though).

---

### Post by monkeylin on 2007-08-09
> **zoroko said:**
> NONE... of the above has worked for me... im clueless..

HI, try this method. only adjust/modify/create the icon “distributor-logo.png”  in the custom icons folder  

```
/home/$user/.icons/$theme_in_use/scalable/apps
```

Then run:

```
killall gnome-panel
```


You should now see your logo in your menu bar.

Good luck.

---

### Post by Jim Danner on 2007-08-09
You could try it... More detailed instructions for this solution are in the forum thread I linked to in my last posting. For me, this only changed the icons I get to see in the "Add to Panel" item list, but as soon as I actually drop the Menu Bar or Main Menu applet onto the panel, the default icon is used...

Do report if you have better results, zoroko.

---

### Post by zoroko on 2007-08-09
> **Jim Danner said:**
> Is your panel size 24? (right-click somewhere on it and select Properties). If that's different, you might need to try replacing an icon of different size. Finally, this whole procedure seems to work for Gnome 2.18 in particular (see in the menu System... About GNOME), and only if you put the icon in the folder of the right "icon theme" (see the Theme Preferences, click Customize, click Icons).

You might still try [this one]("http://ubuntuforums.org/showthread.php?t=498890"), including the first and second post. This is actually the most elegant method, because it keeps your customization in your Home folder. But it didn't seem to work for me (I got only as far as the procedure described in the first post, though).


Worked like a charm!  Thanks alot..

I did some poking around, and I found that the icon being used was from the Tango icon set, not the human icon set. So I could have just replaced the icons there. I never got around to trying it because i didn't have a way of converting png to svg.

I like your method much better...  Thanks alot! :)

---

### Post by nullcrux on 2007-10-15
Try inkscape, it handles both png and svg formats.

I can't seem to get this damn thing to change, I've checked every forum and every forum that those forums refer to and I still can't figure it out.

---

### Post by Jim Danner on 2007-10-15
> **nullcrux said:**
> Try inkscape, it handles both png and svg formats.

I can't seem to get this damn thing to change, I've checked every forum and every forum that those forums refer to and I still can't figure it out.

Well, just 3 days until Ubuntu 7.10 comes out... Who knows what may work in the new version!

---

### Post by Jim Danner on 2007-10-31
I have tried the method from my post #13 (in this thread, above), the one described last. On a pristine Gutsy installation, it worked.

Has anyone tried any of the other methods in Gutsy?

---

