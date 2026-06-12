---
title: "[SOLVED] How to get &amp;quot;ls -l | less&amp;quot; in colors?"
date: 2008-07-05
forum: General Help
---

### Post by BlackBaron1024 on 2008-07-05
If use "ls -l | less" I nicely get my list in a browsable way, however, I loose the color information, is there any way around that?

Thanks

---

### Post by chrisccoulson on 2008-07-05
I'm not sure that the color information would get piped from the output of ls in to less. I might be wrong though!

---

### Post by Dr Small on 2008-07-05
Apparently, as I have just tried myself, the colors aren't being piped into less, or less just can't handle colors.

---

### Post by chrisccoulson on 2008-07-05
I think it's a bit of both actually

---

### Post by chrisccoulson on 2008-07-05
Actually, the colors are piped out. It's just that less doesn't understand them. Piping it in to more by doing 'ls -l --color | more' seems to work

---

### Post by John.Michael.Kane on 2008-07-05
> **chrisccoulson said:**
> Actually, the colors are piped out. It's just that less doesn't understand them. Piping it in to more by doing 'ls -l --color | more' seems to work

This also works, I am not sure if it what you are looking for. 

```
ls -l --color=always
```

---

### Post by bodhi.zazen on 2008-07-05
```
ls -l --color=always | less -r
```or

```
ls --color=always | less -r
```

you can alias less in .bashrc

alias less='less -r'

---

### Post by BlackBaron1024 on 2008-07-05
> **bodhi.zazen said:**
> ```
ls -l --color=always | less -r
```or

```
ls --color=always | less -r
```

you can alias less in .bashrc

alias less='less -r'

This is exactly what I wanted. Thank you very much!

---

