---
title: "g++ compiling error"
date: 2008-04-30
forum: General Help
---

### Post by kitsu on 2008-04-30
The following code results in the error below it.  What do I need to configure/change to get some simple c++ code to compile?

System info:

Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubun
tu4)) #2 SMP Tue Feb 12 05:41:34 UTC 2008


The code:

#include<iostream>

int main(int argc, char **argv[])
{

        nook();

        return 0;
}

public nook();
public nook(){}

The command:

g++ nota.C -o nota

The error:

nota.C: In function &#8216;int main(int, char***)&#8217;:
nota.C:7: error: &#8216;nook&#8217; was not declared in this scope
nota.C: At global scope:
nota.C:12: error: expected unqualified-id before &#8216;public&#8217;
nota.C:13: error: expected unqualified-id before &#8216;public&#8217;


How do I fix this?  I will also accept advice as to a better location for these types of questions.

---

### Post by sdennie on 2008-04-30
I think you'll need to move the declaration of "nook" to above where it's used.  So, at the top of the file.    I'm not sure if the way you've declared "nook" is valid either.  Maybe:

```

void nook();

int main()
{
    nook();
}

void nook(){ }

```

---

### Post by kitsu on 2008-04-30
new code:

#include<iostream>

public void nook();

int main(int argc, char **argv[])
{

        nook();

        return 0;
}

public void nook(){}


new error:

nota.C:3: error: expected unqualified-id before ‘public’
nota.C: In function ‘int main(int, char***)’:
nota.C:8: error: ‘nook’ was not declared in this scope
nota.C: At global scope:
nota.C:13: error: expected unqualified-id before ‘public’

---

### Post by sdennie on 2008-04-30
There are a lot of errors in the code you've written.  I would suggest looking on the web for a C++ tutorial or moving your question to: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) (The Ubuntu programming forums).

---

