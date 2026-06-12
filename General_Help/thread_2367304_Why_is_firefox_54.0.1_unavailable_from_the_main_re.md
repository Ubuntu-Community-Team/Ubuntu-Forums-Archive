---
title: "Why is firefox 54.0.1 unavailable from the main repository?"
date: 2017-07-28
forum: General Help
---

### Post by katzelad on 2017-07-28
Hi
Firefox 54 has bugs which should be fixed in version 54.0.1 which, despite being released a month ago, is not available from the main repositories.
Any specific reason for it?
Thanks

---

### Post by vasa1 on 2017-07-28
See [https://ubuntuforums.org/showthread.php?t=2367044](https://ubuntuforums.org/showthread.php?t=2367044)

---

### Post by vocx on 2017-07-28
> **katzelad said:**
> Hi
Firefox 54 has bugs which should be fixed in version 54.0.1 which, despite being released a month ago, is not available from the main repositories.
Any specific reason for it?
Thanks
Many updates are not propagated immediately to the Ubuntu repositories, for one or another reason.

Exactly what is the problem with 54.0, that is solved with 54.0.1? Is this bug very, very critical?

I trust the package maintainers of Firefox in Ubuntu. If they did not package the new version immediately, I feel the bug is probably not that serious, or is already taken care of in another way. Firefox does not work by itself, it depends on many other packages, such as libssl and openssl. Maybe the bug that you are referring to is already solved in one these other packages, so there is not need to update the Firefox component itself.

If it's user interface problems, that don't present a clear, exploitative vulnerability to Firefox, I don't see a big problem with not providing an update.

---

### Post by oldos2er on 2017-07-28
You can always download and run 54.0.1 yourself. The Ubuntu Mozilla team would welcome any help, I'm sure.

---

