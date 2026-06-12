---
title: "gmake and make"
date: 2008-06-23
forum: General Help
---

### Post by carla19 on 2008-06-23
Hello,

I want to ask if there's any difference between gmake and make on ubuntu?
Are they the same or is there any difference?

Thanks in advance

---

### Post by geirha on 2008-06-23
```
$ make --version
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu

```

There is no gmake command in ubuntu (that I know of). I know gmake usually means gnu make on other platforms, but on ubuntu gnu make is the standard, and all other makes you install will have a prefix (afaik). [http://packages.ubuntu.com/search?keywords=make&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=make&searchon=names&suite=hardy&section=all)

---

### Post by MacAnthony on 2008-06-23
You typically only see it referred to as gmake on systems that have their own proprietary version of make like on solaris for example. Sun distributes a version of make, so the gnu version needs to have a different name as to not overwrite the sun version of make.

---

