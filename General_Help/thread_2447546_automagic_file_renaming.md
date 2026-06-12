---
title: "automagic file renaming?"
date: 2020-07-21
forum: General Help
---

### Post by maclenin on 2020-07-21
Just a quick and curious query.

I have two files, which were named (unconventionally) the following:
```
a'b_c.jpg
x_&_y.jpg
```
I had used them, successfully (along with encodeURIComponent), to display images on a website.

After making some recent updates to the website, I noticed the images were no longer displaying, as the filenames had changed - seemingly by themselves - to:
```
a_b_c.jpg
x___y.jpg
```
Both the ' and & had been replaced by _ without human intervention!

How might this be possible?

---

### Post by ajgreeny on 2020-07-21
Have you opened the files in Windows as I believe both apostrophe and ampersand are forbidden characters in Windows file names and maybe Windows which I don't  use any more does that automatically?

---

### Post by TheFu on 2020-07-21
Could be a change in the language or locale settings too.  The file system is UTF-8, but how that gets displayed is controlled by the locale setting, per userid.  Usually, I just try using a different terminal to see the correct name.

---

