---
title: "change directory"
date: 2008-05-25
forum: General Help
---

### Post by raedbenz on 2008-05-25
Hi

the "cd.." doesnt work, i get this:

raed@raed-laptop:~/Documents/compile$ cd..
bash: cd..: command not found

why?
thanks

---

### Post by sisco311 on 2008-05-25
Type a space between the command and the periods.
```
cd ..
```

You can create an *alias* in your ~/.bashrc file.

Copy this line in the file
> alias cd..='cd ..'
and from the terminal:
```
alias cd..='cd ..'
```

---

### Post by Sarah L on 2008-05-25
You should put a space between cd and ..
like this : ```
cd ..
```

The .. is the argument and cd is the command; if you mix them together, Linux wants to run the command cd..!

---

