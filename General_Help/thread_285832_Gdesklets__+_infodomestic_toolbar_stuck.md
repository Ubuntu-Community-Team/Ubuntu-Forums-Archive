---
title: "Gdesklets  + infodomestic toolbar stuck"
date: 2006-10-27
forum: General Help
---

### Post by shane2peru on 2006-10-27
Ok, here is my problem.  I'm using Edgy up-to-date system.  I have gdesklets installed.  I was playing around with them, and seeing what they look like.  I got down to tool bars.  I added one called "Infodomestic"  Now I have a tool bar that is stuck to the mouse cursor.  Everywhere the mouse goes it goes with it.  Also, it renders the mouse useless because when you try to click on something, you click on the annoying tool bar, and that is it.  The only way I can get rid of it is to run alt-F2 ```
gdesklets stop
``` Which shuts off all my gdesklets.  When I restart gdesklets, it is there again.  How can I shut this thing off, without a mouse?  Also in the gdesklets I can't remove themes, or whatever they are because I don't have enough permissions, and when you try and run gdesklets as superuser, it refuses to let you run in superuser mode.  So I once I figure out how to get rid of this problem, I can't delete it from my system for good.  Ahhrg.  ](*,)   I think I have attached a screen shot so you can see my dilemma.  I'm open for suggestions.  Thanks!

Shane

Oh, I think I seen a post on this earlier, but I cannot find it now.  I don't know where I saw it.

Edit = ok, screen shot worked. However you cannot see the cursor, however it is right by the tool bar that is over top of the Firefox window.

---

### Post by shane2peru on 2006-10-28
^^^Bump^^^  Does anyone have any ideas about this?  Thanks!

Shane

---

### Post by shane2peru on 2006-10-28
Ok, I found it.  Hope this helps someone else.  I opened my /home directory and opened .gdesklets (it is a hidden folder)  It has a file called displays I opened it up and there was that little rascal - infodomestic - something, I deleted that line, and that took care of the problem.  

Shane

---

### Post by Phil38 on 2006-12-14
Thanks Shane, that corrected my problem as well :D

---

### Post by chipdip on 2006-12-27
W00T, thanks, I had some problems with it too, that solved everything. Thanks!

---

### Post by makhand on 2007-01-29
If anyone happens to stumble on this and would like to actually use the infodomestic bar, I have figured out a solution. Alas!, i'm too lazy to type it up unless someone asks :-).

---

### Post by Armadillo Kilr on 2007-09-23
hey guys, i had the same problem with my toolbar getting stuck to the cursor. i looked up displays in .gdesklets and couldn't find anything inside could it possibly be in another folder?

thanks

---

