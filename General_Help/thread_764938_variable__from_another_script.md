---
title: "variable  from another script"
date: 2008-04-24
forum: General Help
---

### Post by big136 on 2008-04-24
Hi,
in script11 I define a variable (myvar11) and give him a value.
I want use the value of this varible in script22 but in a new variable. I thought to give the value of myvar11 to exit value of script11. Is it a good idea ? If yes how can I do that ? If not any other solution ?
 Many thanks.

---

### Post by bingoUV on 2008-04-24
Does script22 invoke script11? If so, it is a reasonable solution.

---

### Post by justleen on 2008-04-24
in bash your kinda limited to pass variables.. the easiest (if not the prettiest) is to just to store the var in a file
```

file1:
echo myvar11 > tempfile

file2:
script11=`cat tempfile`
rm tempfile


```

---

### Post by big136 on 2008-04-24
YES but I do not know how ?
Thanks for help.

---

### Post by justleen on 2008-04-24
dummy example when invoked in the script:
file1: ```

#!/bin/bash

echo "this is your output"

```file2```


#!/bin/bash

VAR=`./test`

echo $VAR

```

---

### Post by big136 on 2008-04-24
thank you.

---

