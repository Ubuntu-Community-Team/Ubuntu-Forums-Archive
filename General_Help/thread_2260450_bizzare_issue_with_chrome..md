---
title: "bizzare issue with chrome."
date: 2015-01-12
forum: General Help
---

### Post by bryanlester2290 on 2015-01-12
Semi-Newbie here

So I have this bizzare issue on 14.04. My chrome browser has dissapeared. The chrome apps are still there. . . but the actual browser is gone. Nothing in the dash menu cants seem to open it via command line. Just gone. But I can still see and use the chrome apps. Can't seem to remove those. After digging online a bit I tried a purge of chrome. Didn't seem to make a difference. Not noticeable at least. After the purge I reinstalled. No difference. Restarting the computer does nothing either. Before this happened my chrome instances would be labeled "hangouts" on the side bar in unity and the bottom bar in cinnamon. One day it just up and dissapeared. Now the really odd part is if I right click the hangouts icon and select about chrome it opens up a chrome window (still labeled hangouts but otherwise fully functional) this persisted even after I supposedly uninstalled chrome "successfully" via command line. Probably going to do a fresh install but would prefer to avoid that if possible. Anyone know what's going on here; How to fix it and what not to do so i don't make it happen again? 

I'll provide more details and screenshots if it means figuring it out.  Its the only problem this system is having

---

### Post by kerry_s on 2015-01-12
maybe some settings you did or add on. if it was me i would go in to my file manager press ctrl+h to show the hidden files, look for all the chrome folders and delete them, that should give you back a stock chrome.

---

### Post by ajgreeny on 2015-01-12
I agree with kerry_s except that I would not delete the hidden configuration folders.
I would just rename them as a backup so that I could get back any bookmark folders etc etc that may be needed later.

The folders are all in the hidden **/home/username/.config/google-chrome** or something similar to that; search around and I'm sure you'll find it.

What error messages, if any, do you see if you try to open it from the terminal?

---

### Post by kerry_s on 2015-01-12
lol, it's google bookmarks are in the clouds.

---

### Post by ajgreeny on 2015-01-12
> **kerry_s said:**
> lol, it's google bookmarks are in the clouds.
What, always?

I've never used Chrome, and apart from a short time with Ubuntu-One I've never used the cloud either.  I prefer all my own files on my own disks!

---

### Post by Mike_Walsh on 2015-01-12
Kerry_s IS right, AJ.

You can even do it with Firefox; it's the 'Sync' option in Preferences.

I always used to save my bookmarks as a Firefox .json HTML file, and manually transfer them to each new instance of FireFox that I've installed.....until somebody told me that Firefox works the same way as Chrome. You CAN save the bookmarks manually in both browsers; but you can also sync both browsers via the cloud.

I guess when it comes right down to it, it's all a matter of individual preferences, really....


Regards,

Mike. ;)

---

### Post by kerry_s on 2015-01-12
i have chrome/chromium & firefox synced to the clouds. it's very useful since i'm distro hopping, i just log in to whatever new installs browser & i'm ready to go. i got both because some have firefox default & some use chromium for default browser. it even saves passwords so i don't have to type them all back in.

the cloud is perfect for a old fat lazy dude like me with a bad memory. lol

---

