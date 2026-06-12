---
title: "Compile problems"
date: 2005-10-06
forum: General Help
---

### Post by refdoc on 2005-10-06
I am using currently breezy - which uses gcc 4.0

Unfortunately a lot of stuff compiles quite nicely on gcc 3.3. but seems to struggle on gcc4.0. Specifically for me this is mol on my ibook and wine on my Dell latitude throw up endless warnings about wrongly signed thsi and that and eventually fail. I made wine compile by checking by hand all mentions of 'gcc' in the config file and change it to gcc-3.3. - at least where it appeared to be useful. eventually I succeeded with a compile without problems (under gcc-3.3)

Now the question - is there a way short of finding that elusive referral to gcc in the config files - to force make use a certain compiler version and not another?

Or am I really daft here?

Thanks

---

### Post by darkmatter on 2005-10-06
To force your system to use a specific gcc version, execute the following in a terminal
```
gcc -V <version_to_be_used>
```

For example, to switch to version 3.3.4 on a system running 4.0 (or any other version) by default:
```
gcc -V 3.3.4
```

Then, you can do a version check to insure the change was made with
```
gcc -v
```

---

### Post by refdoc on 2005-10-06
[I]sudo gcc -V 3.4
powerpc-linux-gnu-gcc-3.4: no input files[/I]

No joy.

3.4 is installed.

---

### Post by claydoh on 2005-10-06
Try this just before you start:

>  sudo CC=gcc-3.4
sudo export CC

it temporarily sets your compiler to 3.4. I have had no real use to do this (unless I want newer Nvidia drivers) so far, but I am not on a ppc machine.

---

