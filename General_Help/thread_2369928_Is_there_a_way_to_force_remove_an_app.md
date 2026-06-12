---
title: "Is there a way to force remove an app?"
date: 2017-08-28
forum: General Help
---

### Post by mike370 on 2017-08-28
I'm very new to Ubuntu, was a Mac user all my life before.  So far I am loving he experience but am having an issue with an app that won't open any more and I can't remove.  The app is Zoho Docs, which is just a little sync client, much like the Dropbox of Google Drive sync clients.  I had it set up as a login item, but noticed recently that it stopped opening.  When I try to open it from the activities pane nothing happens.  

I installed it using the software center and have tried removing it the some way.  I get the pop window asking "are you sure you want to remove this app?" but when I click yes nothing happens.   

I tried using "apt get remove" from terminal, but that gives me a message that no file by that name can be found.  Though I don't really know my way around the command line so I may not have typed everything in correctly.  I thought maybe my syntax on the app name might be wrong, is it zoho docs, zohodocs, zoho_docs? I still don't know.  

I tried listing all my installed apps in terminal and it does not appear in the list, though it still appears in software center as an install app.  

I'm running Ubuntu Gnome 17.04 which I upgraded to Pop!_OS 17.04 from System 76, on a 2009 Core 2 Duo MacBook Pro.  

Any advice or suggestions would be much appreciated.

---

### Post by Frogs Hair on 2017-08-28
Hello and Welcome

I find two applications and one is mail the other is for viewing/storing documents on line . Try the following in the terminal.
 ```
sudo apt remove webservice-office-zoho 
```

---

### Post by gordintoronto on 2017-08-29
BTW with apt, "get" is not an action. The most common actions are "install" and "remove".

---

### Post by mike370 on 2017-08-30
Thanks for this suggestion.  Strangly, when I logged into my computer today the app was already gone.  Not sure why it wasn't showing it before, but then this app was giving me issues otherwise so may it was just a buggy app, or maybe it's my system and they don't get along.  Not sure.  But thanks.

---

