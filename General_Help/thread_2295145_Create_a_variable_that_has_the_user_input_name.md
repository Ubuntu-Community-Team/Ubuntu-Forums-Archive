---
title: "Create a variable that has the user input name"
date: 2015-09-16
forum: General Help
---

### Post by CkDGTAT on 2015-09-16
Hi,

How can I create a variable named by the user input?

In other words:

[LIST]
[*]I ask the user to enter a variable name
[*]He answers 'input'
[*]I now want to have a global variable called $input and be able to assign a value to it
[/LIST]

Thank you

---

### Post by brian-mccumber on 2015-09-16
Does not compute... Syntax error in "variable named by the user input"...jk

Normally this is not how variables are made, why would you want to do this? This is just asking for trouble, users could input anything and quite possibly break the program very easily. But if you really want to do this you could possibly do it by using pointers.

---

### Post by steeldriver on 2015-09-16
If you are referring to the bash shell, you *could* use eval

```

$ varname=input
$ eval $varname=someval
$ echo $input
someval

```

However there are some caveats - especially with respect to word-splitting: see [http://stackoverflow.com/questions/9714902/how-to-use-a-variables-value-as-other-variables-name-in-bash](http://stackoverflow.com/questions/9714902/how-to-use-a-variables-value-as-other-variables-name-in-bash)

Generally, I'd recommend avoiding this kind of thing

---

### Post by QDR06VV9 on 2015-09-16
> **steeldriver said:**
> If you are referring to the bash shell, you *could* use eval

```

$ varname=input
$ eval $varname=someval
$ echo $input
someval

```

However there are some caveats - especially with respect to word-splitting: see [http://stackoverflow.com/questions/9714902/how-to-use-a-variables-value-as-other-variables-name-in-bash](http://stackoverflow.com/questions/9714902/how-to-use-a-variables-value-as-other-variables-name-in-bash)

Generally, I'd recommend avoiding this kind of thing
I was Having a senior moment here.:redface:
Old Habits Die Hard.:D
Thanks for the link steeldriver
> [FONT=Helvetica Neue]This breaks:
[/FONT]eval $name_of_variable="word splitting occurs"
[FONT=Helvetica Neue]The fix:[/FONT]
[FONT=Consolas]eval $name_of_variable="\"word splitting occurs\""  # not anymore[/FONT]
Regards

---

