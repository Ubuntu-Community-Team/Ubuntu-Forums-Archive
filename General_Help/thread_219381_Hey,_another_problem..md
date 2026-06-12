---
title: "Hey, another problem."
date: 2006-07-19
forum: General Help
---

### Post by Roasted on 2006-07-19
Trying to install RealPlayer 10. I follow the instructions that can be found here.

[http://www.real.com/linux](http://www.real.com/linux)

Click "installation instructions" directly below the DOWNLOAD button.


I get this:


jason@Linux:~$ sudo chmod a+x realplayer10gold.bin
Password:
chmod: cannot access `realplayer10gold.bin': No such file or directory
jason@Linux:~$


Am I doing something wrong?

---

### Post by meng on 2006-07-19
Okay, starting with the basics:
1) Are you sure you are in the right directory?
2) The file is probably called RealPlayer10GOLD.bin - Linux is case-sensitive

Shortcut: if you type "sudo chmod a+x Re" and then press TAB, then it will auto-complete the filename for you (unless you have more than one file beginning with "Re".

---

### Post by Roasted on 2006-07-21
I just redownloaded RealPlayer 10 (I deleted it before). Now the BIN file is on my desktop. It's the only file I got. I tried to do the install code with the info you gave me above, but it just says no file or directory. What to do.... :(

---

### Post by jordilin on 2006-07-21
> **Roasted said:**
> Trying to install RealPlayer 10. I follow the instructions that can be found here.

[http://www.real.com/linux](http://www.real.com/linux)

Click "installation instructions" directly below the DOWNLOAD button.


I get this:


jason@Linux:~$ sudo chmod a+x realplayer10gold.bin
Password:
chmod: cannot access `realplayer10gold.bin': No such file or directory
jason@Linux:~$


Am I doing something wrong?
Forget doing a sudo, it's not necessary, you are the owner of this file. Secondly, write down the name exactly as it is called.

---

### Post by Roasted on 2006-07-21
"No such file or directory."

---

