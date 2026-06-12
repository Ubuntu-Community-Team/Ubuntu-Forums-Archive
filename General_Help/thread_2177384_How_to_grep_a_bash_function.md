---
title: "How to grep a bash function"
date: 2013-09-28
forum: General Help
---

### Post by CkDGTAT on 2013-09-28
Suppose I have a file containing

```


REST1

function myfunction(){

body of the function

}

REST2 
```

I 'd like to grep only (given the name myfunction)

```
function myfunction(){

body of the function

}
```

Thank you

---

### Post by steeldriver on 2013-09-28
If there are no other right braces before the closing brace of the function, you could awk or sed it

```
awk '/myfunction/,/}/ {print}' myfile
```

```
sed '/myfunction()/,/}/!d' myfile
```

If there *are* other braces, then afaik you'd need a true syntax-aware parser

---

### Post by Lars Noodén on 2013-09-28
> **steeldriver said:**
> If there are no other right braces before the closing brace of the function, you could awk or sed it

```
awk '/myfunction/,/}/ {print}' myfile
```

That's listed in [awk](http://manpages.ubuntu.com/manpages/raring/en/man1/awk.1posix.html) but not really explained.  Thanks for showing it.

One further refinement might be to only look for the string when it is at the start of a line.  Otherwise, you risk printing calls to the function rather than just the function alone.

```

awk '/^myfunction/,/}/ {print}' myfile

```

---

### Post by sudodus on 2013-09-29
You can also use csplit. See the info page

```
info csplit
```

for example

```
csplit file.bash '/^function/' '{*}' 
```

---

