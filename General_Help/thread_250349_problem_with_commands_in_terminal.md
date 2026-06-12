---
title: "problem with commands in terminal"
date: 2006-09-04
forum: General Help
---

### Post by adamstar on 2006-09-04
Hi,
When I enter commands in the terminal or Konsole I keep getting file or directory does not exist. If I put in /root/, no problem, but anything other them that it gives the bash...error message. I dont know if I have an improper configuration issue or just missing something simple....please help, its driving me nuts.

Adam

---

### Post by meng on 2006-09-04
Please give an example of a command and the error message. I suspect you may not be pointing to the correct file or directory.

---

### Post by adamstar on 2006-09-04
Hi,

It does not matter what i put in as far as directories go....basic commands are usually fine, by anything with : (example) cd /root/Desktop or to any file with /root/Desktop/ any folder ...does not go there...what am i doing wrong?

Adam

---

### Post by meng on 2006-09-04
Maybe you don't have a /root/Desktop folder (I know I don't). Why don't you do this:
ls /root
and see whether there's anything IN your /root directory to start with?
(ls is to Linux what dir is to Windows)

---

### Post by adamstar on 2006-09-04
here is an example of what i mean:

adam51@adam51-laptop:~$ Is /root
bash: Is: command not found
adam51@adam51-laptop:~$ ls /root
adam51@adam51-laptop:~$ Is/root
bash: Is/root: No such file or directory
adam51@adam51-laptop:~$ Is /root/
bash: Is: command not found
adam51@adam51-laptop:~$ /root/
bash: /root/: is a directory
adam51@adam51-laptop:~$ Is
bash: Is: command not found
adam51@adam51-laptop:~$

---

### Post by blackened on 2006-09-04
That's L as in Lava, or Licorice, or Lynx.
l(as in Laverne)s /root

---

### Post by jamesrose on 2006-09-04
Wow, ive neverseen that before

---

### Post by meng on 2006-09-04
> **adamstar said:**
> here is an example of what i mean:

adam51@adam51-laptop:~$ Is /root
bash: Is: command not found
adam51@adam51-laptop:~$ ls /root
adam51@adam51-laptop:~$ Is/root
bash: Is/root: No such file or directory
adam51@adam51-laptop:~$ Is /root/
bash: Is: command not found
adam51@adam51-laptop:~$ /root/
bash: /root/: is a directory
adam51@adam51-laptop:~$ Is
bash: Is: command not found
adam51@adam51-laptop:~$

Sorry perhaps I should have specified that the command is l-as-in-lousy-s

Anyway the fact that there was no output (no error and no output) after your correct second command reveals that there is no Desktop directory within /root, which is why you keep getting messages that the directory doesn't exist. So stop trying to do things to a non-existent directory!!!

Perhaps you are looking for your own Desktop directory, e.g. /home/adamstar/Desktop. Or ~/Desktop for short.

---

