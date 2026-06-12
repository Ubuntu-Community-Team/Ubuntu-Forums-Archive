---
title: "Sticky Notes"
date: 2008-06-07
forum: General Help
---

### Post by JohnnyPea on 2008-06-07
Hello, I am using "Sticky Notes" and when I make some, they always hide when I click on the desktop, can I somehow avoid this? It works normally for me before.thx:KS

---

### Post by le singe on 2008-08-11
ok, sorry JohnnyPea I don't have a solution.

I found your post searching sticky notes hoping to answer your very same question, though.  You are trying to make the sticky notes *stick* and not hide away whenever you click somewhere on the desktop, right?  "Lock Notes" does not do it, this only prevents you from editing the notes.  Nothing in preferences seems to do it.

So I'm bumping your thread as I'd like to find an answer as well.  Has anyone found a way to make sticky notes stay put on the desktop?  Thanks to any insights.

---

### Post by IamIthinkIwill on 2008-09-20
Bump. I think it has something to do with compiz-effects. I've been looking for a solution to this as well.

thanks

edit:
I've switched to xpad, and with a bit of tweaking, it shouldn't be too difficult to adjust to.

---

### Post by mb_webguy on 2008-09-20
I don't use sticky notes, so this is just a guess, but you might try enabling the Widget Layer in Compiz, and adding the sticky notes to the list of Widget Windows.

---

### Post by statikeffeck on 2008-10-08
I was also wondering why the note doesn't stay open... and then I realized that the desktop acts like a window in itself; In other words, if I have the sticky note open, then activate another window (i.e. Firefox) the note will still be there. Only if you click the desktop does it go away.

Maybe someone can find a way to make the sticky notes "always on top" -- when you right click them they don't use the standard window menu.

---

### Post by j_zhill on 2009-04-19
The sticky notes are a panel applet - so (I think) their window rules are defined by both the panel settings and the applet settings. You can see that there are two configuration entries in the configuration editor: on in /apps/panel/ and one in /stickynotes_applet or similar. I think the only way to put them always on top would be to add a key to that effect in the settings defaults. Which I have no idea how to do.

As a hack, you could put them in the widget layer by turning on compiz widgets and putting "class=Stickynotes_applet" in the windows field, then leave the widget layer on by unchecking the "end with click" setting and turning background brightness right up. Hackety-hack, it works for me.

---

