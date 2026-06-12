---
title: "Rename multiple files to remove ;1"
date: 2008-07-02
forum: General Help
---

### Post by cormic on 2008-07-02
Hey,

I have a problem that when I extract an ISO file all the files are have ;1 appended onto them.  This is annoying to say the least.  

The files are called

```
readme.txt;1
```

instead of

```
readme.txt
```

I found a simple command that removed these extra two characters but I did not save it and cannot find it anywhere.  The script I had did all sub directories as well.

If anyone can find this or knows what it was I would be very grateful.

Many Thanks
Corm

---

### Post by cormic on 2008-07-02
Mere minutes after posting this I found the script

```
find . -name "*;1" |while read FILE ; do mv "$FILE" ${FILE/;1/} ; done
```

It works a treat.

---

