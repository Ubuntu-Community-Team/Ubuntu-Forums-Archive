---
title: "How do I restart compiz from command?"
date: 2012-11-08
forum: General Help
---

### Post by colobix on 2012-11-08
Hello.
A steam bug makes the mouse really small if you have compiz enabled.
So how do you restart compiz in one command?
I want to have this as a shortcut, so it can't be two commands such as killall compiz followed by compiz.

---

### Post by garginis on 2012-11-08
I don't understand you very well.
Anyway, try 

```
compiz --replace
```

---

### Post by HiImTye on 2012-11-08
you can separate commands with semicolon like:
```
echo hello; echo world
```
but ```
compiz --replace
```should work fine.

---

### Post by colobix on 2012-11-08
> **garginis said:**
> I don't understand you very well.
Anyway, try 

```
compiz --replace
```

Thanks. But what do you mean you don't understand me?
I'm running xubuntu, and yesterday I installed Steam (new linux version).
It has an annoying bug.
When I close steam, the mouse becomes microscopic.
This does not happen if I start steam without having compiz enabled.
Or more specifically, it happens when you zoom. The mouse is normal when the zoom is on 0 or off.

But your command solved it. Thanks.

---

