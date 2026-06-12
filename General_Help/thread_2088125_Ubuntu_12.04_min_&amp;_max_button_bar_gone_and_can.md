---
title: "Ubuntu 12.04 min &amp; max button bar gone and can't resize icons"
date: 2012-11-25
forum: General Help
---

### Post by 4tomic on 2012-11-25
Hi guys, I was having a good ol' time and thought I ought to give compiz a whirl... see if it was up-to-snuff with Unity yet... sure enough my GUI was broken in seconds. So now to trouble shoot myself back to normal. I read all the forums and tried replacing metacity and compiz. I notice the following when I try to replace metacity : 

Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_2"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_3"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_1"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_4"

Also, my graphics card isn't showing up in my "details". These are my comp details:
[Asus-14-U43F-Core-i5]("http://hothardware.com/Reviews/Asus-14-U43F-Core-i5-Notebook-Review/")

I'm a bit of a noob with linux, so don't lay it on me too heavy...

-----------------------------------edit----------------------------
By the way, I was messing with the cube when it all started to go wrong.

---

### Post by personalpc on 2012-11-25
Ctrl+alt+F1

login with username and password

sudo apt-get install gnome-session-fallback

sudo shutdown -r now

when it boots back up select gnome classic from the drop down list with no effects. that should disable compiz then you can edit your config files or dpkg-reconfigure compiz-core or dpkg-reconfigure -a

---

### Post by daslinkard on 2012-11-25
> **4tomic said:**
> Hi guys, I was having a good ol' time and thought I ought to give compiz a whirl... see if it was up-to-snuff with Unity yet... sure enough my GUI was broken in seconds. So now to trouble shoot myself back to normal. I read all the forums and tried replacing metacity and compiz. I notice the following when I try to replace metacity : 

Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_2"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_3"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_1"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_4"

Also, my graphics card isn't showing up in my "details". These are my comp details:
[Asus-14-U43F-Core-i5]("http://hothardware.com/Reviews/Asus-14-U43F-Core-i5-Notebook-Review/")

I'm a bit of a noob with linux, so don't lay it on me too heavy...

-----------------------------------edit----------------------------
By the way, I was messing with the cube when it all started to go wrong.

The easiest thing to do is to reset your unity and start over....
```

unity --reset
```

Have fun tweaking, breaking, fixing, tweaking, breaking, fixing your machine...it's the best part!

---

### Post by 4tomic on 2012-11-26
> **daslinkard said:**
> The easiest thing to do is to reset your unity and start over....
```

unity --reset
```

That's interesting, I had tried that reseting several times earlier with no luck, but after you suggested it I gave it one more try and it seems to have worked. Everything is fine now... *knock on wood*

I think I'm done experimenting for a bit.  I'm actually traveling and using this laptop as my work computer... I had 2 months of work (thesis and website SRS) on this machine and it wasn't until things went south that I remembered "I have that work ONLY on this machine!" Needless to say I learned my lesson and moved everything into cloud storage... but still, I'll wait til I am back home to mess around more.

Personalpc, thanks for your reply too. I didn't try it, but switching to gnome was a good idea. I'll save it away as something to remember for next time.

Anyways, I wonder if compiz will ever run smoothly with unity. I'd love to see a compiz-light that cut off all the excess and concentrated on supporting just a few of the best features. I'm not looking for lots of customizablity or improved usability, just one or two really flashy things that remind everyone else how boring their Windows/Macs are. Oh well... I guess I do have the HUD. And I'm loving how stable and fast 12.04 has been (as long as I suppress my urge to experiment too much).

---

### Post by daslinkard on 2012-11-26
> **4tomic said:**
> That's interesting, I had tried that reseting several times earlier with no luck, but after you suggested it I gave it one more try and it seems to have worked. Everything is fine now... *knock on wood*

I think I'm done experimenting for a bit.  I'm actually traveling and using this laptop as my work computer... I had 2 months of work (thesis and website SRS) on this machine and it wasn't until things went south that I remembered "I have that work ONLY on this machine!" Needless to say I learned my lesson and moved everything into cloud storage... but still, I'll wait til I am back home to mess around more.

Personalpc, thanks for your reply too. I didn't try it, but switching to gnome was a good idea. I'll save it away as something to remember for next time.

Anyways, I wonder if compiz will ever run smoothly with unity. I'd love to see a compiz-light that cut off all the excess and concentrated on supporting just a few of the best features. I'm not looking for lots of customizablity or improved usability, just one or two really flashy things that remind everyone else how boring their Windows/Macs are. Oh well... I guess I do have the HUD. And I'm loving how stable and fast 12.04 has been (as long as I suppress my urge to experiment too much).

Sweet...I'm glad you were able to get this corrected....if you would, please mark this thread as solved and just know that any time you need anything that we are here for you in the forums!

---

