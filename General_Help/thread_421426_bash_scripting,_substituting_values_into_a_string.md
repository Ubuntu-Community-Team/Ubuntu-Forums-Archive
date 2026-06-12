---
title: "bash scripting, substituting values into a string"
date: 2007-04-24
forum: General Help
---

### Post by Skrynesaver on 2007-04-24
I have a string in a bash script such that 
STRING ='$USER'
how can i echo this string as though I was calling
echo $USER
directly, ie
echo $STRING
return literal $USER as opposed to skrynesaver

---

### Post by AusIV4 on 2007-04-24
It's 
STRING=$USER
not 
STRING='$USER'

---

### Post by Skrynesaver on 2007-04-24
Would that it were, the situation is that I am iterating through several users in an ldap server and updating a given attribute.  I wish to be able to offer a command line value \u which will be evaluated as $USER in the new value, thus when setting $NEW_VALUE I have to insert a placeholder which will be evaluated to $USER for each user on the server or within a specified domain or whatever the search term works out as.

---

### Post by Skrynesaver on 2007-04-24
Ahh, eval was what I needed, just wasn't sure how to use it
in the above case
```

eval echo "$STRING has cracked it"
skrynesaver has cracked it"

```

---

