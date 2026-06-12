---
title: "Multiline operations with sed"
date: 2014-08-29
forum: General Help
---

### Post by hojjat on 2014-08-29
I have a text file in wihch I want to replace the instances of   [COLOR="#008080"]*"\n"","*[/COLOR]   with    [COLOR="#008080"]*","*[/COLOR]   and I can do that with VI using [COLOR="#800080"]%s/"\n"","/","/g[/COLOR] but I have to do it one file at a time. I was wondering if I could do that same thing inside a script, and using sed. It seems that sed takes the input line-by-line and therefore cannot ever match "\n" which I need for above. Any recommendations on how to make regex replacements in a blob of text just using shell commands?

---

### Post by Lars Noodén on 2014-08-29
> **hojjat said:**
> I have a text file in wihch I want to replace the instances of   [COLOR="#008080"]*"\n"","*[/COLOR]   with    [COLOR="#008080"]*","*[/COLOR]   and I can do that with VI using [COLOR="#800080"]%s/"\n"","/","/g[/COLOR] but I have to do it one file at a time.

You could use [tr](http://manpages.ubuntu.com/manpages/trusty/en/man1/tr.1posix.html) instead, as long as the substitute is only a single character:

```

tr '\n' ',' < somefile.txt

```

> **hojjat said:**
> 
 I was wondering if I could do that same thing inside a script, and using sed. It seems that sed takes the input line-by-line and therefore cannot ever match "\n" which I need for above. 


Here is one explanation of how to do it with sed:
[https://stackoverflow.com/questions/1251999/sed-how-can-i-replace-a-newline-n](https://stackoverflow.com/questions/1251999/sed-how-can-i-replace-a-newline-n)

```

sed ':a;N;$!ba;s/\n/ /g' < somefile.txt

```

> **hojjat said:**
> 
Any recommendations on how to make regex replacements in a blob of text just using shell commands?

For regex, I would tend to use perl myself.  However, some substitutions can be done with bash by itself.  Vaphell or some others have that down and hopefully will find the thread here.

---

### Post by hojjat on 2014-08-29
tr wouldn't work in my case, because more than one character was involved. The example you gave me for sed actually is astounding. I will explore that more.

Thanks a lot!

---

