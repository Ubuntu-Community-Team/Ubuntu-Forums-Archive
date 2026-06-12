---
title: "Using ps with grep and awk doesn't work with watch"
date: 2015-05-27
forum: General Help
---

### Post by matheusgeres on 2015-05-27
Greetings,

I made this command to see my usage memory of Google Chrome.

```
ps -aux|grep chrome|awk 'BEGIN{x=0;y=0;}{x=x+$4;y=y+$6}END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}'
```

And I receive this response.

```
23.2% Memory and 1.34965 Memory Size(GB)
```

But when I try to use this command with watch I receive this message
```
matheus@lighter:~$ watch -d -n1 "ps -aux|grep chrome|awk 'BEGIN{x=0;y=0;}{x=x+$4;y=y+$6}END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}'
bash: syntax error near unexpected token `('
```

Anyone can help me?

---

### Post by steeldriver on 2015-05-27
Hello and welcome to the forums

You may need to play some tricks with the quoting - for example

```

watch -d -n1 'ps -aux|grep chrome|awk [COLOR=#0000ff]**'\''**[/COLOR]BEGIN{x=0;y=0;}{x=x+$4;y=y+$6}END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}[COLOR=#0000ff]**'\''**[/COLOR]'

```

You may also want to consider turning the grep expression into a regex so it doesn't count itself

```

watch -d -n1 'ps -aux|grep [COLOR=#0000ff]**[**[/COLOR]c[COLOR=#0000ff]**]**[/COLOR]hrome|awk [COLOR=#0000ff]**'\''**[/COLOR]BEGIN{x=0;y=0;}{x=x+$4;y=y+$6}END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}[COLOR=#0000ff]**'\''**[/COLOR]'

```

---

### Post by matheusgeres on 2015-05-27
Very simple to resolve!
It works perfect! 

Thanks.

---

### Post by steeldriver on 2015-05-27
FWIW you probably don't need grep - you could do the pattern matching right in awk

```

watch -d -n1 'ps -aux|awk '\''BEGIN{x=0;y=0;} /[c]hrome/{x=x+$4;y=y+$6} END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}'\'''

```

---

### Post by matheusgeres on 2015-05-28
Very interesting, I think if I work only with awk the code is more clear.

Thanks again, steeldriver!!

---

### Post by Lars Noodén on 2015-05-28
Edit: Oops.  /way/ too slow  ;)  Not sure how that happened.  

With awk present, grep is not needed since conditional action based on the presence of a pattern is an inherent part of awk.

```

 watch -d -n1 'ps -aux|awk '\''BEGIN{x=0;y=0;} [color=#0000ff]**/[c]hrome/**[/color] {x=x+$4;y=y+$6} END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)"
);}'\'''

```

Or

```

 watch -d -n1 'ps -aux|awk '\''BEGIN{x=0;y=0;} [color=#0000ff]**$11 ~ /chrome/**[/color] {x=x+$4;y=y+$6}END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}'\'''

```

Performance-wise, for such a one-off task the extra grep might not matter much, but it is the core of awk.  So not to consider it is to be missing something important about awk.

---

