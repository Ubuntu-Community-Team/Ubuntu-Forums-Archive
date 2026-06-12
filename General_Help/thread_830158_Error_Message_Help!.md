---
title: "Error Message Help!"
date: 2008-06-15
forum: General Help
---

### Post by Landscapeman on 2008-06-15
I need help on this error message. Any Ideas?


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 58 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.'

---

### Post by drs305 on 2008-06-15
> **Landscapeman said:**
> 
'E:Malformed line 58 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.'

the message is telling you there is an error in your /etc/apt/sources.list

Look at line 58 for the error. If you can't figure it out, please post:
```
cat /etc/apt/sources.list
```

---

