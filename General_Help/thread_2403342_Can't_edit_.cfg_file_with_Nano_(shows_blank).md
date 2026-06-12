---
title: "Can't edit .cfg file with Nano (shows blank)"
date: 2018-10-10
forum: General Help
---

### Post by rlaviolette on 2018-10-10
Hello, 

I am using the newest version of ubuntu server and I am unable to edit a .cfg file with nano but if I use cat it shows the contents of the file. I am root. Any ideas?

Rlaviolette

---

### Post by TheFu on 2018-10-10
which file?

---

### Post by Impavidus on 2018-10-10
If it shows blank, that suggests that nano thinks it's an empty file or a new file, which in turn suggests that nano and cat don't try and open the same file. Have you double checked the current directory and file name?

Another suggestion: If the file is long, cat will only show the final lines in the terminal (the first lines will scroll out of view), but nano will only show the first lines (but should allow you to scroll down). Maybe there are many empty lines at the start of the file?

cat even has an option to suppress consecutive empty lines (-s). If cat is aliased to use that option and the file has many empty lines, they would disappear in cat's output, but show up in nano.

---

### Post by SeijiSensei on 2018-10-10
Are you using "sudo nano /path/to/file"?  Most configuration files can only be edited by the root user.

---

