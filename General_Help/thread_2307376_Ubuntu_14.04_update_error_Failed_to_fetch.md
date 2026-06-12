---
title: "Ubuntu 14.04 update error: Failed to fetch"
date: 2015-12-24
forum: General Help
---

### Post by Afnan on 2015-12-24
Suddenly today I see an pink icon on my top panel that says that "Update Information is outdated". After running ```
sudo apt-get update
``` I get the following error:

```
W: Failed to fetch http://repo-xen.rhcloud.com/deb/Packages  503  Service Temporarily Unavailable

E: Some index files failed to download. They have been ignored, or old ones used instead.



```

How do I fix this error? Please help

---

### Post by slickymaster on 2015-12-24
That server ([http://repo-xen.rhcloud.com/](http://repo-xen.rhcloud.com/)) is temporarily unable to service your request, probably due to maintenance downtime or capacity problems. You'll have to be patient and try again later. As soon as that server is up again, that error message will disappear.

---

### Post by grahammechanical on 2015-12-24
You try again later & hope that whatever is wrong at repo-xen.rh.cloud.com has been fixed. Actually, I think the problem is more likely connected to the rhcloud.com servers than to the repo-xen site.

After doing a web search on rhcloud I get a list of web sites hosted at rhcloud.com but they are taking a long time to load. So long that I gave up waiting.

Of course, if you remove repo-xen.rhcloud.com from your software sources list so that it is no longer a repository then you will not get that error when you run apt-get update. But it should not prevent you from updating/upgrading Ubuntu as normal.

Regards.

---

### Post by Afnan on 2015-12-27
Thanks a lot. I have temporarily disabled update from repo-xen.rh.cloud.com and its alright now. I'll re-enable it after a few days and check if the server up again.

---

