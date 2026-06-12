---
title: "Simple regex question"
date: 2013-02-03
forum: General Help
---

### Post by terminator14 on 2013-02-03
I have a small regex question for you guys. If I have several lines of input and I want to use grep to exclude strings that are "one or more numbers, followed by the letter a" from it, it makes sense to me that I would run:

```
echo -e '1z\n1a\n4b\n10a\n10b' | grep --color=always '[0-9][0-9]*[^a]'
```

The output I would expect is:
```
[COLOR="Red"]1z
4b
10b[/COLOR]
```

but instead, I get:

```
[COLOR="Red"]1z
4b
10[/COLOR]a
[COLOR="Red"]10b[/COLOR]
```

when it comes to the "10a" line, grep seems to break it down like this (as far as I can tell):

the first [0-9] of the expression matches the first character (1). The [0-9]* does NOT match the second character (0) but instead matches nothing (zero occurrences). The [^a] matches the second character (0).

Is this what it does? And if so, why does it do it this way instead of [0-9] matching "1", [0-9]* matching "0", and [^a] matching the "a", and excluding the string from the output?

PS. Yes - I'm aware that there are 10 different ways to do this, including using "grep -v", and "egrep [0-9]+", but my question is why the method above doesn't work the way I expect it to.

---

