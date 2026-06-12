---
title: "need help pleaset to copy files   in var"
date: 2007-08-14
forum: General Help
---

### Post by kingbuntu on 2007-08-14
hello
i just installed ubuntu on my pc

eveything goes well

now i need to transfer some files inside the  var directory

i cant do it 

i tryed to log in with root   root  but also i have no permission 

please can you help

---

### Post by mikewhatever on 2007-08-14
Try the following
> gksudo nautilus

---

### Post by kingbuntu on 2007-08-14
thank you for your help 

but i am new in linux

can you specify what is that and how it works 

regards

---

### Post by kingbuntu on 2007-08-14
ok great 

it works 

but everytime i need to make any change i must run that 
gksudo nautilus

is there any way to be admin or root

---

### Post by mikewhatever on 2007-08-14
> **kingbuntu said:**
> ok great 

it works 

but everytime i need to make any change i must run that 
gksudo nautilus

is there any way to be admin or root

Gksudo nautilus loads nautilus with root privileges. It is useful to manage files in system directories, but also is very dangerous. One can delete half of the system files with a few clicks for example. That is why, users are strongly discouraged to use root privileges all the time. What you want is doing things Windows way here, which is plainly bad. I think Ubuntu and a lot of other distros have a wiser approach to privileges.

---

### Post by kingbuntu on 2007-08-15
> **mikewhatever said:**
> Gksudo nautilus loads nautilus with root privileges. It is useful to manage files in system directories, but also is very dangerous. One can delete half of the system files with a few clicks for example. That is why, users are strongly discouraged to use root privileges all the time. What you want is doing things Windows way here, which is plainly bad. I think Ubuntu and a lot of other distros have a wiser approach to privileges.

thank you very much 

i understand that 

but as i was running suze linux 
there i can open nd replace files and doing everything easy 

in ubuntu its not easy

---

