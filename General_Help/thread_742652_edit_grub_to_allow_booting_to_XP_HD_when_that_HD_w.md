---
title: "edit grub to allow booting to XP HD when that HD was previously a Vista HD"
date: 2008-04-01
forum: General Help
---

### Post by theknowledgeist on 2008-04-01
Hello folks,

When I first installed Ubuntu and grub onto my computer, I had two hard drives: one with Ubuntu, and one with Vista. I have since dumped Vista because it is crap, and I replaced the Vista hard drive with a different hard drive that has XP installed. 

How do I edit grub so that it will now work with my XP hard drive?

I am a Ubuntu noob, and I'd prefer to do this without using the command line if possible. 

Gracias.

---

### Post by dcstar on 2008-04-01
> **theknowledgeist said:**
> Hello folks,

When I first installed Ubuntu and grub onto my computer, I had two hard drives: one with Ubuntu, and one with Vista. I have since dumped Vista because it is crap, and I replaced the Vista hard drive with a different hard drive that has XP installed. 

How do I edit grub so that it will now work with my XP hard drive?

I am a Ubuntu noob, and I'd prefer to do this without using the command line if possible. 

Gracias.

Post the contents of your /boot/grub/menu.lst file.

---

### Post by kbless7 on 2008-04-01
In your grub menu, you'll have a list with vista as one of the titles. Just change the title to XP and make sure the root is set to the new hard drve location, ie hd1, hd2, etc.

---

