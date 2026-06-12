---
title: "Change color of text in python"
date: 2008-05-26
forum: General Help
---

### Post by Roberto_Lapuente on 2008-05-26
Is it possible to change the color of the text output in python running in terminal?

---

### Post by pointone on 2008-05-27
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)

```
#! /usr/bin/python

print "\033[34mThis is blue\033[0m"
```

---

### Post by michitoshi on 2011-07-19
For some reason it only appears:
[31mRed Text[0m
on my python shell when I write the code:

#! /usr/bin/python
print('\033[31mRed Text\033[0m')
 
Can someone please help me?

---

