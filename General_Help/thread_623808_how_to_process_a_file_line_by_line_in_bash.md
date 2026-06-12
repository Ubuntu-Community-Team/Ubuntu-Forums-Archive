---
title: "how to process a file line by line in bash"
date: 2007-11-26
forum: General Help
---

### Post by jamadagni on 2007-11-26
I am aware of [this thread](http://ubuntuforums.org/showthread.php?t=510619) but I am searching for a different answer so I am posting.

I need to process a file line by line in bash. I am able to use ```
for x in $(cat filename)
``` only so long as the lines don't contain whitespace. If the lines contain space then the above code iterates over each word separated by whitespace.

The method in the other thread, which is to use exec and then while read line somehow seems like a hack. Besides, it can't be used on a commandline directly, (i.e. other than from inside a script). So is there another elegant method to do this? If I use line < filename then I get only one name and there is no way to make it iterate.

Thanks in advance.

---

### Post by HermanAB on 2007-11-26
There is no built-in debugger in Bash, but here are some tips:
[http://tldp.org/LDP/abs/html/debugging.html](http://tldp.org/LDP/abs/html/debugging.html)

In my experience, once you need a loop in Bash, you should switch to Perl.

Cheers,

Herman

---

### Post by geirha on 2007-11-26
Here are two ways of doing it. 

1. Change the internal field separator ($IFS) to only separate on newline:
```
#!/bin/bash

IFS=$'\n'
for line in $(cat filename); do
  echo $line
done
```

2. Use read in a while-loop:
```
#!/bin/bash

cat filename | while read line; do
  echo $line
done
```

---

### Post by jamadagni on 2007-11-26
Very nice people, thanks! Especially geirha!

---

