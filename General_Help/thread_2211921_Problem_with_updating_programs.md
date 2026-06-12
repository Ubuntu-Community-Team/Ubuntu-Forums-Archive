---
title: "Problem with updating programs"
date: 2014-03-18
forum: General Help
---

### Post by Audiosurfer on 2014-03-18
I'm using Ubuntu 13.10 and it alerts me that I have things with available updates. I click Install Now, then it will tell me to authenticate, which I do. From there, it informs me that "This requires installing packages from unauthenticated sources". If I click OK, the download doesn't start. Instead, the download window closes and nothing gets updated, then it will notify me of the available updates in a later session and the problem will repeat. How do I solve this?

---

### Post by deadflowr on 2014-03-18
When it asks does it first run a scanner bar, or is it simply opening a window listing the update-able packages?

If it is simply opening a window listing the update-able packages, then I would say to open the dash and launch the software updater to try to get it to reload the package list.
Also, you could do a simple
```
sudo apt-get update
```
Which will also reload the package list.
```
sudo apt-get upgrade
```
will then upgrade the update-able packages.

It's probably simply a matter of the packages it says it can update are older than the packages available.
reloading usually fixes this issue.

---

### Post by Audiosurfer on 2014-03-18
Ok, did this and it worked, thanks :)

---

