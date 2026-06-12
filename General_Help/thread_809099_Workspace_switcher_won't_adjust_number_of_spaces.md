---
title: "Workspace switcher won't adjust number of spaces"
date: 2008-05-27
forum: General Help
---

### Post by RheaHS on 2008-05-27
Tried several times, but nothing happening. I have no idea what to try to actually get it working, have tried getting rid of compiz and fusion, but that's the only idea I had. Tried the other one too, OSD applet, same problem.

---

### Post by justleen on 2008-05-27
I've seen this at a friends place.. we fixed it there by creating a whole new profile..
to "test"  wether this will work, create a (new) test user, and login as this test user. if the workspaces work, there is something wrong with the profile..
press CTRL-ALT-F2 to go to a terminal:
```

sudo /etc/init.d/gdm stop
sudo su
cp /home/user /home/user.old
mkdir /home/user
chown user:user /home/user
/etc/init.d/gdm start

```
afterwards you can copy data/settings from the old dir (like the .mozzila or thunderbird  contents.

maybe overkill, but it worked..

---

### Post by RheaHS on 2008-05-27
And if it does turn out like that, how do I fix the profile?

---

### Post by RheaHS on 2008-05-27
It worked on the new profile, I found out that the dialogue saying the workspace names etc was missing, as well as the "show current only" part. All I have is "Workspaces, columns and rows"

---

### Post by justleen on 2008-05-27
you could try to delete just the .gconf .gnome .gnome2  folders in your home folder (create a copy first!), but creating a whole new home folder might be the way out..

---

### Post by RheaHS on 2008-05-27
creating a new home folder means I lose everything though, i've got too much on there to do that.

---

### Post by justleen on 2008-05-27
no, you dont lose anything.. 
you create a copy.. It just a bit more clicking to get everything out of your old folder in to the new folder..

---

### Post by RheaHS on 2008-05-27
Hmm, you mean creating a new home directory while you're logged in as you? I may sound stupid, but how do you do that, since I'm guessing it's a system folder.

---

### Post by Arthur Archnix on 2008-05-27
Let's just go over the basics one more time. We're talking about the Workplace switcher right? Sits in the panel and lets you change workspaces? If so, let's take compiz out of the equation for a moment and hit Alt+F2, then 
```
metacity --replace
```
Now, if you've already got a workspace switcher in your taskbar remove it. Now, replace it with a new one. Right-click, choose add to panel, choose workplace switcher. Trust me, I had one in my taskbar that wouldn't let me change number of workspaces, removing it and adding a new one fixed it.

Now you should be able to right-click on the workspace changer and choose properties, and change the number of workspaces. Yes, no? 

Another thing you can try is to open gconf-editor (alt+f2 then type "gconf-editor" without quotes) and search for this key:
> /apps/metacity/general/num_workspaces
Try changing that directly to set the number of workspaces.

---

### Post by RheaHS on 2008-05-27
metacity --replace worked. Thanks so much, I'm still getting acquainted totally with this.

---

### Post by Arthur Archnix on 2008-05-27
Unfortunately I don't have compiz installed on my system. I still believe it's too buggy to be included as a default window manager, but the masses obviously disagree. Anyway, now you know the source of the problem it shouldn't be too hard to search for people having the same problem with terms like "compiz + workspaces" or "compiz can't change number workspaces". 

If you just like having a little bling you can enable some basic compositing effects with metacity (which also supports things like the Avant Window Manager - that mac like bar at the bottom). Just search for "compositing_manager" in gconf-editor (check key names) and put a check mark in the appropriate box.

Unfortunately, you either have to fix compiz or switch to metacity. Right now, everytime you reboot you're going to land in compiz and have a broken workspace switcher. If you just want to switch then once again in gconf-editor search for "window_manager" and check key name, then change the /usr/bin/compiz the one that says default, not current, change compiz to metacity. So it says /usr/bin/metacity

That's it. Next time you restart metacity will be your window manager.

---

