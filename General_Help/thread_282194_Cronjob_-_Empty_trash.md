---
title: "Cronjob - Empty trash"
date: 2006-10-22
forum: General Help
---

### Post by LeNath on 2006-10-22
Hi,

I would like to setup a cronjob which would automatically empty the trash every day at 6:30PM. The following is the command I will insert in crontab, will this do the job?

```
30 18 * * * rmdir -r ~/.Trash/*
```

This may not delete invisible files/folders... If I do the following, will this delete both normal and invisible files/folders?

```
30 18 * * * rmdir -r ~/.Trash/.*
```

Thanks for your help and suggestions!

---

