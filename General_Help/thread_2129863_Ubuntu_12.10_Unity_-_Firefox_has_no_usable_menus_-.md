---
title: "Ubuntu 12.10 Unity - Firefox has no usable menus - how do I add a bookmark?"
date: 2013-03-27
forum: General Help
---

### Post by ArlieS on 2013-03-27
I'm running Ubuntu 12.10, with the Unity desktop manager. With a firefox window selected,  the menus at the top of the screen don't appear when hovered over. I get the titles, e.g. "Help" or "Bookmarks" but when I select them I get what looks like an empty stub. Keyboard shortcuts work, when I remember them. Unfortunately I don't remember the keyboard shortcut to add a bookmark. (I can get my bookmarks in a side panel of the firefox window by using Ctrl-B, fortunately.)

This is driving me crazy. Is this a known bug with some version of firefox, unity, some library, etc.? I.e. will upgrading to the latest versions of everything help, or better yet, is there a specific version of something I can instal individually? (I'm afraid to simply let update manager do its thing, or even do "sudo apt-get upgrade"; my experience with 12.10 has been that every time I do that, I spend 2 or 3 days with impaired functionality, sometimes approaching unusability. So now I only instal fixes if I have some specific reason to believe they'll fix something important *to me*.)

Also, is there a keyboard shortcut to add a bookmark? I'd rather memorize a keyboard shortcut than upgrade anything, given the stability issues I've experienced with upgrades to 12.10. 

I'll happily post specifics of what versions I have, if someone will tell me how to extract that information in convenient form. IIRC, I last permitted update manager to do its thing approx. 2 weeks ago, after the box re-developed a habit of losing access to one or more monitors almost every time I let it get idle to the point of the screen going dark. That fixed the big graphics problem, at least for now, but it's probably when I picked up the firefox/unity interaction problem.

AFAIK firefox is the only application affected. Menus for pidgin and 'terminal' work correctly.

---

### Post by ArlieS on 2013-03-27
This looks like [http://ubuntuforums.org/showthread.php?t=2128579](http://ubuntuforums.org/showthread.php?t=2128579)

I found a way out of my specific problem. Most menus still aren't working, but I can now add a bookmark. 

First fiddle around right clicking various areas near the top of the firefox window. If you get the right spot, you'll get an option to enable a bookmarks toolbar. Actually, you'll get a set of check marks for toolbars you can enable. I'd describe this better, but once I selected the bookmarks toolbar, I was never able to find this menu again. 

Enabling the bookmarks toolbar gives you some useless looking buttons and menus with titles like "most visited" and "getting started". But if you right click in line with those useless items, you get a menu that includes some of the options that were on the old bookmarks menu, including "new bookmark" etc. None of them are marked with keyboard shortcuts. 

So far so good - but how do I get e.g. the contents of the old "tools" menu?

---

### Post by Frogs Hair on 2013-03-27
A simple way to bookmark in Firefox is double clicking the star in the URL box . This opens the edit dialog and you  can shorten the title and move to a folder from there.  If you right click the bar in the tab area  and go to customize it's possible to drag the bookmarks menu drop-down indicator to the tab area. It may not appear if placed on the URL bar area depending on how many indicators are there already If you disable the global menu integration in add-ons > extensions and restart you can have the old style menu bar or tab menu access.

---

