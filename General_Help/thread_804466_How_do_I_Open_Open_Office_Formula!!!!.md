---
title: "How do I Open Open Office Formula!!!!"
date: 2008-05-23
forum: General Help
---

### Post by Vigh on 2008-05-23
I know this is a really dumb question but how do I open, open office formula! I want to show my dad. Cheers Anthony

---

### Post by ugm6hr on 2008-05-23
It is not installed as default - find it in Add/Remove.

Presumably it appears in the Office Menu... but I'm not 100% certain.

---

### Post by angry_johnnie on 2008-05-23
the command is

```
ooffice -math
```

Or, you could right-click on the menu, select edit menus, go to office, and then check the box next to it.

---

### Post by Vigh on 2008-05-23
Yeah I added it in Add/Remove, its not appearing in the office menu under applications where can i find the .exe. I tried typing in ooffice -math in the terminal, it says java runtime missing. Or something along the lines of that.

---

### Post by angry_johnnie on 2008-05-24
> **Vigh said:**
> it says java runtime missing. Or something along the lines of that.

Yeah, OO needs java.  Have you installed the package **sun-java6-jre**?

I'm not sure whether you'll find it in Add/Remove, but you can definitely find it in synaptic.

Or, just do

```
sudo apt-get install sun-java6-jre
```

or, maybe

```
sudo apt-get install openoffice.org
```

I don't think the entire metapackage is installed on Hardy by default.

---

### Post by keithpeter on 2008-05-24
> **angry_johnnie said:**
> 

I don't think the entire metapackage is installed on Hardy by default.

Yup, only the writer, calc and impress are installed with the drawing tools. My fresh install of Ubuntu 8.04 Hardy Heron from the 'finished' iso installed Java OK, but I had to use Add/Remove to install the maths editor. I noticed that the meta-package (the one just labelled OpenOffice.org) was not ticked.

---

### Post by billbog on 2009-01-21
I find open office org calc  incredibly hard to use .
You have to go to **view**,  **toolbars**,  **formula bar** then tick formula bar
I spent about half an hour trying to find out how to add up a column.

---

### Post by Feivel on 2009-01-21
> **Vigh said:**
> Yeah I added it in Add/Remove, its not appearing in the office menu under applications where can i find the .exe. I tried typing in ooffice -math in the terminal, it says java runtime missing. Or something along the lines of that.

exe? You still messing around with Microsloth?

---

### Post by Sef on 2009-01-21
Unhelpful posts = Necromancing = Locked.

---

