---
title: "[SOLVED] Messing around with Python, this seems weird"
date: 2008-05-25
forum: General Help
---

### Post by Watt on 2008-05-25
Hi all

Long time viewer, first time caller...

So in an effort to procrastinate instead of reading up for an exam I have been playing around in Pythons interactive shell and this happens:

```
>>> def poppop(s):
...     for t in s:
...             print t
...             if type(t)==int:
...                     s.pop(s.index(t))
... 
>>> s=['k','l',1,2,3,'k','l',4]
>>> poppop(s)
k
l
1
3
l
4
>>> s
['k', 'l', 2, 'k', 'l']
>>> type(s[2])
<type 'int'>
>>> poppop(s)
k
l
2
l
>>> s
['k', 'l', 'k', 'l']
```

Keep in mind that this is not supposed to be useful, or in fact used at all, but it seems odd that the "2" is left in "s" after the first run. Or am I missing some finer point?

BTW: I was wondering if this is supposed to go in the programming/development subforum, but I posted it here instead since I didn't figure it would actually qualify as programming. If I am wrong please let me know...

Kind regards
Watt

---

### Post by bwhite82 on 2008-05-25
Yeah, should have posted there, you would have gotten more responses. It is programming.

---

### Post by Watt on 2008-05-25
Never mind... I think I figured it out, sort of. When pop() is called the items in "s" change index and "s" is not updated. I feel kind of silly posting now, but I'll survive. And I will remember to post in programming/development next time, should I stumble on something similar.

Watt

---

