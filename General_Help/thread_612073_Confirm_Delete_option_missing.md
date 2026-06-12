---
title: "Confirm Delete option missing"
date: 2007-11-13
forum: General Help
---

### Post by retrodans on 2007-11-13
This seems to be a common question, but it would seem I am missing a setting.  I type in the terminal:

gconftool-2 -g /apps/nautilus/preferences/confirm_trash

And get true as a response.  But when I click on an item with the left mouse button, and press delete on the keyboard, the item gose straight to the recycle bin, no áre you sure you would like to delete this item' prompt or anything.

In Nautilus Edit > Preference > Behaviour there are two relevant check boxes saying

Ask befoer emptying the Deleted items folder or deleting items permanently (this is checked)

Include a delete command that bypasses deleted items folder (this is not checked)

Neither of these sound like they will prompt before going to the recycle bin which is what I am after though.  As others use this machine, and it can get frustrating for me and them when they accidently swipe the delete key!

Thankyou for your help
Dan Duke

---

### Post by oldos2er on 2007-11-13
Someone correct me if I'm wrong, but I *think* the "confirm_trash" preference means the file(s) are simply moved to trash rather than being truly deleted--in other words, your system's doing what it's supposed to do. i don't know of anything in Gnome that would prompt you before being moved to trash. The whole purpose of trash is to prevent items being wrongly deleted, and/or easily recovered; your users should be able get back their files after "accidentally swiping the delete key," no?

---

### Post by Technophobia on 2007-11-13
The trash bin is a huge problem in Gnome it seems. I have read other posts about people wanting the ability to restore what was sent to the trash. Good luck with your quest.

---

### Post by retrodans on 2007-11-14
Yes it&#347; not so much a matter of losing the files, but I am trying to teach my other users about Ubuntu, and this missing alert box is causing more panic to them than necessary.  I do get an alert when I empty the trash, but it the delete between desktop and trash i after.  I think i&#314;l just have to wait and hope this is added in a later release!

Thankyou for your help

---

