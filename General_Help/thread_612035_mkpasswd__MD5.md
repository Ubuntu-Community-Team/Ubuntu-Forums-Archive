---
title: "mkpasswd / MD5"
date: 2007-11-13
forum: General Help
---

### Post by poisonmushroom on 2007-11-13
I have installed ircd-hybrid along with hybserv to create my own little IRC server, and it's great it works fine! but the thing is that i need to make a password for OPER's (operators) and in the config file it says i have to use the PROGRAMS mkpasswd file to generate a password...

first they told its supposed to be in a BIN directory inside the ircd / ircd-hybrid directory and i found nothing...

i downloaded the package and extraxted it, i found a folder called Tools and saw a mkpasswd.c file there and thought if it's included here then it should work, but i have no idea HOW to use it... i tried ./mkpasswd and ./mkpasswd.c but i just get invalid command.

has anyone ever encountered a similar problem? please reply if you have!

Thank you! :)

---

### Post by poisonmushroom on 2007-11-14
sorry for the double post but, anyone? :)

---

### Post by smartbei on 2007-11-14
You can'r run c files like that, first you need to compile them using gcc.

Try this (run in terminal from the directory with the .c file):

```

gcc mkpasswd.c

```

That should create a file called a.out in the same directory. Run it with
```

./a.out

```
and see what it does. I haven't used hybserv myself, so I have no idea what this program does. If you want, and if the source code is short, post it here and someone will be able to tell you for sure.

Hope that solves your problem.

---

### Post by poisonmushroom on 2007-11-14
I did 'gcc mkpasswd.c' the first time, it didn't show any output (whether failed or succeeded) so i figured everything went ok, but i wouldn't find a.out anywhere, infact i found no new files in the directory at all.

i tried doing it again, and got: collect2: ld returned 1 exit status
then after random tries of doing ./mkpasswd.c and different unsuccesful tried i tried the gcc comand again and it told me:
mkpasswd.c:(.text+0x2ed): undefined reference to `crypt'
collect2: ld returned 1 exit status

maybe this doesn't have to be compiled? the damn readme file for ircd-hybrid says i can find the specific MKPASSWD file to generate a crypted password in the bin directory of where ircd-hybrid is installed but i can't find it anywhere.

Any help is greatly appreciated, thank you.

---

### Post by smartbei on 2007-11-14
No, a .c file definately needs to be compiled before it can be used. If I was next to my Ubuntu computer I would try to do it myself, but I am not right now unfortunately. I hope you manage to get it to work, otherwise I will take a look at this tomorrow from home :).

---

### Post by poisonmushroom on 2007-11-14
Alrite mate, i'l try to get it to work meanwhile!

Is there anyway i can contact you without spamming this thread? maybe PM? maybe if you happen to be free tomorrow you could spare 5 minutes of your time i can create a new user for you on my server :)

thank you for replying!

---

### Post by smartbei on 2007-11-16
I installed the package on my computer to see what is up. 
I think you can use the default mkpasswd utility to generate the password. To do so open the terminal and type:
```

mkpasswd <your password>

```
The output should be what you need to put in the config file. Tell me how that works out.

I am not exactly sure what package you downloaded and unzipped. If the above doesn't work, please include more detail.

---

### Post by poisonmushroom on 2007-11-16
Hey, i un-installed the IRCD-HYBRID daemon and installed Unreal instead, i'l go for that one!

the normal mkpassd found in ubuntu doesn't work, you have to use the one included in their package and it's all complicated so i went for unreal, looks like a better daemon to me ;)

Thanks for your help mate, i'm sure i missed something when i installed.

P.S: i learned something today, apt-get install is not always good :P

---

### Post by smartbei on 2007-11-16
Ok, well glad you found a solution anyway.

I don't think it was apt-get's fault though. :D

---

