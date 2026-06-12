---
title: "how to modify my bash file"
date: 2008-06-14
forum: General Help
---

### Post by suhailsqm on 2008-06-14
I am new to linux....i want to be lucky..
could some one tell me how i can manipulate my bash files..
which bash file ..
i can't file the file .bash-profile in my home directory or my user name directory.i.e /home/qmss2/

i can only find the file /home/qmss2/.bash-history

please help me regarding the concept of bash and how i do it..

thanks in advance,

suhail

---

### Post by bingoUV on 2008-06-14
> **suhailsqm said:**
> I am new to linux....i want to be lucky..


I hate to break it to you but modifying bash files does not make you lucky at all. Since it wastes time, it makes you a bit unlucky.

If you still insist, I'll tell you. 
1. Do you mean .bashrc file? Just run 
```

gedit ~/.bashrc

```

2. If you really mean a bash file, first you have to create a bash file. Say, suhail.bash. Do, 
```

gedit ~/suhail.bash

```

This will open a window in which you can modify it to your heart's content. Press ctrl-S to save after you are done.

---

### Post by suhailsqm on 2008-06-14
hi a .bashrc file opened but it is  empty..:(:(
actually i need to add a few paths.. for my gcc to compile and use a few libraries.

some guy gave me an advise to create my own environment such that every time i log in i need not add the PATH ...

he told me just search in net for info...

i just want to add some paths and now i see that there is nothing in my bash file..

could you tell me if it is empty or some thing wrong with my pc..

get back soon plzzz..
suhail

---

### Post by bingoUV on 2008-06-14
I guess it is a bit unusual for ~/.bashrc to be empty. But it is no big deal, your system will run fine even if it is empty.

Just add your paths in this file, I guess something like this
```

export PATH=$PATH:<path1>:<path2>:<path3>

```

Replace <path1> etc with the paths that you want to enter.

---

### Post by suhailsqm on 2008-06-16
thanks ...
could you please tell me how i should compile it....

---

### Post by pedro_orange on 2008-06-16
The bash files; .bash_profile, .bash_logout & .bashrc setup your account environment automatically when you login and when you invoke another bash shell. They are not compiled.

If you don't have these files in your home directory, you may be using the default ones in /etc/profile.

I guess what the guy was telling you to do, was to add some bash environment variables, so that when you use g++ you can use bash aliases instead of typing 'path/to/library/files' everytime you tried to compile an application.
Which would mean you compile as normal, but just use the bash alias path you created.

---

### Post by suhailsqm on 2008-06-16
cool i think it is source .bashrc
it worked and i don't    have to add path now everytime i start ..
thanks...

---

