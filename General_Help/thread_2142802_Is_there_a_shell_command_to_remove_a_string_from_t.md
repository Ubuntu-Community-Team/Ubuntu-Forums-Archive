---
title: "Is there a shell command to remove a string from the middle of multiple file names?"
date: 2013-05-06
forum: General Help
---

### Post by dmravaet on 2013-05-06
_**UPDATE - THIS PROBLEM HAS BEEN SOLVED**_

In case someone else runs into this problem, it was a much simpler solution than I expected:

```
rename 's/\. - String A -//' *
```

That was all it took.

_**ORIGINAL POST:**_

So here's the problem: I have something like a thousand files following similar naming conventions "**##. - String A - String B.extension**" that I want to cut down to "**## String B.extension**" (just removing "**. - String A -**")

More information in case it's necessary: ## is two digits; ## and String B are unique to each file in a given folder, whereas String A is the same for all files in a given folder or set of folders; both strings A and B contain spaces.

I figure I'll have to do it differently for each folder, but there are enough files in each folder (30-50) and few enough folders (<20) that this isn't a problem - I have a propensity for screwing up regular expressions and would like something into which I can just plug the relevant bits and paste it all into the command line to get this mess behind me. 

Thanks!

---

### Post by Lars Noodén on 2013-05-07
Remember that you can test your pattern thoroughly before applying it.  The open **-n** or **--no-act** lets you make a dry run and see what would have been changed without actually changing it.  This is something very useful when the patterns get complex.

---

