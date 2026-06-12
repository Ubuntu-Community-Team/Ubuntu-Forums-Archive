---
title: "Shotwell permission denied error"
date: 2013-11-02
forum: General Help
---

### Post by rihikz on 2013-11-02
Hello. Im having this problem when i launch Shotwell. 

[IMG]http://i41.tinypic.com/b87n7q.png[/IMG]

---

### Post by ajgreeny on 2013-11-02
Can we see the output of ```
ls -l /home/rihikz/.local/share/shotwell/
``` to make sure we know what the current permissions are.

---

### Post by syam-nair on 2013-11-02
check your permissions as ajgreey has quoted and if no sufficient permissions use **sudo** **chmod 764 /home/rihikz/.local/share/shotwell -R**, or chmod 766...... if you require its access for everyone.

---

### Post by ajgreeny on 2013-11-02
It is also worth noting that if you have somehow got this problem in the .local/share/shotwell folder, you may also have similar problems in other /home folders.   Have you made any changes to ownership or permissions of folders in your home?

However, let's move one step at a time and see what the output of that command is.

---

