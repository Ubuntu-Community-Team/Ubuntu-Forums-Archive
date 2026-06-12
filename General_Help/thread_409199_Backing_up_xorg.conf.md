---
title: "Backing up xorg.conf"
date: 2007-04-14
forum: General Help
---

### Post by Deviltongue on 2007-04-14
how do you back up the xorg.conf?

---

### Post by bulldog on 2007-04-14
Open a terminal and```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

---

### Post by Deviltongue on 2007-04-14
okay then how do you use the back-up?

---

### Post by bulldog on 2007-04-14
Pardon??
What do you mean exactly,you can make a backup from the xorg.conf with the previous command.
When you want  to replace the xorg.conf with the backup you made,
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

That wasn't so hard,was it?

---

### Post by Deviltongue on 2007-04-14
thanx man

---

### Post by dreadlord_chris on 2007-04-17
> **bulldog said:**
> Pardon??
What do you mean exactly,you can make a backup from the xorg.conf with the previous command.
When you want  to replace the xorg.conf with the backup you made,
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

That wasn't so hard,was it?

actually, shouldn't that be:
```

sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

```

---

