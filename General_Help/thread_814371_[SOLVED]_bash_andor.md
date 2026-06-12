---
title: "[SOLVED] bash and/or"
date: 2008-05-31
forum: General Help
---

### Post by ezramorris on 2008-05-31
Hi, if I did the following in bash:
```
command1 || command2 && command3
```
would command3 execute if command1 is successful or command2?

If command2, then how do I make command2 run if command1 fails and command3 run if command1 is successful?

At the moment I do this, but it's a bit bulky:
```
command1
case in $?
  0) command3
  *) command2
```

Thanks.

---

### Post by dagnabit dang doohickey on 2008-05-31
This would be the most obvious way to write the code:
```
if command1 ; then
    command2
else
    command3
fi
```


The following will execute command2 if command1 is false, then execute command3 if command2 is true. Or, execute command3 if command1 is true.
```
command1 || command2 && command3
```


The following will execute command2 if command1 is true, then execute command3 if command2 is false. Or, execute command3 if command1 is false.
```
command1 && command2 || command3
```

As you can see, the above two examples lack the if-then-else symmetry.

---

### Post by ezramorris on 2008-06-01
> **dagnabit dang doohickey said:**
> This would be the most obvious way to write the code:
```
if command1 ; then
    command2
else
    command3
fi
```


The following will execute command2 if command1 is false, then execute command3 if command2 is true. Or, execute command3 if command1 is true.
```
command1 || command2 && command3
```


The following will execute command2 if command1 is true, then execute command3 if command2 is false. Or, execute command3 if command1 is false.
```
command1 && command2 || command3
```

As you can see, the above two examples lack the if-then-else symmetry.

Thanks, that's a great help.

---

