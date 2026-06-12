---
title: "File name include spaces"
date: 2016-08-12
forum: General Help
---

### Post by wintersoldier on 2016-08-12
I use an application but this application can not open or see some files. These files have a space in name. How can i solve this problem?

Example: 

This application opens wintersoldier.txt but this app can not open    winter soldier.txt

---

### Post by howefield on 2016-08-12
What's the application ?

If you are opening the files via a terminal you can usually escape the space by enclosing the file name in quotes or using a \ 

```
application winter\ soldier.tx
```
```
application "winter soldier.txt"
```

---

### Post by wintersoldier on 2016-08-12
> **howefield said:**
> What's the application ?

If you are opening the files via a terminal you can usually escape the space by enclosing the file name in quotes or using a \ 

```
application winter\ soldier.tx
```
```
application "winter soldier.txt"
```

I'm not opening the files via a terminal. I think, I should change application config settings but I don't know which command is available ?

---

### Post by vasa1 on 2016-08-12
> **wintersoldier said:**
> I'm not opening the files via a terminal. I think, I should change application config settings but I don't know which command is available ?
Again, what is this application's name?

---

### Post by wintersoldier on 2016-08-12
> **vasa1 said:**
> Again, what is this application's name?

UYAP. Probably, you don't know this application. This app opens special text f&#305;le.

---

### Post by steeldriver on 2016-08-12
Well if we won't know it's name, we probably won't know its application config settings either (if it has any) - you will need to search the documentation or contact the application's maintainers

---

### Post by vasa1 on 2016-08-12
Some text editors deal with spaces in filenames. geany and gedit are two. So you can double-click on a file in a file manager. But leafpad and medit can't.

---

### Post by wintersoldier on 2016-08-12
This Application  opens .udf formats and the app maintainers is my director :-?. He said you must solve this problem. Do you know any commands for this problem in shell script ?

---

### Post by CatKiller on 2016-08-12
So you're actually asking how to make your own application handle strings better? As has already been said, if your function for opening the file is interpreted by the shell you'll need to either use quotes around the path or put in the facility to escape special characters.

---

### Post by steeldriver on 2016-08-12
Short of renaming the files (for example, replacing the spaces with underscores), I can't think of a generic solution

You'd at least need to know what API or specific filechooser widget the application uses, and even then there's no guarantee it even has a configuration option that (a) does what you want and (b) is configurable at runtime (rather than when the application was built)

---

