---
title: "[SOLVED] Showing Hidden Files in Dolphin keeps getting Disabled (instantly!)"
date: 2008-05-20
forum: General Help
---

### Post by OzzyFrank on 2008-05-20
Just so you know, I'm not a novice who has no concept of the "Show Hidden Files" setting in file browsers... so I can tell you that in Dolphin, I've found where that is, and have repeatedly enabled it... but it keeps going back to the default of hiding hidden files. Like I mean as soon as I've clicked my way into a folder then gone back to the parent, it is disabled (eg. in my user folder I have to enable that to see the .gnome2 folder - I then click into it, then back up into my user folder - and .gnome2 and all other hidden folders and files are hidden once again).

Now, call me suspicious, but I have a feeling I shouldn't need to go into the menus and enable showing of hidden files/folders _every_ time... and would be surprised if Dolphin shipped like this with Hardy... so is there a fix for this?

I am using Hardy and yes, I have tried both enabling "Show Hidden Files" and also "Adjust View Properties" (enabling "Show hidden files" and applying it to "All folders") but it never sticks. Any ideas?

---

### Post by stefangr1 on 2008-05-20
It's the same here. I wanted to change "large icons" to "detais", but gave up my attempts. Whenever a new session of Dolpin is started, everything I changed in the settings panel is simply gone.

---

### Post by OzzyFrank on 2008-05-20
I don't even have to wait for a new session for the system files and folders to be hidden again... just go into a folder and it's disabled again. Wonder why they chose Dolphin as the default file manager over Konqueror? Dolphin seems a bit buggy, not just coz of this and similar issues (like the Details view etc), but coz with me it has crashed after some pretty minimal use, whereas Konqueror has come across as much more stable.

As for this issue of view settings not holding, hopefully someone knows of a patch or command or something that can get Dolphin to behave.

---

### Post by NightwishFan on 2008-05-20
Is it set to use the same settings for each folder? (I use konqueror for file browsing anyway)

---

### Post by OzzyFrank on 2008-05-20
Yes, as I mentioned, I've set "Adjust View Properties" to "Show hidden files" and applied it to "All folders". I'm afraid it's not a lack of knowledge issue, but something amiss with Dolphin, at least on my system.

---

### Post by stefangr1 on 2008-05-20
> **OzzyFrank said:**
> Yes, as I mentioned, I've set "Adjust View Properties" to "Show hidden files" and applied it to "All folders". I'm afraid it's not a lack of knowledge issue, but something amiss with Dolphin, at least on my system.

I agree with you.

---

### Post by NightwishFan on 2008-05-20
I see. Odd. My only issue is that it would resize a lot if I moved mouse over a file with a long name, which was distracting.

---

### Post by OzzyFrank on 2008-05-20
OK, more whacky behaviour from Dolphin, hehe. I haven't tried to replicate the other oddities mentioned here, but wouldn't surprise me if I got the same results. And it also wouldn't surprise me if there was some little trick or command or whatever to rectify this... this has been what has impressed me most about Linux/Ubuntu - the ability to fix things.

Believe me, I had plenty of Windows experience (14 years) in fixing my own systems and that of clients, and even knew tricks/fixes/amazing-technical-things many "certified professionals" didn't. But there is no comparison between the success rates of fixing what could be called critical issues, in the OS itself, or just with programs running on it. I've always relied on search engines and forums for the hard-to-get info, yet I've had to admit defeat so many times in Windows, yet in K/Ubuntu/Linux, I've hardly had anything that hasn't been resolved.

But I digress... especially since, the more I think of it, I doubt there is a cool little command or fancy editing of a system file to rectify this Dolphin situation. If others have noticed all sorts of weird behaviour in Dolphin, I would venture that this current version is a bit screwy ie: bug-infested.

If someone does know of a fix, please let us know... but I am guessing it is just one of those times we sit back and wait for an update.

---

### Post by mc4man on 2008-05-20
the hidden file setting works here
dolphin -> settings -> configure dolphin -> save view properties for each folder and then view -> show hidden files

---

### Post by OzzyFrank on 2008-05-20
Thanks, that did it. I never expected the showing of hidden files to be associated with the view properties of individual folders (in Nautilus and Windows Explorer when you enable the showing of hidden files it affects the whole browser, and saving of settings for individual folders means the icon view). Besides the fact I enabled it from 2 different places in the View menu, hehe. Cheers

---

### Post by COKEDUDE on 2011-02-07
> **OzzyFrank said:**
> Yes, as I mentioned, I've set "Adjust View Properties" to "Show hidden files" and applied it to "All folders". I'm afraid it's not a lack of knowledge issue, but something amiss with Dolphin, at least on my system.

Thank you for that.

---

### Post by ktook on 2011-08-01
> **mc4man said:**
> the hidden file setting works here
dolphin -> settings -> configure dolphin -> save view properties for each folder and then view -> show hidden files

:( Just wondering?  Using the current version (I think) of Ubuntu and trying to do a search for a hidden file (.mozilla). The Dolphin version here is 1.6.1.   Have things changed since your response?  I can find dolphin ->settings-> .... but where is configure dolphin?  I looked around and found -> general -> view properties -> Remember properties for each folder  but, but, no view -> show hidden files..  Wow, where do I go from here to find hidden files?  ~help~  And thanks..

---

