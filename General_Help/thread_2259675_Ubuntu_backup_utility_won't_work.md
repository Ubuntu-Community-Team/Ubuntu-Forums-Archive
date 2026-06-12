---
title: "Ubuntu backup utility won't work"
date: 2015-01-06
forum: General Help
---

### Post by angelo8 on 2015-01-06
I'm new to Ubuntu and just recently put Ubuntu 14.04 on my Toshiba Satellite. I'm trying to back up my files in case anything gets messed up and the back up utility won't work. Every time I get the error message

Could not back up the following files. Please make sure you are able to open them.

/home/username/.cache/dconf
/home/username/.gvfs

How do I fix this?

---

### Post by deadflowr on 2015-01-06
Add those folder to the ignore list.
Open backup, go to the subsection folders to ignore.
Click on the plus symbol at the bottom.
You may need to enable show hidden folders and files, so right click inside the window where the folders and files are listed and then click on the line for show hidden folders and files; or something like that.
Then highlight the .cache folder and hit add, then repeat and highlight the .gvfs.
Then backup should run without error, at least those errors.

---

### Post by angelo8 on 2015-01-06
ok thanks!

---

