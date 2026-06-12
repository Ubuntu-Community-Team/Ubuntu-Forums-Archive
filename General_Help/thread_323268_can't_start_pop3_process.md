---
title: "can't start pop3 process"
date: 2006-12-21
forum: General Help
---

### Post by squrl on 2006-12-21
Can someone please tell me why I would get "can't start the pop3 process when I try to retreive or send mail in kmail. I like the program and menu but can't get it to send or receive.

Thanks

---

### Post by Jussi Kukkonen on 2006-12-22
You could try running kmail from the command line, maybe it outputs something more informative there...

---

### Post by wireddad on 2007-01-06
Hello,

I am having the same problem.  Any luck?

---

### Post by squrl on 2007-01-09
Yeah I went back to evolution

---

### Post by wireddad on 2007-01-09
My fix was to reload Kubuntu and all is good.  :)

---

### Post by suzao on 2007-02-05
For the record, when using kmail on GNOME a significant number of kdelibs need to be installed.  They are not linked as dependencies to kmail, so they don't get installed automatically. Installing kdebase-kio-plugins and dependencies will take care of this problem.

Probably most of the packages are unnecessary but difficult to tell which ones.  Kmail and Kontact are worth it in my opinion.

---

