---
title: "[SOLVED] Gutsy, Nautilus and the Documents icon"
date: 2007-10-19
forum: General Help
---

### Post by adam_kimber on 2007-10-19
After upgrading to Gutsy several things broke all bar one I have fixed. I am having the utmost problem trying to get the Documents folder to appear on my desktop again. Last time it was simple, fire up gconf-editor and click "documents_icon_visable" and presto the icon appears. 

However after the upgrade the icon has gone and when i go to the setting in the gconf-editor is now states "The key has no schema". 

I have removed the .gconf directory and replaced this with a backup however the problem persists.

Does anyone has any suggestions as to the problem might be? 

Adam

---

### Post by DagMan on 2007-10-20
Can you drag and drop it out from  the menu maybe?

---

### Post by Chonnawonga on 2007-10-20
Hrm. At first I thought, "Aha! It's too easy!" But that only seems to be creating a new folder called "Documents" on the Desktop, unrelated to the "real" Documents folder.

Any other ideas?

---

### Post by DagMan on 2007-10-20
No none from me.  I'm confused about what the real Documents folder is though.  If it has a location you can browse with nautilus then you should be able to drag and drop it from there but if not then I don't know either.

---

### Post by misfitpierce on 2007-10-20
Drag to panel and then to desktop... or go to terminal and type gconf-editor

apps-nautilus-desktop

Enable desktop icons of choice.

---

### Post by Chonnawonga on 2007-10-20
Thanks, misfitpierce.

Confirmed: dragging the documents icon from the "Places" menu onto the panel and THEN onto the desktop works.

gconf-editor doesn't, as that option seems to have been removed (or perhaps just moved?) for this release. Go figure.

---

### Post by adam_kimber on 2007-10-21
Confirmed. This works as it originally did as my temporary solution was to create a shortcut to Documents but when using breadcrumbs it thinks it on the Desktop, anyway its back to normal now. 

This is great! I got my link back. Thanks guys. 

And why on earth would they remove that option from gconf :confused: That is silly.

---

