---
title: "Seamless startup?"
date: 2008-03-22
forum: General Help
---

### Post by ZarathustraDK on 2008-03-22
As it is now, logging in is all but seamless. What usually happens is :

Login-screen appears (user logs in) --> Background color appears (default the ubuntu orange color) --> If running compiz, then the screen goes black, then default color, then black again --> wallpaper appears --> icons appear --> docks and other programs appear.

Is there any way to make this whole process seem more seamless? I saw a guy demonstrating compiz once, who, when he enabled compiz, had a sort of fade-in into the compiz desktop. Not exactly what I'm aiming at, but the idea is basically the same. Can you somehow make the transition from login to ready desktop seem seamless, and not having to witness the gradual build-up one process at a time?

---

### Post by Mr. Picklesworth on 2008-03-24
Could that have been the Login / Logout plugin for Compiz?

I know it's available with the version packaged in Hardy. There's also some work going into tidier login with GNOME 2.22 (the new version). For example, the panel keeps itself hidden and then slides into view once all its applets are loaded.

Transition from usplash to gdm is the weak link right now, and it would be nice if GDM didn't disappear to a background colour, but instead to the user's desktop background. (On that thought, Fedora does a neat job with its boot splash -> GDM transition).

Err, in other words, you will have your answer in a little over a month :)


One thing you can do in the mean time is fiddle with the login screen background colour, for example to get something that matches your desktop. You can do that in System -> Administration -> Login Window if you go to the Local tab.

---

