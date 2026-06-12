---
title: "Missing Perl Headers"
date: 2007-02-16
forum: General Help
---

### Post by upsfeup on 2007-02-16
I have a perl script that requires an header.

```

    require 'linux/input.ph';
```

It happens that the file is missing and I'm having problems in finding and installing it. 

the interpreter complains that I should use h2ph but when I try to do so it says that

```

Destination directory /usr/local/lib/perl/5.8.8 doesn't exist or isn't a directory
```

Besides, which input.h should I try to convert?

I tried to install perl 5.8.8 but without success. Are there any packages that I should install?

---

### Post by upsfeup on 2007-02-17
Bumping this a bit since it was already in page 10! :o

Still haven't figured out what I need in order to have those perl headers.

Ideas?

---

### Post by upsfeup on 2007-02-20
Just to wrap this up

This is how I solved it: 

manually created  /usr/local/lib/perl/5.8.8 

and them cd to the src/linux-headers folder of the running kernel and ran h2ph -r *

It didn't complain anymore but other problems arised.

Is weird because when i tried this before it didn't work... probably I was checking the wrong place.

---

