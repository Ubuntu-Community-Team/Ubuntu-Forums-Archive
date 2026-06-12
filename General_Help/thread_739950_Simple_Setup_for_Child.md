---
title: "Simple Setup for Child"
date: 2008-03-30
forum: General Help
---

### Post by Creationist225 on 2008-03-30
My 7-year old nephew (who lives with me) is very active on our computer using my account.

However, I would like to set up a separate Ubuntu account just for him that would allow him easy access to his games but also have a decent (and filtered) web browser that is easier to use for kids than Firefox.

Ideally, I would like to setup a browser that gives him a list of his favorite websites (preferably with large icons) to choose from, search Google (he loves looking for pictures of bugs) and generally just have fun online.

I do want to be able to filter out inappropriate websites, however, similar to what the Foxfilter extension does for Firefox.

I also want to completely restrict his access in his account to ONLY the applications I setup.  While I understand this can be done by simply creating icons on his desktop and removing the panels, I wondered if there was a more graceful way to do it.

If there isn't a complete solution to this yet, why not? :)  I'm sure a large percentage of Linux users have children and it would be awesome if we could have an easy way to create their own account that we could control and keep safe for them.

Any ideas?

---

### Post by niteshifter on 2008-03-30
Edubuntu?

Caveat: While I know that Ubuntu and Kubuntu (or Xubuntu) can be combined I have no idea if Edubuntu can - but since under the hood they are all the same, I should think it can be.

[http://www.edubuntu.org/]("http://www.edubuntu.org/")

---

### Post by strabes on 2008-03-30
I'm not sure how you could get simpler than firefox; maybe epiphany? It has fewer options than firefox does and has large buttons (history, bookmarks, etc) For firefox, you could install a child-friendly theme, and make the sidebar appear by default with bookmarks (ctrl+B). Another thing you could do is make the bookmarks toolbar appear by default (View -> Toolbars -> Bookmarks Toolbar) and put all his bookmarks in there. That's nice because the bookmarks toolbar also supports folders which drop down when you click on them.

As far as filtering, you could set up opendns on your router or computer and enable adult site blocking, etc. It's what I use at my house, but unfortunately it doesn't block inappropriate google image searches. [www.opendns.org](www.opendns.org)

You can restrict his account in System -> Administration -> Users & Groups.

What you suggested (removing the panel) actually sounds like a great idea. Instead of "removing" both panels, you could simply disable them from starting up. That way, when you needed to do some changes, you could simply run gnome-panel. For a 7-year-old, not enabling a panel, not putting a terminal icon on the desktop, and disabling the alt+f2 shortcut should be enough to keep him from running other applications.

I also suggest you disable various keyboard shortcuts which might confuse him, like alt+f2, run a terminal, activate window menu (alt+space), fullscreen (f11), and probably most of the other ones under the window management category. Oh yeah, another tip: inexperienced users have a hard time with the whole multiple desktop thing.

---

### Post by Creationist225 on 2008-03-30
Thank you very much for your ideas.  Edubuntu is out, however, because this is the same machine that I use myself (he simply has his own login).

I'll give it a shot setting up Firefox like you said, but I really liked the idea of the Glubble extension, just hated the implementation (couldn't set it up to automatically launch the child's interface)...

---

### Post by warp99 on 2008-03-30
I have three children under the age of 7 on the same computer using KDE with no problems. I have their favorite programs on the desktop plus I installed some children's icons and wallpaper. They all have separate shares with logins and passwords.

I also use a firefox extension called FoxFilter, which will filter out unwanted content. The current version, which is 5.3, dropped support for Linux, but version 5.1 works very well. 

Just remember to turn off printer services or use a quota otherwise you'll walk into a room filled with prints of different "designer" outfits from myscene.com. :lolflag:

---

### Post by JGrubbs on 2008-06-22
> **Creationist225 said:**
> However, I would like to set up a separate Ubuntu account just for him that would allow him easy access to his games but also have a decent (and filtered) web browser that is easier to use for kids than Firefox.

Ideally, I would like to setup a browser that gives him a list of his favorite websites (preferably with large icons) to choose from, search Google (he loves looking for pictures of bugs) and generally just have fun online.

I do want to be able to filter out inappropriate websites, however, similar to what the Foxfilter extension does for Firefox.

I have both my 6 year old and my 8 year old setup with Edubuntu on their computers, I installed Glubble on Firefox to keep them safe online. You can find both at the URLs below:

Edubuntu - [http://edubuntu.com/](http://edubuntu.com/)
Glubble - [http://glubble.com/](http://glubble.com/)

---

