---
title: "deleting compressed file contained brackets() in its name"
date: 2014-08-13
forum: General Help
---

### Post by Harsh_Parikh on 2014-08-13
Hey,please help me...
I want to delete a compressed tar.gz2 file through terminal....
Its name is Webkit-SVN-source(2).tar.gz2
But when I typed in terminal :
rm Webkit-SVN-source(2).tar.gz2
I get an error that :
syntax error near ( unexpected token 
something like that......
Please help me what can I do to remove that file....

---

### Post by steeldriver on 2014-08-13
Either escape or quote

```

rm Webkit-SVN-source[COLOR=#0000ff]**\**[/COLOR](2[COLOR=#0000ff]**\**[/COLOR]).tar.gz2

rm [COLOR=#0000ff]**'**[/COLOR]Webkit-SVN-source(2).tar.gz2[COLOR=#0000ff]**'**[/COLOR]

```

---

### Post by Harsh_Parikh on 2014-08-14
> **steeldriver said:**
> Either escape or quote

```

rm Webkit-SVN-source[COLOR=#0000ff]**\**[/COLOR](2[COLOR=#0000ff]**\**[/COLOR]).tar.gz2

rm [COLOR=#0000ff]**'**[/COLOR]Webkit-SVN-source(2).tar.gz2[COLOR=#0000ff]**'**[/COLOR]

```
Thank you very much....
And if there is a space in name,then is this solution will work or not...?
If not,then Please tell how to do it....

---

### Post by Lars Noodén on 2014-08-14
Both methods also work for files with spaces in the names.  They will also work with other [weird characters](http://www.grymoire.com/unix/Quote.html).

---

### Post by Iowan on 2014-08-14
Yes, it works for a space, too. I tried the following:
```
touch 'this one'
ls 
rm this\ one
ls
```The **ls** verified the existence (and removal) of the file.

---

### Post by Harsh_Parikh on 2014-08-14
Thanks to everyone....
[weird characters]("http://www.grymoire.com/unix/Quote.html") is very useful.....

---

