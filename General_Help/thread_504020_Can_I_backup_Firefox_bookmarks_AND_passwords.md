---
title: "Can I backup Firefox bookmarks AND passwords?"
date: 2007-07-18
forum: General Help
---

### Post by diablo75 on 2007-07-18
Just wondering if there is an easy way to backup and then restore my Firefox bookmarks and passwords.  I'm going to do a fresh install of a slightly different disto just to try it out, and I'd like to save myself a little trouble after the install is finished.

Thanks!

---

### Post by aysiu on 2007-07-18
Yes. Everything related to Firefox (extensions, bookmarks, passwords) all live in /home/*username*/.mozilla

.mozilla is a hidden folder, so you may have to press Control-H to see it.

Have you considered [creating a separate /home partition](http://www.psychocats.net/ubuntu/separatehome)?

---

### Post by jocko on 2007-07-18
It should all be stored in a folder named ".mozilla" (hidden) in your home folder.

---

### Post by diablo75 on 2007-07-18
> **diablo75 said:**
> Just wondering if there is an easy way to backup and then restore my Firefox bookmarks and passwords.  I'm going to do a fresh install of a slightly different disto just to try it out, and I'd like to save myself a little trouble after the install is finished.

Thanks!

That sounds pretty cool.  How would you go about doing that?

---

### Post by aysiu on 2007-07-18
> **diablo75 said:**
> That sounds pretty cool.  How would you go about doing that?
It's all in a folder called .mozilla that lives in /home/*username*

Back up the folder, reinstall, and then restore the folder.

---

### Post by diablo75 on 2007-07-18
Gottcha!  Thanks!

I'm putting UU 1.4 on right now...thought I'd give it a chance.  I liked 1.3 for a little while, but it got old, and slower, and kinda bloated.  1.4 should be a lot better...we'll see.... :guitar:

---

### Post by tahitiwibble on 2007-08-16
> **aysiu said:**
> It's all in a folder called .mozilla that lives in /home/*username*

Back up the folder, reinstall, and then restore the folder.

I wonder if you could give me the name of the file in which passwords are stored ......... **please.**

Also, how can I review/modify password settings?

Thank you Sir.

---

### Post by aysiu on 2007-08-16
I don't know what file the passwords are stored in. Asking "please" doesn't magically give me that knowledge any more than it would give you that knowledge.

You can review and modify password settings from within Firefox itself, though. Just go to Edit > Preferences > Security > Passwords

---

### Post by tahitiwibble on 2007-08-16
:lolflag: aysi ........... well **thank you** for your help. :rolleyes:

---

