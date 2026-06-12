---
title: "windows folder name has the &quot;#&quot; character"
date: 2008-04-11
forum: General Help
---

### Post by d_hart on 2008-04-11
I am trying to create a desktop launcher to a folder in a mounted smb share. The problem is that the folder name is "MO#". This is perfectly fine folder name in windows but linux doesn't seem to like it. When trying to create the launcher it returns an error saying it can find the folder "MO". It is disregarding the "#" character. Can anyone help me resolve this issue without renaming the folder.

Thanks

---

### Post by bodhi.zazen on 2008-04-11
You have to either "escape" the # with a \ like this

MO\#

Or use quotes

"MO#"

---

### Post by d_hart on 2008-04-11
Yes I have. That doesn't work. Any other ideas?

---

### Post by ghostdog74 on 2008-04-11
you escape # with \# , not \

---

### Post by bodhi.zazen on 2008-04-12
> **d_hart said:**
> Yes I have. That doesn't work. Any other ideas?

Permissions on samba mounts are a little odd.

What are you trying to run ?

Is there an error message ?

What happens when you

sh /path/to/"MO#" ?

---

### Post by d_hart on 2008-04-14
> **ghostdog74 said:**
> you escape # with \# , not \

The text in my launcher is "file:///media/network/engineering/MO#", less the quotes of course.
This returns an error of "Couldn't find "/media/network/engineering/MO"". If I surround the MO# in quotes, I still get the same error. If I precede the # symbol with a \ backslash symbol and then try to run the launcher, nothing happens.

---

### Post by d_hart on 2008-04-14
> **bodhi.zazen said:**
> Permissions on samba mounts are a little odd.

What are you trying to run ?

Is there an error message ?

What happens when you

sh /path/to/"MO#" ?

If I run sh /media/network/engineering/"MO#" in a terminal, I get no response. It just returns me to the prompt.

---

### Post by d_hart on 2008-04-14
All I am trying to do is make a link or shortcut to this folder on my desktop. Thanks to all of you that have responded.

---

### Post by bodhi.zazen on 2008-04-14
If all you need is a link,

```
ln -s /path/to/"MO#" ~/Desktop/"MO#"
```

you need to make a soft link, with the -s flag

---

### Post by d_hart on 2008-04-14
> **bodhi.zazen said:**
> If all you need is a link,

[cold]ln -s /path/to/"MO#" ~/Desktop/"MO#"[/code]

you need to make a soft link, with the -s flag

That worked. Excellent! Thank you.

---

### Post by MrKlister on 2008-06-13
Had the same problem with the caracters "[" and "]". I solved the problem by using the "browse" button to browse to the location (Unfortunately you have to locate a file to be able to open a location, so create a temporary file if your folder is empty and then remove the file name from the result)

It looks like the special caracters are described with "%5B" respektively "%5D"

---

