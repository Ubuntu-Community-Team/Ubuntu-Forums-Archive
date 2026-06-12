---
title: "admin needs permission to create folder in root"
date: 2007-10-09
forum: General Help
---

### Post by redarrow01 on 2007-10-09
advance thank you .

i need help please i am the admin on my server i need to create a folder in root.

i currently get told i have not got permission please help.

thank you.

---

### Post by jnorthr on 2007-10-09
prefix your terminal command with the
sudo command. This turns your profile into a superuser profile. You will be asked for the root password (hope you wrote it down!) but this command when placed first on the same line as any other command will grant special powers to the command. Example:
sudo lshw
to list your hardware. This only works for the FIRST profile you created on the system, as it has the ability to pretend to be god.

---

### Post by redarrow01 on 2007-10-09
Thank you but all those commands i dont no, i am from windows got rid off that sillyness now on this linux box, i am currently using the desktop version can you kindly give me step by step instructions from your post and thank you for your time.

---

### Post by jonobr on 2007-10-09
Hello ,

jnorthr describes the method for creating the folder in the root using "terminal".
Im guessing your trying to do it using file broswer?

Using a terminal gives you a lot more control and as you become more and more used to Linux/ubuntu,
you will find yourself more and more using a terminal.

What you can do is, on the desktop, select applications->  then accessories-> terminal, once this opens, type
sudo mkdir /newfolder

It will prompt for your password , enter it and the new folder is created.

The terminal screen allows you to do powerful things but you can also cause a lot of problems so be careful using the sudo, the systems lets you be God at that point.
One last point you should probably just create these folders in your homw directory unless there is a specifc reason for you to put it in the root user

---

### Post by redarrow01 on 2007-10-09
I get the following error.


sudo: mkdir/test: command not found


sorry but that didnt work.

i get these commands i am allowed to use is it correct there little there.

usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

---

### Post by Samhain13 on 2007-10-09
Space between mkdir and /test?

---

### Post by redarrow01 on 2007-10-09
Hi there thank you yes it worked so now i can make a dir with the command.

make the dir.

sudo mkdir  /test

remove the dir.

sudo rmdir /test

now if i wanted to copy somethink to the directory from d:  drive what the command please?

a guess

sudo copy d:program /

or what the command, thanks for the help i notice it a bit like old basic programming or dos commands .........

---

### Post by Samhain13 on 2007-10-09
I keep this link handy:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by redarrow01 on 2007-10-09
Thank you so much that what i needed the most all the commands.........


Thanks for everyones help all the best redarrow01.

---

### Post by strabes on 2007-10-09
Please mark this thread SOLVED.

---

### Post by jnorthr on 2007-10-10
thanks for the ss64 link sam

---

### Post by Samhain13 on 2007-10-11
You're welcome. :D

---

