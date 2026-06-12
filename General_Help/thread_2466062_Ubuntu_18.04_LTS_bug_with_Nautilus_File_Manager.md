---
title: "Ubuntu 18.04 LTS bug with Nautilus File Manager"
date: 2021-08-18
forum: General Help
---

### Post by db75oh on 2021-08-18
I use File Explorer constantly, and this bug has been going on for many months. I could almost move to another distro, but have been putting up with it. I spent weeks wondering what I was doing wrong, until I realized that this was an OS flaw.

When using the GUI "File Explorer", which is a core part of Ubuntu (not sure about 20.04 LTS or later). when you drill down into a folder, then later move back up - the previous sub-folder visited, remains in the title bar. This tells you that you're in the previous folder, although you've navigated away from it.

Even Win10 builds do not have this problem. Please fix it - it is driving me crazy! This should fall under a "bugfix" that could be deployed without having to change LTS level. Thanks.

---

### Post by db75oh on 2021-08-18
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289001&stc=1[/IMG]

Posted a screenshot. As you can see, I had seconds ago, drilled down into the folder I named "I-was-here-before". I then went up a level to the mounted drive "data0". However, "I-was-here-before" remains in the top bar's folder tree of where you are at.

Yes, I can manipulate files and folders from a terminal. But the GUI is very frustrating, if you spend alot of time here, and don't really know where you're at.

---

### Post by monkeybrain20122 on 2021-08-18
Well I think it is a feature rather than a bug. i.e it is intentional. As far as I can remember Nautilus (gnome file) always behaves like this. I suppose the idea is to keep track of where you have been? If you look carefully the color of "where-I-was-before" is a bit different from your current path, meaning that it is not a part of the current path.

If you want to show the actual current path you can just press ctrl+L (say you need to cut and paste), you can make it the default behaviour in settings.

Also it is not a core part of Ubuntu, not even a core part of the gnome desktop. I have replaced it with nemo as the file manager in gnome because its other "features" are driving me nuts and I have removed it. Nothing blows up.

---

### Post by monkeybrain20122 on 2021-08-18
OK, I just checked Ubuntu 21.04 vm where I still haven't delete nautilus and it doesn't show last visited location.  Since I have ritualistically removed nautilus since the latter part of 16.04 I don't have an earlier version of nautilus to compare on other versions of Ubuntus.

---

### Post by db75oh on 2021-08-18
I tried the CTRL+L that you mentioned. It just changes the GUI focus to the path in the taskbar.

If this is a "feature" - well I can't imagine that. I have to think that these things went through Ubuntu QA and user feedback before going live?

What do others have to say? Clearly, I despise this "feature" and Windows sadly, is the leader on these things. Even they - in Win10 1909 and 20H2 - do not force users in a folder view - to see where they were?

Feedback beyond me may be needed. I get that. I'd encourage others to give input. Some others have the same feelings as me.

Otherwise, I'd think this thread should be moved to a dev or other forum. Is "General Help" the best place? I dunno; I posted here as the best place to start. Thanks.

---

### Post by Impavidus on 2021-08-19
Definitely a feature. the different parts of the path are on different buttons, so you can quickly move up and down by clicking them – I assume. I don't use Nautilus myself, as I'm on Xubuntu. And I don't really use the file manager anyway.

Of course, you can report that you don't like it, but some devs liked it, so it may be less easy to convince them to change it. And in any case, only bugfixes are backported to older Ubuntu releases. A new feature may only appear in a new release of Ubuntu.

---

### Post by dragonfly41 on 2021-08-19
I admit I had not noticed this <feature> before .. I use Krusader as my file manager .. 
but this seems to offer a left-to-right history of folders clicked .. like a breadcrumb trail.

---

### Post by tea for one on 2021-08-19
> **db75oh said:**
> I use File Explorer constantly, and this bug has been going on for many months. I could almost move to another distro, but have been putting up with it. I spent weeks wondering what I was doing wrong, until I realized that this was an OS flaw.

When using the GUI "File Explorer", which is a core part of Ubuntu (not sure about 20.04 LTS or later). when you drill down into a folder, then later move back up - the previous sub-folder visited, remains in the title bar. This tells you that you're in the previous folder, although you've navigated away from it.

Even Win10 builds do not have this problem. Please fix it - it is driving me crazy! This should fall under a "bugfix" that could be deployed without having to change LTS level. Thanks.

No need to be driven crazy by a [COLOR="#0000FF"]feature[/COLOR] ;)
Although, I'm using Ubuntu 20.04 with Files (nautilus) 3.36.3, I'm pretty sure that the versions are similar.

When you have opened two destinations in the file manager, have a play with the arrows in the top left (screenshot attached)
I think that it's a clever way to move between two file locations within the same window.

---

