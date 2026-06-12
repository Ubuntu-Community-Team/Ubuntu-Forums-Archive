---
title: "X11 Cursor only show theme in some windows"
date: 2008-07-08
forum: General Help
---

### Post by Ioky on 2008-07-08
I install some new Cursor theme. However, I will use them, it only work on something windows, and when they get out of those windows, it will go back to the default Cursor. Is there anything thing I miss during installation. I mean I just put all the theme into /usr/share/icons. 

Thanks

---

### Post by Bruce M. on 2008-07-12
> **Ioky said:**
> I install some new Cursor theme. However, I will use them, it only work on something windows, and when they get out of those windows, it will go back to the default Cursor. Is there anything thing I miss during installation. I mean I just put all the theme into /usr/share/icons. 

Thanks

OK, I use a hidden directory in my home directory: /.icons for my mouse pointers. Now create a directory called: default
```
/home/your_name_here/.icons/default
```
in that directory create a text file: index.theme

Put something like this in there:

```
[Icon Theme]
#Inherits=93Aero
#Inherits=Around
Inherits=Marbre
```

As you can see I'm using Marbre at the moment.  :)

Of course you could go to:
```
/usr/share/icons/default/index.theme
```
and do the same.

Either of these methods will set what you have as Inherits=xxxxx as the default theme **system wide**.

Hope this helps.
Bruce

---

### Post by Ioky on 2008-07-12
Thanks you very for the help. Actually I figure it out few days ago. I just forget to post the solution. It is still good to have it here so any one have the same problem can get an answer. 

again thanks.

---

