---
title: "Deskbar unable to open files."
date: 2007-04-26
forum: General Help
---

### Post by potrick on 2007-04-26
Hey, I've got Beagle working with Deskbar and it's quite exciting, except files won't open straight from it. Instead, I'll get a message like this:

Cannot show URL:

 'file://file%3A///home/potrick/media/audio/Louis%2520Armstrong/Unknown%2520Album'

The files doesn't open, it just gives me that message in a window. 

What's going on? Is anyone else experiencing this?

---

### Post by mithras86 on 2007-04-27
I get exactly the same! searching for documents, I get the error

> Kon programma niet uitvoeren:

'/home/jurian/some/folder/here/file.pdf'This is Dutch for "Cannot execute program". Is it a bug or something? Perhaps others have the same thing, so a bug should be filled :)

---

### Post by mithras86 on 2007-05-04
Nobody having the same problem? I have opened a bug: [http://bugzilla.gnome.org/show_bug.cgi?id=435952](http://bugzilla.gnome.org/show_bug.cgi?id=435952)

---

### Post by zarmando on 2007-05-05
> **potrick said:**
> Hey, I've got Beagle working with Deskbar and it's quite exciting, except files won't open straight from it. Instead, I'll get a message like this:

Cannot show URL:

 'file://file%3A///home/potrick/media/audio/Louis%2520Armstrong/Unknown%2520Album'

The files doesn't open, it just gives me that message in a window. 

What's going on? Is anyone else experiencing this?


I have the same problem. :guitar: 
I'm pretty sure it worked before installing Beagle.

Only the three of us ???

By the way, I'm speaking French and I wonder if it could be related to the Keyboard or character map or something...

Any ideas???

---

### Post by mwheeler on 2007-05-05
I've got the same problem. Any news of what's going wrong or how to fix it? It kind of seems like deskbar is sending bad paths.

---

### Post by soulitary on 2007-06-05
> **mwheeler said:**
> I've got the same problem. Any news of what's going wrong or how to fix it? It kind of seems like deskbar is sending bad paths.

I have the exact same problem

ubuntu fiesty
beagle + deskbar

I have beryl. maybe that is what's doing it. do any of you guys?

---

### Post by metalelf0 on 2007-06-15
I have the same problem and it's not Beryl or Beagle causing the error.
It's something much simplier: the program cannot handle correctly spaces in the links. I tried changing the name of all the folders in the pathname containing a space to names without spaces, and it worked again.

---

### Post by xilef on 2007-06-20
I have the same exact problem here. 

Feisty + XFCE + xfce4-xfapplet-plugin + deskbar

---

### Post by LMP900 on 2007-07-02
I've found a solution (the last two posts):

[https://bugs.launchpad.net/deskbar-applet/+bug/93845](https://bugs.launchpad.net/deskbar-applet/+bug/93845)

So far, opening files works perfectly, without other issues arising. I hope that helps!

---

### Post by nphx on 2007-07-09
> **LMP900 said:**
> I've found a solution (the last two posts):

[https://bugs.launchpad.net/deskbar-applet/+bug/93845](https://bugs.launchpad.net/deskbar-applet/+bug/93845)

So far, opening files works perfectly, without other issues arising. I hope that helps!
Thank you!!!

[COLOR="Red"][SIZE="4"]Confirmed that the bug fix works.[/SIZE][/COLOR]

[INDENT]In /**usr/lib/deskbar-applet/handlers/beagle-live.py** changing line number **106** to: 
>   "action": lambda d: url_show(d["uri"]),
fixes the "file://file://" redundancy issue.
[/INDENT]

---

