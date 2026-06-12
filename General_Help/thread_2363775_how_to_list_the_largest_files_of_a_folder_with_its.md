---
title: "how to list the largest files of a folder with its subfolders?"
date: 2017-06-14
forum: General Help
---

### Post by ronjjjg8885 on 2017-06-14
because i don't find a file that i need.
it's a file meant to be a container of encrypted data made with veracrypt

thank you

---

### Post by steeldriver on 2017-06-14
You can list files larger than a given size using the `find` command e.g.

```

find . -type f -size +1G

```

If you want to get more fancy you can sort them from small to large or vice versa

```

find . -type f -size +1G -printf '%s\t%p\n' | sort -nk1,1

find . -type f -size +1G -printf '%s\t%p\n' | sort -rnk1,1

```

(assumes filenames don't contain newlines)

---

