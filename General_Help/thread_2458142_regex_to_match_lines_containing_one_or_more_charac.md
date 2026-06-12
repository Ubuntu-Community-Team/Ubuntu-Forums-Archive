---
title: "regex to match lines containing one or more characters"
date: 2021-02-17
forum: General Help
---

### Post by jcdenton1995 on 2021-02-17
Hello all,

I'm trying to write a sed expression which will insert a tab at the start of each line which has some content, i.e I don't want to simply insert a tab at the beginning of every line. I've tried the following but it doesn't seem to match...```
sed s/^.+$/\\t&/g [input file]
```There seems to be two problems, first as mentioned the regex doesn't match anything, and also according to the sed info pages...```
the REPLACEMENT can contain unescaped '&' characters which reference the whole matched portion of the pattern space
```but when I try this as in my example above, it results in the subsequent "/g" being interpreted as a filename

Any pointers would be much appreciated!

---

### Post by dragonfly41 on 2021-02-17
There is a tool named SearchMonkey in Ubuntu.
In Advanced tab there is a RegEx Expression Builder.
You can use the builder to test regex expressions on a sample file.

---

### Post by TheFu on 2021-02-17
The requirements as written are ambiguous.
```
This matches
   This matches
     
   # this matches
#$ this matches

```

Line 3 has spaces which can be considered "content", so it gets a tab added too.
The last line is empty, but exists. No tab is added.

Must the 1st column always have a non-space character or not?
If it was me and I didn't have perl, I'd use a 2-stage solution.
[LIST=1]
[*] add the tab the the beginning of every line  -e s/^/\t/g
[*] remove the tab on all lines that don't have any other content  -e s/\t$//g
[/LIST]

That would look like:
```
$ sed -e 's/^/\t/g' -e 's/^\t$//g' {input_file}
```

I tested the above input file with that and it appeared to work to me.

With perl, we can do smarter matching and grouping so the prior match isn't just removed, but captured for use later.  Very handy when we need to swap columns in code.  Of course, swapping columns is trivial in vim. ;)

If you want to include whitespace in the definition of content, but only at the front of the line. Then questions about the requirements still exist.  In perl, a little function that removes all leading and trailing whitespace is handy:
```
 $line =~ s/^\s+|\s+$//go;
```
I don't think sed supports \s.  Maybe there is a -E options for full regex support in sed? Seems so from the sed manpage: 
```
       -E, -r, --regexp-extended

              use extended regular expressions in the script (for portability use
              POSIX -E).
```

---

### Post by spjackson on 2021-02-17
> **jcdenton1995 said:**
> 
```
sed s/^.+$/\\t&/g [input file]
```
There are 2 problems with that.
1. & has meaning to the shell. An incomplete sed command is backgrounded then another command beginning with /g is attempted to be executed. You need to prevent the shell from interpreting the &.
2. + only has the meaning of "one or more" if the -E switch is used.
Hence:
```
sed -E 's/^.+$/\t&/g' [input file]
```

---

### Post by jcdenton1995 on 2021-02-17
> **TheFu said:**
> Must the 1st column always have a non-space character or not?In a manner, I'm just trying to find a way of applying indentation to all the lines within a given range that actually contain something, there are also lines that contain nothing at all (no white spaces, tabs or the like) which I *don't *want to prepend with a tab. Mainly because it's messy and not really the correct way I guess.
> If it was me and I didn't have perl, I'd use a 2-stage solution.
[LIST=1]
[*] add the tab the the beginning of every line  -e s/^/\t/g 
[*] remove the tab on all lines that don't have any other content  -e s/\t$//g 
[/LIST]

That would look like:
$ sed -e 's/^/\t/g' -e 's/^\t$//g' {input_file}I had to chuckle at this because I never considered doing it in two stages :) I'll give it a try tomorrow when I'm not falling asleep. As for the Perl, I'll steer clear of that for now, I don't think I'm equipped to learn regular expressions and Perl at the same time! Thanks.

---

### Post by jcdenton1995 on 2021-02-17
> **spjackson said:**
> There are 2 problems with that.
1. & has meaning to the shell. An incomplete sed command is backgrounded then another command beginning with /g is attempted to be executed. You need to prevent the shell from interpreting the &.
2. + only has the meaning of "one or more" if the -E switch is used.
Hence:
```
sed -E 's/^.+$/\t&/g' [input file]
```

Thanks, good to know about the -E (for extended regular expressions?). Also confusing is how the sed documentation says the '&' can be unescaped, but I suppose that might be like saying that as far as 'sed' is concerned it can be unescaped, but it makes no assumptions about which shell you are using and how that will interpret the ampersand.

---

