---
title: "[SOLVED] help me with a little script"
date: 2007-11-08
forum: General Help
---

### Post by buuntuu! on 2007-11-08
hi everybody
i have got a little homework, should be a piece of cake,  but i seem to have an idea-jam!
 i need to write a script that prints the parameters given to it in reverse order to the screen like this

```

$ ./script parameter1 parameter2 parameter3
parameter3 parameter2 parameter1

```

any ideas?

---

### Post by digitalbenji on 2007-11-08
This will do it.  It's a one liner, but I split it up so its a bit more readable.  
```

#!/bin/sh
echo $* | awk '{ 
        i=NF
        while (i > 0) {
                printf $(i)
                 printf " "
                i--
        }print '\n'
}' 

```

Some comments:
in any shell script $0 , $1, $2, etc provide access to the arguments passed in.  $* is a nice way to pull all the arguments out, and echo with the pipe spits them into awk to be processed.  In awk NF is the number of fields built in variable, and from here we just walk backward through all the fields.  printf does not append new lines, and voila.

Did I just do your homework for you?

---

### Post by buuntuu! on 2007-11-08
i guess you did ;)
it uses some commands we didn't do yet and my teacher is going to get suspicious, but at least i can find some sleep tonight! i was unable to get this out of my head all day!
thanks a bunch digitalbenji!

---

