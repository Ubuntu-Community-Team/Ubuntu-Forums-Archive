---
title: "Can I alias this code?"
date: 2015-11-15
forum: General Help
---

### Post by vasa1 on 2015-11-15
```
awk -F"\t" '{ printf "%5s %12s %10s\n",$1,$2,$3 }' ~/Dropbox/CurrSoc/bills-for-blog.txt > ~/Dropbox/CurrSoc/15-$(date +%b)-bills-for-blog.txt
```works when I run it from the terminal but if I try to alias it I run into trouble:```
alias bills='awk -F"\t" '{ printf "%5s %12s %10s\n",$1,$2,$3 }' ~/Dropbox/CurrSoc/bills-for-blog.txt > ~/Dropbox/CurrSoc/15-$(date +%b)-bills-for-blog.txt'
```fails when I run the alias *bills*.```
06:59 PM ~ $ bills
awk: line 2: missing } near end of file
06:59 PM ~ $ 

```Is this because of the internal single quotes?

Edit: meanwhile I'm reading [http://unix.stackexchange.com/a/159572](http://unix.stackexchange.com/a/159572) which suggests adding a function to .bashrc instead and this works:```
bills () {
    awk -F"\t" '{ printf "%5s %12s %10s\n",$1,$2,$3 }'\
    ~/Dropbox/CurrSoc/bills-for-blog.txt >\
    ~/Dropbox/CurrSoc/15-$(date +%b)-bills-for-blog.txt
}

```

And I found this > For almost every purpose, aliases are superseded by shell functions.from [http://unix.stackexchange.com/a/73416](http://unix.stackexchange.com/a/73416)

---

### Post by steeldriver on 2015-11-15
Yes it's probably because of the single quotes - you could probably have made it work using

```

alias bills='awk -F"\t" [COLOR=#0000ff]**'\''**[/COLOR]{ printf "%5s %12s %10s\n",$1,$2,$3 }[COLOR=#0000ff]**'\''**[/COLOR] ~/Dropbox/CurrSoc/bills-for-blog.txt > ~/Dropbox/CurrSoc/15-$(date +%b)-bills-for-blog.txt'

```

but the function solution is maybe cleaner

---

