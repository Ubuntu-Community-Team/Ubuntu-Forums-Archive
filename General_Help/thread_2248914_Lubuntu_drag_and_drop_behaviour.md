---
title: "Lubuntu drag and drop behaviour"
date: 2014-10-18
forum: General Help
---

### Post by rdh61 on 2014-10-18
Hi,

In Lubuntu 14.04 when I drag and drop a file I expect to be moved from one place to the other. Sometimes, inexplicably to me, this does not happen - instead, a link to the file is created in the location I want to drop it to. To my knowledge I have done nothing to trigger this behaviour, and I can't find a way to change it back to what I want, short of rebooting. Can somebody please explain why this might be happening, and what to do to get normal behaviour back? 

Many thanks.

---

### Post by prshah on 2014-10-18
The created file behaviour varies depending on the source / target.

If you are dragging and dropping a file from one filesystem to the same filesystem (eg a folder from your home directory to another folder in your home directory) then the file is usually MOVED.

If you are DnD between file systems (eg, home directory to your pen drive), then the file is usually COPIED.

You can modify the behaviour by using CTRL (always copy), SHIFT (always link) or ALT (Ask) keys before releasing the drag button.

---

### Post by prshah on 2014-10-18
The created file behaviour varies depending on the source / target.

If you are dragging and dropping a file from one filesystem to the same filesystem (eg a folder from your home directory to another folder in your home directory) then the file is usually MOVED.

If you are DnD between file systems (eg, home directory to your pen drive), then the file is usually COPIED.

You can modify the behaviour by using CTRL (always copy), SHIFT (always link) or ALT (Ask) keys before releasing the drag button.

---

### Post by rdh61 on 2014-10-18
Thank you for your reply.

> **prshah said:**
> If you are dragging and dropping a file from one filesystem to the same filesystem (eg a folder from your home directory to another folder in your home directory) then the file is usually MOVED.

Exactly, USUALLY, but in my case not always. Sometimes, as explained before, it is linked to. That is the problem. This happens randomly, without my pressing any other key (CTRL, SHIFT, ALT, etc.). Here I am talking only about DnD to the same file system.


> **prshah said:**
> You can modify the behaviour by using CTRL (always copy), SHIFT (always link) or ALT (Ask) keys before releasing the drag button.

As simple DnD to move files is working normally now as I type, I just tried the modifiers you suggested. CTRL and ALT do as you say, SHIFT has no effect. (Remember I am on Lubuntu not Ubuntu, does that make a difference?) Well, at least by using ALT I will be able to get it to do what I want next time it's misbehaving (hopefully).

---

