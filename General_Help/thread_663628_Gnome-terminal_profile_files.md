---
title: "Gnome-terminal profile files?"
date: 2008-01-10
forum: General Help
---

### Post by Drakx on 2008-01-10
Hi

How do I make a profile file so that I can say write a script to launch gnone-terminal with the name of the file which has the settings I want to have

set title to irssi
set with to 100
set height to 20
and start irssi

the above is what im trying to achive 

Thanks

---

### Post by Jussi Kukkonen on 2008-01-10
See *man gnome-terminal*.

You can start with a certain profile, but don't actually need to:
  --geometry=100x20
  --title=irssi
  --execute irssi

---

### Post by Drakx on 2008-01-10
Thanks

For some reason I thought it would be some kind of "special" file guess not.

Thanks.

---

### Post by Neotonian on 2008-06-11
(My apologies for earlier `replying' using the report button.)

I would really like to know where the gnome-terminal profiles are stored. The gnome-terminal man and info pages show how to launch with various options but to customize colours one has to use

gnome-terminal --window-with-profile=PROFILENAME

I use colours because I use 6 or 8 workspaces at once. (I have bad sight so use large fonts and so not much will fit on each workspace.) The different colours tell me where I am without looking at the (tiny) workspace clicker. 

I've been doing this for years but every time I use a new installation I have to create all the profiles from scratch. 

Knowledge transfer really appreciated !

N

---

### Post by drs305 on 2008-06-11
> **Neotonian said:**
> I would really like to know where the gnome-terminal profiles are stored. The gnome-terminal man and info pages show how to launch with various options but to customize colours one has to use


There are xml folders in  /home/username/.gconf/apps/gnome-terminal/profiles with all the settings for the default gnome-terminal. I imagine if you create a profile it would be stored here as well. The xml files have background, theme, color etc info.

---

### Post by Neotonian on 2008-06-12
Fantastic! There they are. I spent so much time hunting in /usr/share/gnome-terminal/ 

Many thanks!

N

---

### Post by drs305 on 2008-06-12
> **Neotonian said:**
> Fantastic! There they are. I spent so much time hunting in /usr/share/gnome-terminal/ 

Many thanks!

N

Glad you found them. An individual's settings will be found in some subfolder of the user's home directory. For gnome-related items, the folder is often .gconf  

The /usr folder is sometimes incorrectly thought of as having to do with USER, but in fact stands for "Unix System Resources".

If your questions have been answered on this issue, please mark this thread solved via the Thread Tools link at the top right of the original post.

---

### Post by Neotonian on 2008-06-12
> **drs305 said:**
> The /usr folder is sometimes incorrectly thought of as having to do with USER, but in fact stands for "Unix System Resources".

If your questions have been answered on this issue, please mark this thread solved via the Thread Tools link at the top right of the original post.

That option isn't in the Thread Tools menu, I guess because the thread was already in the archive. 

Thanks too for the tip on /usr: you read my mind on that one. 

All the best, Neo

---

### Post by drs305 on 2008-06-12
> **Neotonian said:**
> That option isn't in the Thread Tools menu, I guess because the thread was already in the archive. 

Thanks too for the tip on /usr: you read my mind on that one. 

All the best, Neo

you are welcome. i'll have to own up on this one - you couldn't mark it solved because only the original poster can do that. i hadn't noticed that wasn't you ;-)

---

