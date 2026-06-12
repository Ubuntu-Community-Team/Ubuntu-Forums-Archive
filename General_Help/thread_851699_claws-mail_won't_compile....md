---
title: "claws-mail won't compile..."
date: 2008-07-06
forum: General Help
---

### Post by moore.bryan on 2008-07-06
okay, so i never had this problem before, but now i can't build the latest claws-mail from cvs. the following are the relevant error lines:
```
/home/moore/downloads/sylpheedclaws/sylpheed-claws/src/etpan/nntp-thread.c:453: undefined reference to `mailstream_ssl_set_client_private_key_data'
collect2: ld returned 1 exit status
make[4]: *** [claws-mail] Error 1
make[4]: Leaving directory `/home/moore/downloads/sylpheedclaws/sylpheed-claws/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/moore/downloads/sylpheedclaws/sylpheed-claws/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/moore/downloads/sylpheedclaws/sylpheed-claws/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/moore/downloads/sylpheedclaws/sylpheed-claws'
make: *** [all] Error 2

```

---

### Post by colinleroy on 2008-07-10
You need the latest CVS of libetpan since a few days, too, due to the new implementation of SSL client certificates:

[http://www.claws-mail.org/snapshots/libetpan/](http://www.claws-mail.org/snapshots/libetpan/)

---

### Post by moore.bryan on 2008-07-10
> **colinleroy said:**
> You need the latest CVS of libetpan since a few days, too, due to the new implementation of SSL client certificates:

[http://www.claws-mail.org/snapshots/libetpan/](http://www.claws-mail.org/snapshots/libetpan/)
thanks for the info... i actually, somewhat, gave up on the compiling issue when i found that the claws-mail repos had practically the same version (3.5.0) as cvs (3.5.1).

once again, thanks for the info, though...

---

