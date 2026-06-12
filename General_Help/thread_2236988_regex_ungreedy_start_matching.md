---
title: "regex ungreedy start matching"
date: 2014-07-30
forum: General Help
---

### Post by lvm on 2014-07-30
Regex allows ungreedy matching but it works only for the end of the match, is it possible to ungreedily match the start? E.g. 'a.*b' grabs everything between the first a and the last b (the result of applying s/a.*b/X/ to aabb is X), 'a.*?b' grabs everything between the first a and the first b (the result of applying s/a.*?b/X/ to aabb is Xb), but I want to match eveything between the last a and the first b - the expression which when applied to aabb returns aXb

---

### Post by steeldriver on 2014-07-30
maybe

```

echo 'aaaaabbbbb' | sed 's/a[^ab]*b/X/'
aaaaXbbbb

```

or if the regex language that you are using supports lookaheads, you could do something like

```

$ echo 'aaaaabbbbb' | perl -pe 's/a(?!a)b/X/'
aaaaXbbbb

```

---

