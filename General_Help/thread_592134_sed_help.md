---
title: "sed help"
date: 2007-10-26
forum: General Help
---

### Post by I.You on 2007-10-26
Hi there,

Since I'm using BusyBox, no -s option in sed.
Only -efinr options in sed of BusyBox.
Any way instead of -s option?
I think sed command inside a loop is a way.
But I have no idea how to do.

The problem is 

...
out=`echo $$file | sed -s 's/po/mo/'` ; \
msgfmt -o $${out} $${file} ; \
if ...
fi ; \
...

Any idea?

---

