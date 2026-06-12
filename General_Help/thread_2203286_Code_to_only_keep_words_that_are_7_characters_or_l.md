---
title: "Code to only keep words that are 7 characters or less and delete all others?"
date: 2014-02-02
forum: General Help
---

### Post by Rytron on 2014-02-02
Hi.

Can someone give me code that will take a text file with many words and only keep those that are 7 characters or less and delete all others?

Thanks.

---

### Post by erind on 2014-02-02
Try this perl code:

```
perl -pe 's/\b\w{8,}\b//g'  filename
```

---

### Post by Rytron on 2014-02-04
> **erind said:**
> Try this perl code:

```
perl -pe 's/\b\w{8,}\b//g'  filename
```

Cool, nice one erind.
I added "> file2.txt" to copy the selected text to a new file.

```
perl -pe 's/\b\w{9,}\b//g' file1.txt > file2.txt
```

Would it be possible to leave all words of 7 chars or less in the original file and delete all other words? No problem if not as the initial code is great.

---

### Post by erind on 2014-02-04
> **Rytron said:**
> [...]

Would it be possible to leave all words of 7 chars or less in the original file and delete all other words? No problem if not as the initial code is great.

Yes, use the -i (inplace) option, but take extra care when using it - it overwrites the original file:

 ```
perl -i -pe 's/\b\w{8,}\b//g'  file1.txt
```
Another option is keeping a backup of the original file (file1.txt.bak), while modifying the original (file1.txt): 

 ```
perl -i.bak -pe 's/\b\w{8,}\b//g'  file1.txt
```

Yet another common (shell) way is using a temporary file:

```
perl -pe '...'  file1.txt > temp && mv temp file1.txt
```

---

### Post by Rytron on 2014-02-05
Cheers erind. You are a code wizard. :-)

---

