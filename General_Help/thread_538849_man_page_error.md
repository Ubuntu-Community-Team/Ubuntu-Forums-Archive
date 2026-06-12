---
title: "man page error"
date: 2007-08-30
forum: General Help
---

### Post by smmathew on 2007-08-30
When trying to use man I get the error message

man: can't create a temporary filename: No such file or directory


How can I remedy this?

I am using server edition 6.06.1

Thanks

smmathew

---

### Post by diffuze on 2007-08-30
First, see if you can do it as root.
If so, then it's probably a permission issue, make sure that /tmp has 777 permission.

---

### Post by smmathew on 2007-08-30
Well it seems as though my /tmp folder was deleted somehow... I re-created it and man is now working. I just wish I knew what deleted it.

---

