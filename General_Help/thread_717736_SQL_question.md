---
title: "SQL question"
date: 2008-03-07
forum: General Help
---

### Post by Marco_Polo on 2008-03-07
Is there a way to store computed values in a field?  For example, if I have two columns storing floats, can I have a third column containing their sum?

One idea I've had is to issue:
SELECT (A + B) AS C FROM test; 
and then insert the values - is there a single query way to do that?

I realize that one generally wants stored data to be independent, but I'd like to build up sort of complex values like r = (x^2+y^2+z^2)^1/2, and then be able to use r in other calculations.

Thanks for any help.

---

### Post by indytim on 2008-03-07
how about:

update t1 set f3=f2+f1 where id>0

(assuming id is your auto-incrementing primary key)

IndyTim

---

