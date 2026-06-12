---
title: "How can I open rar files?"
date: 2006-12-22
forum: General Help
---

### Post by jcroot on 2006-12-22
I would like to know how can I extract RAR files in Ubuntu 6.10, I don't know how to do it, I tried installing the non free rar from the terminal but it didn't work, I think the non rar is not support any more.

I search the forum for any help and I tried almost everything but no luck. :-|

---

### Post by Antarctica on 2006-12-22
Well, there's always Wine and WinRAR, although that wouldn't be convenient.  Have you tried installing the additional archiving tools from Automatix2?

---

### Post by raul_ on 2006-12-22
It's pre installed. 
```

man rar

```

You could always right-click the file and choose "extract here" :mrgreen:

---

### Post by riven0 on 2006-12-22
> **jcroot said:**
> I would like to know how can I extract RAR files in Ubuntu 6.10, I don't know how to do it, I tried installing the non free rar from the terminal but it didn't work, I think the non rar is not support any more.

I search the forum for any help and I tried almost everything but no luck. :-|

Easy! Just do:
> 
sudo apt-get install unrar


Then to extract in the terminal, (not sure about the gui way):

> sudo unrar e whatever

---

### Post by jcroot on 2006-12-23
Thanks man! The last option worked!

sudo apt-get install unrar

---

### Post by meng on 2006-12-23
I think there's ALSO a package called unrar-nonfree, but you may need to have universe or multiverse repositories enabled in order to install this.

---

