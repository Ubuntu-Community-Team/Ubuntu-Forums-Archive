---
title: "Newbie trying to get C code to work..."
date: 2013-08-30
forum: General Help
---

### Post by Timmoore001 on 2013-08-30
I'm using Ubunty 12.4 and my attempts to get 'Hello World' to work have failed !

I need some help here (I'm try to lean C) so geting anything to 2ork would be great !

Any examples or tutorials would be great !

Any thought anyone ?

[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by Impavidus on 2013-08-30
```

[COLOR=#0000ff]$ cat hello.c[/COLOR]
#include <stdio.h>

int main()
{
    printf("Hello world!\n");
    return 0;
}
[COLOR=#0000ff]$ gcc -o hello hello.c[/COLOR]
[COLOR=#0000ff]$ ./hello[/COLOR]
Hello world!

```
What exactly doesn't work? Writing the code, running the compiler or running the code? Do you use any IDE? I think google can point you to plenty of tutorials.

---

### Post by Timmoore001 on 2013-08-30
Ah !    It worked !  I think it was simple finger problems such as missing out the word hello !  *LOL*

Many many thanks !

I think an idiots guide to C from Amazon is the next step.

Many many thanks as I was panicking !

I found this that seems very good !


[http://phoxis.org/2009/12/01/beginners-guide-to-gcc/](http://phoxis.org/2009/12/01/beginners-guide-to-gcc/)


[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

### Post by add7 on 2013-08-30
Here, you could try this tutorial: [http://c.learncodethehardway.org/](http://c.learncodethehardway.org/)

---

### Post by Timmoore001 on 2013-08-30
> **add7 said:**
> Here, you could try this tutorial: [http://c.learncodethehardway.org/](http://c.learncodethehardway.org/)

Err.. looks like a 29 US$ bill for checking it out.  Have I got that right ?  Think I'll spend less on a book.

Many thanks for the suggestion tho...

Tim

---

### Post by Timmoore001 on 2013-08-31
I found this which is very interesting from a historical point of view !

[http://www.lysator.liu.se/c/bwk-tutor.html](http://www.lysator.liu.se/c/bwk-tutor.html)

Does not better than that !  *LOL*



[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

Tim

---

