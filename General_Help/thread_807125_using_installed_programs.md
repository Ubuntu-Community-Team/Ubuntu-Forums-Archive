---
title: "using installed programs"
date: 2008-05-25
forum: General Help
---

### Post by the.fubz on 2008-05-25
How do you use programs that you install in Linux?  I cannot find programs I install.  for example using the Synaptic Package Manager I installed context so I had some sort of editor besides the terminal editor but I cannot find it in the "Open With..." dialog.  

Thanks.

---

### Post by jimbob on 2008-05-25
Open a terminal and enter **[COLOR="Blue"]locate context[/COLOR]** - will list all files with that name in them.

---

### Post by the.fubz on 2008-05-25
I get way too many results that the terminal does not let me scroll up all the way to read them.

---

### Post by jimbob on 2008-05-25
OK - pipe it to more and you will get one screen at a time:

**[COLOR="Blue"]locate context | more[/COLOR]**

---

