---
title: "qcad and mutt"
date: 2007-05-23
forum: General Help
---

### Post by cssutto on 2007-05-23
I use mutt.

I need help entering the proper line in mailcap to get  attachments received in mutt to be opened by Qcad.

Any help would be appreciated.

CSSJR

---

### Post by fanatik on 2007-05-24
looks as simple as:

video/x-mpeg;/usr/bin/gxine %s

ie

MIME type;program %s

do you know the MIME type for your attachments? in mutt you can press v to view attachments, and it'll show you the MIME type.

also man mailcap will show you some useful info.

HTH.

---

### Post by cssutto on 2007-05-24
applica/octet-stre, base64, 11M

Thanks for the help.

CSSJR

---

