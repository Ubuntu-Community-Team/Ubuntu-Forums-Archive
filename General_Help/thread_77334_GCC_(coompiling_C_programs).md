---
title: "GCC (coompiling C programs)"
date: 2005-10-16
forum: General Help
---

### Post by Sebek on 2005-10-16
I installed GCC with the comand "sudo apt-get install build-essential". Then I checked that libc6-dev is instaled in my system, but I still have strange errors when I compile programs.

clidns.c:245: warning: incompatible implicit declaration of built-in function ‘strlen’
clidns.c:249: warning: incompatible implicit declaration of built-in function ‘memcpy’
clidns.c:262: warning: incompatible implicit declaration of built-in function ‘memcpy’
clidns.c:276: warning: incompatible implicit declaration of built-in function ‘memcpy’
clidns.c:290: warning: incompatible implicit declaration of built-in function ‘memcpy’
clidns.c: In function ‘decompact_type_cname’:
clidns.c:312: warning: incompatible implicit declaration of built-in function ‘memcpy’

Can anyone help me with this? I'm desperate.

Sebek

---

### Post by el toro on 2005-10-16
Those are just warnings--do you get any actual error msgs that stop you from compiling the program?  Which program is it, btw?

---

### Post by Sebek on 2005-10-16
its a project (program) I'm doing for a course in university.
before I was using Ubuntu 5.04 and my program didn't have any warnings or errors. then I upgraded to 5.10 and I got those warnings...
anyone can help me?

---

### Post by chunk on 2005-10-16
It's probably the libraries you're using. Paste your headers.

---

### Post by seldenthuis on 2005-10-16
Hoary uses GCC 3.3.5, Breezy uses 4.0.2. It seems 4.0.2 its not entirely backwards compatible. You could either install 3.3.5 or manually debug your programs. I don't think there's any other way.

---

### Post by Sebek on 2005-10-16
I instaled gcc 3.3 with apt,  and now the comand gcc doesn't work.  If I install build essential he will install gcc 4. what else is missing?

---

### Post by stoffe on 2005-10-30
Actually, I think you must include the headers now, and that is all:

Try adding
```
#include <string.h>
```
and see if that helps. Maybe need to add more headers too.

---

