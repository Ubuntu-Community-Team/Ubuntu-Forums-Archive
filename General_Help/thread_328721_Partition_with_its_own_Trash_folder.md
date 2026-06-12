---
title: "Partition with its own Trash folder"
date: 2006-12-31
forum: General Help
---

### Post by jordilin on 2006-12-31
I have a partition for my data and mounted as /data separated from /home which has its own partition. When I delete some file in the /data partition it goes into the .Trash folder in this partition. It doesn't go to the general trash folder. Why is this? The same happens with USB pen drives, which GNOME automatically assign a .Trash folder to them. Is this a general rule in Gnome? I know, this is quite a silly question, but I've never know why is this.

---

### Post by Archmage on 2007-01-25
Moving a file from one partition to another would take time and will use the harddrive space of the target. Therefore each partition has it own .Trash-folder but all files can be found with the trash-icon.

---

### Post by Ramses de Norre on 2007-01-25
I think the gnome-dev's are thinking about changing this and creating only one Trash folder, which would seem much more logical to me.

---

### Post by Malac on 2007-01-25
> **Ramses de Norre said:**
> I think the gnome-dev's are thinking about changing this and creating only one Trash folder, which would seem much more logical to me.
Unfortunately this multiple trash folders thing seems to be a hang over from copying the way MS do it. Please, one trash folder gets my vote.

---

### Post by anaconda on 2007-01-25
I find the whole idea of a .Trash -folder annoying. If I want to delete something it usually means that I want to DELETE it!!  Hiding it somewhere sounds just like windows..

I am sure this can be switched of, but I usually delete fiels using the terminal. When deleteing from the terminal .Trash isn't used.

---

### Post by Malac on 2007-01-25
> **anaconda said:**
> I am sure this can be switched of, but I usually delete fiels using the terminal. When deleteing from the terminal .Trash isn't used.
You can also delete files from the GUI by pressing <Shift> then <Delete>. This bypasses the Trash folder. :)

---

### Post by Hemmer on 2007-01-25
> **Malac said:**
> You can also delete files from the GUI by pressing <Shift> then <Delete>. This bypasses the Trash folder. :)

cool - didnt know this! :D

---

### Post by Ramses de Norre on 2007-01-25
In the preferences there is a checkbox to include both "delete" and "move to trash".

---

### Post by xucrute on 2007-04-25
> **Archmage said:**
> Moving a file from one partition to another would take time and will use the harddrive space of the target. Therefore each partition has it own .Trash-folder but all files can be found with the trash-icon.

I am using Ubutu 7.04 and it foes not work like this here...
I delete a file on a second hard drive and it does not show on the trash bin at lower panel. I have to go to that partition, show hidden files, entre trash bin there and then I can see the file I deleted.

I'd like to have it all in one place... any ideas what is going on?

---

