---
title: "Automated Script"
date: 2006-07-27
forum: General Help
---

### Post by pat270881 on 2006-07-27
Hello,

I want to write a script which creates automatically 40 accounts with the name visitor1, visitor2,...,visitor40. For all acounts should be set the same password guest. Furthermore all visitors should be in the same group visitor.

I started with the script in that way:

```

#!/bin/bash

for x in `seq 1 40`
do
         addbesucher visitor$x -ingroup visitor 
         //I have created a second adduser.conf file which name is
         //addbesucher.conf therefore I think I have to use addbesucher
done

chpasswd

for x in `seq 1 40`
do
        visitor$x:guest
done

CTRL+D 

```

But this script does not work fine, I think there is a problem with the section where I set the password guest for every user.

Has anybody some tipps what I made wrong here?:confused:

---

### Post by CameronCalver on 2006-07-28
just a question 
why would you want to do this

---

### Post by shaulmm on 2006-09-12
you can merge the loops, and use chpasswd like this:

```

#!/bin/bash

for x in `seq 1 40`
do
         addbesucher visitor$x -ingroup visitor 
         //I have created a second adduser.conf file which name is
         //addbesucher.conf therefore I think I have to use addbesucher

         echo visitor$x:guest |chpasswd
done

CTRL+D 


```

see too: [http://www.ubuntuforums.org/showthread.php?t=250818&highlight=chpasswd](http://www.ubuntuforums.org/showthread.php?t=250818&highlight=chpasswd)

---

### Post by Ramses de Norre on 2006-09-12
With adduser I always get annoying messages you have to answer that I can't get off, this is what I made of it: ```
#!/bin/sh
for x in `seq 1 40`
do
    **adduser --conf /etc/addbesucher.conf** --disabled-login --ingroup visitor$x visitor$x
    echo "visitor$x:guest"|chpasswd
done
```

An alternative is useradd:
```
#!/bin/sh
for x in `seq 1 40`
do
    useradd -m -s /bin/bash visitor$x
    echo "visitor$x:guest"|chpasswd
done
```

---

