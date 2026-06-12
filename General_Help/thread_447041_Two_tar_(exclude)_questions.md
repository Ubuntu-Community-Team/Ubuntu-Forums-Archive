---
title: "Two tar (exclude) questions"
date: 2007-05-17
forum: General Help
---

### Post by W. Irving on 2007-05-17
I'm trying to set up a backup routine for my laptop. Basically I want to backup / with a few exceptions, these are:

/proc
/dev
/lost+found
/mnt
(simple to exclude, even for me)

- Any file or folder in /home that does _not_ begin with a . (period/dot, as in "this file/folder is hidden")
- Any lost+found found in any folder (I found one of them in /boot - hardly any point in saving!)

I understand the pattern you put in the --exclude switch (or indeed the file referenced by -X) is similar to a regex, but not quite fully compatible. Regex negations have always been my weak side, and I have no idea how to match files that do not begin with a .

To skip any lost+found occurence other than in the root I tried
> .*lost+found.*
Also tried escaping the + with a backslash, but no luck.

How do I do this?

---

### Post by Pollywoggy on 2007-05-17
Instead of .*lost+found.*  try

'*lost+found*'

---

### Post by W. Irving on 2007-05-17
That did the trick! Thank you very much!

How about my other question?
Excluding all files and folders that do not begin with a . ? :)

---

### Post by Pollywoggy on 2007-05-18
> **W. Irving said:**
> That did the trick! Thank you very much!

How about my other question?
Excluding all files and folders that do not begin with a . ? :)

tar is including files that begin with "." ? I think that is because you had included the dot in the command.
Try without the dots.

Or you can try something like

tar cf backup.tar --exclude .. --exclude . * .*

I thought you wanted to exclude hidden files, so I might be a little confused.

---

