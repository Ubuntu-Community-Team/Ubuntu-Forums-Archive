---
title: "Dropbox won't change default directory in 12.10"
date: 2012-10-19
forum: General Help
---

### Post by bclintbe on 2012-10-19
Seems to be a problem in the 64 bit version of Dropbox. On a fresh install of 12.10 I need to be able to set a different path for the Dropbox directory (not the standard placement in Home). Although I’ve done this before, now when I try to change it in the advanced settings it sticks with the default directory. Can’t get it to actually change to a different drive/directory.

---

### Post by davidbragat on 2012-10-20
I'm have the same issue.:(

---

### Post by ciociocio on 2012-10-21
+1 same issue

---

### Post by ciociocio on 2012-10-22
> **ciociocio said:**
> +1 same issue

Also fresh install and 64bit. You can browse for another folder, but it always remain in /home/user

---

### Post by bra|10n on 2012-10-22
Perhaps a solution is to edit the dropbox.rc file by hand in your home directory.

---

### Post by rdaguls on 2012-10-22
Worked!

In window "Select a Folder" click on icon "Type a file name", so you can write the patch, ex:  /mydir/mystuff/
So it will create /mydir/mystuff/Dropbox, or will use it if already exists.

This way worked for me.

I know, my english is terrible... sorry.

---

### Post by ciociocio on 2012-10-22
> **rdaguls said:**
> Worked!

In window "Select a Folder" click on icon "Type a file name", so you can write the patch, ex:  /mydir/mystuff/
So it will create /mydir/mystuff/Dropbox, or will use it if already exists.

This way worked for me.

I know, my english is terrible... sorry.

Thanks! It worked, but I'll explain what I did.

I created a new Dropbox folder, as I couldn't sync with the old one, but when I tried to sync writing the name of the new path, it says that there's already a dropbox folder, and didn't offer an option to resync.

Exit dropbox, rename the new Dropbox folder to Dropbox.old, and enter dropbox again.

I will say that you have to resync, so you write your path to your beloved old folder and it will sync at last! :guitar:

---

### Post by CyborgMax on 2012-10-24
I cannot write a path. It's greyed out. :(

---

### Post by Chodid on 2012-10-31
The "type filename" workaround worked for me too. 
You have to open the dialogue to choose a folder - there, in the top left corner, you'll find a button with three dots and a pen on it. Click on that button and type the exact path to the location you want Dropbox to put your Dropbox Folder. (eg. "/home/username/Backup/" for the Dropbox folder being "/home/username/Backup/Dropbox")
Best regards,
Chodid

---

### Post by lyn240690234 on 2012-11-14
> **rdaguls said:**
> Worked!

In window "Select a Folder" click on icon "Type a file name", so you can write the patch, ex:  /mydir/mystuff/
So it will create /mydir/mystuff/Dropbox, or will use it if already exists.

This way worked for me.

I know, my english is terrible... sorry.

Thanks!!! It works for me as  well. I wonder this is a bug of Dropbox.

---

### Post by Shinger on 2013-01-08
> **Chodid said:**
> The "type filename" workaround worked for me too. 
You have to open the dialogue to choose a folder - there, in the top left corner, you'll find a button with three dots and a pen on it. Click on that button and type the exact path to the location you want Dropbox to put your Dropbox Folder. (eg. "/home/username/Backup/" for the Dropbox folder being "/home/username/Backup/Dropbox")
Best regards,
Chodid


YES!!!.. Did also worked for me.

---

### Post by speichmans on 2013-03-13
Worked for me. Thanks for the tip.

---

### Post by ankur.trapasiya on 2013-04-06
> **Chodid said:**
> The "type filename" workaround worked for me too. 
You have to open the dialogue to choose a folder - there, in the top left corner, you'll find a button with three dots and a pen on it. Click on that button and type the exact path to the location you want Dropbox to put your Dropbox Folder. (eg. "/home/username/Backup/" for the Dropbox folder being "/home/username/Backup/Dropbox")
Best regards,
Chodid

Hey thanks a lot. It worked for me too.

---

