---
title: "Automatic run syncevolution"
date: 2008-02-22
forum: General Help
---

### Post by Hendry on 2008-02-22
Is it possible to automatic run syncevolution? I'm now running it manual, but it would be great if this was done automatic :)

---

### Post by jpastore on 2008-02-24
yes put the command in the crontab. just be careful that you don't shut down mid sync. It can cause some problems....I have mine setup to run every hour. Really I should trim that back to 8,12,4,8 no reason to sync much more than that....

look at man crontab for examples...

```

man 5 crontab

```

---

