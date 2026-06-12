---
title: "make archive in multiple parts"
date: 2007-12-20
forum: General Help
---

### Post by htor on 2007-12-20
I want to send a big file using email so I need to use format that supports  archiving in multiple parts. 
I know I can do this with RAR but are there some open formats that support it ?

---

### Post by nick_h on 2007-12-20
Create the archive first then split it using the *split* command.  Then you can re-combine it using the *cat* command.

Type:
```
man split
```
for the manual page.

---

### Post by htor on 2008-01-01
Do you know if  this way is cross platform ?
Are there applications that allows extract such files on windows/mac ?

---

### Post by nick_h on 2008-01-01
> Are there applications that allows extract such files on windows/mac ?

There are a few ports of Unix tools for Windows.  You can Google for them, but I have given you a link to one as an example.

Have a look at [http://unxutils.sourceforge.net/](http://unxutils.sourceforge.net/)

This provides split and cat and many other useful Unix tools for Windows.

---

### Post by htor on 2008-01-01
Thanks ! :)

---

