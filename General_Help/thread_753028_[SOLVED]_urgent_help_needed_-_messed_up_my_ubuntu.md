---
title: "[SOLVED] urgent help needed - messed up my ubuntu"
date: 2008-04-12
forum: General Help
---

### Post by abh83 on 2008-04-12
I am in need of urgent help. I haven't backed up my files on ubuntu in a long while. (Files such as: emails, contacts and my private documents in my home folder).

I'm not sure what exactly i did last night but today it seems like ubuntu crashes right after the login screen.

I am currently in windows. :(

Last night i was playing around and installing plugins for awn, rhythmbox, audacious etc. Of course i had to compile a lot of these apps myself and a lot of dependencies were missing.

I guess i installed something i shouldn't have and now my system messes up.

I'll try to describe the issue as i can't take screenshots anymore.

Basically, after loging in, my desktop loads normally with awn (avant window navigator) and my wallpaper. However, everything else seems missing. My gnome-panel loads as a plain white bar with nothing on it. No menus, apps or icons. All the icons on the desktop are missing (filesystem, hdd etc). When i click on my terminal icon on my awn dock, the terminal window loads but immediately becomes dark and crashes. All other icons (evolution, home folder, vlc) on my awn dock do not function.

Sorry for the long post.

Any help is greatly appreciated!

Thx

---

### Post by cotcot on 2008-04-12
First thing to do is backup your critical data. You can access the ubuntu partitions by installing the [[COLOR="Red"]fs-driver[/COLOR]]("http://www.fs-driver.org/") in your windows OS. This will allow you to pick up your data on the ubuntu partitions (hoping you had it installed on the ext3 as proposed during ubunut install.

To repair the problem maybe you could reinstall the gnome-desktop from the recovery console. But wait for other suggestions on this please.

---

### Post by abh83 on 2008-04-12
> **cotcot said:**
> First thing to do is backup your critical data. You can access the ubuntu partitions by installing the [[COLOR="Red"]fs-driver[/COLOR]]("http://www.fs-driver.org/") in your windows OS. This will allow you to pick up your data on the ubuntu partitions (hoping you had it installed on the ext3 as proposed during ubunut install.

To repair the problem maybe you could reinstall the gnome-desktop from the recovery console. But wait for other suggestions on this please.

I'm not sure what u mean with ext3. However, i usually can access my ubunut partition from windows via a software i dled called: "Ext2 IFS 1.10b for windows xp".

However, as of today, i no longer can access my ubuntu partition. I get an error message in windows saying: "The disk in drive U is not formatted. Do you want to format it now?".

but it seems that all my data is still present on my ubuntu partition!

---

### Post by abh83 on 2008-04-12
btw reinstalling the gnome-desktop seems like a very smart idea! I wonder if i should go a head with it?

---

### Post by duncan.hawthorne on 2008-04-12
try starting in a safe session.

change the session at the login screen by clicking the session button, and change to gnome safe mode (named something like that)

---

### Post by abh83 on 2008-04-12
thx i'll give this a try and report back!

---

### Post by abh83 on 2008-04-12
> **duncan.hawthorne said:**
> try starting in a safe session.

change the session at the login screen by clicking the session button, and change to gnome safe mode (named something like that)

GREAT! Thx so much this worked!

I'm finally back in Ubuntu. Now how do i fix the mess?

Is it possible de-install everything i installed yesterday? Or can i restore my system to an earlier period in time?

I had to install so many dependencies i can't recall all of them.

---

### Post by duncan.hawthorne on 2008-04-12
try creating a new user in 
system>admin>user+groups as a system administrator

see if that works, 

if it does you have located the problem (it in your home folder, so uninstalling packages is unnecessary and wont fix anything) 
if so (you could either switch to a new profile, or if you feel attached to the old one), try removing entries in system>prefs>session>startup programs)

if it doesnt work, then problem is system wide

post back results

---

### Post by abh83 on 2008-04-12
great! thx to all!

I will back up my files now and then i'll try duncan.hawthorne's method.

Will post back asap!

cheers

---

### Post by abh83 on 2008-04-12
> **duncan.hawthorne said:**
> try creating a new user in 
system>admin>user+groups as a system administrator

see if that works, 

if it does you have located the problem (it in your home folder, so uninstalling packages is unnecessary and wont fix anything) 
if so (you could either switch to a new profile, or if you feel attached to the old one), try removing entries in system>prefs>session>startup programs)

if it doesnt work, then problem is system wide

post back results

So I created a new user account and trashed the old one! Its working fine again! Thx a lot for ur help. 

I was expecting the problem to be much more complicated. :)


thx to all for ur time!

---

