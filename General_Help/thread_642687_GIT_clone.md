---
title: "GIT clone"
date: 2007-12-16
forum: General Help
---

### Post by 00arthuryu on 2007-12-16
```

git clone git://git.freedesktop.org/git/xorg/app/compiz && cd compiz && git checkout compiz-0.6 && cd ~/compiz
remote: Generating pack...
remote: Done counting 15545 objects.
remote: Deltifying 15545 objects.
fatal: read error (Connection reset by peer)
fatal: early EOF
fatal: index-pack died with error code 128
fetch-pack from 'git://git.freedesktop.org/git/xorg/app/compiz' failed.

```
Everytime i do a git clone it will fail on 14%
Are there any quick fixes for this?
Or am i just being really stupid and forgetting something? :(

thanks for any help!

---

### Post by sciurus on 2007-12-18
"Connection reset by peer"

That's probably their problem, not yours.

---

