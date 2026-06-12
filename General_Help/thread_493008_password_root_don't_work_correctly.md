---
title: "password root don't work correctly"
date: 2007-07-05
forum: General Help
---

### Post by thekarsillo on 2007-07-05
Hello all,
last yesterday, after a new system software update, I tryed to use the commad "su" from my terminal. I have not changed the password, but when I typed it, the system didn't recognized. So now I able to do login with all account restired on system, but I can belee root.
How can be happened? What can I do to resolve this problem?
Another thing, from terminal , when I try to list files/directory with command "ls" and/or "dir", I can't see the grant of the files, but only the names! Why this ??:(
Thanks very much....
Michele

---

### Post by kuja on 2007-07-05
You should take a look at this to see how Ubuntu deals with root privileges: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

ls is only supposed to list the names, if you want more verbose infromation use  "ls -l"

---

### Post by bodhi.zazen on 2007-07-05
+1 kuja

---

### Post by Bothered on 2007-07-05
If you want to change your root password (or enable root, if it isn't enabled), see [here]("http://ubuntuforums.org/showthread.php?t=7118"). Note however that enabling root login is not usually recommended (see RootSudo in ubuntu wiki, linked to above).

---

### Post by bulldog060 on 2007-07-05
There are a few ways you can set the root password:
   1) sudo passwd root
   2) System->Administration->Users and Groups; click `Show all users'; go to root's properties and select `Set by hand'
   3) Just use sudo with -s, su, or the shell you use ( should be bash )
       * to avoid entering your password every time change the %admin line /etc/sudoers to:          %admin ALL = NOPASSWD:  ALL

 As far as the directory listing goes using `dir' is a filthy habit so forget that :) ... but to see the permissions edit your .bashrc and add: 
alias ls='ls -l' 
by doing this you will lose the colors from the default so if you want color do 'ls -l --color=auto', I personally don't like using colors so I use the `-F' flag which gives you /, *, @ for directories, files with execute, and symbolic links.

Hope this helps,
~ron

---

### Post by bodhi.zazen on 2007-07-05
so set a root password :

sudo passwd

(don't need "root" on the end)

MORE IMPORTANT to lock the root account again if you change your mind later :

```
sudo passwd -l
```

*That is a small "L" and not the number 1

Or just passed -l if you are root already ;)

---

