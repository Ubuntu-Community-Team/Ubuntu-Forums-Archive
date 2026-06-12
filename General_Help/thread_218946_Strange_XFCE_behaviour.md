---
title: "Strange XFCE behaviour"
date: 2006-07-19
forum: General Help
---

### Post by Kimm on 2006-07-19
Sometimes when I click the button to open Thunar it opens two... and sometimes three instances.
I am sure that I am only clicking the button once.

Same thing with ALT + F2, sometimes 2... or even 3 instances of the dialog.
This happens with no other application... and Its confusing.

---

### Post by Dubbel on 2006-07-19
> **Kimm said:**
> Sometimes when I click the button to open Thunar it opens two... and sometimes three instances.
I am sure that I am only clicking the button once.

Same thing with ALT + F2, sometimes 2... or even 3 instances of the dialog.

This happens with no other application... and Its confusing.

I'm having the same problem !!

---

### Post by -Phi- on 2006-07-19
I get the same thing with thunar and the terminal launchers. I've seen a few others post about it too, but I haven't found any reason for it yet. It's also not consistant at all (most of the time I only get one program instance).

At least it's not a big issue.

- Phi

---

### Post by quedigg on 2006-07-20
Which packages are you using , XFCE independent packes ,or the Xubuntu package ?

---

### Post by Dubbel on 2006-07-20
> **quedigg said:**
> Which packages are you using , XFCE independent packes ,or the Xubuntu package ?
I'm not sure what you mean, but I did a clean xubuntu install 6.06.

---

### Post by Kimm on 2006-07-20
I installed xubuntu-desktop after installing Ubuntu

---

### Post by OlineSixtyOne on 2006-07-20
I installed just the xfce4 package from the repos (I also had to specify thunar, because for some reason it wasn't brought in as a dependency by xfce4). I haven't experienced this problem, knock on wood.

---

### Post by -Phi- on 2006-07-21
Found a reason and a solution! [http://xubuntu.wordpress.com/2006/07/11/how-to-solve-the-thunar-opening-twice-problem/](http://xubuntu.wordpress.com/2006/07/11/how-to-solve-the-thunar-opening-twice-problem/)

> 1) Go to Xfce Menu > System > Xfce 4 Task Manager.

2) Scroll through until you see Thunar. Right click it, and click Kill. If it asks if you want to actually kill the process, say yes.

3) Exit all of your programs, and go to Xfce Menu > Quit. Check “Save session for future logins”, and log out.

4) Log in, start Thunar, and hopefully it will only load once. This works for xfrun4 too!

* Note: To make sure Thunar doesn’t load up in the background next time you log in, uncheck “Save session for future logins”. 
Seems to be working so far :)

- Phi

---

### Post by picpak on 2006-07-21
Perhaps I should clarify. To stop Alt + F2 from opening twice, change everything in that guide from Thunar to xfrun4.

Thing is, sometimes it still opens twice :-k

---

### Post by TuxCrafter on 2006-07-21
I have to respond to this message i posted a bug report some month ago but did not get a respond. I did not use the correct channels i think.

I will explain the bug.

I believe it is a memory issue.

If a application is not yet loaded in the the memory (Linux does this called caching) it can start twice i think it is some timing problem. I only get this if i install xubuntu on slower machines.

If the application has been cached before and i try to load it again. It will be loaded like it should. used one time.

please contact me for more information. But i currently don't have a slow machine for reproducing the bug.

---

