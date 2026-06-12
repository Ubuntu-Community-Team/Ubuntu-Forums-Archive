---
title: "can't renaming a file"
date: 2015-01-10
forum: General Help
---

### Post by Harsh_Parikh on 2015-01-10
Hello, I am stuck at renaming a file.... 
```
 root@me-REKCAH:/home/hparikh/my_c_project/completeLinkedList# rename reversingLinkedList.c reversingLinkedListWith\(O\/2\).c Bareword "reversingLinkedList"
 not allowed while "strict subs" in use at (eval 1) line 1.
 Bareword "c" not allowed while "strict subs" in use at (eval 1) line 1. 

```  
When i use command mv,result is  
```
 root@me-REKCAH:/home/hparikh/my_c_project/completeLinkedList# mv reversingLinkedList.c reversingLinkedListWith\(O\/2\).c 
mv: cannot move `reversingLinkedList.c' to `reversingLinkedListWith(O/2).c': No such file or directory
 
```
  I don't understand what to do.... Please help me.....

---

### Post by steeldriver on 2015-01-10
The command `rename` works differently - it's generally used for renaming multiple files according to some pattern/replacement syntax - use `man rename` to read about it. 

To do a simple rename of a single file use mv **however note that a forward slash is not a legal character for a filename** no matter whether you escape it or not:

```

mv reversingLinkedList.c reversingLinkedListWith\(O\**[COLOR=#ff0000]/[/COLOR]**2\).c

```

You will need to choose a different character like

```

mv reversingLinkedList.c reversingLinkedListWith\(O**_**2\).c

```

You could also use quotes to avaoid needing to escape special characters

```

mv reversingLinkedList.c "reversingLinkedListWith(O**_**2).c"

```
or
```

mv reversingLinkedList.c 'reversingLinkedListWith(O**_**2).c'

```

---

### Post by Harsh_Parikh on 2015-01-10
Thank you very much....
I understand...
Can you give me any reference for using rename command...
Thanks..

---

