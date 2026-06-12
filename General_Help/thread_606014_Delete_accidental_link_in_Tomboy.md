---
title: "Delete accidental link in Tomboy"
date: 2007-11-07
forum: General Help
---

### Post by sicofante on 2007-11-07
I've clicked on the link button in a tomboy note while the word "advanced" was selected. A new note appeared and I just deleted the note, but the link is still there, and if I click on it, a new note appears again (which I have to delete again...).

How can I undo this "Link" action and get that word back to normal?

---

### Post by erginemr on 2007-11-07
Apparently, there is no direct way to undo a hyperlinking in Tomboy, but as a work-around, you may select copy the whole text into "a hyperlink unaware" text editor, such as gedit, and select it (Ctrl+A) from gedit and copy (Ctrl+C) it once again to paste (Ctrl+V) back onto the existing Tomboy note.

---

### Post by keyboardashtray on 2007-11-07
Another thing you can do is delete the "advanced" note, and then delete and retype every instance of the link "advanced" you come across. One way, would be to go to the "advanced" note, use the tool "What links here", open all those notes, then delete the "advanced" note, and go and adjust all instances of "advanced" in those opened notes.

Not exactly super convenient, but it will get the job done. Just be sure you are careful not to click on the link again as you highlight or the note will be created again.

---

### Post by sicofante on 2007-11-07
I see. Thanks for the suggestions.

Is Tomboy beta software?

Are there any good alternatives until Tomboy is mature?

---

### Post by keyboardashtray on 2007-11-07
> **sicofante said:**
> I see. Thanks for the suggestions.

Is Tomboy beta software?

Are there any good alternatives until Tomboy is mature?

:lolflag: I take it there were too many "advanced"s to clear?

Well, you could give Zim Desktop Wiki a try, it is in the repository. This is assuming you want that wiki-style. Otherwise there is stickynotes, for very simple notes, which you should already have. Just right click and add to panel.

---

### Post by erginemr on 2007-11-08
+1 for sticky notes

---

### Post by sicofante on 2007-11-08
Zim looks interesting, thanks. Although it's not what I really need, I'll check it out for other uses.

I find sticky notes very ugly, but I guess I'll give them a try too.

On the other hand, I found some sed scripts that can "clean" broken links in Tomboy, and the workarounds suggested here might mitigate the issue too.

I'm really surprised that Tomboy, being an "official" Gnome project, has a "non-undoable" thing like creating those links. At least I expected that when the user deletes the linked note, the link would vanish with it. That's why I thought it was beta software, although after researching a bit I've come to the conclusion that it's a design flaw. And a serious one, IMHO.

---

