---
title: "[SOLVED] GPG questions"
date: 2007-12-17
forum: General Help
---

### Post by oneadvent on 2007-12-17
```
find * -exec gpg -e -r jwelch {} \ -exec rm {};
```
would that encrypt all files in whatever directory it is in and remove the original?

---

### Post by geirha on 2007-12-17
No, the syntax is wrong so it will just return with an error message.
```
find . -maxdepth 1 -type f -exec bash -c 'gpg -r jwelch -e {} && rm {}' \;
```
This should encrypt all files in the current directory ("-maxdepth 1" makes it non-recursively) and delete the original file if the encryption succeeded.

---

### Post by oneadvent on 2007-12-17
fantastic, worked like a charm.

i understand, I was missing bash -c 'command && command' part.

Thanks for the explain, I went to probably 20 sites trying to find this answer.

---

