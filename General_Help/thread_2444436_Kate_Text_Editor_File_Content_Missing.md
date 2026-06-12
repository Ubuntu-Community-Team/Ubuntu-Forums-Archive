---
title: "Kate Text Editor File Content Missing"
date: 2020-05-30
forum: General Help
---

### Post by Dynamata on 2020-05-30
My SSD ran out of space, I deleted 10GB of files, closed all applications & rebooted. A Kate text file is blank & the file size is 0bytes, is it possible to recover a backup of the file?

From another forum:

"if you are working on a text file (that exists as file on disk), a swap  file is created next to the file, called .filename.kate-swp. Now, if  Kate starts again, Kate searches for these swap files. If found it  replicates all edit actions that were recorded in this swap file, and  your data is fully restored"

what is the swap file location? :-?

---

### Post by Impavidus on 2020-05-30
I don'y use kate, but my guess is it's in the same directory as the text file you were editing. It's a hidden file.

---

