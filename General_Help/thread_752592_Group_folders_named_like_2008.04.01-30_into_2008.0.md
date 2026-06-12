---
title: "Group folders named like 2008.04.01-30 into 2008.04"
date: 2008-04-11
forum: General Help
---

### Post by Meson on 2008-04-11
My backup-dir folder for my rsync backups puts all backups into a folder named YYYY.MM.DD-HH.MM.SS

I want to be able to merge folders once the day, month, and year is up.

For example if I have these folders:
```

2008.04.11-13:20:20
2008.04.11-11:20:20
2008.04.11-10:20:20
2008.04.02-11:20:20
2008.04.02-12:20:20
2008.04.02-13:20:20
2008.03.11-10:20:20
2008.02.02-11:20:20
2008.02.02-12:20:20
2008.01.02-13:20:20
2008.01.11-10:20:20
2008.01.02-11:20:20
2007.06.12-12:20:20
2007.04.02-13:20:20

```

I want to merge them to look like:

```

2008.04.11-13:20:20
2008.04.11-11:20:20
2008.04.11-10:20:20
2008.04.02
2008.03
2008.02
2008.01
2007

```

So the backup folders have a time precision for the current day, a day precision for the current month, and month precision for the current year, but anything earlier is only stored by year.

Anyone have any experience doing something like this?

---

