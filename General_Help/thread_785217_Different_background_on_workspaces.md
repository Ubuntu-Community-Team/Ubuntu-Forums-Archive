---
title: "Different background on workspaces?"
date: 2008-05-07
forum: General Help
---

### Post by Chamelion on 2008-05-07
Is it possible to have different backgrounds on 4 workspaces?
Thanks

---

### Post by prshah on 2008-05-07
> **Chamelion said:**
> Is it possible to have different backgrounds on 4 workspaces?
Thanks

It's easy in KDE (Kubuntu), don't know about Ubuntu (Gnome)

EDIT: I mean to say; I don't know of any options for this in Gnome (ubuntu). I use gnome but have not been able to find any suitable options, and thus I _assume_ (in the humblest possible way) that it can't be done.

---

### Post by drunkmatador on 2008-05-07
I was just going to write a post asking the same thing when I saw yours. It should be possible.. you'd think so anyways, right? I mean with having this big 3D cube you can spin around, and have transparant video all this other junk, got to at least be able to have a different background on each right? hah.

---

### Post by todoporron on 2008-05-07
Try wallpapoz, it's really cool. You can have different background on each workspace, and you can set it to change every x minutes. I just don`t remember if it is on the repos; if not, it should be not difficult to compile.

---

### Post by darco on 2008-05-07
Sure you can....choose your wallpapers in CCSM. Then you must deactivate the desktop which will no longer let you access any destop shortcuts you have. Type gconf-editor in a terminal, navigate to Apps/Nautilus/Preferences and uncheck show_desktop.
Dont forget  your caps!

good luck

darco

---

### Post by Chamelion on 2008-05-07
Thank you. Now , if somebody could tell me how to thank somebody for an individual post please.:)
Cheers

---

### Post by darco on 2008-05-07
Look for the little gold star medal in the corner of the post of the poster you want to thank :)

darco

---

### Post by caro on 2008-05-07
> **Chamelion said:**
> Thank you. Now , if somebody could tell me how to thank somebody for an individual post please.:)
Cheers

Just go to their post and click on the medal icon in the lower right.

---

### Post by SAKO2008 on 2008-05-08
I have a problem, I set backgrounds in my cube with CCSM and I unchecked show desktop, but now never appear my right clic menù in desktop. How can I solve it?

---

### Post by trappy on 2008-05-08
Hm.. exactly where should I change these options...?

---

### Post by malspa on 2008-05-08
Is there any way to have different backgrounds on different workspaces in GNOME without wallpapoz and if you're not using COMPIZ?

---

### Post by milanvora2 on 2008-05-08
Yes,

go under System> Preferences > Advanced Desktop Settings
Select Desktop cube > appearance > Background Images.
Add all the images you want as background

start alt + f2 run gconf-editor
go under apps > nautilus > preferences
disable show desktop

and voila... i saw it on another thread and it worked yesterday.
please note that it now shows a different background but all shortcuts on desktop are not visible as they are hidden by these wallpapers.

---

### Post by filtro_tuc on 2008-05-08
> **darco said:**
> Sure you can....choose your wallpapers in CCSM. Then you must deactivate the desktop which will no longer let you access any destop shortcuts you have. Type gconf-editor in a terminal, navigate to Apps/Nautilus/Preferences and uncheck show_desktop.
Dont forget  your caps!

good luck

darco

Thanks!!
works excellent.
And you are right about the icons over the desktop, they are not accessible.
Is there something to do for access to those icons?

---

### Post by anuban on 2008-05-09
How can I get the original setting back?  I tried the above thing.  Works perfect, but now I am not able to right-click on my desktop.  How do I get it back?
I tried changing the gconf-editor >nautilus >app; checked show desktop.
But I still can't see my original desktop.
Thanks

---

### Post by prshah on 2008-05-09
> **anuban said:**
> 
I tried changing the gconf-editor >nautilus >app; checked show desktop.
But I still can't see my original desktop.
Thanks

I think you need to log out and log back in for the change to take effect.

---

### Post by anuban on 2008-05-09
> **prshah said:**
> I think you need to log out and log back in for the change to take effect.

This is a very old thing dude...
I did everything...
Something else..

---

### Post by killer_d76 on 2008-05-09
are you using Hardy Heron?... if so, i believe that you need to wait until this "bug" is fixed.. the bug here is that you won't be able to revert the changes that you have done on your desktop using gconf-editor :(, which actually forced me to re-install hardy on my laptop, but i heard that somebody was able to bring back the desktop by restarting his computer after changing back the changes that he have done on the gconf-editor.

---

### Post by zieglerj on 2008-05-13
hold down alt+ctrl+backspace, you need to do this for most changes in compiz...it will instantly kill anything that is open so close everything!!!

---

