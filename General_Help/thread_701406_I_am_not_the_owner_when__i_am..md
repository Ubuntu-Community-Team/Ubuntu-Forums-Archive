---
title: "I am not the owner when  i am."
date: 2008-02-19
forum: General Help
---

### Post by krissyafc on 2008-02-19
Well i was editing a file and when i try ed to save it, it didn't let me. It was a read only file. When i tryed to change the permissions it says i am not the owner when i am. Its like that with all files and i want to be able to change there permissions.

Thanks.

---

### Post by aysiu on 2008-02-19
This link will help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by zanak on 2008-02-19
you have to bee root to modify files that are not in you home folder (like desktop) to modify files in /etc you have to use sudo.

hope it helps

---

### Post by tact on 2008-02-19
are you sure you are the "owner" of the file?   how did you determine that?

would you try either of the below and give feedback...

Either...
1.   right click on the file and click properties then the "permissions" tab... is that your username, your login name, listed as "owner"?

or....

2.  assuming the file is in your home directory -  pull up a terminal and execute the following command
```
ls -l 
```

This will result in a directory listing of all files in your home directory and their ownership/permissions.   You could then copy/paste just the line related to your problem file.  It would look like this...perhaps...
```
-rw-r--r--  1 tact tact   466944 2008-02-16 15:11 nautilus-debug-log.txt
```

This will help to diagnose...

---

### Post by aysiu on 2008-02-19
If you're not the owner, do not change ownership of the file. There are ways to edit the file when you are not the owner.

Root-owned files are root-owned for a reason.

Read the link I posted earlier for more details.

---

### Post by krissyafc on 2008-02-19
Well i was editing a file and when i try ed to save it, it didn't let me. It was a read only file. When i tryed to change the permissions it says i am not the owner when i am. Its like that with all files and i want to be able to change there permissions.

Thanks.

---

### Post by orlox on 2008-02-19
if you get to the files directory in a terminal and type ls -l, what's your output???

---

### Post by sryth on 2008-02-19
Many files in ubuntu are protected from accidental changes by belonging to "root"  So you have to use sudo to work on them.  This keeps "bad things" from happening unintentionally.  So be very careful about removing those protections.

---

### Post by krissyafc on 2008-02-19
Type what? How do i go to itsDIR in termanal.

---

### Post by orlox on 2008-02-19
open up a terminal, and use cd to change the directory. For example, if you want to go to your home folder you could type:
```

cd /home/your_username

```
where your username is your username... once you've done this, you can type on the terminal:
```

ls -l

```
and a los of things should appear. This is just a listing of the files contained on that folder along with the permissions of each of them,

---

### Post by bodhi.zazen on 2008-02-19
Threads merged.

@krissyafc: Please do not start multiple threads on the same topic.

---

