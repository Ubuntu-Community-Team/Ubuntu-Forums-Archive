---
title: "saving email messages"
date: 2007-12-11
forum: General Help
---

### Post by Luke111 on 2007-12-11
I have started saving email messages that I have about genealogy after my disastrous time in XP and all the viruses and crap that infected the computer. Don't want to lose any information again. So my question is, when I save an email message in Evolution how do I save it as a text file and not an executable text file? I've tried opening the properties for a particular email and turning off the executable button on the permissions page. It is either a dash or a check mark and either one lets it remain an executable. For me anyway, text files don't need to be executable just readable.

---

### Post by Butthead on 2007-12-11
Personally, I (in KDE's Mail program) hit the right mouse button, choose "view source," and then copy and paste what I want to save in the particular e-mail to the Kate text program where I then save it as a *.txt file.

I don't know if it would be that much more different in Gnome?

---

### Post by Lokine on 2007-12-11
In terminal, do:
chmod -x <your file>

It should no longer be executable.

---

### Post by dcstar on 2007-12-11
> **Luke111 said:**
> I have started saving email messages that I have about genealogy after my disastrous time in XP and all the viruses and crap that infected the computer. Don't want to lose any information again. So my question is, when I save an email message in Evolution how do I save it as a text file and not an executable text file? I've tried opening the properties for a particular email and turning off the executable button on the permissions page. It is either a dash or a check mark and either one lets it remain an executable. For me anyway, text files don't need to be executable just readable.

All your Evolution e-mails are in your (hidden) .evolution directory, you can just copy this entire directory to a USB stick (or whatever) and you will have a full backup of your e-mails (do this with Evolution not running).

If your hard disk crashes you can simply restore this directory onto a fresh Ubuntu system and you will have everything from the time of the backup.

---

