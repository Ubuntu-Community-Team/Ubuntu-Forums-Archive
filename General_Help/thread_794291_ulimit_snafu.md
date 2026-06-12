---
title: "ulimit snafu"
date: 2008-05-14
forum: General Help
---

### Post by vashfish on 2008-05-14
I'm working on a website where we have a sandboxed AJAX lua interpreter. When a user submits a command, it executes it via a ulimit command similar to:

```
ulimit -c 0 -t 2 -v 10000 && <rest of command>
```

It works fine on the live site and on our lead developer's working machine, but on my working machine (ubuntu 7.10 x86-64, fully updated) it errors out with:

```
ulimit: 1: too many arguments
```

Turns out Lua's execute command uses /bin/sh by default, so I changed the command to:

```
/usr/bin/env bash ulimit -c 0 -t 2 -v 10000 && <rest of command>
```

And now I get the error:

```
bash: ulimit: No such file or directory
```

Any ideas on what I need to do to get this working? :confused:

---

### Post by HermanAB on 2008-05-14
You probably have a different version of ulimit.

Upgrade!

Cheers,

H.

---

### Post by vashfish on 2008-05-14
> **HermanAB said:**
> You probably have a different version of ulimit.

Upgrade!

Cheers,

H.

How can i upgrade a bash builtin? :confused:

---

### Post by bingoUV on 2008-05-15
> **vashfish said:**
> How can i upgrade a bash builtin? :confused:

Upgrade bash of course. But I don't think that is the problem. Try
```

bash -c "ulimit -c 0 -t 2 -v 10000 && <rest of comand>"

```

---

### Post by vashfish on 2008-05-15
Thanks, that did the trick! :)

---

