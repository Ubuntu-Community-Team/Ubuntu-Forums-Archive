---
title: "Did Firefox 3.0 get installed?"
date: 2008-06-18
forum: General Help
---

### Post by jimford on 2008-06-18
A recent update suggested that Firefox 3.0 was installed. /user/bin/firefox is also linked to /user/bin/firefox-3.0.

But 'Help->About Mozilla Firefox' says that 2.0.0.14 is installed!

So, is Firefox 3.0 _really_ installed?

Jim

---

### Post by Nepherte on 2008-06-18
You likely have a conflict issue with Firefox 2 and 3. They both use the same .mozilla folder for their profiles,... I suggest you backup your current .mozilla folder:
```
mv ~/.mozilla ~/.mozilla_backup
```
and run firefox again as you say this is linked to firefox-3. It will automatically create a new .mozilla folder and you start with a clean sheet.

---

### Post by geraldm on 2008-06-18
```
 firefox --version

```
This should show the version of the executable.  You may have a link pointing to a different version if you have more than one executable installed.

Gerald

---

