---
title: "Gnome panel/menu/systray backgrounds"
date: 2008-07-07
forum: General Help
---

### Post by CheeseEatingBulldog on 2008-07-07
I have always wondered how to change the background of the menus/systrays. One can change the panel background easy enough, but then the menu and systray still stay the same, which makes it look fugly.

I am using Emerald, but guess that the panels are still on gtk, as it appears as the standard theme. Is there an easy way to change the backgrounds? I know it is possible as some themes from gnome look change the whole panels, so it can't be rocket science.

---

### Post by sayakb on 2008-07-07
Goto System->Preferences->Appearance->Customize->Colors tab and change the menu colors from there.

---

### Post by CheeseEatingBulldog on 2008-07-07
Thanks for that, but one can't add a panel background there. I also tried to get the menu/panel/systray to be transparent, but then everything on the bar becomes transparent, and I would like the icons/menus to be left non transparent.

---

### Post by sayakb on 2008-07-07
What are you referring to as Systray? The notification area? Right click on Panel, Select **Properties** and click the **Backgrounds** tab. Make the panel transparent/have a background image from there. The notification area will also become transparent/have a background image. You might provide some screenshots if you are referring to something otherwise.

EDIT: You may also download Ubuntu Tweak from [http://www.getdeb.net](http://www.getdeb.net) and see if it works for you. (Applications->System tools->Ubuntu Tweak)

---

### Post by CheeseEatingBulldog on 2008-07-07
If you edit the background of the panel, the notification area and clock/date and menus (apps, places, system) do not change with it, they stay the theme colour.

Have tried ubuntu tweak, but can't find anything to the effect of what I am asking.

--EDIT-- 

Right it turns out that some themes have somehow fixed the background of the menus/clock/notifcation area, so, for say Macosx theme it won't change. For others, (say standard theme in ubuntu) it will. So, how do I hack the osx theme to allow me to make it transparent.

Also when changing colours (say changing the menu text to white to make it more readable when transparent), it also changes all text in all windows to white...is there no differentiation?

---

### Post by sayakb on 2008-07-07
If you want to add a png background image, right click on panel. click properties and Background tab. You have 3 options there:
1. **None**: Would use the Macosx theme or whatever theme is applied for the whole panel.
2. **Solid color**: This uses a solid color + transparency
3. **Background image**: To set an image as panel background.

1. When you are using the Mac OSX theme, keep this value to None so that the whole panel gets themed by th Mac theme.
2. Set the Background image or the Solid Color option when you use a theme which **does not** apply themes to the panel. If you do, you will have the partial theming problem as you mentioned.

You may edit the Mac theme and set it **not** to theme your panel at all.
Also, the Menu and Window text color are the same unless set by the GTK theme itself.

---

### Post by sayakb on 2008-07-07
[http://www.gnome-look.org/content/show.php/Panel+backgrounds?content=71025](http://www.gnome-look.org/content/show.php/Panel+backgrounds?content=71025)
^^^ Panel background images.

---

### Post by CheeseEatingBulldog on 2008-07-08
Thanks for the info, but what do I change in theme to stop it 'theming' the menu and 'notification bar' ?

---

### Post by sayakb on 2008-07-08
You have to edit the gtkrc file to remove all instances of the pixmap within the **style "panel-whatever"**

---

