---
title: "GPG BADSIG error prevents upgrade after fresh install"
date: 2005-10-17
forum: General Help
---

### Post by halstead on 2005-10-17
I have just installed a fresh copy of 5.10 and couldn't use the software updater due to a BADSIG issue with GPG. I tried using the restore default keys option but no help. Finally I changed every us.archive.ubuntu.com to a plain archive.ubuntu.com and all the us.security.ubuntu.com to plain security.ubuntu.com and now it upgrades flawlessly. 

Maybe there are some bad package files on the US mirrors? Or something else I couldn't identify. 

Could anyone know will changing this cause major problems for the ubuntu infrastructure?

Thanks,
--Halstead

---

### Post by eitan on 2005-10-17
thank you for this post!  i was banging my head on this problem for the last few hours.  changing the urls from us.archive.ubuntu.org to archive.ubuntu.org fixed it for me as well.

/ eitan

---

### Post by geofff on 2005-10-18
Happened to me too with gb. repositories. Removed gb and it works fine. Thanks

---

