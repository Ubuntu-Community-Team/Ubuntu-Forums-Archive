---
title: "hellanzb and umask"
date: 2007-12-07
forum: General Help
---

### Post by romeyde on 2007-12-07
I'm running hellanzb as a daemon and it's working great.   Got just one issue that I can't quite figure out.   I modified the umask option in the config to "Hellanzb.UMASK = 0000" but downloaded files still show up in my "giganewsdone" folder owned by root with 755 permissions.   I suppose I could just add a cronjob that periodically chmod's the files in that dir, but would rather do it right.   Any ideas?

---

