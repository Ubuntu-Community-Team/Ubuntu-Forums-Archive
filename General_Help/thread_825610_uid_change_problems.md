---
title: "uid change problems"
date: 2008-06-11
forum: General Help
---

### Post by jackinloadup on 2008-06-11
hey all, If changed my uid to match the one my mac partition so i could access my user data on that partition but i have run into a few small problems.

First when i login the gnome-panel has no panels but can be fixed by killing it then starting it over. All around my preferences dont seem to be in effect. background theme.. ect. infact i cant change anything in the "appearances" app for the most part.

Here is what i have done so far.
enabled root and logged in via terminal 2 (ctr+alt+f2)
then changed my uid (usermod -u 501 jackinloadup)
next changed the ownership on my home folder and any /tmp/ folders with my name in them.  via chown -hR

so i still cant edit preferences for various things and cant add things to the gnome-panels or stuff like that.

Any help would be greatly appreciated.

---

### Post by elvinatom on 2008-06-11
why don't you just delete your user and remove the home folder that belongs to it, then recreate it with the correct uid right from the start?

---

### Post by sdennie on 2008-06-11
How did you do the chown?  There is a difference between the following two commands:

```

sudo chown -R username /home/username/*

```

and

```

sudo chown -R username /home/username

```

Specifically the first command won't change the owner of your configuration files whereas the second will.

---

### Post by jackinloadup on 2008-06-11
> **elvinatom said:**
> why don't you just delete your user and remove the home folder that belongs to it, then recreate it with the correct uid right from the start?

i didnt know i would need to change my uid 2 years ago when i started using ubuntu. though i might still backup my home folder and recreate it. 


> Specifically the first command won't change the owner of your configuration files whereas the second will.
I know i did something more similar to the second but i might have added a / to the end. so i will re run this and see if it helps.. thanks

---

