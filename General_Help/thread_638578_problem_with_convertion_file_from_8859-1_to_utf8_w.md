---
title: "problem with convertion file from 8859-1 to utf8 with iconv"
date: 2007-12-12
forum: General Help
---

### Post by romaluca on 2007-12-12
I have a text file to convert from 8859-1 to utf8.

I use the iconv command

iconv -c --verbose -f ISO8859-1 -t UTF-8 source.sql -o dest.sql


if i open dest.sql there are errors with some letter like "è" "à" "ù"

The letter "è" is show: Ã¨


How can i do?
Thanks

---

