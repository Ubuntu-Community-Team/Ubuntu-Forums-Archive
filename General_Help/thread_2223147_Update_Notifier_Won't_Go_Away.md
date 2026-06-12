---
title: "Update Notifier Won't Go Away"
date: 2014-05-09
forum: General Help
---

### Post by wyth on 2014-05-09
Ever since I updated one of my machines to 14.04, the update notifier won't go away on one of them. The notifier pops up a few minutes after I log in, and won't go away even when there are no updates to install. This only happens on my desktop, not my laptop. It's a minor annoyance, but an annoyance nonetheless.

Has anyone else experienced this, and is there a fix?

---

### Post by ibjsb4 on 2014-05-10
Try

```
sudo apt-get update && sudo apt-get upgrade
```

This should reset your package manager.

---

