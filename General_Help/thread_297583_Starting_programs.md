---
title: "Starting programs"
date: 2006-11-11
forum: General Help
---

### Post by b0rys on 2006-11-11
Hi! I have a little problem with installing/starting some programs.
The file exist. It has +x chmod. Ubuntu 6.10 (amd64) Here some logs:

b0rys@b0rys-desktop:~/hlds_l$ ls -l
razem 9268
-rwxrwxrwx 1 b0rys b0rys 7506846 2004-09-22 13:54 steam
-rw-r--r-- 1 b0rys b0rys 1962970 2004-09-22 13:55 steam.tar.gz
b0rys@b0rys-desktop:~/hlds_l$ ./steam
bash: ./steam: No such file or directory
b0rys@b0rys-desktop:~/hlds_l$ 

And with "sh"


b0rys@b0rys-desktop:~/hlds_l$ sh steam
steam: 1: Syntax error: "(" unexpected

---

### Post by kidders on 2006-11-11
Hi there,

If it's a binary or a shell script, it sure is a big one! What does **file steam** tell you?

---

