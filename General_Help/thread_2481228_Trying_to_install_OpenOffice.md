---
title: "Trying to install OpenOffice"
date: 2022-11-22
forum: General Help
---

### Post by preitman on 2022-11-22
Good evening,

Trying to install OpenOffice following this guide: [https://www.geeksforgeeks.org/how-to-install-openoffice-on-ubuntu/](https://www.geeksforgeeks.org/how-to-install-openoffice-on-ubuntu/)
-I have gotten all the way to step 8, and when trying to do step 9 - I put in "sudo dpkg -i *.deb" (without the quotes) into the terminal and I get the following prompt back:
~Downloads/en-US$ sudo dpkg -i *.deb dpkg: error: cannot access archive '*.deb': No such file or directory

I am running Ubuntu 22.04.1

---

### Post by ian-weisser on 2022-11-22
The tutorial clearly shows that the deb are in the "en-US/DEBS" directory, not the "en-US" directory.

This is a mistake in the tutorial. You should let them know about it.

Step 8 should be "cd en-US/DEBS"

---

### Post by preitman on 2022-11-23
Thanks! That worked splendidly!  Still a lot to learn about Ubuntu/Linux after migrating from Windows

---

### Post by mrdc76 on 2022-11-24
> **preitman said:**
>  Still a lot to learn about Ubuntu/Linux after migrating from Windows

In that case it is quite possible that you should not have installed OpenOffice at all. LibreOffice is what everyone uses nowadays, and it is installed by default on Ubuntu.

---

### Post by ne29914 on 2022-11-24
"OpenOffice is not dead. It just smells funny." Paraphrased from Frank Zappa. :)
But really: use the preinstalled LibreOffice instead. AFAIK, it's the same base code.

---

