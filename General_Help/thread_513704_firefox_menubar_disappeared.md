---
title: "firefox menubar disappeared"
date: 2007-07-30
forum: General Help
---

### Post by willnapier on 2007-07-30
Hi. I have no idea what I did, but I now don't have a menubar showing in firefox. I am using feisty and firefox 2.0 (I don't have access to the help-about so I can't be more specific about the release). How can I restore it? Due to not having the menubar, I don't have access to the 'view' menu which I would normally use to hide or show toolbars. I hope there's a simple answer - something like going to about:config perhaps? Fortunately I know the keyboard shortcuts to bring up the search (ctrl-k) or the address bar (ctrl-l) so I can access about:config, but I'm not sure that is the solution.

I have the compactmenu extension which may further complicate things - I wonder if alt-v would normally bring up the view menu, but if it would normally, it won't due to my having this extension.

Any help greatly appreciated.

Will

---

### Post by AlexThomson_NZ on 2007-07-30
It's not in fullscreen mode (F11)?

---

### Post by willnapier on 2007-07-31
Nope I can toggle that with F11 but it makes no difference to the absence of the menubar.

---

### Post by willnapier on 2007-08-08
Solved!

For the benefit of other unfortunates, I have just worked out what happened. My solution to this was unnecessarily drastic: I uninstalled firefox, but saved some of my profile files. So I was ok again. Just now it happened again - my menubar just disappeared for no apparent reason. This time I hit upon the solution:

If you have any other toolbars still showing, take the cursor as far to the right or left edge as it will go (but on the same level/height as the showing toolbar), then right-click. It will offer you the menu of toolbars to view. Reselect menubar.

Here's what I think I did: I was using a mouse-gesture to go back (right-click and drag to the left), but I happened to start the drag at the extreme right edge of one of the toolbars. This will have momentarily shown a context menu offering me choice of which toolbars to view, and the rest of the drag will have randomly deselected the menubar.

I hope this helps anyone else who comes across this obscure problem.

Will

---

