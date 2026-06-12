---
title: "How do I find latest version of file on a FAT partition from a terminal"
date: 2008-04-12
forum: General Help
---

### Post by john_spiral on 2008-04-12
Hi,

What's the simplest way to find the latest version of a file on a FAT partition from the terminal?

The drive I'm trying to search is a complete mess with lots of folders and sub folders.

---

### Post by bingoUV on 2008-04-12
There is no "version" of any file in FAT. All files have one and only version which is themselves. 

Maybe you mean something other than "version"?

---

### Post by john_spiral on 2008-04-12
by latest , I'm meaning date.

---

### Post by ghostdog74 on 2008-04-12
you can show the latest file in a directory using ls -ltr. the last entry is the latest file. If you want to find whether a file is updated since the last modified time, you can use find.
```

# touch .dummy
# echo "something" >> file
# find . -name file -newer ".dummy"
./file

```

---

### Post by john_spiral on 2008-04-13
Thanks for the help so far.

I didn't explain myself very well in the first post:

I've got a FAT32 drive with lots of folders & sub folders.

I'm looking for the latest (newest) version of a file called registrationForm.php that I created a while ago.

I reverted to using the Windows search facility and sorted the results by the date column to get the file I was looking for.

Is there a way I could have done this via the terminal?

---

### Post by ghostdog74 on 2008-04-13
you should already have mounted your fat32 partition. let's call it /mnt/windows
```

find /mnt/windows -type f -name "registrationForm.php" -printf "%A@:%p\n" | sort -k1 -t:

```

---

### Post by john_spiral on 2008-04-13
excellent thanks for your help!

---

