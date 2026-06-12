---
title: "emerald at startup"
date: 2008-04-30
forum: General Help
---

### Post by jdix123 on 2008-04-30
Hi.  

I want to use emerald rather than kwin or compiz but don't know how without using 

```

emerald --replace

```

Also, when my kde 3.5.9 loads it looks like its loading one configuration file, then going through and loading a different one.  What might be causeing this?

Kubuntu 8.04
AMD Sempron 2800 1024MB RAM nVidia GeForce 8600

Thanks!

---

### Post by gerbman on 2008-04-30
> **jdix123 said:**
> Hi.  

I want to use emerald rather than kwin or compiz but don't know how without using 

```

emerald --replace

```
If you don't want to enter the "emerald --replace" command every time you boot up, add it to your session start command list. Go to System->Preferences->Sessions, click "Add", enter any name and "emerald --replace" for the command. Your session should then start with the emerald decorator.

---

### Post by darco on 2008-04-30
Also you can add it to CCSM/Window Decoration/command

darco

---

### Post by mahuyar on 2008-05-01
According to this [post]("https://help.ubuntu.com/community/CompositeManager/CompizFusion"), it would be like:

In the konsole, type:
```
 echo "emerald --replace" > ~/.kde/Autostart/startcompiz.sh 
```
and make it executable:
```
 chmod +x ~/.kde/Autostart/startcompiz.sh 
```

The 2nd post is for GNOME I guess.  I see you're using Kubuntu.  Hope this helps.

---

