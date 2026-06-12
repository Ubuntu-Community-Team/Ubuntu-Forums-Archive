---
title: "Get current working directory"
date: 2007-03-20
forum: General Help
---

### Post by pan69 on 2007-03-20
Hi,

Within my bash script I would like to assign the current directory, the directory were the script was started, not the directory of the script file itself, to a variable. Anyone knows how to do this?

Thanks!

---

### Post by ewankho on 2007-03-20
pwd?

---

### Post by pan69 on 2007-03-20
Yes, but from within a bash script and assigned to a variable.

---

### Post by kaamos on 2007-03-20
```

#!/bin/bash

working_directory=$(pwd)

echo $working_directory

```

---

