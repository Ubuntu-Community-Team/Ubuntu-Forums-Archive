---
title: "diff command  ignore-matching-lines"
date: 2007-11-30
forum: General Help
---

### Post by Tex-Twil on 2007-11-30
Hello,
I have problems with excluding some specific lines when running a diff command on two files

The documentation say
> 
-I RE  --ignore-matching-lines=RE
Ignore changes whose lines all match RE.

So I have to specify a reg ex to exclude the lines I want but when I try

```
diff -I '^[a]' b.txt a.txt
```
this has no effect on files containing lines starting with "a" that I would like to exclude.

thank for your help.,
regards,
TEx

---

### Post by jamvegan on 2007-11-30
If I understand your goal, then that command should work.  I just tested it with a file "one":
> a something
not a something else
howdy
blah
and a file "two":
> not a something else
howdy
a different line
blah

```
diff -I '^[a]' two one
```

This produces no output.  If I add a line that does not begin with 'a' to one of the files and run the same command, only the new line is output as a difference.

Are you certain that there is no whitespace or control character of any kind before the 'a' in the lines you're trying to ignore?

---

### Post by Tex-Twil on 2007-12-03
Hi,
how about this:
one:

[QUOTE=one]not a something else
howdy
blah diff
a different line
a something[/QUOTE]


two :

[QUOTE=two]not a something else
howdy
blah[/QUOTE]


```

diff -I '^[a]' two.txt one.txt

```

The output diff compares also the lines starting with an "a" since the whole "block" is starting with a non-matching line.

---

### Post by Tex-Twil on 2007-12-03
Another question but more related to the regular expression. What is the RE which stands for "all the lines that** don't **begin with a string HELLO"

---

### Post by jamvegan on 2007-12-03
> The output diff compares also the lines starting with an "a" since the whole "block" is starting with a non-matching line.

Ah, I see.  Well, you could use this:
```
diff -I '^a' one.txt two.txt | grep -v '^< a'
```
Which outputs this:
```
3,5c3
< blah diff
---
> blah
```

If the first line of diff's output is particularly significant to you, then this won't help, because it still shows the count based upon its strange behavior.  If all that you're concerned with is seeing the actual differences, though (minus lines starting with 'a'), this should work.

> 
Another question but more related to the regular expression. What is the RE which stands for "all the lines that don't begin with a string HELLO"

I do not know if there is a way to write a regular expression that negates itself.  Most tools that use regular expressions have an option or flag for this purpose, however.  (For instance, above I use "grep -v", which tells grep to output lines that do **not** match the regular expression.)  Actually, I do know of one way that you can do it in the regular expression itself, but it seems a little clunky to me:
```
^[^H][^E][^L][^L][^O]
```
The first '^', of course, matches the start of the line.  Within a set, however, if '^' is the first character after the '[' it means "match any character not in this set".

---

### Post by Tex-Twil on 2007-12-03
Ok thanks, it helps. I think with all these information I can do it :)

cheers,
Tex

---

### Post by jamvegan on 2007-12-03
> ^[^H][^E][^L][^L][^O]

You know, in thinking more about it, even this won't work.  It will not match a string starting with "HELLO", but it also will not match a string starting with "JELLO" or even "TALK", since it checks each character individually.  I really think that if you want to say not to match a string you need to do it with whatever you're passing the RE to, not in the RE, itself.

Hope some of this still helps! :-k

---

