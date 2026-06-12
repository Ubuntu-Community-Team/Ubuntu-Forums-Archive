---
title: "PLEASE HELP! Accidentally deleted an important Tomboy Note. Any way to recover it? :("
date: 2007-11-14
forum: General Help
---

### Post by enthusaroo on 2007-11-14
I'm screwed. :(

I temporarily saved some important information in a Tomboy note. Perhaps it's because I've been up all night working... but I just did something stupid by accidentally deleting that important note. Is there any way to recover it??

---

### Post by TidusBlade on 2007-11-14
I use Kubuntu so I wont really know, but If I was you, I would probably try looking in it's directory, something like* /home/name/.tomboy* or somewhere else. You could search your system for it aswell ;)

---

### Post by enthusaroo on 2007-11-14
> **TidusBlade said:**
> I use Kubuntu so I wont really know, but If I was you, I would probably try looking in it's directory, something like* /home/name/.tomboy* or somewhere else. You could search your system for it aswell ;)

Thank you so much!

Luckily Tomboy keeps a copy of notes in a folder called "Backup" under the /.tomboy directory. My data is still there.

Sweet! :guitar:

---

### Post by sharm on 2007-11-14
Hi Shaun,

Sorry I missed you on IRC.  When Tomboy deletes a note, it copies it to ~/.tomboy/backup/, so you'll want to grep through there to find your note.  Tomboy notes are XML files that end in a .note extension, and the main part of the file name is a unique ID.  Close Tomboy, find your note, move it back into ~/.tomboy, and then restart Tomboy and all should be well again.

Hope this helps,
Sandy

---

