---
title: "Menu's appearing behind the current window!"
date: 2007-08-13
forum: General Help
---

### Post by staks on 2007-08-13
Hi everyone, new Ubuntu user here but having problems 2 weeks after installation.  Everything was going fine until i installed *all* the software updates which included a kernal update. Now what happens is that when i have a program open, clicking any menu's or right clicking on the screen brings up the menu's *behind* the current window i'm using. How do i know? Because i'm using a transparent theme and i can see the menu's behind my current window. Sometimes it works fine, but after i open a second tab in firefox it seems to start happening.

Programs i'm using are as follows -

Ubuntu x64 fiesty latest kernal
Compiz fusion
Swiftfox 32bit

If anyone has any ideas i would really appreciate it because it gets very frustrating being unable to right click in swiftfox, and having to minimize windows when i want to open something from the appllications menu.

Cheers, Staks

PS alternatively, is there any way to rollback the kernal? I notice in the grub menu it has both kernals listed?

---

### Post by ZipoTe on 2007-08-13
> **staks said:**
> 

Programs i'm using are as follows -

Ubuntu x64 fiesty latest kernal
Compiz fusion
Swiftfox 32bit


maybe it's a compiz fusion problem... i remember my brother having some trouble like yours.


> **staks said:**
> 
PS alternatively, is there any way to rollback the kernal? I notice in the grub menu it has both kernals listed?


you can edit the grub menu located here: /boot/grub/menu.lst

---

### Post by staks on 2007-08-13
Thanks Zipote, it was a compiz fusion problem. After i disabled it the menu's were appearing at the front of windows again.  So my next question is, how do i troubleshoot Compiz Fusion? Is there a way to check for updates?

Thanks

---

### Post by ZipoTe on 2007-08-13
As I'm not a compiz guru :-P i recommend visiting [compiz forums]("http://forum.compiz-fusion.org/") There you will find an answer, sure :)

---

### Post by ramjet_1953 on 2007-08-13
I'm not sure about Compiz Fusion, as I still use Beryl.

In Beryl, in the general options there is an item called [COLOR="Blue"]Level of Focus Stealing Prevention[/COLOR].

If you set that to [COLOR="Blue"]None[/COLOR], the problem of windows opening behind another window is solved.

I hope it is the same in Compiz Fusion.

Regards,
Roger :cool:

---

