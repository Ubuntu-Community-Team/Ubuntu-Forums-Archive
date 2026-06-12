---
title: "where does vi store .swp files?"
date: 2007-12-14
forum: General Help
---

### Post by shilpa1 on 2007-12-14
> If you make a mistake when saving a file, such as pressing Ctrl-ZZ or closing Vi before saving the file, you'll end up with a swap file (akin to a DOS/Windows temp file) in addition to the original file. Usually the swap file will have the .swp extension. The original file will not contain the recent changes you made; attempting to reopen it will result in an error message.

The swap file is not readable but can be recovered by typing a command like this at the $ prompt and pressing Enter:

vi -r {your file name}

In some extreme cases, recovery is not possible. But in most cases, such as closing Vi before saving, a system crash, or a power failure, recovery works very well. After you recover, you must manually delete the swap file using a command like this at the $ prompt:

rm .{your file name}.swp


where is this file stored?in swap partition or somewhere else?

---

### Post by pointone on 2007-12-14
Usually in the same directory as the file you were working on.

---

### Post by shilpa1 on 2007-12-14
which means? i dont have yet saved a file if so where will the file be saved? can i make files with vi?if then where will be swp files saved?

---

