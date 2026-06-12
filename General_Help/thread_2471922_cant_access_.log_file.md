---
title: "cant access .log file"
date: 2022-02-13
forum: General Help
---

### Post by zenrebel432 on 2022-02-13
I am having issues trying to access a .log file in my system. I have tried entering superuser but not having any luck.

Can someone please help me?

---

### Post by ajgreeny on 2022-02-13
What log file? Give us the full name and where it is in the filesystem.

What commands have you used; which application are you using to try to open the log?

---

### Post by Impavidus on 2022-02-13
What are the permissions, owner and group of that log file? In terminal:```
ls -l /path/to/file.log
```(you can drag and drop the file from the file manager to get the path in the terminal, but I found that's the slow way) or use the file manager if you prefer.

Normally, log files are plain text. If you have permission to open the file for reading, reading it shouldn't be hard.

---

### Post by TheFu on 2022-02-13
Use **journalctl** to view system logs.  No sudo needed that I've noticed with that command. Some links for more details about the command:
[https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/](https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/)
[https://www.freedesktop.org/software/systemd/man/journalctl.html](https://www.freedesktop.org/software/systemd/man/journalctl.html)
[https://www.youtube.com/watch?v=9Fi7qG5y43Q](https://www.youtube.com/watch?v=9Fi7qG5y43Q)

---

