---
title: "drwxrwsr-x Help what does that mean"
date: 2018-01-27
forum: General Help
---

### Post by uwe-bungto on 2018-01-27
I have a drive where the dirs have drwxrwsr-x as a file permission That does the 's' mean. how do I change that permission? I have tried chmod 775, sudo chmod 775 the 's' stays.

Is it possible that this permission would prevent an app from writing to that drive?

I have never seen this before.

Thanks

---

### Post by Bashing-om on 2018-01-27
uwe-bungto; Uh Huh -

the "s'"  == "setgid" ; indicates that the file/folder does not have executable permissions for that user on that particular file/folder.
see:
[http://stackoverflow.com/questions/9133024/www-data-permissions](http://stackoverflow.com/questions/9133024/www-data-permissions)
[http://mywiki.wooledge.org/Permissions](http://mywiki.wooledge.org/Permissions)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by steeldriver on 2018-01-27
The [setgid]("https://en.wikipedia.org/wiki/Setuid#GUID") bit allows files created under the directory to inherit the group of the directory, instead of that of the creating process

It is separate from the execute bit

If you want to remove it you would need to give an extra digit to the chmod command i.e.

```

chmod 0775 path/to/dir

```

or (symbolically)

```

chmod g-s path/to/dir

```

and restore it with

```

chmod 2775 path/to/dir

```

or (symbolically)

```

chmod g+s path/to/dir

```

---

### Post by uwe-bungto on 2018-02-01
> **steeldriver said:**
> The [setgid]("https://en.wikipedia.org/wiki/Setuid#GUID") bit allows files created under the directory to inherit the group of the directory, instead of that of the creating process

It is separate from the execute bit

If you want to remove it you would need to give an extra digit to the chmod command i.e.

```

chmod 0775 path/to/dir

```

or (symbolically)

```

chmod g-s path/to/dir

```

and restore it with

```

chmod 2775 path/to/dir

```
I have tried 
or (symbolically)

```

chmod g+s path/to/dir

```
I have tried chmod 0775, sudo chmod 0775, chmod 2775 sudo chmod 2775 chmod -R. Nothing changes the the permissions of that HDD. All the content has the same permission. Anyway of fixing that short of removing all the content from the drive and reformatting it?

---

### Post by uwe-bungto on 2018-02-05
Thanks everyone. I found the source of my misunderstanding. The 's' bit is inherited the reason I could not change it in a dir was, I didn't go high enough in the directory tree. :redface: The bit was set for the whole drive.

---

