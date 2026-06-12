---
title: "Update problem"
date: 2013-01-06
forum: General Help
---

### Post by stefano91 on 2013-01-06
Hi everybody!

I have some troubles, when I try to update this error appear:
```

W:Failed to fetch http://deb.opera.com/opera/dists/lenny/non-free/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources  404  Not Found
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources  404  Not Found [IP: 193.206.140.37 80]
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources  404  Not Found [IP: 193.206.140.37 80]
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources  404  Not Found [IP: 193.206.140.37 80]
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources  404  Not Found [IP: 193.206.140.37 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

And this prevent me to update ubuntu from the launcher, while i can still do it from the terminal. 

But how can I fix this?

Thank you very much!

---

### Post by JiuJitsu500 on 2013-01-06
What ubuntu version are you running?

maverick-backports is odd for any new release, or I haven't noticed that you could use a backport for a future release... And it's trying to download Opera. Looks just like you can't connect to their servers though.

First try going into your software-sources and check everything on the first tab, and use the main server. Then uncheck anything that says "ubuntu CD" or whatever it says, and use all other PPA's and cononical partner jazz.

If you do all that, then "sudo apt-get clean" and "sudo apt-get autoremove" it should clean itself unless there's a more difficult problem. Either way, after cleaning and autoremove, run "sudo apt-get update" again and see if it clears up.

---

### Post by stefano91 on 2013-01-06
It was already exactly how you said, I have 12.04.

Should I set to use the newest update or the ones for my version? (prefences of synaptic)

And I have tried to clean a bit the system some time ago, but I think I canceled too much from the repository...

---

