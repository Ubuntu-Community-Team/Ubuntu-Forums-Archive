---
title: "Rest in piece terminal (escape characters breaks terminal?)"
date: 2016-09-03
forum: General Help
---

### Post by Delupara on 2016-09-03
I was messing around with aliases and something weird happened.

I made a function to make other aliases (don't ask why I'm that kind of guy)
this is what the 'ba' function does

```
function ba() { echo alias $1 >> $HOME/.bashrc; }
```

of course the entire argument must be in quotations so that it conserves the entire appended text. If I did something like this:

```
ba foo=echo bar
```

it would only echo

```
alias foo=echo 
```

so I need to put the entirety of #1 in quotations like so

```
ba 'foo=echo bar'
```

 now it appends it entirely. But there's another problem. I need the alias to be in quotation as well like so

```
alias foo='echo bar'
```

I said "no biggie" and did some escape characters. Well this is what happened

```
delupara@Crypt44:~$ ba 'test=\'echo test\''
>
```

And my terminal is stuck with this ">" character. I tried using double quotation instead of single quotations but it appended "alias $1" instead of the actual thing...

Wth is going on here?

---

### Post by steeldriver on 2016-09-03
The 
```

>

```

prompt means that the shell is waiting for a closing quote - you can return to the regular shell prompt using Ctrl-C

To quote quotes, you can do either

```

echo "alias foo='echo bar'"

```
or
```

echo 'alias foo='\''echo bar'\'''

```

Don't forget to quote your $1 argument inside the function as well

```

"$1"

```

---

