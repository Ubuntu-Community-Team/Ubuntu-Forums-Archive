---
title: "Ubuntu gcc problem"
date: 2007-09-28
forum: General Help
---

### Post by Saicho on 2007-09-28
I installed FF 7.04, but using kernel 2.6.22-12. When I try to compile this with gcc (version 4.1.2)

```

#include <stdio.h>
int main() {
    printf("Hello World!\n");
    return 0;
}
```

I get:

```
warning: incomplete implicity declaration of built-in function 'printf'
```

Also

```
sudo apt-get install gcc
```

is up to date.

This same code compiles on other OS. I tried to search but found nothing. Does anyone have any idea what is going on here? Thanks in advance.

---

### Post by Saicho on 2007-09-28
I upgraded to gutsy gcc version 4.1.3 and still having the same problem

---

### Post by Saicho on 2007-09-28
using the gutsy repoes, installing g++

```
sudo apt-get install g++
```

fixed the problem. Code compiles with both gcc and g++

hope this helps someone

---

### Post by geraldm on 2007-09-28
Just a warning, not an error ?   It would then be OK to ignore.

But implicit declaration of built-in function "printf" means it did not find the function declared
in stdio.h, which MAY mean that gcc did not find the header file stdio.h
Find that file, usually in /usr/include/ OR  ( common error )

sudo apt-get install build-essential

Gerald

---

