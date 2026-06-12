---
title: "makefile error"
date: 2008-05-02
forum: General Help
---

### Post by dluu13 on 2008-05-02
I'm trying to install something, and I downloaded the sourcecode.

I navigated to the directory and did the ./configure

Now when I type make, it gives me the error
> make: *** No targets specified and no makefile found.  Stop.

I ls the folder and there is a makefile.am and a makefile.in.  Why isn't it finding it?

---

### Post by Anduu on 2008-05-02
If make doesn't work in means the ./configure failed.Run ./configure again and make note of any errors.

Typically when ./configure fails it is because some required libraries were not found.It will let you know which ones and you just need to install them.

---

