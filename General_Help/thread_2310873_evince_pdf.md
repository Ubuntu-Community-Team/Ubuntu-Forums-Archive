---
title: "evince pdf"
date: 2016-01-22
forum: General Help
---

### Post by wyndlass on 2016-01-22
i'm using evince to view pdfs.  i'm using vivid on a samsung np-nc10. evince isn't saving bookmarks or last page read in the current pdf. i have tried adding bookmarks w/n evince but it doesn't keep them. i can't figure out were the config file is for it so i can straighten out the problem. this has been going on for about 2 wks i think. didn't really pay attention at first. 

nautilus has been giving me a similar problem as well. what do i need to do to fix this? i've tried ctrl-t, drop down menu, and siderbar in evince to no avail. in nautilus, it won't save the file sort listing as type for some reason. i'm guessing( maybe incorrectly so) that both problems are linked. i can't figure out what's going on. 

it's more annoying than anything else but i would like to solve this. thanks for the help.

---

### Post by QDR06VV9 on 2016-01-22
I went through this a while back and decided to take  a different approach..[URL="https://okular.kde.org/"]
Okular[/URL] viewer does remember the last reading position, but it is not necessarily lightweight, especially if you don't use KDE software at the moment 
and need all the dependencies just for this one tool.
And Also [MuPDF]("http://mupdf.com/") should also work it did for me in Trusty(14.04)
I know this not what you were after but other possibility's

---

### Post by wyndlass on 2016-01-23
evince was saving last page read then quit. nautilus likewise was keeping file listings set to view by type. i'm not sure what happened in either instance.

---

### Post by mc4man on 2016-01-23
As far as nautilus - 
If you want **all** folders to sort by type then open nautilus > edit > preferences > change in Default view. (set a new default
Then any individual folders that you don't want at your default (now type), change while in that  folder > View > pick one in dropdown
(- at this point clicking on View > Reset View to Defaults would set to your default (type), if not already.

If only some folders then try from within folder > View > pick one. It should be persistent

Bookmarks **per pdf** in evince are saved in ~/.local/share/gvfs-metadata, nothing really user editable there. This is  where nautilus view settings are also saved.

---

### Post by wyndlass on 2016-01-25
will the file be recreated if it's deleted?

---

### Post by mc4man on 2016-01-25
> **wyndlass said:**
> will the file be recreated if it's deleted?

Yep
Edit: you can delete the whole folder, then log out/in, ect.

---

### Post by wyndlass on 2016-01-25
cool. i'll try that and see if evince saves the last page read like it used to or if might have to reinstall it, which i don't want to do, nor can i right now do to not having internet at home and my laptop screen is broke, using an old crt for an external monitor. can't carry one of those around all day long, or even a few blocks. i will post if deleting the directory you mentioned fixes my problem or not. thanx mc4man.

---

### Post by mc4man on 2016-01-25
Generally speaking re-installing an app doesn't help any config issues. Sometimes one can test in a guest session though in this case you'd need to provide a pdf for the guest session (like from a usb stick or data cd.
Otherwise you could set up a temp new user, log into that user & you should be able to navigate to some of your current user's home folder to open or copy out a pdf to test with..

---

### Post by wyndlass on 2016-01-26
thanks for the help mc4man. evince is back to normal again. i had forgotten about preferences in nautilus.

---

