---
title: "Please explain this?"
date: 2014-10-06
forum: General Help
---

### Post by prasanna_kumar3 on 2014-10-06
```
sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta' 
```

filenamethe decsription from where i got this says:[COLOR=#000000][FONT=Helvetica Neue]

Add commas to all numeric strings in a file, changing "1234567" to "1,234,567" 
[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-10-06
Is there a prize for guessing correctly? Do I get a certificate of excellence?

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

Regards.

---

### Post by prasanna_kumar3 on 2014-10-06
thank u for the wonderful link!! :p

---

### Post by nerdtron on 2014-10-06
Thanks for the link. Been using sed for some time now but time to study more :)

---

### Post by steeldriver on 2014-10-06
Specifically, the regex

```

\(.*[0-9]\)\([0-9]\{3\}\)

```

matches a (group of **3** digits) following the longest (group of characters that **ends** in a digit), and 

```

\1,\2

```
substitutes the two groups back with a comma in between. The

```

ta

```
is a conditional branch back to label :a, which causes this substitution expression to be applied repeatedly on the pattern space, until there are no further matches/substitutions to be made. So it effectively (if required) places a thousands separator, then (if required) a millions separator and so on. If there are multiple numbers in a line it will start from the last and work back towards the first (due to the greedy .* in the first group). At least I *think* that's how it works.

---

