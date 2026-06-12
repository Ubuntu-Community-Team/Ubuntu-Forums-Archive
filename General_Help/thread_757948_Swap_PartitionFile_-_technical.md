---
title: "Swap Partition/File - technical"
date: 2008-04-17
forum: General Help
---

### Post by IndigoRage on 2008-04-17
Hi all, Indigo here. I'm not entirely new to Linux, but not particularly adept with it either. I've been using Ubuntu 7.10 for a couple months, and have managed to figure out how to do most things with it, even a few things I hadn't planned on figuring out in the first place.

Now I'm wanting to do something a bit different with it, but I've no idea how to go about do it, so here I am, asking the forum.

Here's what I'd like to do:

Install Ubuntu to a CF card, using a CF/IDE adapter. (Got this much done already).

Remove the Swap Partition from the CF card entirely, and place it on a regular hard drive. (This is the part I need help with).

I've done CF/IDE OS installs with Windows 2000 more than once, and it's a pretty simple process - just turn off the Swap File on the CF card, and enable it on a hard drive.

But I've no idea how to do this in Ubuntu.

I also do not speak Ubuntun worth a darn, so telling me "oh, just gksudo this, /dev/something that" isn't going to help me. I need actual commands and some detailed notes to make this work. Explainations of what the commands mean would also be helpful to me, since as I said, I'm not fluent in Ubuntun. And if this can be done via the GUI, that would be even better, though I suspect this is going to be more terminal based than anything - and that's fine, as long as I can follow the instructions I'm given.

Hey - we all had to learn sometime, right?

Thanks in advance!

Indigo

---

### Post by Het Irv on 2008-04-17
I don't know how to help you exactly, but I can point you in the right direction.

System->Administration->Partition Management

This is gParted, a good partition manager.  It is also on the Live CD, so if you are going to have to change the drive that Ubuntu is using it might be better to use it from there (its in the same place).  It sounds like if you have the right tools you can do what you need to do, so I hope this helps.

---

