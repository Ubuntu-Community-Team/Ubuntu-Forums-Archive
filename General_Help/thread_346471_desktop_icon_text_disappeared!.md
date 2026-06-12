---
title: "desktop icon text disappeared!"
date: 2007-01-25
forum: General Help
---

### Post by dennis1200 on 2007-01-25
I recently installed Edgy (and love every bit of it - truly replaces windows now that I found CUPS GUIs like gtklp), but icons on my desktop have no text. Not invisible, not blending in, just not there. They were there early on, then I tried out some themes (currently aqua skinned), and the text vanished forever (regardless of what theme I use now).  It is annoying when dealing with my removable hard drive, since there are two partitions - fat32 and ext2. Both are backup functions, basically, though the fat32 has stuff like music and pictures not on my comp harddrive. When I want to open one, I have to guess, since the icons are the same and there is no text beneath.

I've seen lots of posts on how to make icons without text, but I want the text back! Any ideas?:roll:

Also, the icons now have a default size that is really tiny (smaller than a mouse cursor), meaning I have to stretch anything I put on there.

---

### Post by dennis1200 on 2007-01-31
Man, am I really the only one with this problem? 18 views in a week!?:shock:  I'll bump just this once, in hopes...

---

### Post by dennis1200 on 2007-03-06
Not so much a bump as a slight update - it is not a system-problem, only a user problem. I created a new user account to test things out and icon size is correct, and text appears correctly. Does that help diagnose the problem and lead to a solution?

---

### Post by bjornolai on 2007-03-14
Maybe you've gotten it fixed by now, but anyhow: Goto System > Preferences > Menu and toolbar preferences.  In the toolbar button labels drop down menu choose eg. text below icons.

Hope this resolves the problem :)

---

### Post by dennis1200 on 2007-03-17
That is already selected. And that is more for menus and toolbars, not desktop icons. I still haven't figured it out, sadly. Probably some gconf value, but I haven't found it (they all look to be in order).

---

### Post by dennis1200 on 2007-08-04
After leaving it for abandoned, I checked again in gconf-editor, and searched for "icon" entries. Sure enough, the nautilus icon settings were somehow set to "smallest". I changed it to standard and the size was right (and the text re-appeared!)

---

