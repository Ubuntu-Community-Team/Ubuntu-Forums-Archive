---
title: "syntax error near unexpected token `fi'"
date: 2022-08-18
forum: General Help
---

### Post by raleigh3 on 2022-08-18
I am trying to find if 18.04 is in File.

When I run the script below,  I get

```


When I run this I get


/home/andy/bin/test.sh: test.sh: line 12: syntax error near unexpected token `fi'
/home/andy/bin/test.sh: test.sh: line 12: `fi'

#!/bin/bash

File="/home/andy/Downloads/linux_Version_Running.txt"

lsb_release -d -s > "$File"
 
if grep -q 18.04 "$File"; then
   # SomeString was found
fi


```

---

### Post by &amp;KyT$0P# on 2022-08-18
You need an actual command in the if block, not just a comment.

---

### Post by raleigh3 on 2022-08-18
Thanks a lot halogen2.

---

