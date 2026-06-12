---
title: "gcc Compilation problem"
date: 2008-05-01
forum: General Help
---

### Post by rebel_angel on 2008-05-01
hi everyone,
Im possibly the newest user of ubuntu 7 ( started 2 hrs ago :) ). Im having some difficulty in compiling my codes in C.

i wrote the following code

#include <stdio.h>
```

int main()
{
	printf("test \n");
	return 0;
}

```

in the command line i typed 
```
gcc -o test test.c
```

it shows the following error

```

test.c:1:19: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```

anybody has any clue ?

--
Soumit Salman, CCNA

---

### Post by bite on 2008-05-01
```

sudo apt-get install build-essential

```

---

### Post by rebel_angel on 2008-05-01
ooowh i fixed it :) 

```
 sudo apt-get install build-essential
```

thanx to me :)

---

### Post by rebel_angel on 2008-05-01
hei bite , thanx man ! 

Anyway can someone help me with Anjuta IDE. When i compile a code its okey but when i when i try to execute it or debug it, i get an error msg 

```
Program '/home/soumit/Academics/Codes/test' is not a local file
```

---

### Post by bite on 2008-05-01
Hmm, I'm not using anjuta... anyway, what do you mean by "compile"? You should use something like "build" ore "generate", not just "compile" --  compilation does not link the object file(s) into the executable.

---

### Post by rebel_angel on 2008-05-02
problem solved ! anjuta 2.4 requires a project to be created for linking and executing.

---

