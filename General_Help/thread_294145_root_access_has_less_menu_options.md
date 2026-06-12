---
title: "root access has less menu options"
date: 2006-11-06
forum: General Help
---

### Post by razor7 on 2006-11-06
Hello, i have re-enabled root acces in Edgy 6.10 and enabled the root graphical access. The thing is that ROOT has less menu options in "Preferences" and "Administration", as a normal user.

Also, if I try to use the menu editor, the options are there .like "Synaptic package manager", but I cant enable them...

How can I re enable theese valuable menu options?


Thanks a lot...!!!

---

### Post by CatKiller on 2006-11-06
If logging in as root gives you fewer tools, and is a blatant security and configuration risk, why do it?

Anyway, as a wild stab in the dark, perhaps your root account needs sudo powers to have those menu items show up?

---

### Post by kerry_s on 2006-11-06
You might as well wave a big sign come & get me. Most attacks look for root, now all they have to do is crack your password, you just lowered your security by 50%.

I don't have an answer, but you can try opening a terminal and run>  update-menus  <this will give you debian menu, you might have to enable it in the menu editor.

---

### Post by razor7 on 2006-11-06
Thanks guys..i have disabled root account...

---

### Post by hikaricore on 2006-11-06
Security I can see, but some items I've noticed missing in my many ubuntu installs are just plain silly.  On one system I couldn't access the Screen Resolution changer in Preferences.  :P  I had to copy the damn thing from another profile to the desktop and then to my /root/Desktop.  I've also noticed on most installations Shared Folders in the Administration menu was missing... come on seriously if someone is going to destroy my system the first thing they're going to look for is Screen Resolution and Shared Folders....


/me Ph33rz

lol sorry had to rant

---

