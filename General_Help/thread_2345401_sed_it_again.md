---
title: "sed it again"
date: 2016-12-03
forum: General Help
---

### Post by maclenin on 2016-12-03
With deference to this earlier [post]("https://ubuntuforums.org/showthread.php?t=1835526&p=11199193#post11199193"), I am trying to append an incremental sequence of numbers - starting with 0 (and then +1) - to a known quantity of matches in a file.

The source file and the match "id"
```
id
data
data
data
id
data
data
data
...
id
data
data
data
```
I have run grep to capture the quantity of "id"
```
a=$(grep -c '^id' source)
```
I have started to test a while loop to append a number to each matching "id"
```
c=0
while [ $c -lt $a ]
do sed "s/id/id:$c/"
((c++))
done < source > target
```
...which yields the following target file:
```
id:0
data
data
data
id:0
data
data
data
...
id:0
data
data
data
```
...for some reason the value of "c" does not increment?

Thanks for any guidance!

---

### Post by steeldriver on 2016-12-03
Why sed? it would be much easier to use something like awk

```

$ awk '/^id/ {$0=$0":"i++}1' source
id:0
data
data
data
id:1
data
data
data
...
id:2
data
data
data

```

---

### Post by maclenin on 2016-12-04
Indeed - a much simpler turn-key solution - thank you (with a redirect appended)!
```
awk '/^id/ {$0=$0":"i++}1' < source > target
```
Just a few additional comments / questions:

1. Why sed? I have experience with sed - that's it. Now I'll play with awk.
2. What does the 1 at the end of the 'increment' statement do?
3. There must be a way to get the c to increment (for the sake of solving the sed riddle).

Thanks, again, for the great awk!

---

### Post by steeldriver on 2016-12-04
The `1` is awk shotrhand for `{print}` (awk's default action is to print if a rule evaluates as `true`)

--

Your whole loop approach makes no sense imho

It will read `source` - ONCE - and apply the sed command to all of it, with the initial value of `c` (i.e. c=0)

You could modify it to re-read `source` on every iteration - but then it will replace EVERY instance of `id` with the CURRENT looped value of `c`

Or you could modify it to read and process each line of `source` separately - but then `c` will increment once for each line, rather than once for each replacement

So you need to process the whole file ONCE but keep track of the number of replacements made - to do that using sed in a shell loop you would need to find and replace the first *unmodified *occurrence each time

---

### Post by maclenin on 2016-12-04
Thanks for the '1' clarification.

Point taken re: loop and sed. I was trying to modify the linked (from OP) solution - in hamstrung fashion - hoping to marry loop (increment) with sed (matching).

awkward and upward!

---

