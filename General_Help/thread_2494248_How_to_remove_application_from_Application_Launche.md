---
title: "How to remove application from Application Launcher?"
date: 2024-01-09
forum: General Help
---

### Post by goemonburo on 2024-01-09
I've found that in my Application Launcher (the leftmost button in the panel that then has categories of applications and then the applications themselves), I have two entries in the "Graphics" section for Digikam.  One is at the top, the other at the bottom.  One runs an older version of digikam that I don't use, the other starts up 8.1.  At some point I will probably remember which is which, but I don't use Digikam that often and thus, whenever I'm trying to start it, I inevitably start the wrong instance and have to close it and choose the other one.

It would be so nice if there were a Right Click > Remove from Launcher option but that's not there.  How do I remove these or order them?  Like if I wanted to sort them alphabetically or put the one I use most at the top?

Thank you.

---

### Post by ne29914 on 2024-01-09
Go to /usr/share/applications and identify the offending entry. Open it with a text editor and add the line "NoDisplay=true" to the file.
Entry is now removed, but can be reactivated later if needed.

---

### Post by goemonburo on 2024-01-09
Thank you @ne29914.  I'm looking at /usr/share/applications and can't see any obvious entry there for Digikam.  Is there any chance this is part of a different package?  Or is in .local or somewhere else?  

Again, thank you for the suggestion.  Assuming I can find it, I think the "NoDisplay=true" is exactly what I'm looking for.  (Though I probably don't need it, now that I'm using a newer version.)

---

### Post by MAFoElffen on 2024-01-09
Tip:
```

grep -i 'digikam' /usr/share/applications/*

```
Choose from those choices...

---

### Post by goemonburo on 2024-01-09
That worked!  However it turned out the offending file was indeed in .local/share/applications, and I had to use the --exclude-dir=wine to get grep to stop failing when it found a directory.  But I did edit that file, and it did vanish from the menu, so I'm all set.  I'd love to know how to place the remaining digiKam up at the top of the menu instead of buried in the middle.  But thank you all, this was exactly the solution I needed.

---

