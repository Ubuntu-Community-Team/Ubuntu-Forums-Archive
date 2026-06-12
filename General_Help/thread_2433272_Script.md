---
title: "Script"
date: 2019-12-16
forum: General Help
---

### Post by lernwillig on 2019-12-16
hi, i want to search a file welch.txt in many directories, make a copy to welch.txt-ORG and then an other file kotch.txt should override welch.txt.
welch.txt and kotch.txt is located in the same (last) directory
the path ist 
/a/b/c/1/2/3
a,b,c ist always the same named Path, 1,2,3 are diffent directories but the file i`m searching for is always in the last directory
manual my find works
cd /a/b/c/1/2/3
find . -type f -name "welch.txt" -exec cp {}"welch.txt-ORG
find . -type f -name "kotsch.txt" -exec cp {}"welch.txt
Please, can someone explane me how to script this in Bash? Thank you

---

### Post by yancek on 2019-12-16
If the commands at the end of your post are what you want and work as you want in a terminal, you could simply put them in a bash script and have a semi-colon at the end of each command (except the last of course)
Start the script with #!/bin/bash and make it executable.

---

