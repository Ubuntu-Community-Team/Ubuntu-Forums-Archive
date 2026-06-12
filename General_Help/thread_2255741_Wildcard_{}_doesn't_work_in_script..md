---
title: "Wildcard {} doesn't work in script."
date: 2014-12-07
forum: General Help
---

### Post by vincent25 on 2014-12-07
I'm new to scripting, and I wanted to do something on all images.
So I did something like this : 

```

#! /bin/sh

for i in images/*.{jpg,png}; do
    echo $i
done
```

If I run this directly from a terminal it works fine, but when ran from a script, it returns this :

```
images/*.{jpg,png}
```
Furthermore the others wildcards I've tested seem to work fine. So why  doesn't {} work ?

---

### Post by Lars Noodén on 2014-12-07
Expanding {} is a [bashism](http://mywiki.wooledge.org/Bashism), so you'd have to run bash for that to happen.

```

#!/bin/bash

```

sh, or more specifically [dash](http://manpages.ubuntu.com/manpages/trusty/en/man1/dash.1.html), is leaner and meaner containing fewer bells and whistles.  Thus it's faster to start and a bit more portable than bash, but then again these days bash is just about everywhere, even on OS X.

---

### Post by vincent25 on 2014-12-07
Oh okay.
On school's computers it worked, but I guess it's only because /bin/sh is a different shell on Centos.

---

### Post by nerdtron on 2014-12-07
In ubuntu the /bin/sh is pointed to the **dash **shell. In CentOS systems, the /bin/sh is pointed to **bash** that's why it works on the centos system
Ubuntu:
```
kenneth@ubuntu:~$ ll /bin/sh
lrwxrwxrwx 1 root root 4 Nov  7 09:03 /bin/sh -> dash*

```
CentOS:
```
[kenneth@centos ~]# ll /bin/sh
lrwxrwxrwx 1 root root 4 Sep 27 04:44 /bin/sh -> bash

```

---

