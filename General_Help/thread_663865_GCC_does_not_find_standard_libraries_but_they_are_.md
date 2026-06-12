---
title: "GCC does not find standard libraries but they are there"
date: 2008-01-10
forum: General Help
---

### Post by grayfin on 2008-01-10
Hi,

I'm a newbie to C and gcc. I've just writen a hello world code :
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}

but when i run...
gcc hello.c
i get the following error:

 stdio.h: No such file or directory

I have done apt-get install build_essentials and upgrade.
The files are there! but gcc just does not want to find them.
What do i do?

Thank you,

---

### Post by taurus on 2008-01-10
You mean you have installed the **build-essential** package.

---

### Post by grayfin on 2008-01-10
Yeh, my apologies. build_essentials are installed :KS

---

### Post by jocko on 2008-01-10
> **grayfin said:**
> 
#include [COLOR=Red]< stdio.h>[/COLOR]

void main()
{
    printf("\nHello World\n");
}

What happens if you change "[COLOR=Red]< stdio.h>[COLOR=Black]" to [/COLOR][/COLOR][COLOR=Black]"[/COLOR][COLOR=Red]<stdio.h>[COLOR=Black]" (remove the space)?[/COLOR][/COLOR]

---

### Post by LaRoza on 2008-01-10
A few things:

* Put in code in [ code ] or [ php ] tags, so we can read it.
* It is <stdio.h>, no spaces
* main() returns **int** not void.

[php]
#include <stdio.h>

int main(int args, char ** argv)
{
    printf("\nHello World\n");
}
[/php]

---

### Post by stchman on 2008-01-10
> **grayfin said:**
> Hi,

I'm a newbie to C and gcc. I've just writen a hello world code :
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}

but when i run...
gcc hello.c
i get the following error:

 stdio.h: No such file or directory

I have done apt-get install build_essentials and upgrade.
The files are there! but gcc just does not want to find them.
What do i do?

Thank you,

Try this:

```

#include <stdio.h>

void main(void)
{
    printf("\nHello World\n");
}

```

That should work.

---

### Post by grayfin on 2008-01-10
Yes it worked!! GRR... i copied that code from a tutorial, and it had the space there too. Thanks Guys!

---

