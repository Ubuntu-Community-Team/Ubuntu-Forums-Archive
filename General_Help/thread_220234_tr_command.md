---
title: "tr command"
date: 2006-07-21
forum: General Help
---

### Post by rob3000 on 2006-07-21
hello,

I want to use the tr command in the vi to delete certain caracters of a text, but when I try to use it in the command mode like that:

:tr 'abc' ' '

so the caracters a b and c should be deleted from the text. but when I press after entering this statement in the command mode there occurs an error - Trailing Caracters.

Has anybody an idea how I have to define that tr statement to make it work?

---

### Post by kabus on 2006-07-21
Couldn't you just use the internal search and replace functionality?

```
%s/[abc]//g
```

---

### Post by der_joachim on 2006-07-21
I agree with Kabus. Why use all the effort for something which is already built-in?

 For the sake of completeness: you will want to use the *-d* argument for tr. The console command would be something like ```
tr -d [abc] < foo.txt
```

---

