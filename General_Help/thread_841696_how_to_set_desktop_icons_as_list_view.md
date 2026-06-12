---
title: "how to set desktop icons as list view"
date: 2008-06-26
forum: General Help
---

### Post by spacepirates on 2008-06-26
OK, i am fairly sure that this must be possible to do, as nautilus manages the desktop and nautilus can set the default view to list view.

my question is how to make the desktop icons look like a list, as in, smaller icons, closer together, and with text to the right of the icon.

another thing i am looking to do is set a max character limit on the file names of desktop icons so that a file named "really_long_file_name.extension" might appear as "really_long..."

---

### Post by cosine352 on 2008-12-03
I am also interested in this.:D

---

### Post by ghosthere on 2009-02-09
Me too! The list on the right with the text on the left would look nice as well.

---

### Post by UbuntuNerd on 2009-02-09
Ok try this, in a terminal type:
```
gconf-editor
```
next click on Apps > nautilus > icon view.
see if any of the settings in this section are what you looking for.

---

### Post by syn4k on 2009-05-04
In your terminal:
# Default view type
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_view "list_view"
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer "list_view"

# Default icon view size
gconftool-2 --type string --set /apps/nautilus/icon_view/default_zoom_level "smaller"

Done.
Full source: [http://nettekk.com/downloads/tools/ubuntu/setup](http://nettekk.com/downloads/tools/ubuntu/setup)

---

### Post by Dreamsellerlb on 2009-05-04
I tried this, it didn't work the way I was hoping.  Has anyone else had any luck?

---

### Post by syn4k on 2009-05-20
My post, right before yours works flawlessly.):P

---

### Post by noice742 on 2009-05-21
Thanks syn4k. That worked out just great for me. Thank you so much! :D

---

### Post by jurialmunkey on 2009-06-22
> **syn4k said:**
> In your terminal:
# Default view type
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_view "list_view"
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer "list_view"

# Default icon view size
gconftool-2 --type string --set /apps/nautilus/icon_view/default_zoom_level "smaller"



Nope this doesn't work (not on Jaunty anyway)... makes the icons smaller and that's it. There are easier ways to make the icons smaller. The big question is how to get the text to be on the right or left of the icons like a list rather than underneath.


------------------------------// EDIT **
I'm currently using global-menu in gnome. When on the desktop, you can see the nautilus menus. It appears that for the desktop nautilus is locked into "Desktop" display mode and changing to icon, list or compact does nothing - even with a restart. Even with the text beside icons option checked, nautilus still displays desktop icons with text underneath and not beside. 

This was one of the main reasons I use to use Tclock2 in windows. It had a function to set all icon sizes to 16x16 with text besides. With all the ability to customise in Ubuntu/Gnome, it seems ridiculous that there is so little control over nautilus' display of the desktop even though it has the ability to do so. Is this a paper cut that will never be healed?

---

### Post by MrLeap on 2009-07-07
I've been cracking at this for hours, I really want this to work. :(

---

### Post by Donalb on 2009-07-27
On Windows (sorry about that) there is a great freeware prog called Pitaschio (note slightly weird spelling) that allows you to change the desktop icons to List view (amongst a whole host of options).
I entered the lack of this option on 'Buntu desktop as a launchpad bug about a year ago, but there's no action on it.
I would LOVE to be able to use this option, I hate Icon view, List View is much tidier and quicker (for me).
Any chance anyone who got this potential fix working could post a Screenshot of the working change, so we could see if it's what's we are looking for?

Cheers

---

### Post by Donalb on 2009-07-27
The best I can do is stop displaying Mounted Volumes as visible, set Zoom Level to Smaller, Text Ellipsis Level to [0] from [3]. Labels beside icons seems to have no effect. If I set Zoom level to Smallest then the bloody text goes all over the place.

Screenshot attached:


Cheers

---

### Post by syn4k on 2009-10-20
Please make sure I do not cover this previously...

---

### Post by Donalb on 2009-10-20
Hey Syn4k,

As Jurielmunkey said earlier in the thread:
"Nope this doesn't work (not on Jaunty anyway)... makes the icons smaller and that's it. There are easier ways to make the icons smaller. The big question is how to get the text to be on the right or left of the icons like a list rather than underneath."

See the snapshot of my desktop in my previous post. Can you post a snapshot of your desktop if you've managed to set it up differently, as an actual list?

Thanks

---

