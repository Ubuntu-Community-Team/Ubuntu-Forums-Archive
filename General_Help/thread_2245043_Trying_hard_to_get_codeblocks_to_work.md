---
title: "Trying hard to get code:blocks to work ?"
date: 2014-09-20
forum: General Help
---

### Post by rigidigital on 2014-09-20
HI,
      I installed code:blocks  to usr as aqn IDE to learn C programming. It installed from the Ubuntu repository. I am given the option , when starting a new preoject for it to be compiled etc as C or C++, I always choose C. Trouble is it is not working. A hello World program will have 2 errors one is about not finding  STDIO.H ? CAN ANYONE HELP 

Here is the all importqant program ;-)

```

int main()
{
    printf("Hello world!\n");
    return 0;
}

```


This is the Build Log message


[COLOR="#A52A2A"]
-------------- Build: Debug in page14_downandDirty (compiler: GNU GCC Compiler)---------------

g++  -o bin/Debug/page14_downandDirty obj/Debug/main.o   
/bin/sh: 1: g++: not found
Process terminated with status 127 (0 minute(s), 0 second(s))
0 error(s), 0 warning(s) (0 minute(s), 0 second(s))
 [/COLOR]

And if you are interested here is the Build Message... saying Build Failed ?
[COLOR="#A52A2A"]
||=== Build: Debug in page14_downandDirty (compiler: GNU GCC Compiler) ===|
||=== Build failed: 0 error(s), 0 warning(s) (0 minute(s), 0 second(s)) ===|[/COLOR]

---

### Post by steeldriver on 2014-09-20
Your program needs a

```

#include <stdio.h>

```

for the printf prototype. I honestly don't recommend using an IDE like code:blocks until you have a better level of understanding - you can just create a text file anywhere e.g. I called this one 'hello.c'

```

#include <stdio.h>

int main()
{
  printf("Hello world!\n");

  return 0;
}

```

and then compile it on the command line using something like

```

gcc -o hello -Wall hello.c

```

---

