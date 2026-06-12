---
title: "missing org.gnome schema"
date: 2015-06-10
forum: General Help
---

### Post by BeachBuddah on 2015-06-10
Hey folks,
I have a recent install of Vivid (with lots of personalization going on, I admit).  Yet without (much) provocation I ran into two problems - my shutdown is down to a crawl - not sure what's up with that - and this issue that has my wireless mouse going haywire, though the touchpad works as well as ever...

I tried (since I had a different look to my system after the dist-upgrade reboot) to check my stuff with Unity tweak tool and got the message that I was missing a schema and I should ought to reinstall before tweak tool would do its tweaking thing.  I looked how to do it and found a post over at AskUbuntu describing this issue and the fix - --reinstall org.gnome-bla-bla-bla.  But when I did so, I was told I had the newest version already but it would happily reinstall over.  But checking the end result in gedit, I found that the missing schema was still rather missing.  'org.gnome.settings-daemon.peripherals.touchpad' was not in the text but 'org.gnome.settings-daemon.peripherals.touchpad.deprecated' was.  Don't know what all to do now, so any help would be appreciated.

Like I said - 15.04 installed just a few days ago on an HP DV6-Envy notebook using all open source drivers and mostly open source stuff - yeah yeah - ubuntu restricted extras are on board and a few other such, but nothing that would be doing anything silly like this (I wouldn't IMH and not very knowledgeable O think).  

Should I just delete the '.deprecated' and hope for the best or is there a real fix for this?

---

### Post by mc4man on 2015-06-10
I see no sign of that line in any schemas that matters (/usr/share/glib-2.0/schemas), but if I did I'd  just ignore. 
What could be more interesting is - 

What package or whatever  did you reinstall?, don't know org.gnome-bla-bla-bla too well..
What askubuntu post did you follow?
What text are you referring to that you found this line?
What makes you think ubuntu-tweak would work well on 15.04? ( seems to have some issues here in a quick look before purging.

---

