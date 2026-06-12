---
title: "Looking for a text replace program."
date: 2008-05-20
forum: General Help
---

### Post by EarloftheWest on 2008-05-20
Does anyone know of a program that will automatically replace text I type with other text?

For example, if I type
lvm

the application will automatically replace it with Left a message.

Thanks.

---

### Post by cdtech on 2008-05-20
You could use the ~/.bash_aliases to do that.
alias lvm="echo 'leave a message'"

Hope this help........

P.S.
I just noticed.
> the application will automatically replace it with Left a message.
That would be the program your using (maybe shortcut keys). I commented using the command line.

---

### Post by bingoUV on 2008-05-20
What application are you typing into? Different applications have different ways to do it. Some applications may not have a way to do it at all. e.g. in vim, 
```

:abbreviate lvm Left a message

```
Typing lvm after this will leave "Left a message" on the screen.

---

### Post by barnex on 2008-05-20
You can use the program 'sed' to edit data streams. eg, in your case: ```
sed 's/lvm/Left a Message/g'
``` This will read text from the standard input, then globally substitute ('s', 'g') lvm by Left a Message, and print the result to the standard output. You can also pipe data from other programs through one or more sed filters: ```
program-that-generates-output | sed 's/lvm/left a message/g' | program-that-reads-input
``` Also nice, 'awk' is a more sophisticated program to manipulate text.

---

### Post by EarloftheWest on 2008-05-20
Thanks folks. I will give these a try.
I'm looking to use these keystroke short cuts in several applications so I'm looking for something that can be used globally.

Thanks again.

---

