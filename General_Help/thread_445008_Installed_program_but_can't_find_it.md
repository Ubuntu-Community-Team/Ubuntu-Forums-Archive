---
title: "Installed program but can't find it"
date: 2007-05-15
forum: General Help
---

### Post by oxygenjunkie88 on 2007-05-15
I installed 7zip from the install manager and I can't seem to find it under 'Applications'. Anyone know where it could be?

---

### Post by drs305 on 2007-05-15
> **oxygenjunkie88 said:**
> I installed 7zip from the install manager and I can't seem to find it under 'Applications'. Anyone know where it could be?

Here's an inelegant way:

To update the file locations (including newly installed files)  This takes a little while, depending on your disk.
```

sudo updatedb

```

Then:

```

locate 7zip

```

That will give you a list and location of all files with '7zip' in the name.

---

