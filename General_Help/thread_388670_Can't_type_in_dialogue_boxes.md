---
title: "Can't type in dialogue boxes"
date: 2007-03-19
forum: General Help
---

### Post by jiminy on 2007-03-19
I've got a nasty feeling this problem might be unique: whenever I call up a dialogue box in an application (say, Find in gedit) I can't type in text fields in it. The field is highlighted as normal, the cursor stops flashing, but no text appears, and in the case of "find" boxes, the actual "find" button remains dimmed.

I'm running Ubuntu Edgy on PowerPC, and have previously set up SCIM (without difficulty) and tried to install KMFL (without success); I also have my modifier keys remapped to something a bit more sensible for a Mac laptop keyboard (basically, Control is remapped to Command, alt/Meta to Control, and the faux-keypad enter key to Compose). Unfortunately, I'm not sure exactly when the problem started, so I can't hold any one of these things responsible with any certainty.

*Edited to add:* Problem solved&#8212;but only by disabling SCIM altogether (using the method of removing the Input Method configuration file described [here]("https://help.ubuntu.com/community/SCIM"), though I used mv rather than rm -rf in case I need the file again later). This is slightly less than ideal, but I don't absolutely need it, so it'll do for now . . .

---

