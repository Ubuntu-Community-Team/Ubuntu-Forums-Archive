---
title: "Renaming multiple directories"
date: 2014-11-12
forum: General Help
---

### Post by meanmrmustard on 2014-11-12
I have multiple directories whose names are prefaced with a four digit number eg. "1801 - " seven characters in all,  that I would like to remove, leaving only the file names.

I know the mv command would rename them but I'm not sure if this would be the best way or if it can be invoked to act on all the directory names.

Am I on the right track or is there a better way go about it?

---

### Post by Vaphell on 2014-11-12
4 digits, space, -, space?

```
for d in [0-9][0-9][0-9][0-9]*/; do mv "$d" "${d#*- }"; done
```

---

### Post by meanmrmustard on 2014-11-12
I just found this:
```
rename -nv 's# \([0-9][0-9][0-9][0-9]+\)/#/#' */
```

which works on four digits at the end of the dir's name.

How can I test your code without it actually doing anything?

---

### Post by papibe on 2014-11-12
Hi meanmrmustard.
> **meanmrmustard said:**
> How can I test your code without it actually doing anything?
Just like that. The option -n is for 'dry run'. It would print 'renaming this for that', but it won't actually do it.

When you tune the command and are sure it's going to do want you want, just run it with out that option.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by meanmrmustard on 2014-11-12
Hi Papibe,

I was referring to Vaphell's code:
```
for d in [0-9][0-9][0-9][0-9]*/; do mv "$d" "${d#*- }"; done
```

---

### Post by Vaphell on 2014-11-12
usually i use *echo* in front of or instead of *mv*, then if i like the results printed to the screen i restore the actual command

---

### Post by meanmrmustard on 2014-11-12
Thanks!

What exactly is this code anyway?
I barely have a passing familiarity with the CLI, let alone anything else like sed or awk.
What do I need to study to understand this kind of code?

---

### Post by meanmrmustard on 2014-11-12
> **Vaphell said:**
> 4 digits, space, -, space?

```
for d in [0-9][0-9][0-9][0-9]*/; do mv "$d" "${d#*- }"; done
```

I placed echo in front of mv and got:  ```
syntax error near unexpected token `echo'
```
Same result when I replaced mv with echo.

edit:
I finally got brave and just ran the command.
Thanks again, now to find out what I did :)

---

### Post by Vaphell on 2014-11-13
it's a loop that goes over the 4digits+whatever directories
${d[COLOR="#0000CD"]#[/COLOR][COLOR="#008000"]*- [/COLOR]} means [COLOR="#0000CD"]strip leftside[/COLOR] [COLOR="#008000"]anything+'- '[/COLOR]
as a whole means rename dir saved in $d to $d with prefix stripped.

[http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)

---

### Post by meanmrmustard on 2014-11-29
Thanks.

---

