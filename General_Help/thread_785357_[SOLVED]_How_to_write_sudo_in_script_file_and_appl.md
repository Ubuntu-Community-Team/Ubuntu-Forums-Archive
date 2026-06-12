---
title: "[SOLVED] How to write sudo in script file and apply password?"
date: 2008-05-07
forum: General Help
---

### Post by abcuser on 2008-05-07
Hi,
I need to execute one statement that only user1 has permitions to do. But this user does not have a read/write privileg to file.

So now I have two scripts:
==========================
1. script executed by root
==========================
cd /directory
chmod 777 *

===========================
2. script executed by user1
===========================
some commands that access files in /directory


Is there any way I could write only one script. I would need something like: sudo and apply my password in file to execute first script file. How to write sudo and apply password in bash script file?
Thanks,
Abcuser

---

### Post by bingoUV on 2008-05-07
You need to do make sudo not ask for a password when running a particular command. Read this for a small how-to :  [http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7)

---

### Post by caljohnsmith on 2008-05-07
> **bingoUV said:**
> You need to do make sudo not ask for a password when running a particular command. Read this for a small how-to :  [http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7)
I just wanted to mention that in case abcuser simply wants to run the script as root on startup (as you describe in the above thread link, bingoUV), another alternative is to just stick it in his /etc/rc.local file; anything in rc.local is run as root on startup.

---

### Post by abcuser on 2008-05-12
Hi,
thank you very much. Configuring sudoer solved the problem.
Regards,
Abcuser

---

### Post by danested on 2009-09-24
> **caljohnsmith said:**
> I just wanted to mention that in case abcuser simply wants to run the script as root on startup (as you describe in the above thread link, bingoUV), another alternative is to just stick it in his /etc/rc.local file; anything in rc.local is run as root on startup.

Thank You, I was just trying to find a way to connect to the net on log on instead of having to go through the whole open terminal, run sudo wvdial, then keep the window open thing. "rc.local" did it.:popcorn:

---

