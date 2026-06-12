---
title: "error processing plone-site"
date: 2005-03-18
forum: General Help
---

### Post by Myles3 on 2005-03-18
I installed plone-site by mistake and now when I try to remove it, it gives me this:
```
(Reading database ... 74024 files and directories currently installed.)
Removing plone-site ...
/var/lib/dpkg/info/plone-site.postrm: line 20: dzhandle: command not found
dpkg: error processing plone-site (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 plone-site
sh: line 1: dzhandle: command not found
E: Problem executing scripts DPkg::Post-Invoke 'dzhandle restart-pending-instances'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can anyone help me?

---

