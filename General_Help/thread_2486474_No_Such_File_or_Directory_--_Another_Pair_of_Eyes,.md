---
title: "No Such File or Directory -- Another Pair of Eyes, Please!"
date: 2023-05-01
forum: General Help
---

### Post by morgannahyde on 2023-05-01
Single user computer
New install this AM

Added the last entry in my bash.rc
helen@mars:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin:/opt/cmucl-21d/bin

helen@mars:~$ lisp
bash: /opt/cmucl-21d/bin/lisp: No such file or directory
#R!!mjh?!?!@@XF -- or words to that affect

helen@mars:~$ /opt/cmucl-21d/bin/lisp
bash: /opt/cmucl-21d/bin/lisp: No such file or directory
More Words

helen@mars:~$ ls /opt/cmucl-21d/bin
lisp
Yes!

helen@mars:~$ file /opt/cmucl-21d/bin/lisp
/opt/cmucl-21d/bin/lisp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=8330e37f9873d48fff8bf712a0e2ac6e2120d6a1, with debug_info, not stripped
helen@mars:~$ 

I can't see where I'm going wrong. Coffee didn't help :-(

---

### Post by ajgreeny on 2023-05-01
***Added the last entry in my bash.rc***

Is that a typo?
I think you may have meant .bashrc not bash.rc, the latter not being a normal file in your home folder.

I have no idea what that cmuci-21d is nor what it does so give us all the details pleae

---

### Post by morgannahyde on 2023-05-01
Hi ajgreeny,

Yes - typo; my .bashrc file in my home directory. The cmucl-21d is the Common-Lisp version 21d developed at [Carnegie Mellon University]("https://www.cs.cmu.edu/") ([https://www.cs.cmu.edu/](https://www.cs.cmu.edu/))

Helen

---

### Post by ne29914 on 2023-05-01
Did you logout/login? That's necessary to get the new $PATH working.

---

### Post by morgannahyde on 2023-05-01
Hi ne29914,

Yes - in fact I had reset and, again just now, I logged out and back in -- no joy.

helen

---

### Post by ne29914 on 2023-05-01
Permission/rights problem?

---

### Post by morgannahyde on 2023-05-01
Yeah ne29914 == somebody 502.  Dunno. Doing a lot of "chown's". So far no joy

---

### Post by ne29914 on 2023-05-01
chown would be my last resort. I was more thinking about x group permissions (to traverse a directory).

---

### Post by morgannahyde on 2023-05-01
Well permissions are mostly x's in the right places. Just doesn't sit right some unknown (502) owning directories and files. But I think all that's deflecting. Doesn't explain:
     helen@mars:~$ lisp
     bash: /opt/cmucl-21d/bin/lisp: No such file or directory

One other thing. The executable (lisp) has a asterisk at the end of the name in the terminal window; no asterisk in the graphical file manager view. I'm running the default 22.04 LTS; Wayland window manager. Don't know what the "*" means.  Including it in the command has no effect.

Thanks for hanging in ne29914.

---

### Post by aljames2 on 2023-05-01
> **morgannahyde said:**
> Well permissions are mostly x's in the right places. Just doesn't sit right some unknown (502) owning directories and files

You can view all user/processes by name & UID with the following, perhaps this will give some clues as to the ownership question:
```
awk -F: '{printf "%s:%s\n",$1,$3}' /etc/passwd
```

> **morgannahyde said:**
> One other thing. The executable (lisp) has a asterisk at the end of the  name in the terminal window; no asterisk in the graphical file manager  view. I'm running the default 22.04 LTS; Wayland window manager. Don't  know what the "*" means.  Including it in the command has no effect.

```
alias l

and

alias ll
```
Each will show the alias (shortcut) for the ls (list) command on your system.  This means if you just type l or ll at the command line, you will get the output based on the ls alias implemented on your system.  On mine l = ls -CF, and ll = ls -alF.  Both l & ll use the -F option which is what is causing you to see the asterick at the end of executalbe files.  If you see an @ at the end of a name, this indicates a symbolic link.  A / indicates a directory.  Read more about the ls command at man ls

Not sure I'm helping. Perhaps others can help more since I am not familiar with setting up a environment for this programming language.

---

### Post by morgannahyde on 2023-05-01
Hi aljames2,

Used awk earlier - no user 502 on this platform. I'm familiar with the various variations (groan) of the ls command. In any case I've lost interest; purged the lot and installed sbcl. 
Thanks

---

### Post by morgannahyde on 2023-05-02
This is my first interaction with this forum, though I have found answers to my questions here over the years.

Solved? Not from what's shown here. My bad; my unfamiliarity with mechanics. I have scrapped my attempts to install Common-Lisp promulgated by CMU. From previous experience I knew I could "apt install" SBCL and get on with it. So that's what I did. Perhaps I'll venture into the CMUCL camp and try to solve this. Apologies to any in a similar fix; I just wanted to move forward. So no real solution today.

---

### Post by ne29914 on 2023-05-02
> **morgannahyde said:**
> Just doesn't sit right some unknown (502) owning directories and files.

Do you mean user:group is 502:502?
That would be odd. Users normally reside at 1000:1000 and up in Ubuntu. UIDs below that are system related.

---

