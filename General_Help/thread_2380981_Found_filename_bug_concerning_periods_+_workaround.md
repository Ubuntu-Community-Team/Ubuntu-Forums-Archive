---
title: "Found filename bug concerning periods + workaround."
date: 2017-12-24
forum: General Help
---

### Post by splatman2 on 2017-12-24
Bug: Filenames that start with a period do not show. Or am I misunderstanding a feature of Ubuntu?
Workaround: When saving a file, make sure the file name does not start with periods.

Case in point: When I downloaded *...Spring powered boots?*, I could not find it in my downloads folder, so I thought I did not download it (I did a download marathon, so I thought I forgot it; it has happened before), so I went back to DL it again, same result, then I remembered: Files and folders and start with a . are invisible. So I DL'd the file a 3rd time, this time, I scratched off the *...* before clicking Save.

---

### Post by jeremy31 on 2017-12-24
That is how Linux distros hide files and folders.  A file named .config is hidden and a folder named ./config is also hidden.  If you are using the file manager, try CTRL + h and see if the hidden files appear

---

### Post by coffeecat on 2017-12-24
> **splatman2 said:**
> Or am I misunderstanding a feature of Ubuntu?

Yes. Not just Ubuntu, but all Unix-like operating systems.

It's a feature, not a bug. Filenames of hidden files and directories start with a period.

---

