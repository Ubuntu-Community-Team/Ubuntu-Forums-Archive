---
title: "gcc: iostream not found"
date: 2005-07-25
forum: General Help
---

### Post by mozz on 2005-07-25
Hi,

wenn I compile a program that uses iostream(.h) I get a 'not found' error from gcc, where should this file be located and where can I download it, if it's not on the system?

Thanks!

---

### Post by Zanidor on 2005-07-25
As far as I know, iostream should be a part of the default gcc install. The only thing I can think of is to make sure you are including it like: ```
#include <iostream>
```  and not  ```
#include <iostream.h>
```

The second way will give you depreciated header warnings, but I'm not sure about a 'file not found' error. If you want to find where iostream is residing on your system, you can always run something like ```
sudo find / | grep "iostream"
```

---

