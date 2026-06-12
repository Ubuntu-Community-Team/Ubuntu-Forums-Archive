---
title: "grep - dealing with EOL"
date: 2014-05-07
forum: General Help
---

### Post by bandito40 on 2014-05-07
I am attempting to search through several lines of text with the following reg expression using grep:

```
grep -o '9[0-9] [8-9][0-9] 9[0-9].*\{40\}' sample.txt
```

Works but grep does not always return the following 40 characters. Instead it only returns up to 40 characters to the EOL which ever comes first.

What I am looking to do is get the following 40 characters whether there is an EOL within the following 40 characters or not.

Rather not show with what I have in sample.txt but here is the idea:

sample.txt
```
90 80 90 hello there
good bye
```

returns....

```
90 80 90 hello there good bye
```

---

### Post by steeldriver on 2014-05-07
I *think* that the only way to get grep to do multiline matches is via the (experimental) PCRE mode, with -z flag to stop it splitting on newlines e.g.

```

$ grep -zPo '9[0-9] [8-9][0-9] 9[0-9](.|\n){16}' sample.txt
90 80 90 hello there
goo

```

Note that you need to include \n explicitly because . matches everything *except* newline (also note you can't do that as [.\n] because . is treated as literal in a [ ] range). Also note that (.|\n){40} will not match in your sample because there simply aren't that many characters.

There's also pcregrep which I discovered recently from another forum - it's not installed by default but available from the repository:

```

$ pcregrep -Mo '9[0-9] [8-9][0-9] 9[0-9](.|\n){16}' sample.txt
90 80 90 hello there
goo

```

I don't actually know why -z can't work with BRE / ERE grep modes but it just doesn't seem to.

---

### Post by bandito40 on 2014-05-15
Use grep -a1.  Works like a charm.

---

