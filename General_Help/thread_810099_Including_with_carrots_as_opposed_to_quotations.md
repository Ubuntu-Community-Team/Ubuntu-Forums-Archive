---
title: "Including with carrots as opposed to quotations"
date: 2008-05-27
forum: General Help
---

### Post by harb37 on 2008-05-27
Hi. Simple programming question. I'm using C++, and I was hoping to know the difference between including files like so...
```
#include "blah.h"
// and
#include <blah.h>
```

If the angled brackets point to a specific location in ubuntu's directory structure, where is it pointing to?

Thanks guys,
-Mike D.

---

### Post by LaRoza on 2008-05-28
> **harb37 said:**
> Hi. Simple programming question. I'm using C++, and I was hoping to know the difference between including files like so...
```
#include "blah.h"
// and
#include <blah.h>
```

If the angled brackets point to a specific location in ubuntu's directory structure, where is it pointing to?

Thanks guys,
-Mike D.
Using "" makes the CPP (C Pre Processor) look in the current directory. Using <> makes it look in the predefined directory. I am not on Ubuntu at the moment, but it is is somewhere like usr/src/linux/include (you will have to look for the "include" directory if that is not it, I am guessing)

---

