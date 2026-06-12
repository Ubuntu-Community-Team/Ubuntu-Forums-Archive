---
title: "So I typed &quot;set&quot; in Terminal..."
date: 2013-03-11
forum: General Help
---

### Post by Rebelli0us on 2013-03-11
I typed "set" looking for environment variables, force of habit I guess :popcorn:

I got a screen full of code gibberish. Did I do any damage?

Then out of curiosity:

```
$ set --help
bash: set: --: invalid option
set: usage: set [-abefhkmnptuvxBCHP] [-o option-name] [--] [arg ...]
```

Useful info?

---

### Post by The Cog on 2013-03-11
I don't think so. I've done that too. **env** works as expected.

---

### Post by Rebelli0us on 2013-03-11
Then I tried to learn how to negate or toggle a variable :

> # echo [ 1 = !1 ]
echo [ 1 = sudo visudo ]
[ 1 = sudo visudo ]

visudo ?!

---

### Post by The Cog on 2013-03-11
Try **man bash** - I think that !1 is some kind of history recall - perhaps the first command in your command history?

---

