---
title: "wget get past bad filenames?"
date: 2013-04-18
forum: General Help
---

### Post by conradin on 2013-04-18
Hi all,
I want to download some source code a friend is working on, but his website has some files and folders with a period in the file-name. like ./v1/  , ./v2/
.068671
wget seems to fail there. what should i do to get files marked as hidden?

---

### Post by Doug S on 2013-04-18
I do not understand. It seems to work fine for  me. I created a file ".bla.txt" in my public directory, and it fetched fine with wget.
Directory names can always be referred to as ./v1/ from the current directory, and would need to be converted to a complete path name for wget to work.

---

