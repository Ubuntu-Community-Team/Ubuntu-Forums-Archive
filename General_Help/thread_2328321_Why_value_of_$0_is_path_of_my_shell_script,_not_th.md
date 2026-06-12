---
title: "Why value of $0 is path of my shell script, not the element match * in my array?"
date: 2016-06-19
forum: General Help
---

### Post by sincos2007 on 2016-06-19
Why value of $0 is path of my shell script, not the element match * in my array? How can I reference element match * in the array at place of $0

```
    arrayZ=( one two three four )
    echo ${arrayZ[@]//*/$0}
```

Thanks

---

### Post by CaptainMark on 2016-06-20
I'm not expert but variables with a number I think are reserved for the arguments given to the program, so $0 is the command you used to run the program $1 is it's first argument $2 the second etc.

I think you want to use this to show a variable from an array if that's what you're trying to do 

```

echo ${arrayz[0]}

```

---

