---
title: "cd into directory beginning with a &quot;-&quot;"
date: 2008-04-13
forum: General Help
---

### Post by update_manager on 2008-04-13
How can I cd into a directory that begins with a "-" character?

I get this error:
-bash: cd: -9: invalid option
cd: usage: cd [-L|-P] [dir]

---

### Post by wormser on 2008-04-13
I do not think it can be done.  The shell see the - as an option is coming next.  Go into Nautilus and remove the - infront of the name.

---

### Post by munkyeetr on 2008-04-13
I was able to do it by using:
```

cd ./-hello

```

I tried a few other things
```

cd "-hello"
cd *hello

```
and they didn't work, so I think you need to get something else in front of the "-" character, which is why using an explicit path (like ./-hello) worked.

---

### Post by sisco311 on 2008-04-13
```
cd -- -dirname
```

---

### Post by munkyeetr on 2008-04-13
> **sisco311 said:**
> ```
cd -- -dirname
```
Nice. How did you figure that out and do you know why does it works? Sorry, but I've found (in the last 2 minutes) limited information on the **cd** command. What does the -- do?

---

### Post by wormser on 2008-04-13
It would have been a lot easier on me a week ago if I knew about this.

---

### Post by sisco311 on 2008-04-13
**--**
The *double-dash*         -- prefixes *long*         (verbatim) options to commands.

Used with a Bash builtin, it means the *end of         options* to that particular command.


[http://tldp.org/LDP/abs/html/special-chars.html](http://tldp.org/LDP/abs/html/special-chars.html)

---

### Post by munkyeetr on 2008-04-13
> **sisco311 said:**
> **--**
The *double-dash*         -- prefixes *long*         (verbatim) options to commands.

Used with a Bash builtin, it means the *end of         options* to that particular command.


[http://tldp.org/LDP/abs/html/special-chars.html](http://tldp.org/LDP/abs/html/special-chars.html)

Thank you

---

