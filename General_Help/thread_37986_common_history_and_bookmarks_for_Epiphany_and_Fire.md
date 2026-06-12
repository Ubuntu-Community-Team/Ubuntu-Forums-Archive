---
title: "common history and bookmarks for Epiphany and Firefox"
date: 2005-05-29
forum: General Help
---

### Post by 23meg on 2005-05-29
Firefox has been the only browser i've been using, until recently i discovered Epiphany. now i feel like using both; Firefox is clumsy but has extensions that i make use daily of, and Epiphany is much faster and very practical but lacks in features, but if i am to use both this means two separate histories that i'll need to search in order to find something i'm looking for, and two sets of bookmarks.

now, i know there are others among us who make use of both, so here i declare my request for a possible hack that will make the two browsers share their bookmarks and histories.. to be honest i haven't looked into how this can be achieved; i don't even know where Epiphany stores its bookmarks and history, but maybe there are others who've already figured this out, so...

---

### Post by kwalo on 2006-10-08
AN old thread, but I found it, while lookingfor something else :)

Epi's history is stored in **~/.gnome2/epiphany/mozilla/epiphany/Cache**

Firefox stores it's history in **~/.mozilla/firefox/${YOUR_PROFILE}/Cache**, where ${YOUR_PROFILE} looks like this: xxxxxxxx.default

The history format is the same for both of theese applications (no surprise, since Epi uses Mozilla engine), so there is a chance, that browsing history can be stored between theese two apps ([COLOR="Red"]I didn't test it[/COLOR] however).

[COLOR="Red"][SIZE="4"]NOTE:[/SIZE][/COLOR] This might be dangerous, since now two apps will be writing to the same files. It might cause unexpected crashes if you run both browsers at the same time. You have been warned.

If you still want to try: This is how it should look like:
1. Close both browsers

2. Make Epi's Cache dir be a symbollic link to Firefox's one (You have to erase it's history first)
```
rm -rf ~/.gnome2/epiphany/mozilla/epiphany/Cache
ln -s ~/.mozilla/firefox/${YOUR_PROFILE}/Cache ~/.gnome2/epiphany/mozilla/epiphany
```This should make your browsers share the same history.

---

