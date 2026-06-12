---
title: "Gnome panel messed up"
date: 2018-03-01
forum: General Help
---

### Post by raleigh3 on 2018-03-01
After installing a game, it messed up my gnome panel.

  
On the far left used to be an icon for shutdown etc, then the date, and my battery icon.

  Can it be repaired?

---

### Post by #&amp;thj^% on 2018-03-01
> **raleigh3 said:**
> After installing a game, it messed up my gnome panel.

  
On the far left used to be an icon for shutdown etc, then the date, and my battery icon.

  Can it be repaired?
EDIT: Just now tried this for **"just the gnome-panel"** and it worked:
```
dconf reset -f /org/gnome/gnome-panel/
killall gnome-panel
```
Good Luck ;)
I would first back-up your settings!
There isn't a great solution but this may do the job or most of it.

```
dconf reset -f /org/gnome/
```

Then log out/in
Oh, just to be safe (e.g., in case you broke something), you can reset **"all"** the gnome settings with:
```
dconf reset -f /
```
****Warning**This will reset all settings to default.**

---

### Post by kerry_s on 2018-03-01
just right click the panel-> panel preferences-> add

select what ever & move it back where you want it.

---

### Post by raleigh3 on 2018-03-01
Not everything can be moved. Like volume for one.

---

### Post by #&amp;thj^% on 2018-03-01
> **raleigh3 said:**
> Not everything can be moved. Like volume for one.

Just so I'm clear here, is this gnome-panel or Mate Panel?

---

### Post by kerry_s on 2018-03-01
> **raleigh3 said:**
> Not everything can be moved. Like volume for one.

volume is just an indicator app, if you right click on that, you'll have settings for that, you can use the arrows in the setting to reorder the indicators.

---

### Post by raleigh3 on 2018-03-01
> **1fallen said:**
> Just so I'm clear here, is this gnome-panel or Mate Panel?

It's mate panel.

I tried deleting the panel and recreating it.

It was a mess, so I restored a Clonezilla image.

If there is a config file for the Mate panel that I could back up, I could restore it the next time it occurs. :-)

---

### Post by kerry_s on 2018-03-01
in the file manager press ctrl+h to show hidden
there should be a folder named ".config" in that folder there should be a mate-panel folder. if i remember right, it's been awhile since i last used mate desktop.

---

### Post by #&amp;thj^% on 2018-03-01
> **raleigh3 said:**
> It's mate panel.

I tried deleting the panel and recreating it.

It was a mess, so I restored a Clonezilla image.

If there is a config file for the Mate panel that I could back up, I could restore it the next time it occurs. :-)
See how a thread title can be important **"Re: Gnome panel messed up"** there is a difference between the two! (Please Amend your Title with "Mate-Panel")
Give this a whirl then:
```
mate-panel --reset --replace
```
> **kerry_s said:**
> in the file manager press ctrl+h to show hidden
there should be a folder named ".config" in that folder there should be a mate-panel folder. if i remember right, it's been awhile since i last used mate desktop.

+1

---

### Post by raleigh3 on 2018-03-01
I just found that in Mate Tweak there is an option to Save Panel Layout.


  Is that would i would need to restore my panel?

  
If so, do I just replace the corrupt one with the backed up one?

---

### Post by #&amp;thj^% on 2018-03-01
> **raleigh3 said:**
> I just found that in Mate Tweak there is an option to Save Panel Layout.


  Is that would i would need to restore my panel?

  
If so, do I just replace the corrupt one with the backed up one?

I just don't know, but it should!
I just use CLI  and not many GUI's
And you can always **"copy"** your .config folder to another directory for use as a back-up or other problems.

---

### Post by raleigh3 on 2018-03-01
I found out that you can use Mate Tweak to backup and restore custom panels.

---

### Post by #&amp;thj^% on 2018-03-01
> **raleigh3 said:**
> I found out that you can use Mate Tweak to backup and restore custom panels.

That's Great, happy to hear.
BUT  (Please Amend your Title with "Mate-Panel") it helps users when searching.
Cheers

---

