---
title: "Something wrong with my Firefox"
date: 2005-10-30
forum: General Help
---

### Post by ecto on 2005-10-30
My firefox is working normally now but there are two instances (most recently yesterday) where my booksmarks got erased! The only time this happened is when i was swtiching guis (the first time to KDE then the second time to Openbox). Has this happened to anyone else. Does anyone know the cause? 
Any information will be helpful thank you.

---

### Post by ozorba on 2005-10-30
[QUOTE=ecto]My firefox is working normally now but there are two instances (most recently yesterday) where my booksmarks got erased! The only time this happened is when i was swtiching guis (the first time to KDE then the second time to Openbox). Has this happened to anyone else. Does anyone know the cause? 
Any information will be helpful thank you.[/QUOTE]

The Firefox bookmarks normally resides in .mozilla/firefox directory.

If you delete this directory you loose your bookmarks.

OZ

---

### Post by suRoot on 2005-10-30
Actually all your bookmarks, settings, etc, etc, are stored in a profile.  You can have multiple profiles which allow more than one person to use the browser / email / whatever.  Look in your ~/.mozilla/firefox directory to see if you have multiple directories with funky names like "shq60re1.default".  If you go in to one of those directories, you'll see the bookmarks file.

I don't know that it's your problem, but I've had problems in the past with firefox seeming to forget that a default profile existed - in those cases, it always prompted me to create a new one.  After which, I'd have to copy all my stuff over from the other profiles.  Maybe this is what happened to you?

If you do have more than one profile, have a look at ~/.mozilla/firefox/profiles.ini , which will tell you about each of the configured profiles.

---

### Post by mustang on 2005-10-30
This happened to me (in windows actually) and it was quite a pain to replace all of them. From then on, I installed this extension: 

[http://extensionroom.mozdev.org/more-info/bookmarkbackup](http://extensionroom.mozdev.org/more-info/bookmarkbackup)

---

