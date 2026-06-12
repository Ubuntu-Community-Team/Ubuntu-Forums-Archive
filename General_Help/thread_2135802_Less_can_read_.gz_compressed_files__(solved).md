---
title: "Less can read .gz compressed files ? (solved)"
date: 2013-04-15
forum: General Help
---

### Post by cogset on 2013-04-15
Just a dumb question,I've seen that less can read my older .gz logfiles just fine,no need to use zless - is this normal ?

---

### Post by schragge on 2013-04-15
[size=-1]*double-post, deleted*[/size]

---

### Post by schragge on 2013-04-15
See [lessfile(1)]("http://manpages.ubuntu.com/manpages/quantal/en/man1/lessfile.1.html"). BTW, this is my *~/.lessfilter*
```

#!/bin/sh
case "$1" in
*.ttf)
  ftdump -n "$1";;
*.cpio)
  cpio -itv < "$1";;
*.odt)
  odt2txt "$1";;
*.ps)
  pstotext "$1";;
*.md)
  markdown --html4tags "$1" | html2text;;
*)
  exit 1;;
esac
exit 0

```

---

### Post by cogset on 2013-04-19
Many thanks.

---

