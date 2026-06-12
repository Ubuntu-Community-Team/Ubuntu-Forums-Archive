---
title: "What to backup to do a fresh install?"
date: 2007-10-21
forum: General Help
---

### Post by spotdog14 on 2007-10-21
I upgraded from feisty to gusty and some things just dont really work right, they worked fine on the gusty live cd, so im guessing some of my pre existing settings conflicted with the new version.

So i would like to know what all i need to backup to save my data for a fresh install. The only things i am really worried about are my tomboy notes, and if i recall correctly they are in /home .tomboy. Should i be alright just copying this over? The second is my Evolution calendars and mail, would i be alright just copying /home .evolution? Now the next things are what i dont know, i would like to backup the themes i have installed, the login themes i have and all the icon sets i have installed. 

So if anyone could give me some pointers on this, that would be great!

Thanks!

---

### Post by Nekiruhs on 2007-10-21
You can just backup ~/.themes ~/.icons ~/.fonts for the themes.

---

### Post by por100pre1 on 2007-10-21
Use Backup Preferences to save and restore your Gnome settings:

```
sudo aptitude install gnome-reset
```

Even better is to save your whole user folder to removable media or external hard disk drive.

---

### Post by spotdog14 on 2007-10-21
> **por100pre1 said:**
> Use Backup Preferences to save and restore your Gnome settings:

```
sudo aptitude install gnome-reset
```

Even better is to save your whole user folder to removable media or external hard disk drive.

so what exactly does "install gnome-reset" do? Besides the obvious of what it sounds like, what all does it entail? Does it just take gnome itself back to the default status or the whole system?

Thanks for the help by the way guys!

---

### Post by spotdog14 on 2007-10-22
so no ideas what gnome-reset does?

---

### Post by g2g591 on 2007-10-22
for future refrerance, you only need to reformat/reinstall on your root partation if you have a seperate /home, thus saving all your personal settings and files.

---

### Post by loganm10 on 2007-10-22
just save your entire /home directory to a different place, that contains all your settings, tomboy notes, email settings, that contains everything, because as a regular user you cant write anywhere else

---

