---
title: "D language code segfaults"
date: 2008-05-28
forum: General Help
---

### Post by strattonbrazil on 2008-05-28
Has anyone had segmentation faults running the tutorials?  This segfaults on my computer (Ubuntu 8.04) using dgc.  It's taken from one of the tutorials, but several similar tutorials also fail.  

```

import std.stdio;

int magicNumber = 42;
char[] password = "sesame";

void main() {
  writefln("Magic number: ", magicNumber);
  writefln("Password: ", password);
}

```

---

### Post by aanderse on 2008-05-28
i don't know D but shouldn't it be:

  writefln("Magic number: %d", magicNumber);
  writefln("Password: %s", password);

?

---

### Post by strattonbrazil on 2008-05-28
Hrmm, I pulled that directly from the Digital Mars site.  I figured they know D well enough.  I did put in the '%d's but it still segfaults.  Thanks.

---

### Post by aanderse on 2008-05-28
ok, sorry...
was just taking a guess based on c

---

### Post by strattonbrazil on 2008-06-02
Just FYI to anyone, I went to the D forums and they recommended using the 4.1 compiler instead of the 4.2 compiler.  Both are currently in the repository.  Using gdc-4.1 instead did not cause any seg faults and the program ran normally.

---

