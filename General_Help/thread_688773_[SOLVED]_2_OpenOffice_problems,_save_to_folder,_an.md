---
title: "[SOLVED] 2 OpenOffice problems, save to folder, and printing"
date: 2008-02-05
forum: General Help
---

### Post by shane2peru on 2008-02-05
Ok, I have two problems and have searched but not turned up anything.  These are probably pretty easy, I just don't know the answer.

1.  save to folder problem:

  Ok, this is a minor annoyance, and I don't know if it is with OOO, or a setting in gnome.  I noticed that Ubuntu added this Documents folder to my /home directory, which I already have my setup, and really don't care to change now.  Everytime I try and save a new document it sends me to this folder, is there any way I can just have it send me automatically to my /home directory?  I know it is minor and only one click to get out of that folder, but I would like to not have to make that extra click any longer.  

2.  printing problem

  This too is a minor annoyance that should be a simple fix somewhere.  I live in Peru and only have access to A4 paper, not letter.  So I set my printers in the printer setup to always use A4 paper.  However in Draw or writer, when I try and print something, OOO always assumes I'm using Letter size paper (this is not good if you are trying to do a project and placement is important).  My printer setting is set to A4 does anyone know how to let OOo know about this setting?  

Any help on these would be greatly appreciated.  Thanks.

Shane

---

### Post by seventhc on 2008-02-05
If you open open office word processor click on *Tools>Options>Paths*
you can edit those lines, so just point '*My Documents*' to the folder you want
I don't have a printer set up here, so I can't help with that. I'm sure someone here can though. :)

---

### Post by shane2peru on 2008-02-05
> **seventhc said:**
> If you open open office word processor click on *Tools>Options>Paths*
you can edit those lines, so just point '*My Documents*' to the folder you want
I don't have a printer set up here, so I can't help with that. I'm sure someone here can though. :)

Thanks, I knew there had to be a simple trick to fix that!

Shane

---

### Post by seventhc on 2008-02-05
You're Welcome :)
I just found something about printing, they actually needed to do the opposite of what you need, but it will work the same for both. here is the link:
[http://www.oooforum.org/forum/viewtopic.phtml?t=802](http://www.oooforum.org/forum/viewtopic.phtml?t=802)

**Edit: **This is much easier, I left the above in case there is anything useful but to set default paper size do this: Open a terminal and put this in
```
gksu gedit /etc/papersize
```It is most likely set to letter, so just change that to a4. Hope that helps. :) 
You will also need to close open office and reopen it before the changes take affect. (If it was open while making the changes)

---

### Post by shane2peru on 2008-02-05
> **seventhc said:**
> You're Welcome :)
I just found something about printing, they actually needed to do the opposite of what you need, but it will work the same for both. here is the link:
[http://www.oooforum.org/forum/viewtopic.phtml?t=802](http://www.oooforum.org/forum/viewtopic.phtml?t=802)

**Edit: **This is much easier, I left the above in case there is anything useful but to set default paper size do this: Open a terminal and put this in
```
gksu gedit /etc/papersize
```It is most likely set to letter, so just change that to a4. Hope that helps. :) 
You will also need to close open office and reopen it before the changes take affect. (If it was open while making the changes)

Thanks again!  Saved the day on two accounts.  :lolflag:

Shane

---

