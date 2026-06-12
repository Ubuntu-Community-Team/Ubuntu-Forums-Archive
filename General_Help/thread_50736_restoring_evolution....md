---
title: "restoring evolution..."
date: 2005-07-21
forum: General Help
---

### Post by gammyhand on 2005-07-21
I backed up the .evolution directory when I re-installed. I now put it back but evolution does not load up with the correct settings and email. It just says it needs an account setting up. I have changed all the files to allow read/write/execute for the owner (I had to do that with the .amule directory to get that program working where it was).

---

### Post by soonindallas on 2005-07-21
I'm interested in this too... I will have to return my laptop under warranty for a screen problem and I will want to restore my evolution to the point I'm at when I send it back.

your help appreciated to find out what needs to be saved, and how to restore it, to keep the profiles and mail folder contents.

thanks

/PC

---

### Post by Majlo on 2005-07-21
Hi ..

I backup evolution with these commands

[I]gconftool-2 --shutdown
evolution-2.0 --force-shutdown
cd ~
tar -cvzf evolution.tar.gz .evolution .gconf/apps/evolution .spamassassin .gnome2_private/Evolution[/I] 

You must backup also .gconf/apps/evolution & .gnome2_private/Evolution .Or too .spamassassin

---

### Post by gammyhand on 2005-07-21
[QUOTE=Majlo]Hi ..

I backup evolution with these commands

[I]gconftool-2 --shutdown
evolution-2.0 --force-shutdown
cd ~
tar -cvzf evolution.tar.gz .evolution .gconf/apps/evolution .spamassassin .gnome2_private/Evolution[/I] 

You must backup also .gconf/apps/evolution & .gnome2_private/Evolution .Or too .spamassassin[/QUOTE]
 Unfortunately the advice I was given before I reinstalled was to backup the .evolution directory and all would be fine. I wish I had checked it out more. Thanks.

---

