---
title: "How do I translate digits to alphanumerics?"
date: 2008-02-15
forum: General Help
---

### Post by newnet on 2008-02-15
```
echo "15" | tr [:digit:] [:alnum:]
```
```
echo "15" | tr [:digit:] [0-9A-Z]
```

None of the above worked.  The answer should be "F".

How do I translate digits to alphanumerics?

---

### Post by neurostu on 2008-02-15
when you say 15 should be F, this is in reference to what mapping, Ascii, Unicode, etc?

---

### Post by B'man on 2008-02-15
If you're talking about converting denary to hexadecimal, you can use bc:

```
echo 'ibase=10; obase=16; 15' | bc
```

---

### Post by newnet on 2008-02-15
I do not know what the term is called.  It is something simular to "denary to hexadecimal".  But hexadecimal ends at F.  What I am looking for ends at Z.

So (0 is ignored) 1-9 would be translated normally.  10 would be translated to A. 35 would be translated to Z.

B'Man, the code you have given me works, but it only goes as far as 16 since it based on hexadecimal.  I tried to adjust the code, but the bc manual says 16 is the limit.

Any more ideas?

---

### Post by Zwack on 2008-02-15
Um, any particular reason for trying to use base 36?  It's not a particularly common base to use.

tr translates single characters form one set into another so tr [A-Z] [a-z] would lowercase everything...  It doesn't know that you consider 15 to be one chareacter not two.

You might need to do some simple programming to achieve the results that you want.

Z.

---

### Post by ebash on 2008-02-15
This one liner can only handle numbers from 0 to 35:

```
perl -le '$n = shift; print $n < 10 ? $n : chr( ord("A") + $n - 10 )' 28
```

Beyond that you will need to write a function.

---

