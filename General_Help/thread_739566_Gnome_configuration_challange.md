---
title: "Gnome configuration challange"
date: 2008-03-29
forum: General Help
---

### Post by deb on 2008-03-29
I want to do a very basic thing in gnome, after an hour of fighting with gconf editor i thought it will be much simpler to as the comunity. Please have a look at the snapshot attached. I would like to change the default black colour of the main menu text, switcher text and the applet text. Is there any way I can do it? It will be a geat help if any one can point a thread or post...

---

### Post by fragos on 2008-03-29
I'd love to do the same but haven't found a way.

---

### Post by ibuclaw on 2008-03-29
```
 sudo apt-get install gnome-color-chooser 
```

Then open
System>Preferences>GNOME Color Chooser

Hope this is the effect you want (Top and Bottom Panels)

[[IMG]http://img410.imageshack.us/img410/1635/screenshotqt7.th.png[/IMG]](http://img410.imageshack.us/my.php?image=screenshotqt7.png)

That wasn't hard, now was it? :lolflag:

Regards

---

### Post by deb on 2008-03-29
WOW... that is something... this tool exists!!!!!!!!!!:o
I was going this way [http://therantman.wordpress.com/2007/07/12/how-to-change-the-gnome-panel-text-colour/](http://therantman.wordpress.com/2007/07/12/how-to-change-the-gnome-panel-text-colour/)
now why doesn't it come as default with ubuntu?:confused:

but the puzzle is not completely solved look at the snapshot below...:-k

---

### Post by Bubba64 on 2008-03-30
I couldn't get the gnome color chooser to download in Gutsy, but it is in synaptic in Hardy and works great.

---

### Post by Cresho on 2008-03-30
> **deb said:**
> WOW... that is something... this tool exists!!!!!!!!!!:o
I was going this way [http://therantman.wordpress.com/2007/07/12/how-to-change-the-gnome-panel-text-colour/](http://therantman.wordpress.com/2007/07/12/how-to-change-the-gnome-panel-text-colour/)
now why doesn't it come as default with ubuntu?:confused:

but the puzzle is not completely solved look at the snapshot below...:-k

Gnome wants to make things easier on us.  They want us to function better and not fiddle too much with the operating system.  They give you the option to go beyond simple if you want.

Try Devil's pie

[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)

Here is a debate about kde and gnome.  I use both and submit bugs for kde4

[http://www.lockergnome.com/blade/2007/02/20/linuxlinusgnome-users-are-idiots-mentality/](http://www.lockergnome.com/blade/2007/02/20/linuxlinusgnome-users-are-idiots-mentality/)

---

### Post by deb on 2008-03-31
So I guess no one has been able to change the text color of fast user switch applet in gnome? come on guys... i know you can do it...

---

### Post by ibuclaw on 2008-03-31
It appears that the Fast-User-Switch-Applet requires its own unique line to do it.
(sigh)

open up .gtkrc-2.0 in a text editor:
ie:
```
 nano ~/.gtkrc-2.0 
```

And you will see this (if you have gnome-colour-chooser installed)
```
 include ".gtkrc-2.0-gnome-color-chooser" 
```
That line includes all your gnome-colour-chooser settings. So leave it!

Now, all we need to do is add this below it.
```

style "fusa"
{
 fg[NORMAL] = "#FFFFFF"
}
widget "*fast-user-switch-applet*" style "fusa"

```
fusa is an acronym of "fast-user-switch applet", you can rename it to whatever you want.

[[IMG]http://img388.imageshack.us/img388/3763/screenshotee4.th.png[/IMG]](http://img388.imageshack.us/my.php?image=screenshotee4.png)

Regards
Iain

[EDIT]
Oh, and by the way.
```
 killall gnome-panel 
``` to restart the panel and see your changed settings.

---

### Post by deb on 2008-04-02
You Rock!!! :-D

---

