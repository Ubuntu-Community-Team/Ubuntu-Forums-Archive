---
title: "Unable to unmount USB key ( Losing files)"
date: 2007-05-05
forum: General Help
---

### Post by gwatts on 2007-05-05
Trying to copy files with USB key.

In this forum below about halfway down:

[http://ubuntuforums.org/showthread.php?t=401591&page=2](http://ubuntuforums.org/showthread.php?t=401591&page=2)

 (Sorry I don't know how to link in this forum)

I issued this command as suggested:

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

and now I have lost disk (the USB key) from the desktop.

It is still present in "Computer" but I cannot access it.

Please advise either how to nullify that command or how from here to unmount the key 
so that I can use it to transfer files. (They disappear when I unplug the key)

Sources suggest previous Ubuntus had an unmount on right click that is not present on 7.04.

Thank you.

---

### Post by tgm4883 on 2007-05-05
Do you know what that command does?

:EDIT:

You really shouldn't just run commands that strangers tell you to run.  Not everybody is here to help.  Some bad people give commands that do bad things and it you dont check them out first then your asking for trouble

---

### Post by sdide on 2007-05-05
you basically moved a file.  (mv is an abb. for "move")

if you want to undo it, move it back. eg.

~$ sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.bak /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi

or better yet make a copy of the file back into the original location

~$ sudo cp /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.bak /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi

---

### Post by gwatts on 2007-05-05
Thank you but both commands by copy and paste as well as by typing > :

kk@jjj:~$ sudo cp /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.bak /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi
cp: cannot stat `/usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.bak': No such file or directory
kk@jjj:~$

---

### Post by gwatts on 2007-05-05
And I can see the bak file.

---

### Post by sdide on 2007-05-05
hmm could you do a 

~$ ls -l /usr/share/hal/fdi/policy/10osvendor/

and post output?

and

~$ lsof | grep 10-storage

and post output

---

### Post by gwatts on 2007-05-06
Thank you.

kk@jjj:~$ ~$ ls -l /usr/share/hal/fdi/policy/10osvendor/
bash: ~$: command not found
kk@jjj:~$ ls -l /usr/share/hal/fdi/policy/10osvendor/
total 48
-rw-r--r-- 1 root root   442 2007-03-30 13:53 10-keyboard-policy.fdi
-rw-r--r-- 1 root root  5776 2007-03-30 13:53 10-laptop-panel-mgmt-policy.fdi
-rw-r--r-- 1 root root  1373 2007-03-30 13:53 10-macbook-backlight.fdi
-rw-r--r-- 1 root root  3356 2007-03-30 13:53 10-power-mgmt-policy.fdi
-rw-r--r-- 1 root root   465 2007-03-30 13:53 10-toshiba-buttons.fdi
-rw-r--r-- 1 root root  1214 2007-03-30 13:53 15-storage-luks.fdi
-rw-r--r-- 1 root root 15210 2007-03-30 13:53 20-storage-methods.fdi
-rw-r--r-- 1 root root   523 2007-03-30 13:52 storage-policy.fdi.bak
kk@jjj:~$ 

kk@jjj:~$ lsof | grep 10-storage
kk@jjj:~$

---

### Post by gwatts on 2007-05-06
I don't know what I did if anything but the key is back on the desktop and there is an unmount on right click and the files transfer as they should to the XP computer.

Thank you Soren.

---

