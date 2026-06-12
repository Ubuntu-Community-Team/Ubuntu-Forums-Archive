---
title: "Filter files in Nautilus"
date: 2007-10-17
forum: General Help
---

### Post by dlanor78 on 2007-10-17
I'm looking for a way to filter out files I want to see vs. what I don't want to see in nautilus similar to the way that it's done in konqueror and even dolphin.  I'm aware of the ctrl+s option (Select Pattern) but all that does is selects a one file that matches that pattern.

That means if I have a bunch of .iso files mixed in with other file types, it will only select the first .iso file it finds for me.  I want to just see a list of all the isos in the directory.

Is there any way to get this functionality in nautilus?  I use it quite a bit when using kde.

---

### Post by LanDan on 2007-10-17
not really sure what the added value is here, ever considered the option to put all your .iso files in a seperate folder? :)

---

### Post by dlanor78 on 2007-10-17
The iso thing was just an example.  It's also great for when I only remember part of the file name and the part I remember isn't at the beginning of the name.

For example, I use gp4/5 and ptb files which are for guitar pro and power tab.  One file in particular is "lesson_guitar-joe_satrianis_10_tips_to_make_you_a_better_guitarist-24088.ptb".  If I can't remember that the file starts with lesson, but remember that it has the name joe in it, then I simply filter out files that have the word joe in it and there it is.

My other problem with the nautilus ctrl+s is that it's case sensitive (the filter in konqueror and dolphin is not).  So if I tried to do Joe here it wouldn't work.

I think I might try to change the default file manager from nautilus to dolphin if that's even possible.  Researching it now.

---

### Post by Brucevdk on 2007-10-17
> **dlanor78 said:**
> I'm aware of the ctrl+s option (Select Pattern) but all that does is selects a one file that matches that pattern.

Did you use a wilcard? The default expression has to be an exact match, so *Joe* wouldn't match *Joe Donut* but *Joe** would. It'll select all matching files, it just won't hide non-matching ones like Dolphin/Konqueror do.

> **dlanor78 said:**
> My other problem with the nautilus ctrl+s is that it's case sensitive (the filter in konqueror and dolphin is not).  So if I tried to do Joe here it wouldn't work.

Looks like this is correct, I can't find a way to make it case insensitive. Bugzilla won't load for me atm, might be a ticket somewhere.

---

### Post by dlanor78 on 2007-10-17
Okay, my bad on the ctrl+s only selecting the first match.  It does indeed select all of the matches when using the wild card correctly.  It would still be nice if it filtered out all the stuff that doesn't match and it would be nice if it wasn't case sensitive.  At any rate this could help me organize my files better by having it select all iso files and then moving them all into a separate directory (but mv *.iso /path/to/put/them is faster imho ;)).

For now I'm just using dolphin whenever I need this feature.  It takes longer to load but still saves me some frustration ;-)

---

