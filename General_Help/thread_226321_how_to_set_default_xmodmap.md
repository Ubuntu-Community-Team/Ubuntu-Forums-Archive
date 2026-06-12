---
title: "how to set default xmodmap?"
date: 2006-07-31
forum: General Help
---

### Post by it.henrik on 2006-07-31
The first thing I have to do every time I log in to my ubuntu-box is to run 
```

xmodmap /usr/share/xmodmap/xmodmap.se
```

I used to have wy sweet sweet swedish keyboard layout as default but it stoped working after I tried a xgl+compiz howto in the forums here.

please help me get my swedish keyboard layout back as default :)

---

### Post by ckempo on 2006-07-31
If you've got a compiz statup script being called in your startup list, you can add a similar in there to alter your keyboard layout.

Here's my file (called /usr/bin/compiz-start):

--START--
killall cgwd
wait
xmodmap /usr/share/xmodmap/xmodmap.uk &
cgwd &
compiz --replace gconf &
---END---

If you do something similar (change the cgwd for gnome-window-decorator if you're using that instead) and set the "xmodmap.uk" bit to "xmodmap.se" then your keyboard will be fixed.

---

### Post by it.henrik on 2006-07-31
Thnx for the reply :)

Where can I find my startup list?

---

### Post by ckempo on 2006-07-31
System>Preferences>Sessions - then the startup tab.
If you've followed the XGL walkthroughs, most of them have you place a startup script in there. The script itslef is usually in somewhere like /usr/bin though (that's where i've put mine anyway).

Are you still using XGL?  If not, am sure there's an easier way to just default your system to your specific keymap rather than change it automatically on login... though I'm not sure how yet

---

### Post by ckempo on 2006-07-31
Or thinking about it, of course, if you're not using XGL and thus don't have a script running on start up that makes the amendments, then there's nothing wrong with simply putting the "xmodmap /usr/share/xmodmap/xmodmap.se" line into your startup list, that will work I think.

---

### Post by it.henrik on 2006-07-31
I removed compiz .. but I think im still running xgl.

I tried to put the right modmap in the sessions-startup list .. didnt help at all. :( 

I did put it in my .bashrc .. and it works most of the times .. I still have to go to the system-preferences-keyboard and toggle with the settings there a few times to get some keys like alt and } and \ to work. All I do is to check and uncheck the checkbox next to my swedish layout .. and if that doesnt do the trick I sometimes adds the british layout and remove it again .. usually that works .. and if that doesnt do the trick I kill X and then it might work .. 

its so strange cause there is no consistency in the behaviour .. :/ ?

---

