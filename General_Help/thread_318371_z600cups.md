---
title: "z600cups"
date: 2006-12-13
forum: General Help
---

### Post by M0nk3yM4n on 2006-12-13
So I tried to install my Dell 720 printer via the post on these forums using the Lexmark binary drivers, but something didn't work right and now I can't open the update manager because as soon as it opens it just closes and if I type sudo apt-get install in the console it gets to reading state information....done then it says  

E: The package z600cups needs to be reinstalled, but I can't find an archive for it. 

I tried a bunch of ways of just moving the package via autoclean, clean and remove, but none of them worked. 

What should I do?

---

### Post by cilynx on 2006-12-13
Can you give us a cut & paste of the output of 
```

sudo apt-get remove z600cups

```
That seems like a logical starting place to me...

---

### Post by M0nk3yM4n on 2006-12-14
Here it is...

$ sudo apt-get remove z600cups
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package z600cups needs to be reinstalled, but I can't find an archive for it.

also sometimes my taskbar at the top doesn't load.... why is that? I think it has something to do with Beryl, what can I type in the konsole to start my taskbar? 

Thanks =)

---

### Post by cilynx on 2006-12-14
Do you have the .deb that you installed z600cups from in the first place?  It's sounding like you didn't get it from the official archives, am I correct?  

Not sure what to tell you on the panel.  There are still lots of bugs with Berly and all that, so it's possible that you're right there.  IIRC, the KDE panel is called 'kicker'

---

### Post by M0nk3yM4n on 2006-12-14
I tried going into the synaptic package manager but I hit "reload" and it just says that there is a error so I hit ok and then another error box pops up and says...

E: The package z600cups needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory

How do I manually download the new one, and remove this one? 

There isn't anyway to make sure that my taskbar opens up every time?

---

### Post by M0nk3yM4n on 2006-12-14
I converted the .rpm's from Lexmark using alien to a .deb but they are locked after creating them? They are either corrupted or I don't have the permissions? 

-Stupid stupid printer =(

---

