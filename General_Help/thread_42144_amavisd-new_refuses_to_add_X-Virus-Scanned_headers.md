---
title: "amavisd-new refuses to add X-Virus-Scanned headers"
date: 2005-06-16
forum: General Help
---

### Post by guid00 on 2005-06-16
Hello,

Virusscanning works. Spamtagging by using spamassassin works too. However i would like amavis-new to include some X-Virus-Scanned headers.

In the /etc/amavisd/amavisd.conf file i have set:

> # Add X-Virus-Scanned header field to mail?
$X_HEADER_TAG = 'X-Virus-Scanned by Machine 47';   # (default: undef)
# Leave empty to add no header          # (default: undef)
$X_HEADER_LINE = "by $myversion (Debian) at Machine 47 $mydomain";

But these lines seem to be ignored.. am i overlooking something here?

guid00

---

