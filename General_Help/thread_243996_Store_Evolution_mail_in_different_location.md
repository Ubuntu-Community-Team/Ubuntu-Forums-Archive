---
title: "Store Evolution mail in different location"
date: 2006-08-25
forum: General Help
---

### Post by mpcsm on 2006-08-25
All
I'm a newbie to Ubuntu and Linux in general (1 week old) so please excuse my non technical knowledge.

I'd love to make the switch to Linux and need to make sure my Emails are stored in a "Data" drive separate from the operating system drive.

I've already got the drive setup and has many of my personal data. What I need to know is how to configure Evolution mail to store my Emails, contacts, calendar and notes in a specific folder in the data drive rather that the default location for Evolution (whereever that is)

Any help would be appreciated....please remember I'm new at this.

---

### Post by ifokkema on 2006-08-26
I've never seen an option in Evolution to store the data elsewhere. I guess there's no easy solution for you. If you'd know the console a little, you could move the contents of the .evolution folder (where the data is) to the preferred location, and create a softlink to that new location.

If it doesn't mean a thing to you, I could give you some commands to type in the terminal.

In general: when learning stuff from the console, use 'man'.
```
man mv
```
(information about moving/renaming files and directories)
```
man ln
```
(information about creating links)

---

