---
title: "Problem with &quot;make&quot; command not found."
date: 2007-01-18
forum: General Help
---

### Post by itstabish on 2007-01-18
tabish@tabish-laptop:~/Desktop/BitchX$ make
/usr/local/bin/bash ./configure
make: /usr/local/bin/bash: Command not found
make: *** [default] Error 127

---

### Post by ardchoille42 on 2007-01-18
> **itstabish said:**
> tabish@tabish-laptop:~/Desktop/BitchX$ make
/usr/local/bin/bash ./configure
make: /usr/local/bin/bash: Command not found
make: *** [default] Error 127

```

sudo apt-get install build-essential

```

---

### Post by itstabish on 2007-01-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by taurus on 2007-01-20
Did you remember to run the ./configure first before the make?  Besides, bash is in /bin, not /usr/local/bin.

```
./configure
make
sudo make install
```

---

### Post by po0f on 2007-01-20
itstabish,

What are you trying to install?  I can't fathom why it would look in /usr/local/bin for bash.

[EDIT]

Grammar.

---

