---
title: "How do i change the ubuntu logo next to applications?"
date: 2008-06-04
forum: General Help
---

### Post by latinoheat69 on 2008-06-04
I searched and found some ways but none of theme work for me.  I am on Hardy Heron (8.04).
Thanks

---

### Post by SomeGuyDude on 2008-06-04
Go into your icon theme, look for a folder called "places" and then "start-here.png". Change that.

---

### Post by latinoheat69 on 2008-06-09
ok...let's say the theme is Human...where exactly is it?

---

### Post by sn3rd on 2008-06-10
You should check your home folder for .icons

For me, it's /home/myusername/.icons/Mac4Lin_Icons_v0.4/scalable/places/start-here.png

---

### Post by Epidemic_HardyBoy on 2008-06-10
I think you should look for icon themes on 

[http://Gnome-Look.org](http://Gnome-Look.org)

and go to icons, download the icons you want,

go to system -> preferences -> appearance -> install.

Hope this helps

---

### Post by Locutus_of_Borg on 2008-06-10
/usr/share/icons/THEME_NAME/places/start-here.png is the icon you want to change where THEME_NAME is the theme you are using e.g. Human, Monochrome, Crystal-SVG, etc.

---

### Post by Lantesh on 2008-06-11
Don't overwrite the icon with another one just to change it.  Do it the right way.  Point the object to another icon of your choice.  For example I am using the Ubuntu Menu in Linux Mint, but I wanted the Mint icon instead of the Ubuntu icon.  The procedure was as follows:

Open Configuration Editor. Go to Apps>Panel>Objects> find the one that corresponds to your menu button. Check the use_custom_icon box. Then where it says custom_icon, click to the right of it to put in the path of your desired icon.  The path for the Mint Menu icon is /usr/lib/linuxmint/mintMenu/mintmenu.png

Obviously your icon path will be different, but you get the idea.

---

### Post by Slipminded on 2009-03-31
I have searched the forum for a clear method of changing the logo next to the Applications menu in the panel.  Having not found one I though I would post this here.  I am currently running ubuntu 8.10 64 bit (intrepid) kernel 2.6.27-11-generic
this should work on 32 bit as well

There are two different Applications menus
this is regarding the Menu bar the one with the Applications  Places  System menus on it.
Not the Main Menu that is only Applications
the latter is discussed in this thread.  The Configuration Editor method works well on the Main Menu, however it does not work with the Menu bar
 
How to change gnome applications icon.
check panel size 24x24 32x32 etc.
make image to that size, or scale down one you have.  I used gimp.
copy image to clipboard
check which theme your using under System>Preferences>Appearance
(eg. Human)
open Applications/Accessories/Terminal

	sudo nautilus
	<enter password>

once in nautilus navigate to
filesystem
usr
share
icons
(your current theme)
(your current pixel size (eg. 24x24)
places
rename start-here.png to start-here.png.old (right click > rename)
paste your-image.png 
rename your-image.png to start-here.png
close nautilus
open Terminal again

	killall gnome-panel

close terminal
done



If this doesn't change the logo try to reload the theme by selecting a different one then back to the one you changed.

If your panel is now larger or smaller than it was before not to worry.  Just open nautilus through Terminal again like above.
Navigate back to your image.  Right click to open with gimp.  Once open go to image > scale image.  change the pixel size to correct the issue.  File > Save.  File > Quit
Go through Terminal killall gnome-panel again
panel distortion fixed

---

### Post by EdwinStarr on 2011-02-20
I have been struggling with changing the icon beside Applications for a long time, many hours. I am using Lucid and clearlooks theme. 

This was the default theme when I first installed Ubuntu. I finally figured out that Ubuntu was using the /usr/share/icons/gnome/24x24/places for the start-here.png icon, NOT /usr/share/icons/gnome/scalable/places/.

Then I did the commands:

sudo gtk-update-icon-cache --force /usr/share/icons/gnome/

then

sudo killall gnome-panel

...and presto, the icon changed... finally  :)

later,

EdwinStarr

---

### Post by EdwinStarr on 2011-02-20
Just to clear up my last post on this topic, it seems that the theme clearlooks - in Lucid - was the only theme I was having trouble changing the Ubuntu menu icon. The other themes could be changed easy enough using information at hand on all the forums about this. 

Also, for the clearlooks theme, following Slipminded's post will work except for the folder where clearlooks used start-here.png is in .../24x24/places/.

The png icon file you use should be 24x24 in size. 

It is not that I dislike the Ubuntu icon - now that I know how to change it in the clearlooks theme I may already be missing the Ubuntu icon - it's just the point that I wanted to figure out how to change that icon if I wanted to. I changed it to the gnome-foot.png icon.

I hope others find this helpful.

EdwinStarr

---

### Post by junkie002 on 2013-01-17
Found this thread while googling for this problem.

Just want to chip in with my method using "update-alternatives", check it out:

[http://junktechcorner.blogspot.hu/2013/01/how-to-change-applications-menu-icon-in.html](http://junktechcorner.blogspot.hu/2013/01/how-to-change-applications-menu-icon-in.html)

---

