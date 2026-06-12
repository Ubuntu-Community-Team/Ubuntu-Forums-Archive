---
title: "Screen half black"
date: 2007-06-28
forum: General Help
---

### Post by Krusnix on 2007-06-28
Beryl just crashed on me while I "was" in ubuntu while I was configuring my skydome background. Beryl has crashed several times causing the screen itself to go half black. It works perfectly fine, except that it's got like a black layer over top of the bottom-half of the desktop and below the kiba-dock. I completely removed beryl through autoremove, and purge beryl but the problem still persisted.  When I had beryl I would "relaunch windows manager" or something similar and I'd see a brief glimpse of the bottom before the black rectangle took it over.Upon re-installation of beryl the problem was still there, so I yet again completely removed it from my system. So now when I boot up the ubuntu partition, and reach the desktop the lower half just kills itself. This problem has come about before in the last 48 hours that I had ubuntu (yes i'm an extreme newbie). I had to wipe the drive 2 times, because of the bug that manifests itself each time through some sort of beryl crash. Any help would absolutely be appreciated. This is a learning curve, so just bear with me.

---

### Post by amadeus266 on 2007-06-28
Don't take my word for it as I am somewhat still a newbie myself but I think that when beryl crashed it also turned off the composite manager that Kiba-Dock relies on. At least that is what I have experienced anyway. Try killing kiba-dock and the screen will probably look normal again. If I am wrong, someone please offer better advice.

---

### Post by Krusnix on 2007-06-28
You are 100% correct, does this mean that I cannot run beryl and kiba-dock in conjunction? I know it's possible, but perhaps all of this may have something to do with my graphics driver -.-. I don't even know how to update it, haha! Thanks for you help!

I tried installing Beryl, thinking everything would be fine and dandy alas the darn thing doesn't even work anymore! No cubes, no transparency, ctrol + alt + click only makes me look like a fool while giving me the selection box..

EDIT: After a little experimenting, sudo beryl turned on beryl (so it works), and kiba-dock is working fine on top of that. So what happens is when beryl crashes it shuts down the composite manager which in turn probably gives me the black bar of death. The way to get around it is to probably to re-start beryl (it's broken look at the error below)... I don't quite know why it crashes randomly while I'm configuring it though, but it was awfully nice of you to give me that excellent help ya did there!

"beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialize dbus. This should not happen!" - It should not happen? I know there's a dbus option in kiba, perhaps that is one of the causes? I also am wondering whether or not all of this could be arising out of the lack of dependancies that kiba needs? There's a list, but I don't quite know how to go about installing them.. That's for another time though.

---

### Post by amadeus266 on 2007-06-29
Like I stated in my previous post, I am still learning how all this stuff works as well. You should be aware that Beryl is no longer being developed and Compiz-fusion has included all of Beryl's plugins. I have both on my machine and after spending the time to get Compiz-fusion working the way I want it too, I like it better than beryl. I have my own issues with kiba-dock such as the animations randomly stopping in the middle of their actions for several seconds and then resuming but those are due to my video card drivers being as good as they are going to get (ATI AIW 9200). My suggestion is to completely remove beryl and kiba-dock and very carefully go through the how-to's posted elsewhere in the forum (I printed them out so I had the info at a glance regardless of what was on my screen - that's just the way my brains works). Lot's of VERY good information and got my system running very sweetly in just one evening. Now if I can just stop playing with the settings and messing it all up... Anyway, good luck.:guitar:

---

### Post by aberflasm on 2007-07-28
> **amadeus266 said:**
>  ... after spending the time to get Compiz-fusion working the way I want it too, I like it better than beryl. ... due to my video card drivers being as good as they are going to get (ATI AIW 9200). 

I have the same graphics card and can either get Compiz-Fusion to work or videos to play but not both. I was wondering if you experienced the same issue and if you could share the solution please?

---

