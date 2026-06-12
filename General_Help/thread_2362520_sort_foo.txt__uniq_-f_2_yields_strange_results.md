---
title: "sort foo.txt | uniq -f 2 yields strange results"
date: 2017-05-29
forum: General Help
---

### Post by John_Patrick_Mason on 2017-05-29
I'm getting strange results using uniq. I have a random test file that looks like this:

```

cat -A foo.txt
aaa^Iupc$
b$
c$
aaa^Iztp$
b$
c$
C$
A$
B$
B$
b$

```

I don't get why using:

```

sort foo.txt | uniq -f 2

```

gives me just:

```

A

```

If I tell uniq to ignore the second field, shouldn't I be getting:

```

aaa^Iupc$

```

instead? If uniq ignores the second field meaning upc and ztp, uniq will be left with two lines each with aaa and another aaa, and should therefore print the first occurrence of aaa or "aaa upc" so why doesn't it print it? Also if uniq ignores the second field why doesn't it also print:
```

A
b
B
c
C

```
The preceding lines don't have a second field so why aren't they in the final output?

---

### Post by steeldriver on 2017-05-29
You aren't telling uniq to ignore the second field, you're telling it to ignore *the first two* fields:

```

       -f, --skip-fields=N
              avoid comparing the first N fields


```

So no line in your example has more than two fields, they're all identical once the first two fields are ignored - hence you just get whichever happens to sort first

---

### Post by John_Patrick_Mason on 2017-05-29
> **steeldriver said:**
> You aren't telling uniq to ignore the second field, you're telling it to ignore *the first two* fields:

```

       -f, --skip-fields=N
              avoid comparing the first N fields


```

So no line in your example has more than two fields, they're all identical once the first two fields are ignored - hence you just get whichever happens to sort first

Ohhh, I see. I think I originally got confused after reading about the cut command with the -f option. There's one thing that I still don't get though. How come when I enter the command:

```

sort foo.txt | uniq -f 1

```

I get:

```

A
aaa    upc
aaa    ztp
b

```

More specifically, how come the letters A and b are still there? Isn't uniq with the -f 1 option supposed to ignore the first field where A and b are found?

---

### Post by steeldriver on 2017-05-29
Let's look at the output of the sort:
```

$ sort foo.txt
A
aaa     upc
aaa     ztp
B
B
b
b
b
C
c
c

```

From `man uniq`:
```

       Filter adjacent matching lines from INPUT (or standard input), writing to OUTPUT (or standard output).

```

Now think about what your `| uniq -f1` sees. 


[LIST]
[*]The first line, *ignoring field 1,* is empty
[*]The second line, ignoring field 1, is upc. Since this is different from the previous line, the previous line is unique and is printed (A)
[*]The third line, ignoring field 1, is ztp - different again
[*]The fourth line is different once more (again empty - if we ignore the field 1) so print it (b)
[*]The remainder of the lines, *ignoring field 1, *are the same as line 4 and therefore not unique
[/LIST]

---

### Post by John_Patrick_Mason on 2017-05-31
OK, I think I get it now. But in order to test my understanding I decided to modify the original file as so:
```

cat -A foo.txt
aaa^Iupc$
b$
c$
aaa^Iztp$
b$
c$
C$
A$
B$
B$
bbb^Ixpz$

```

which when I pass the file through sort gives me:

```

sort foo.txt
A
aaa    upc
aaa    ztp
b
b
B
B
bbb    xpz
c
c
C

```

If I then filter the output of sort with uniq I get:

```

sort foo.txt | uniq -f 1
A
aaa    upc
aaa    ztp
b
bbb    xpz
c

```

I understand everything, except one thing: how come the uppercase B is missing from the output? When uniq is told to ignore the first field where the uppercase B is found, just above "bbb xpz", in principle one should get an empty value, which when compared to xpz (again ignoring the first field) should give us the whole line where the uppercase B is found, right? Or am I missing something? If I understand correctly, both an empty value and xpz are unique, so both lines should be printed. So how come is only "bbb xpz" printed in the final output, but not uppercase B?

---

### Post by steeldriver on 2017-05-31
```

b
b
B
B

```

are all the same under uniq -f1, so only the first is printed

---

### Post by John_Patrick_Mason on 2017-05-31
> **steeldriver said:**
> ```

b
b
B
B

```

are all the same under uniq -f1, so only the first is printed

I'm not sure if I understand. Were you trying to answer the first question I had from the very beginning or were you trying to answer my last question, 'cause I was referring to my last question. When using the sort command on the modified file (last question):

```

B
bbb    xpz

```

become adjacent to one another. If I then use uniq -f 1 to tell uniq to ignore the first field,
B ---> (empty)
bbb ---> xpz

The way I see it is, since the empty "value" and "xpz" are both unique to one another, both lines should in principle be printed, lines:

```

B
bbb    xpz

```

so why isn't "B" in the final output? Or am I missing something? I hope the previous example will illustrate how I think uniq works, so that you can make corrections if you think I'm doing it wrong.

---

