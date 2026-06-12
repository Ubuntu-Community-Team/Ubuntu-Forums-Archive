---
title: "alias in .bash_aliases ... with single-quotes in the alias itself"
date: 2014-06-30
forum: General Help
---

### Post by sanderj on 2014-06-30
Hi,

I want to create an alias in .bash_aliases for

```
echo 328383838 9020932903 | awk '{ print $NF " found" }'
```

(just an example; it's about the single-quotes in the awk part)

I tried:

```
alias bla='echo 328383838 9020932903 | awk '{ print $NF " found" }' '
alias bla='echo 328383838 9020932903 | awk \'{ print $NF " found" }\' '

```

but both result in error on the bash login.

Tips how to solve this?

---

### Post by sudodus on 2014-06-30
This is an awkward work-around, but it works for me:

```
alias bla="echo $(echo 328383838 9020932903 | awk '{ print $NF }')"
bla
9020932903
```

---

### Post by sanderj on 2014-06-30
> **sudodus said:**
> This is an awkward work-around, but it works for me:

```
alias bla="echo $(echo 328383838 9020932903 | awk '{ print $NF }')"
bla
9020932903
```

Cool! Thank you.

Is it possible to put "found" after the $NF (like I edited in my post)?

---

### Post by steeldriver on 2014-06-30
This seems to work

```

alias bla='echo 328383838 9020932903 | awk [COLOR=#0000ff]**'\''**[/COLOR]{ print $NF " found" }**[COLOR=#0000ff]'\''[/COLOR] '**

```

```

$ bla
9020932903 found

```

---

### Post by sudodus on 2014-06-30
I have used work-arounds for problems with quotes before, but I don't know awk, so I have no idea about this second question. If we are lucky, someone who knows will find your thread and help you.

Edit: Someone did, even before I posted this reply :-)

---

### Post by sanderj on 2014-06-30
> **steeldriver said:**
> This seems to work

```

alias bla='echo 328383838 9020932903 | awk [COLOR=#0000ff]**'\''**[/COLOR]{ print $NF " found" }**[COLOR=#0000ff]'\''[/COLOR] '**

```

```

$ bla
9020932903 found

```

Cooooool. So the trick is: within the alias replace a 
```
'
```
with
```
'\''
```

The working bash code is:
```
echo "IPv4 (down resp up):"
cat /proc/net/netstat | grep -i ipext | tail -1 | awk '{ print $8 "\n" $9 }' | awk '{ print int($NF/1048576) " MB" }'

echo "\nIPv6 (down resp up):"
cat /proc/net/snmp6 | grep -i octet | head -2 | awk '{ print int($NF/1048576) " MB" }' 
```


Based on the above, I added to my .bash_aliases:

```
alias ipv4traffic='cat /proc/net/netstat | grep -i ipext | tail -1 | awk '\''{ print $8 "\n" $9 }'\'' | awk '\''{ print int($NF/1048576) " MB" }'\'' '
alias ipv6traffic='cat /proc/net/snmp6 | grep -i octet | head -2 | awk '\''{ print int($NF/1048576) " MB" }'\'' '

```
and it works:

```
sander@haring:~$ ipv4traffic 
33 MB
163 MB
sander@haring:~$ ipv6traffic 
69216 MB
616 MB
```

Thank you both very much!

---

