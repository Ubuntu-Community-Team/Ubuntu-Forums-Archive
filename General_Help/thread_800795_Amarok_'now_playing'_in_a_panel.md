---
title: "Amarok 'now playing' in a panel?"
date: 2008-05-20
forum: General Help
---

### Post by misshannah on 2008-05-20
First off sorry if this is in the wrong spot.

I've got ubuntu 8.04 and I'm using Amarok as my music player. I'd love to get the now playing and a play/pause/next track kind of display up into one of the panels alongside things like date/time etc.
I'm new to Ubuntu so was just wondering if this is possible and/or how to do it.
Thanks.

---

### Post by meganox on 2008-05-20
I assume you are using Ubuntu with the default Gnome desktop and not Kubuntu with the kde desktop?  Since Amarok is a kde app, I don't think this will be possible, but I'd love for someone to prove me wrong.

---

### Post by misshannah on 2008-05-20
Yep, I'm using the gnome desktop. I hope someone proves you wrong too!

---

### Post by BatPenguin on 2008-05-20
Try looking for a screenlet that does that. I'm not sure but I think there was either a "now playing" screenlet or a "amarok screenlet" that shows the current song. That should work in Gnome.

Post here if you find it, I'd be interested too but don't have time to look now :)

---

### Post by Tiede on 2008-05-20
Amarok being a KDE app should cause you no problem at all for that. The only downsize is a longer starting time ti get the kde-specific background processes up and running (unless you already have others.)
A screenlet would show up on the background, I believe, so maybe that's not what you are looking for. If you want them to be on the panel, I believe small scripts calling up the program's specific next/play/pause/back functions should work. I am going to make some universal ones (i.e not amarok specific) test them on a few multimedia apps and post.
I like this idea, so I might end up using them as well!
Can't promise anything on ETA though, cause i have class coming up. But I'll do my best (providing I don't forget... ;) )

---

### Post by Tiede on 2008-05-20
I have good and bad news.
Bad news first: Since I am planning on making this application-independent, it may take me a while, cause I will have to actually do some scripting :(
I like too, but now I have to go research for the commands (oh man!)
So, this will come later on.
Good news: Since I **know** misshannah's app, here's a workaround for him.
Alright misshannah, let's have some fun.
Right-click on a panel - preferably where you'd like your buttons to appear- and select add to panel.

now select the first entry in the window that pops up (should be something along the lines of "Custom Application Launcher" -might vary, as I am translating from French...)
Click the "+Add" button.
A smaller window opens.
Leave the type alone (should be Application by default)
[LIST]
[*]In **name**, type in Skip Backwards.
[*]In **command**, type in: amarok --previous
[*]If you want to add a comment, you can do so in the **comment** field.
The comment will show up every time your mouse passes over the newly created button in the panel, so make it relevant. Something like 'Skip backwards' or 'Rewind' should work.
You'll notice the icon is set to Amarok's by default. We don't want that. (would get a little confusing.)
[*]Click on the icon box, copy and paste the following in the address bar of the new window (should be saying something like /usr/share/icons/sometheme/amarok)
```
/usr/share/icons/Tango/scalable/actions/gtk-media-previous-ltr.svg
```
press enter.
[*]Click OK (or Apply) in your add launcher window, and your new shiny skip backwars button should be on the panel!
[/LIST]
Repeat the same thing for the other 4 buttons, replacing --previous with
--play, --pause, --next and --stop
same for the icons. Just change /usr/share/icons/Tango/scalable/actions/gtk-media-**previous**-ltr.svg to what you need, as in:
/usr/share/icons/Tango/scalable/actions/gtk-media-**play**-ltr.svg for the play icon, and so on and so forth.

Enjoy your new panel buttons!
(Yeah, that was quite a work-out)

---

