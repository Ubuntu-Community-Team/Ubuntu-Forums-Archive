---
title: "CWD explaination needed!!"
date: 2008-05-20
forum: General Help
---

### Post by leo83 on 2008-05-20
Hi,

This is the part of the code of a makefile.

what does CWD := $(shell /bin/pwd) mean..I tried out /bin/pwd and is clear.
Gurus,please throw some light on above command and its use.Any tutorial/link?


```

CWD := $(shell /bin/pwd)

all:	
	cd $ /usr/lib;find $(OBJS) $(LIBS) | cpio -pdmu $(CWD);cd $(CWD)
	-arm-linux-strip $(LIBS)
```

Also, while compiling the  above code i get following message
cpio: Too many arguments
cd: 1: can't cd to shell

Complete code is here  [http://pastebin.com/d9311105](http://pastebin.com/d9311105)

---

### Post by tacutu on 2008-05-20
/bin/pwd prints the current working directory. I assume CWD is a variable with the value of the working directory. But it does not look like bash syntax. What does the very first line of the Makefile say?

I'm not an expert, but if you try to change 
```
CWD := $(shell /bin/pwd)
```

into 
 ```
CWD=$(/bin/pwd)
```
does it work?

---

### Post by leo83 on 2008-05-20
> **tacutu said:**
>  What does the very first line of the Makefile say?

Thanks, the complete makefile is here, please have a look [http://pastebin.com/d9311105](http://pastebin.com/d9311105)

Thanks

---

### Post by lisati on 2008-05-20
I have come across other contexts where "CWD" stands for "**C**urrent **W**orking **D**irectory" and suspect that the make file is trying to set or make notes about the current working directory

---

### Post by leo83 on 2008-05-20
compilation results for both commands..

here is compilation results:

```
CWD=$(/bin/pwd)

cpio -pdmu ;cd 
**cpio: Not enough arguments**


```


```
CWD := $(shell /bin/pwd)

 cpio -pdmu /srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/lib_source/tool_libs;cd /srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/lib_source/tool_libs
```
**cpio: Too many arguments**



why doesnt it show me the path in first part as is shown in second path?

Please throw some light on CPIO message above.

---

