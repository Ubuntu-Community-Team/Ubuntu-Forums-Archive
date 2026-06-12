---
title: "Firefox plugin preference:  mplayerplug-in &gt; totem"
date: 2006-10-30
forum: General Help
---

### Post by DNAspark99 on 2006-10-30
Upgraded to edgy and most things went smooth. 
Turns out I'm not a fan of firefox2 (yet), so the quickest way to revert back for me was to download the tarball from mozilla, and put it in /opt/firefox-1.5.0.7. I wrestle with getting my plugins working again until I realize I just need to symlink /usr/lib/firefox/plugins to /opt/firefox-*/plugins - bingo, I've got my plugins back. My questions is, mpg, avi, wmv etc, all default to using the totem plugin - but I prefer mplayerplug-in - so how do I change this 'default' behavior? There must be an easy way, without having to remove the totem plugin? thanks!

---

### Post by reclusivemonkey on 2006-10-30
> **DNAspark99 said:**
> My questions is, mpg, avi, wmv etc, all default to using the totem plugin - but I prefer mplayerplug-in - so how do I change this 'default' behavior? There must be an easy way, without having to remove the totem plugin? thanks!

Removing them _is_ the easy way ;-) If you want to keep them just in case, simply move them to a seperate location.

---

### Post by DNAspark99 on 2006-10-30
ok, then what's the hard way? :P

---

### Post by marcozs on 2006-10-30
I know it's not an answer to your question, but why would you wanna keep the totem-plugin if you're planning not to use it?

---

### Post by DNAspark99 on 2006-10-30
it seems to me they both have their strengths and weaknesses. I guess I'm looking for a way to assign which one handles which media types. Hrm, isn't there a firefox extension or something for this? Nothing in about:config atleast...

So far, it looks like I'll just end up removing the symlinks to the totem libs, and use mplayerplug-in (mozilla-mplayer) for everything.

---

### Post by reclusivemonkey on 2006-10-30
> **DNAspark99 said:**
> ok, then what's the hard way? :P

No idea. I don't do things the hard way :-P

---

### Post by srunni on 2006-10-30
It's actually not that hard. In Firefox 1.5.0.7 you (I think) go to Edit -> Preferences -> Downloads -> Edit Actions (or something like that) and delete the preferences for .avi, .mpg, etc. so that next time you try to play one, you can set it to the MPlayer plugin.

---

### Post by DNAspark99 on 2006-10-30
> **srunni said:**
> It's actually not that hard. In Firefox 1.5.0.7 you (I think) go to Edit -> Preferences -> Downloads -> Edit Actions (or something like that) and delete the preferences for .avi, .mpg, etc. so that next time you try to play one, you can set it to the MPlayer plugin.

This is SOOOO close to being exactly what I'm looking for - however ... it won't let me 'remove an action' - and editing/changing the action won't let you select another plugin, only another program! If it would only let me select from a list of installed plugins, it would be perfect...but alas...such is not the case

---

### Post by DNAspark99 on 2006-10-30
After reading the following:

[http://techpatterns.com/forums/about834.html](http://techpatterns.com/forums/about834.html)

...and fiddling around with the /etc/mplayerplug-in.* files and restarting firefox a lot...it seems theres no equivalant way to tell the totem player to drop responsibility for certain file/mime types. In short, the whole process of plugin mimetype handling is so horribly ill concieved that I have no other option : I must completely disable the totem plugins by either uninstalling it, or removing the symlinks in the /usr/lib/[firefox|mozilla]/plugins directory.

Oh well, totem won't be missed. Imho, mplayerplug-in is superior for all file types anyways. It should be the default plugin.

---

