---
title: "recover from chmod accident - different permission mode for files and directory"
date: 2007-02-25
forum: General Help
---

### Post by yccheok on 2007-02-25
hello all,

when i am in ~/. i accidently execute command

chmod -R 755 *

nows, all my files, including text file is executable. this is not what i want. because everytime i double click on the text file, a dialog box will pop up to ask me whether want to execute it. this is really anonying.

however, i cannot recover just by

chmod -R 655, this will turn off the executable flag for directory. i can no longer cd to the directory anymore.

can anyone tell me, how i can chmod, so that i can turn off the executable flag for file and turn on the executable flag for directories? there are too many files and directories involved.

thank you very much.

---

### Post by nereid on 2007-02-25
You could try this one

```

find ~ -type f -perm 755 -print0 | xargs -r0 chmod 644

```

This will find all files in your home directory (~) with the permission set to 755 and will change the permission of each of these files to 644.

**EDIT:**
Corrected the permission bitmask, as stated in my next post.

---

### Post by yccheok on 2007-02-25
hem... i try d. but it seems that those file execution bit still set...

---

### Post by nereid on 2007-02-26
You could make the command a little bit more general by leaving out the *-perm 755* option. But beware, then all files in your home directory will be set to 644.

**EDIT:**
My bad, I just realised an error in my snippet. The correct permission is **644** not 655.

---

