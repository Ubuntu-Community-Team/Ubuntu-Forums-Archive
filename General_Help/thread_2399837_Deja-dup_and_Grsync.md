---
title: "Deja-dup and Grsync"
date: 2018-08-30
forum: General Help
---

### Post by raleigh3 on 2018-08-30
I currently use Deja Dup.

But it does not have many configuration options.

Like backups can be kept for 6 months, year, or forever.

I would prefer a user selectable interval.

If I want to manually delete some of the backups, do I just delete all .manifest and .gz files with the same date?

I looked at grsync, but not sure how you would do a restore.

---

### Post by #&amp;thj^% on 2018-08-30
Deja-dup does not yet supply a way of removing old backups, _you should also not delete some of the files,_ that will leave your backups without a start file and renders them invalid. (Last Resort>>Remove them all and start over is an option).


You can use the Dconf to modify setting at path "org.gnome.DejaDup", key name delete-after. It's setup to the number of days to keep backup files on backup location.

Or from terminal. For example, to set it to 30 days from the command line, run:
```

gsettings set org.gnome.DejaDup delete-after 30

```
Second part of your question.
To restore using Grsync this might help: [https://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/](https://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/)

---

### Post by rbmorse on 2018-08-30
Backintime will do what you want.

---

