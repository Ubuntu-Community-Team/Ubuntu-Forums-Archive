---
title: "make won't work as expected"
date: 2007-08-21
forum: General Help
---

### Post by leonardopsantos on 2007-08-21
Hi Everybody!
I recently switched do Ubuntu 7.04 and I'm loving it! Today I hit a snag and can't figure out what else to do!
I'm trying to build some SW project and discovered that a Makefile like this won't work:

```

TESTE  := 0x10
TESTE2 := 0x01
RESULT := $(shell printf "0x%8x" $$[$(TESTE)+$(TESTE2)])

all:
	gcc -Wall -O2 -o teste teste.c

```

teste.c:

```

#include <stdio.h>

int main( void )
{
	return 1;
}

```

If I try to make this:

```
$ make
printf: 1: $[0x10+0x01]: expected numeric value
gcc -Wall -O2 -o teste teste.c

```

This is certainly an Ubuntu problem. I tryed this exact Makefile and C file with Fedora 6 and Mandriva 2007 and both compile without any warnings!
If anyone has some pointers, I'd be very grateful!

Thank you very much.

---

### Post by leonardopsantos on 2007-08-22
I figured out what was wrong. Ubuntu ( and I imagine Debian too ) uses dash as the system shell:

```

ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2007-08-09 11:32 /bin/sh -> dash

```

Whereas Fedora and Mandriva use bash. After removing the link and creating a new one pointing t bash, everything works.

---

### Post by taurus on 2007-08-22
> **leonardopsantos said:**
> I figured out what was wrong. Ubuntu ( and I imagine Debian too ) uses dash as the system shell:

```

ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2007-08-09 11:32 /bin/sh -> dash

```

Whereas Fedora and Mandriva use bash. After removing the link and creating a new one pointing t bash, everything works.

Instead of using 

```
#!/bin/sh
```
you should have used

```
#!/bin/bash
```
and leave the /bin/sh alone.

---

### Post by leonardopsantos on 2007-08-22
That would work if we're talking about shell scripts, but it's a Makefile, and make is going to call /bin/sh, so I really don't see any other solution here.

---

