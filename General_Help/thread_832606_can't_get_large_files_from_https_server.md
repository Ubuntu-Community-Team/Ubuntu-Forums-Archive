---
title: "can't get large files from https server"
date: 2008-06-17
forum: General Help
---

### Post by tatere on 2008-06-17
i am using Subversion to update a local copy of code from my company's server. the repository server is a secure Apache server, so the URL to the repository is [https://blablabla/etc](https://blablabla/etc).

whenever svn update tries to get a file of a size greater than 500K, it just hangs. there is no error, no timeout, it just sits there.

out of curiosity, i tried to access the same file using wget, passing in the username and password required to access the site. that also hangs.

lynx and Firefox seem to hang as well.

the thing is, i can get this file with no trouble from my Mac. so it's not a networking issue or a problem on the repository server. it's only the Ubuntu box that has problems. i think that this has only been a problem since i upgraded to Hardy, but it's possible that the files just weren't that big back then, i have no proof one way or the other.

any ideas?

thanks

---