### Post by syn4k on 2009-10-20
My apologies,
I spent a few minutes poking around and found a fix for this which was created by somebody else. The fix requires modifying a c language source file for Nautilus....Check it out here: [http://oi3prnnx.deviantart.com/art/The-New-Nautilus-Desktop-138405468](http://oi3prnnx.deviantart.com/art/The-New-Nautilus-Desktop-138405468)

I did not use the patch because it complained so I instead manually modified the code myself and then cd to src to compile it.

You'll need a c compiler before you do anything...
sudo apt-get -y install libc6-dev g++ gcc

I can confirm that this works as I tested it on my computer as well.
Here is a screenshot of my computer desktop: [http://img15.imageshack.us/img15/4872/screenshotax.png](http://img15.imageshack.us/img15/4872/screenshotax.png)

I found the original information at: [http://ubuntuforums.org/showthread.php?t=1230822&page=3](http://ubuntuforums.org/showthread.php?t=1230822&page=3)
:popcorn:

---

### Post by Donalb on 2009-10-20
Hey Syn4k,

Thanks very much. 
On the good, this shows it's possible. 
(I never thought of searching "text beside icons", I  was searching "list view on desktop" or somesuch).
When it comes to  modding code, that's outside my scope, but I'll try the suggested link and see how it goes...I can cut & paste with the best of 'em. 

Thanks again, pity the "Thanks" button is gone!

Donal

---

### Post by syn4k on 2009-11-01
I created this script to do it all for you...
[http://nettekk.com/index.php?action=content_view&id=218](http://nettekk.com/index.php?action=content_view&id=218)
:popcorn:

---

### Post by Donalb on 2009-11-02
Thanks very, very, very much for your effort here Syn4k!

I waiting to swap & clone my (failing) HDD (if the courier arrives) and then install Karmic today so I hope to try this within the next 2 days. 

Appreciate it very much. Will revert to you when I have it done...


d

---

### Post by ww2 on 2009-12-29
> **syn4k said:**
> I created this script to do it all for you...
[http://nettekk.com/index.php?action=content_view&id=218](http://nettekk.com/index.php?action=content_view&id=218)
:popcorn:

Your script works wonderfully. Thanks!

---

### Post by Donalb on 2009-12-29
Finally got back to this myself last week and yes the script works great. thanks for the effort.

At the risk of sounding ungrateful, _which I'm not_, I'd like to tweak it further.
Currently the icons are various sizes, depending on the application.
Text and OOo docs have the text the approx same size as the text. However PDFs & html files have a much larger icon.(See attached).
If I shrink the icon size (from currently smaller, to smallest) the text also shrinks and actually becomes invisible.

So, is there any way to shrink the default size for PDF's & html?

---

### Post by debili on 2010-05-28
anybody who still has the script ? the appears to be dead already...

thanks a lot

---

### Post by syn4k on 2010-08-17
Ask Donalb,
I gave him a copy. I hosted it on a file sharing website but they removed the file...

---

### Post by Donalb on 2010-08-17
Here it is. Rapidshare.
```

http://rapidshare.com/files/413530833/nautilus_desktop_icon_list_view_mod_script.zip.html
```

---

### Post by reuf on 2012-10-20
Solved here:
[http://askubuntu.com/a/203871/77361](http://askubuntu.com/a/203871/77361)

Text besides icons on Ubuntu Desktop

1-$ mkdir /home/nautilus-source & cd /home/nautilus-source

2-$ apt-get source nautilus #in my case it downloaded source for nautilus-3.4.2

3-$ sudo apt-get install fakeroot build-essential dpkg-dev

4-$ sudo apt-get build-dep nautilus

5-$ cd /home/nautilus-source/nautilus-3.4.2/

6-$ vim src/nautilus-desktop-icon-view.c

7-$ /NAUTILUS_TYPE_DESKTOP_ICON_VIEW

Change from:

g_object_new (NAUTILUS_TYPE_DESKTOP_ICON_VIEW, "window-slot", slot, "supports-zooming", **FALSE**, "supports-auto-layout", FALSE, "supports-scaling", TRUE,"supports-keep-aligned", TRUE, "supports-labels-beside-icons", **FALSE**, NULL);

to:

g_object_new (NAUTILUS_TYPE_DESKTOP_ICON_VIEW, "window-slot", slot, "supports-zooming", **TRUE**, "supports-auto-layout", FALSE, "supports-scaling", TRUE,"supports-keep-aligned", TRUE, "supports-labels-beside-icons", **TRUE**, NULL);

Line numbers in in src/nautilus-desktop-icon-view.c > 785-792

8-$ dpkg-buildpackage -rfakeroot -us -uc -nc -b

9-$ sudo dpkg -i ../nautilus_3.4.2-0ubuntu4_i386.deb

10-$ killall nautilus

11- Open your home folder from launcher -

12- Edit > Preferences > Views > Check Text Besides Icons

ps. also now Ctrl+Scroll - will zoom in zoom out desktop icons

ps2. you can also change location of launcher # edit src/nautilus-places-sidebar.c

[IMG]http://i.stack.imgur.com/bL8Ij.png[/IMG]

---

