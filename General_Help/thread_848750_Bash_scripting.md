---
title: "Bash scripting"
date: 2008-07-03
forum: General Help
---

### Post by markeee on 2008-07-03
Hi - stupid question, i just cant remember how to do it, im at work and cant access my home machine to look at scripts i have written previously


How can i assign the result of the pwd command to a variable?

Thanks 

Mark

---

### Post by sisco311 on 2008-07-03
variable=`pwd`

---

### Post by markeee on 2008-07-03
ahh all i missed was the ` 

thanks mate

---

### Post by ghostdog74 on 2008-07-03
bash
```

variable=$(pwd)

```

---

