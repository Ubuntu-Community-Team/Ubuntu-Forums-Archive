---
title: "Progress of cp"
date: 2012-11-15
forum: General Help
---

### Post by pwabrahams on 2012-11-15
Is there a version of the **cp** utility around, perhaps, that indicates the progress of the copy as it goes?  It would be useful for very large copies.

---

### Post by wieman01 on 2012-11-15
"cp" cannot do that, but you might give "scp" a shot. Use Google to find more documentation on it.

---

### Post by oldos2er on 2012-11-15
> **pwabrahams said:**
> Is there a version of the **cp** utility around, perhaps, that indicates the progress of the copy as it goes?  It would be useful for very large copies.

You can use **pv** for that: [http://www.commandlinefu.com/commands/view/5107/copy-a-file-using-pv-and-watch-its-progress](http://www.commandlinefu.com/commands/view/5107/copy-a-file-using-pv-and-watch-its-progress)

rsync with the --progress option would also work.

---

