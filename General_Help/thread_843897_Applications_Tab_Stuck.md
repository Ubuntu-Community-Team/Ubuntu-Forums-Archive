---
title: "Applications Tab Stuck"
date: 2008-06-28
forum: General Help
---

### Post by Saigon Saigon on 2008-06-28
I have been running Ubuntu 8.04 on an Acer 5050 AMD laptop. 

In the last few days suddenly the Applications Tab has stopped working, every time I click this it highlights but the actual list of applications fail to show up.

The System and Places Tabs next to it are working as normal.

I would be very grateful for any help to resolve this annoying error.

Many thanks.

---

### Post by Saigon Saigon on 2008-06-30
Dear Friends,

I have managed to locate the below very useful advise and have thus solved my earlier issues.

Thanks to Jollo for above! 

+++++++++++++++++++++++++++++
[SOLVED] Re: Gnome Applications menu killed by Main Menu editor (alacarte)
Ok, I got it back in working order.

The corrupted (empty) file was:

/home/affecteduser/.config/menus/applications.menu

Just copy the same file from a newly created user's home, edit it to show the affecteduser home path anywhere the original user's path is used (should be two places) and save: the Applications menu should now be now showing fine (no need to reboot).

While fixing this, I also learned that the individual user's menu dynamically includes a common file (/etc/xdg/menus/applications.menu): that's how all users get the same Applications menu.

Just a couple things:

1) IMHO alacarte is seriously flawed: a piece of software that corrupts a configuration file because the system is out of disk space (not a very exotic exception), *and* then silently fails to start because of the corrupted file (and no other way to fix it) is to be considered broken, and should be fixed. Ok, it's just a very simple ultility, but screwing the main menu can be distressing for inexperienced users or plain 'human beings', which is all Ubuntu is about, isn't it?

2) I am not impressed with the replies to this post: as a new member of this forum, I tried hard to follow the 'be as descriptive as possibile' guideline. Perhaps too much: looking around I noticed way too generic posts (like 'gnome menus are a pain in the a**') that got extensive assistance, discussion and so forth... Next time I'll try to be a little more misterious...

Thanks anyway for the forum administration: good job and useful info.

Take care
__________________
Free islands of the world, unite!

---

