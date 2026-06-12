---
title: "help with this bash script"
date: 2008-05-14
forum: General Help
---

### Post by elflord5 on 2008-05-14
1 #!/bin/bash
  2 pattern1='#! /bin/sh'
  3 pattern2='#!/bin/sh'
  4 pattern3='#!/bin/bash'
  5 pattern4='#! /bin/bash'
  6
  7 for i in `find $1 -type f`
  8 do
  9 str=`head -n 1 $i`
 10 if [grep '$pattern1' $str | grep '$pattern2'  $str | grep '$pattern3' $str | grep '$pattern4' $str]
 11 then
 12 echo $i
 13 fi
 14 done

something wrong with the quoting
any hint ?

thanks

---

### Post by Monicker on 2008-05-14
I believe you need double quotes instead of single quotes for line 10.  Single quotes will cause a literal match on $pattern1, instead of #!/bin/sh, for example.

---

### Post by elflord5 on 2008-05-14
i used double quotes at first
didnt work
thx though

---

### Post by bingoUV on 2008-05-14
1. Are you getting an error?
2. If not, is the script not behaving as you would like?
3. If yes, please outline current behaviour and intended behaviour.

---

### Post by Monicker on 2008-05-14
You should be more specific.  Are you getting error messages?  I know that the single quotes will match literally on $pattern1.

Test it yourself
```

#!/bin/bash

pattern1=test

echo "$pattern1"
echo '$pattern1'
```

---

