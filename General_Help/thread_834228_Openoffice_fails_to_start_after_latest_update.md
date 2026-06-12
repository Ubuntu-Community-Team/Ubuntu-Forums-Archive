---
title: "Openoffice fails to start after latest update"
date: 2008-06-19
forum: General Help
---

### Post by hoarycripple on 2008-06-19
I'm having a strange problem after the latest hardy update with openoffice.  Whenever I try to open an ooffice application from the gnome menu, it fails to start.  If I start it from the terminal, I get no errors, and it starts normally.  If I remove openoffice-gtk, then I can open the app from the gnome main menu again.  Can someone confirm?  I am using the same parameters in the menu that I am in the terminal.  Some tips on how to get more information would also be helpful.  I am getting no error messages at the time.

The command I am using to open the app in menu/terminal is:  oowriter
It also occurrs with: oocalc, ooimpress

Thank you,


HC

---

### Post by hoarycripple on 2008-06-19
I've found an equally strange workaround for this.  Start the application with ```
oowriter -nologo
``` or any other dummy option eg. ```
oowriter -dummy-option
```  The latter still gives me the openoffice splash screen if I really want it.

---

### Post by scorp001 on 2008-06-20
Yes but for me only the nologo option works else all fails...so one cannot read any ms docs or excel directly from mail. I have to save the attachment and then open with nologo option and then open the doc - this is crazy...:confused:

Hey but thanks atleast it is opening:(

---

### Post by hoarycripple on 2008-06-20
Which applications are giving you a problem?  I can open documents directly from firefox/webmail.

---

### Post by DChamp on 2008-07-01
I'm having the same problem.
I can open an existing document, but from the menu, it pops up and goes away instantly.
Happens on all OO but Evolution which does work.

Any help would be great!

---

