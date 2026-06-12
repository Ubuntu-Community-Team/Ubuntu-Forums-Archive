---
title: "stop vim from wrapping"
date: 2007-06-30
forum: General Help
---

### Post by engine on 2007-06-30
OK, so I've more or less got the hang of recording simple keystroke macros in vim - but I can't find an automatic way to make them stop once they've hit the end of the file! (nor, come to that, a way of counting occurrences of a target string so I know what to specify as [count] before running the macro)

Hints and tips gratefully received!

---

### Post by engine on 2008-01-01
So, nobody knows, eh!

For anyone else who ever hits the same problem, I've found that I can work round it by counting the number of lines/occurrences I want the macro to hit. If I want to do something related to all occurrences of "orange", for example, I'd use
```
!grep -c orange %
```

Armed with that information, I can cautiously run the macro n-1 or n-2 times and see how close to EOF I get. I think I saw a reference to another count function in the Vim documentation, but I can't immediately track it down again.

---

