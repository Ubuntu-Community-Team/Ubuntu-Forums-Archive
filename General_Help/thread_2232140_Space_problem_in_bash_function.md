---
title: "Space problem in bash function"
date: 2014-06-30
forum: General Help
---

### Post by CkDGTAT on 2014-06-30
[h=3]Dear all,

I cannot find a way to manage space. Can anybody help?

wo () {
	c "wolfram-alpha.com/input/?i="$(echo "$@" | sed 's/ /\ /g')""
}


[/h]

---

### Post by HermanAB on 2014-06-30
You got to escape a space with a back slash.

---

