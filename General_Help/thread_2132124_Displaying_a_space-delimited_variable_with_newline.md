---
title: "Displaying a space-delimited variable with newlines with cat"
date: 2013-04-03
forum: General Help
---

### Post by Stonecold1995 on 2013-04-03
I want to display a space-delimited variable with newlines.  I'm using cat do do this.

If I have create a variable, say
```
var="a b c d e f g"
```

I want to be able to list each letter in a newline when doing
```
cat << _EOF
The list is:
$var
_EOF
```

The output is
```
The list is:
a b c d e f g
```

How do I make the output
```
The list is:
a
b
c
d
e
f
g
```

---

### Post by steeldriver on 2013-04-03
Well you could use 'tr' to replace spaces with newlines, e.g.

```
$ cat << EOF
The list is:
$(tr ' ' '\n' <<< "$var")
EOF

The list is:
a
b
c
d
e
f
g

```

(sed or awk would do as well)... or you could consider using an array instead of a string variable

---

