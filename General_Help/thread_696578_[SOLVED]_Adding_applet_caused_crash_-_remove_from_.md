---
title: "[SOLVED] Adding applet caused crash - remove from terminal?"
date: 2008-02-14
forum: General Help
---

### Post by Shampyon on 2008-02-14
I'm using kUbuntu Gutsy, with Compiz. Everything was going fine until I added an applet (I can't remember which one, sadly) to my kde panel and a little crash occurred, taking me out to the login screen. I try to log in, and as the panel loads the crash occurs again.

Silly me. If anyone were to take a look through the threads I've started, and probably most of the threads I've posted in, they'd notice that I always manage to cause myself trouble whenever I try to customize the look and feel of my desktop :P

How would I go about removing this applet through the terminal? Or is there perhaps another way around this?

---

### Post by Crooksey on 2008-02-14
You can remove all of your KDE settings with..

```

rm -rf ~/.kd*
```

This will reset your desktop to the default kde, so be carefull :)

---

### Post by Shampyon on 2008-02-14
In my impatience I did something a little sillier than that. I used *gconftool-2 --recursive-unset /apps/avant-window-browser* to reset AWN to default because I'd read that using the same applet in panel and AWN can cause conflicts in some instances. That wasn't the silly bit. 

The silly bit is that I used *ls /home/myusername/.kde/share/config/* to see the config files in terminal, then use *rm* to delete some. I think I may have deleted some files related to my Storage Media, because my drives aren't showing up in the Storage Media applet any more - the applet's completely empty.

See what I mean about causing myself trouble?

 :P

---

### Post by Shampyon on 2008-02-17
Using GDM instead of KDM seems to have solved this problem.

---

