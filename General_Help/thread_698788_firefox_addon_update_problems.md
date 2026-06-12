---
title: "firefox addon update problems"
date: 2008-02-16
forum: General Help
---

### Post by Robbyx on 2008-02-16
I had a major crash when I tried to update from fiesty to gutsy. I have had to do a completely new install of gutsy and go to backups for my firefox profile. At the moment I am accessing the profile via the profiles.ini as follows:

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/old/media/sda1/My Documents/Firefox profiles/id06xco5.default
```

Should isrelalative be 0?

Firefox  is working in that my bookmarks are showing  but when I tried to update my addons none of them would update. Everyone gave an error message and referred me to the console error log.

The error log is full of comments like:

No chrome package registered for chrome://infolister/skin/icon32x32.png .


I have restarted FF and again tried to update the addons but this time each one is  marked to the effect that there are updates available. That would be ok except none of the addons will open and allow me to access their options.  

I wonder if this is to do with file permissions. They are all set to me as owner.

Does anyone have ideas as to what needs correcting?

Robin

---

### Post by ajgreeny on 2008-02-16
Just uninstall the add-ons and then reinstall them. Most are only small downloads, so it shouldn't be too much of a long job.  Bear in mind that it's possible that some of them may not work on the newer version of FF in the updated Ubuntu.

---

### Post by Robbyx on 2008-02-17
thanks

---

