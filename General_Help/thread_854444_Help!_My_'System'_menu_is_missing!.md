---
title: "Help! My 'System' menu is missing!"
date: 2008-07-09
forum: General Help
---

### Post by teledyn on 2008-07-09
I don't know what they did, but the kids were using the computer (using Gutsy) and somehow they removed the text-menu items on the top panel, and as a result we no longer have the System menu.  There is no option to re-enable this under the panel preferences or in the add-to-panel selections.

where it became important is with the new background wallpaper in Hardy, on my laptop I was able to change this back to the old wallpaper, but with this desktop machine just upgraded to Hardy, I cannot find any option anywhere to set the desktop?  Is this now only possible in Nautilus?  It is an old machine and not sufficiently powerful to run Nautilus all the time.

---

### Post by Sealbhach on 2008-07-09
On the panel, click Add to Panel, then Add the Main Menu from there.

Should work, I've just done it now.


.

---

### Post by teledyn on 2008-07-09
saw that, and tried it, but what I got instead was a ubunto cycle-logo that gives me a drop down menu much like the old bottom-panel start button.  what I'm hoping to get is the three text-label menu items for Applications, Places and System.

I also cannot find the Xorg configuration -- this new machine is creeping along yet the load is not high and I wonder if the upgrade mis-selected the Xorg driver.

---

### Post by Sealbhach on 2008-07-09
Try:

```
sudo apt-get install gnome-menus
```


.

---

### Post by Elfy on 2008-07-09
> what I'm hoping to get is the three text-label menu items for Applications, Places and System.That is menu bar in Add to Panel

---

### Post by teledyn on 2008-07-09
> **Sealbhach said:**
> Try:

```
sudo apt-get install gnome-menus
```


.

"gnome-menus is already the newest version"

I suspect it is something in the personal config that has gone wrong as the missing menus persisted past the upgrade from Gutsy to Hardy

---

### Post by Elfy on 2008-07-09
Did menu bar not do it then?

If not try to reset the panels back to default

[http://ubuntuforums.org/showpost.php?p=2450460&postcount=2](http://ubuntuforums.org/showpost.php?p=2450460&postcount=2)

---

### Post by davehouston on 2008-12-18
I also lost these menus after installing some regular updates a week or so before the release of 8.10. They are still missing after the 8.10 upgrade.

---

### Post by Precipitous on 2008-12-18
Right click on the panel and select Add To Panel. Next scroll down to Menu Bar, highlight it and click Add...  This should give you the panel icon/menu you are after.

---

### Post by davehouston on 2008-12-18
No, that gives you an icon with a combined group of menus when clicked - I did that weeks ago when I could not figure out how to restore what was lost. What I lost and would like to recover were text menus on the menu bar for **Applications, Places and System**. I have them on my Debian and Fedora installations and would prefer to have them all the same.

---

### Post by xjcannonx on 2008-12-18
when you go to add to panel, there should be (2) different menu's that you can add. One says custom or something like that, this is the one that has the 3 Applications, Places and System

---

### Post by Izek on 2008-12-18
"Custom Menu" IS the three menus.

---

### Post by arrange on 2008-12-18
Right click on the panel &#8594; add to panel &#8594; choose "Menu bar". This will give you the three option gnome menu.

---

### Post by akelsall on 2008-12-18
I'm not in front of my Linux box, but I believe you need to right-click on the panel, then click "Edit menu". From there, a window is displayed where you can add and remove items from the main panel.

Andy

---

### Post by davehouston on 2008-12-18
> **arrange said:**
> Right click on the panel &#8594; add to panel &#8594; choose "Menu bar". This will give you the three option gnome menu.That was it. Thanks.

---

### Post by Precipitous on 2008-12-19
davehouston - Normally in Ubuntu when you add the Menu Bar you get the Applications, Places and System menus you are looking for. When you add the Main Menu you get only an icon, which brings up one combined menu...  Are you positive you are adding the Menu **Bar**, and not the Main Menu?

---

### Post by dchky on 2009-01-24
> **forestpixie said:**
> That is menu bar in Add to Panel

Thankyou. This probably should have been obvious to me, but I assumed that "menu bar" would simply add an empty launcher, so I never bothered to try it. A little counter-intuitive. Perhaps the gnome or ubuntu folks can rename it to 'default menu bar'

---

### Post by nanonils on 2009-08-05
I can't bring my System menu back either! See attached picture.

I tried resetting it but that only brought back Applications and Places. I also removed it and added it back without success.

It happened to me when my box froze after I run Seti@home with BOINC and I had to do a hard reset. After rebooting my quad core was at 100% but after unistalling BOINC I'm back in shape in that regards.

---

### Post by nanonils on 2009-08-06
I deleted ~/.config/menus/applications.menu and also settings.menu after realizing that there was nothing in them when I opened them with the text editor, so not much to loose. Instantly, all menus were showing including the lost option to edit (when right clicked on the bar).
Gotta remember: it's all files in Linux!

---

### Post by Daan on 2009-12-27
It is very easy to just re-add the Application Places System menus. Right click on the panel, choose Add to Panel... and then add Menu Bar.

---

### Post by nanonils on 2009-12-27
Yes, but the point of this thread was that this did not add the submenus. One had to delete several hidden files.

---

