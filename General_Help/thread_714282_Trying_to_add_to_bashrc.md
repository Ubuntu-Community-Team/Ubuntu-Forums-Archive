---
title: "Trying to add to bashrc"
date: 2008-03-03
forum: General Help
---

### Post by thelugnut on 2008-03-03
I am trying to add a couple of safety commands to the bashrc file.

My entries are:

> # asks if you are sure
alias rm = ' rm -i ' 
# asks if you are sure and tells you what you did 
alias cp = ' cp -iv ' 
# asks if you are sure
alias mv = ' mv -i '  


These entries are made in the area of the comments and suggested alias area.

I restarted the cp, called up the terminal, and executed the "rm" command on a test file. The file immediately is deleted with no warning message. The file just deletes as before.

What am I forgetting?

Thanks

---

### Post by imtheguru on 2008-03-03
$ source .bashrc

Re-reads the file and sets the new variables.

---

### Post by thelugnut on 2008-03-03
Many thanks, for sure.

---

### Post by drs305 on 2008-03-03
Try removing the spaces on both sides of the =  . Spaces inside the quotes seem to be okay.
```
alias rm='rm -i' 
```

---

### Post by thelugnut on 2008-03-03
Yes, removing the spaces did it. 

Thank you very much

---

