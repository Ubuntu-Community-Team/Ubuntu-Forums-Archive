---
title: "Mouse theme problems"
date: 2012-11-09
forum: General Help
---

### Post by Gquann on 2012-11-09
Hi I've just installed lubuntu 12.10 a few says ago. I'm not new to Linux but I am a beginner. I'm trying to change the mouse cursor theme but when I choose a theme and click apply the main pointer doesn't change. All the other cursors work like the busy pointer and hovering over a links and all the others. I tried rebooting but the main pointer isn't changed. 

Is there any manual way of changing this? I've searched all over the Internet but u can't find an answer. 

I hope I've given enough information and someone can advise me. 

Many thanks.

---

### Post by vasa1 on 2012-11-09
See if this helps:
[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

---

### Post by Dennis N on 2012-11-09
> **vasa1 said:**
> See if this helps:
[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

Since that old post I wrote cannot be edited, this is some additional explanation:

Where it says 'Create cursor.theme file if needed' it is a text file and looks like this:

```
[Icon Theme]
Inherits=Theme-Name

```
Create it and save it inside the theme's folder. Theme-Name is the exact name you find on the theme's folder.

For Lubuntu, after using galternatives as described, select mouse cursor theme from Customized Look and Feel dialog and possibly log out and back in. It should be working then. (No need for 'advanced settings' tool (gnome tweak) or 'My Unity' with Lubuntu.)

Good luck.

---

### Post by vasa1 on 2012-11-09
> **Dennis N said:**
> Since that old post I wrote cannot be edited, this is some additional explanation:
....
Oh, oh! I've been linking to that old post quite frequently. I guess the present trend is to have such stuff as a wiki.
From what I've seen, it (the mouse cursor theme) is quite a common request.

---

### Post by Dennis N on 2012-11-09
> **vasa1 said:**
> Oh, oh! I've been linking to that old post quite frequently. I guess the present trend is to have such stuff as a wiki.
From what I've seen, it (the mouse cursor theme) is quite a common request.

Well, the information there is still good. "Create cursor-theme file if needed" needs some explanation. 

Also, at the bottom, you don't need 'advanced settings' (gnome-tweak) with Unity any more. The newest version of 'My Unity' tool now works for selecting the mouse cursor without all the extra baggage. Lubuntu needs neither of those.

---

### Post by Gquann on 2012-11-10
Hi guys and thanks for all your help. Unfortunately it doesn't help. I have installed galternatives but still when I change the cursor theme then logout and back in the main cursor stays the same. All the other cursors in that theme work but the main pointer doesn't change to the new theme.

It's not a great big deal but I would like to be able to change the mouse theme properly.

Thanks again for your repies.

Gquann

---

### Post by stinkeye on 2012-11-10
> **Gquann said:**
> Hi guys and thanks for all your help. Unfortunately it doesn't help. I have installed galternatives but still when I change the cursor theme then logout and back in the main cursor stays the same. All the other cursors in that theme work but the main pointer doesn't change to the new theme.

It's not a great big deal but I would like to be able to change the mouse theme properly.

Thanks again for your repies.

Gquann

You need to change both galternatves and the dconf setting.
I don't know if there is a settings program to change the mouse cursor in Lubuntu.
In unity I can use myunity or unsettings.

Try using the terminal command **gsettings**
eg
get your current cursor theme...
```
gsettings get org.gnome.desktop.interface cursor-theme
```

Set your cursor theme ([COLOR="red"]same name as used in galternatives[/COLOR])...
```
gsettings set org.gnome.desktop.interface cursor-theme *[COLOR="Red"]theme-name[/COLOR]*
```

To reset to default if needed...
```
gsettings reset org.gnome.desktop.interface cursor-theme
```
You will need to log out/in to complete.


or you could use **dconf-editor**, navigating to
org.gnome.desktop.interface

---

### Post by Dennis N on 2012-11-10
> **Gquann said:**
> Hi guys and thanks for all your help. Unfortunately it doesn't help. I have installed galternatives but still when I change the cursor theme then logout and back in the main cursor stays the same. All the other cursors in that theme work but the main pointer doesn't change to the new theme.

It's not a great big deal but I would like to be able to change the mouse theme properly.

Thanks again for your repies.

Gquann

If you haven't done so, I suggest you try the same process with another cursor theme as a test. If that works, your problem probably lies in the particular theme, since you say only one cursor type in the theme doesn't show and the others do.

If you want a collection of color cursors that's proven, try Flatbed Cursors from gnome-look.org:

[http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027](http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027)

Good luck.

---

### Post by Gquann on 2012-11-10
> **Dennis N said:**
> If you haven't done so, I suggest you try the same process with another cursor theme as a test. If that works, your problem probably lies in the particular theme, since you say only one cursor type in the theme doesn't show and the others do.

If you want a collection of color cursors that's proven, try Flatbed Cursors from gnome-look.org:

[http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027](http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027)

Good luck.

Thanks for the info. I tried the Flatbed Cursors and again all except the main pointer actually show. I managed to reset back to the default dmz-white theme. It's just the main pointer remains white while when I hover over links and text it is the Flatbed theme.

I have come across something which is odd. When I install a mouse theme pack the customize look and feel closes and I get a message saying it has crashed or something like that. Maybe that will help get some answers.

Thanks for your replies guys.

Gquann

---

### Post by Dennis N on 2012-11-10
> **Gquann said:**
> 
I have come across something which is odd. When I install a mouse theme pack the customize look and feel closes and I get a message saying it has crashed or something like that. Maybe that will help get some answers.

Thanks for your replies guys.

Gquann

If you use the Install button on the Mouse Cursor Tab, I haven't ever used that. Could be a problem there. I have always just directly copied the extracted mouse theme folder I wanted into /usr/share/icons with the terminal. 

Example: Extract theme folder to Desktop, add cursor.theme file if needed. Open terminal and cd to Desktop, then:

sudo cp -r <folder-name> /usr/share/icons

then use galternatives procedure, and finally customized look and feel to select only. 

Might be worth a try.

---

### Post by Gquann on 2012-11-10
> **Dennis N said:**
> If you use the Install button on the Mouse Cursor Tab, I haven't ever used that. Could be a problem there. I have always just directly copied the extracted mouse theme folder I wanted into /usr/share/icons with the terminal. 

Example: Extract theme folder to Desktop, add cursor.theme file if needed. Open terminal and cd to Desktop, then:

sudo cp -r <folder-name> /usr/share/icons

then use galternatives procedure, and finally customized look and feel to select only. 

Might be worth a try.


Hi, thanks for that. It still isn't working. When I change the icon theme in galternatives all that happens is the main cursor turns from white to black and then from black to white when I change it again. All the other pointers in the theme stay the same as if I hadn't changed them.

I'm getting very confused with all this. I'm trying to make logical sense of what I'm doing but it just doesn't add up. Why would all except one cursor in a theme change? Why does the cursor change from dmz-white to dmz-black when I choose Flatcursor theme in galternatives? (those are kind of rhetorical questions) I've spent hours trying to get this to work :? I think I may just stick with what it's stuck with at the moment. I just wish I could work it out. 

Thanks for the tips.

Gquann

---

### Post by Dennis N on 2012-11-10
> **Gquann said:**
> Hi, thanks for that. It still isn't working. When I change the icon theme in galternatives all that happens is the main cursor turns from white to black and then from black to white when I change it again. All the other pointers in the theme stay the same as if I hadn't changed them.

Gquann

Check your typing carefully in the cursor.theme file. It is all case sensitive (capital and lower case letters matter). 

Example: If you are installing Flatbed Cursors Blue large size,

[B][Icon Theme]
Inherits=FlatbedCursors.Blue.large[/B]

is NOT the same as:

[B][Icon Theme]
Inherits=FlatbedCursors.Blue.Large[/B]

I have made this mistake, and it can be hard to detect. The cursor will not change completely unless you match the folder name exactly. Only the second version will work.

After using galternatives, be sure to hit **Apply** when selecting cursor in "Customized Look and Feel" and then log out and back in.

---

### Post by Gquann on 2012-11-11
> **Dennis N said:**
> Check your typing carefully in the cursor.theme file. It is all case sensitive (capital and lower case letters matter). 

Example: If you are installing Flatbed Cursors Blue large size,

[B][Icon Theme]
Inherits=FlatbedCursors.Blue.large[/B]

is NOT the same as:

[B][Icon Theme]
Inherits=FlatbedCursors.Blue.Large[/B]

I have made this mistake, and it can be hard to detect. The cursor will not change completely unless you match the folder name exactly. Only the second version will work.

After using galternatives, be sure to hit **Apply** when selecting cursor in "Customized Look and Feel" and then log out and back in.

Thanks for the info. I think maybe I'm not understanding how to do it. I've extracted the main folder out of the flatbed cursor tar.bz2 file then I put one of the folders withing the main folder into usr/share/icons. Within the folder FlatbedCursors.Blue.Regular is a cursors folder and and index.theme file. The index.theme doen't have inherits= in there. Do I need to type that in there?

I'm very new to doing things in terminals and not using the gui. I'm spoiled by windows but I'm trying to learn this stuff.

Thanks.

---

### Post by Gquann on 2012-11-11
Quick update: I put the Inherets= and managed to get the cursor theme to work. But..... when I logged back in, the terminals no longer work. Have you had any problems with the terminals crashing. I cannot get any terminals up now.

Could you suggest any way of fixing this? I rebooted which didn't help.

Thanks.

---

### Post by Gquann on 2012-11-11
Another update to say that I've worked out the problem. I basically had to create a file called cursor.theme and put the lines Inherets= and then the cursor type. Then I copied the theme folder into /usr/share/icons/ then went into galternatives and added the cursor.theme that I just created. After that went into customize look and feel and clicked on the theme then logged out and back in.

The problem I had with the terminal crashing seemed to be caused by editing the index.theme. I'm not sure why but there you go!!

So thanks for all the input you gave. It definitely helped.

Gquann.

---

### Post by Dennis N on 2012-11-12
The index.theme should not be changed. The cursor.theme file is a new file made with a text editor and saved in the theme folder.

I hope it worked for you.

---

### Post by begtognen on 2013-02-09
Thank you SO much - after hours of trying to change the mouse cursor size I was beginning to think this was impossible. But this worked beautifully. 

(Install Flatbed Cursors Huge directory in /usr/share/icons, create cursor.theme file, put it in the same directory, add cursor.theme in Galternatives and change the cursor theme in Custom Look and Feel, then reboot.)

---

### Post by na5m on 2013-05-25
[FONT=courier new]Just a third-party verifier here [/FONT]:KS .....[FONT=courier new] this wonderful thread is totally [SOLVED]!  I had the exact same problem as the OP.
Follow this thread to the letter & you'll get the nice fat mouse pointer that you crave.
[/FONT]
[FONT=courier new]un-TAR  **FlatbedCursors-0.3.tar.bz2** into the **/usr/share/icon** folder (you'll probably need root rights).
This folder should now look similar to:
[/FONT][IMG]http://i1122.photobucket.com/albums/l532/na5m/point3_zpse09c88c2.png[/IMG][FONT=courier new]
[/FONT]
Then **touch** a file and name it **cursor.theme**. Now the icon folder will look similar to:
[IMG]http://i1122.photobucket.com/albums/l532/na5m/point1_zps8b14581d.png[/IMG]

Edit **cursor.theme** to look something like:
[IMG]http://i1122.photobucket.com/albums/l532/na5m/point2_zpsac6d2174.png[/IMG]

---

### Post by Dennis N on 2013-05-25
**Comment**: With 13.04 Xubuntu and Lubuntu releases (likely 12.10 also), you probably don't need to do anything after using the "Alternatives Configurator" (galternatives) utility as described. The cursor theme changed with that alone, and selection in the appearance or theme dialog wasn't really needed. 

[this comment added since the earlier posts here cannot be edited after a period of time.]

---

