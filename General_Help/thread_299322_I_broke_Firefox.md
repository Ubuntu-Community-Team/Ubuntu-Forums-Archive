---
title: "I broke Firefox?"
date: 2006-11-14
forum: General Help
---

### Post by J-Rod on 2006-11-14
I don't know how this is possible, but it looks like I managed to severely bork Firefox while simply changing default fonts. I was in Swiftfox for the first time, and was changing the fonts in the preferences from within the browser. I had accidentally chosen German-something or other, I didn't get a chance to see, right after it happened the window closed on me, and will never reopen. 

When I try to run either Swiftfox or Firefox, I get a prompt that tells me it's trying to load, even though it doesn't show up as a process in system monitor.

I have tried completely uninstalling both packages from automatic and synaptic, and reinstalling. I am still getting the same thing. I installed Opera to get here and cry about it :)

Can anyone shed some light on what else I might try to get it working again? I am not a big fan of Opera...

---

### Post by chriscando on 2006-11-14
Try creating a new profile:
```
firefox -ProfileManager
```
maybe your current one keeps crashing at startup.

---

### Post by IusedTObeSOMEONEelse on 2006-11-14
Time to fire up your friend "The Terminal". I'm sure some one can tell you how to remove via 'Terminal'

---

### Post by mayonaise15 on 2006-11-14
If chriscando's solution doesn't work out for you, I would try a backup and removal of the .mozilla directory in your home directory.  Follow these steps in a terminal window:

to backup:
```
tar -cf mozilla.tar .mozilla
```

to remove:
```
rm -r .mozilla
```
This may throw up some questions in the terminal about if you want to erase read-only files.  Just hit y and enter for any/all of them.

Try starting Firefox and good luck.  If it works and you need to restore your  bookmarks, you can put the following into your terminal: 

```
tar --wildcards -x .mozilla/firefox/*.default/bookmarks.html -f mozilla.tar
```

---

### Post by J-Rod on 2006-11-14
Wonderful, worked great mayo! So what exactly is contained in the .mozilla dir that was causing the problem? Is that where all the mozilla settings live, the ones that I changed before it crapped out on me? Well I suppose I can do my own homework on that, shouldn't be too hard to look up. Well, thanks again guys!

---

### Post by mayonaise15 on 2006-11-14
Yes, that is where all your personal settings are stored, including any add-ons. There will be some directory under .mozilla/firefox with a random name ending in .default (for some reason, I have two?) that contains all of your settings.

Glad you got things working again.

---

### Post by bobosity on 2006-11-14
Another way that linux whoops windoze. All those '.' dot files and directories are equivalent to the windoze registry. If you've ever messed with the win registry, you'll know what I'm saying.

---

### Post by mayonaise15 on 2006-11-14
Yeah, I don't miss the registry **AT ALL**.

---

