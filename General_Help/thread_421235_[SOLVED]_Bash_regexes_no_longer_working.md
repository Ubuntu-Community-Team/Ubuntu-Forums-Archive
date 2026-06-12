---
title: "[SOLVED] Bash regexes no longer working"
date: 2007-04-24
forum: General Help
---

### Post by rrwo on 2007-04-24
I have various bash scripts with code like
```

if [[ "$texfile" =~ '^(.*)\.tex$' ]]
then
  file=${BASH_REMATCH[1]}
fi

```
It seems since upgrading to Feisty, that these scripts no longer work.

The regex engine in bash doesn't work when I include metacharacters in regexps like ., *, +, $, or ^. Indeed, "." now maches a period rather than any character.  

What the [expletive] was changed in Feisty?

Was the file globbing behaviour changed in such a way as to affect this? It makes no sense.  I've checked: I am running bash, or at least something that claims to be bash.

The upgrade was so broken for many reasons, I had to do a fresh reinstall from scratch. But wow, regexes don't work out of the box.

---

### Post by rrwo on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bash/+bug/109931](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/109931) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Feisty includes an upgrade to Bash 3.2,which apparently changed the regex syntax.

---

