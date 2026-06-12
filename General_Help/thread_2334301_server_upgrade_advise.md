---
title: "server upgrade advise"
date: 2016-08-18
forum: General Help
---

### Post by Joe67 on 2016-08-18
am running 12.04lts on my vps, do you guys think its about time it was upgraded to a newer version? i am still quite the newbie, so bare with me lol

---

### Post by howefield on 2016-08-18
You have until April 2017 before 12.04 is End of Life, so a fair bit of time, but it would be prudent to start thinking now about the process and testing.

---

### Post by Joe67 on 2016-08-18
what do you recommend upgrading to?

---

### Post by CatKiller on 2016-08-18
The only supported upgrade path from 12.04 LTS now is 14.04 LTS. So, that one ;)

If you were doing a fresh install you'd also have the option of 16.04 LTS, which is the current version.

Or you could go 12.04 -> 14.04 -> 16.04, although that will be a fairly lengthy process.

---

### Post by SeijiSensei on 2016-08-18
You might try spinning up a new virtual host from your provider with 14.04 or 16.04, then use rsync to transfer the files you need from the current host.  Most of these will be custom configurations in /etc, the contents of /home, and any other things you wrote yourself.  (I put all my custom scripts in /usr/local/sbin; /usr/local is not touched during an installation.)  When you get everything working correctly on the new host, you can switch over.  It shouldn't require much more than repointing the DNS records for your server.

---

### Post by Joe67 on 2016-08-18
good stuff, thanks for the replies/help

---

