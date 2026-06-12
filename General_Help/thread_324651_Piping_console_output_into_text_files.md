---
title: "Piping console output into text files"
date: 2006-12-24
forum: General Help
---

### Post by studiesrule on 2006-12-24
I was wondering about how to pipe to output of a console command, say gcc, into a text file. The reason I want to know is that I can go about fixing my compile errors quickly, and whenever I have errors like Xorg init errors, i'd like to save them to file so i can read them or post them.

---

### Post by po0f on 2006-12-24
studiesrule,

You can redirect stdio to a file:
```
[FONT="Courier New"]$ gcc -Wall -o my_program my_source.c > output.log[/FONT]
```
But I don't see how this will help you fix your compile errors faster.

---

### Post by studiesrule on 2006-12-24
ok thanks. basically, I have a linker error, which produces a heck load of junk. I can't get to the beginning of it because its too large. So if i pipe it to a text file, I'll be able to see the first few lines which I think might give me more info on what to do.
Otherwise also, I wanted to know it as a general tool.
Thanks again and merry xmas

---

### Post by po0f on 2006-12-24
studiesrule,

How much is 'a heck load'?  :)  You can't scroll up in the terminal?

BTW, you can use `tee` to view the output and redirect to a log file at the same time.

---

