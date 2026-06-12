---
title: "What is the 3 stands for in libgmp3 ?"
date: 2008-06-11
forum: General Help
---

### Post by hexanol on 2008-06-11
Hi,

I was wondering, what is the 3 stands for in the name libgmp3-dev ? I first thought it was related to the version number, but after running this simple program:

```
#include <stdio.h>
#include <gmp.h>

int main()
{
    puts(gmp_version);
    return 0;
}
```
well, it printed "4.2.2". So... ?

I did some googling but found nothing of interest.

Thanks

---

### Post by olskar on 2008-06-11
> **hexanol said:**
> Hi,

I was wondering, what is the 3 stands for in the name libgmp3-dev ? I first thought it was related to the version number, but after running this simple program:

```
#include <stdio.h>
#include <gmp.h>

int main()
{
    puts(gmp_version);
    return 0;
}
```
well, it printed "4.2.2". So... ?

I did some googling but found nothing of interest.

Thanks

I guess its mp3? As in the musicformat.. gmp3 might be "generation mp3" which you can find on google

---

### Post by dicecca112 on 2008-06-11
That's what I thought but its not gmp refers to this

[http://gmplib.org/](http://gmplib.org/)

As for the 3, maybe the third revision

---

### Post by hexanol on 2008-06-11
Indeed, GMP refers to GNU Multi-Precision... but I already knew this. :p

libgmp3-dev refers to the package I downloaded and installed on my Ubuntu system, via aptitude.

Anyway, since I don't have any problem using the library and it's the latest version, I don't really mind not to know what the 3 stands for, but still, I find it a bit awkward.

And I have to say, I'm quite new to Ubuntu (to Linux-based operating system in general) but software development is so more fun and easy on it than on Windows... :) There's really a great choice of free (and open source) libraries with great documentation, all this easily installable. Plus the community support. It rocks.

---

### Post by bruce89 on 2008-06-11
3 is the [soname]("http://en.wikipedia.org/wiki/Soname") version. Put simply, 3 means it's the 3rd major API revision.

---

