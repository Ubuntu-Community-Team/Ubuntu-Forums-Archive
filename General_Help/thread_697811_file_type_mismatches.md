---
title: "file type mismatches"
date: 2008-02-15
forum: General Help
---

### Post by kaufmannn on 2008-02-15
I don't know what it is called but shortly after installing 7.10 through Wubi I installed something which allowed me to access my main NTFS partition through Ubuntu. This works great, I can use the NTFS for storage and then use those files if I need to go into Vista (rarely).

Anyways, my problem is such: when I double click on .pdf, .avi, and many other filetypes which are on my windows partition, I get the following error -

> Cannot open filename.pdf

The filename "filename.pdf" indicates that this file is of type "pdf document". The contents of the file indicate that the file is of type "PDF document". If you open this file, the file might present a security risk to your system.

At that point I have to right-click on a file and choose the program to open it with. The files then work fine. Also, moving the file over to Ubuntu doesn't seem to fix it, though if I download the file straight to Ubuntu it opens fine.

Anything I can do?

---

### Post by aysiu on 2008-02-15
This is more of a workaround than a solution, but you can try using a different file manager--Thunar or Konqueror instead of Nautilus.

---

### Post by kaufmannn on 2008-02-15
What would that entail? Konqueror is the file manager for KDE is it not? I'm essentially happy with what I'm using (though you could say I just don't know any better)... point remains I don't want to do anything drastic. It's not like it's a serious problem, just a minor inconenvience. 

Thanks for the helpful input, though I doubt I will take it.

---

### Post by antofthy on 2008-07-01
I have been battling this problem for years, on and off. but no one seemed to have an answer.   However I have now finally found the solution in a 'fedora' forum.

The problem is that you personal 'mime' settings do not match the system mime settings.  I have no idea what cases this but it screws up left clicking to open documents.  The solution is simple.
```
rm ~/.local/share/mime/globs
```
Now logoff and log back in.

If this does not work you can also try running
```
update-mime-database /usr/share/mime
```
as the root user.   I myself did not need this.

---

