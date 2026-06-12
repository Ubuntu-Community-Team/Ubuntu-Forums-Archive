---
title: "mutt not sending accents"
date: 2005-10-25
forum: General Help
---

### Post by loucomballa on 2005-10-25
Hi all,
After upgrading to breezy, mutt is failing to send messages with the correct encoding: any à é is sent as ?. Also, some messages are not displayed correctly: è as \350, for instance.
My locales is correct:

LANG=ca_ES.UTF-8
LC_CTYPE="ca_ES.UTF-8"

At the terminal or vim there is no problem with the characters.
And my sent messages are encoded as 'utf8' (looking at the headers).

Any ideas?

Cheers,

Xavi.

---

