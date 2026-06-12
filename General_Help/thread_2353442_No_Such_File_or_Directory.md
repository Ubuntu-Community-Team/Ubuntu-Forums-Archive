---
title: "No Such File or Directory"
date: 2017-02-21
forum: General Help
---

### Post by webmanoffesto on 2017-02-21
I'm trying to get Helium running so I can back up an Android tablet before I Root it (Samsung Galaxy Tab A SM-T350). Helium says they can do that. I installed Helium on the tablet, now I need to get it running on my Ubuntu Gnome 16 laptop. The folder has the files it should have, but I can't run the program.

[email]tom@tom-HP-ProBook-450-G3:~/Downloads/Helium.linux[/email]$ ls
adb  README  run.sh


[email]tom@tom-HP-ProBook-450-G3:~/Downloads/Helium.linux[/email]$ sudo ./run.sh
./run.sh: 2: ./run.sh: ./adb: not found
./run.sh: 7: ./run.sh: ./adb: not found

[email]tom@tom-HP-ProBook-450-G3:~/Downloads/Helium.linux[/email]$ source run.sh
bash: ./adb: No such file or directory



What's the problem here?

---

### Post by oldos2er on 2017-02-21
Do adb and run.sh need to be executable? ```
chmod +x adb run.sh
```

---

### Post by webmanoffesto on 2017-02-21
Thanks  but that didn't change anything

$ chmod +x adb run.sh
- seemed to run fine

But
$ ./run.sh
gave me
./run.sh: line 2: ./adb: No such file or directory
./run.sh: line 7: ./adb: No such file or directory

---

### Post by gordintoronto on 2017-02-22
Run this command:
locate adb

Perhaps you need to start from a different directory.

---

