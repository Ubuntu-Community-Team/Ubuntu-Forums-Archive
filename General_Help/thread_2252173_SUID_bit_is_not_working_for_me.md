---
title: "SUID bit is not working for me"
date: 2014-11-09
forum: General Help
---

### Post by Michael_Knapp on 2014-11-09
My understanding is that the SUID bit on executable files should allow the user to execute it with the same permissions as the user who owns the file.  To practice this I made an example:

```
dude@michael-virtual-machine /var/common $ cat myscript.sh 
#!/bin/bash
echo "run by $(whoami) at $(date)" >> script.log
dude@michael-virtual-machine /var/common $ chmod ugo+x myscript.sh 
dude@michael-virtual-machine /var/common $ chmod u+s myscript.sh 
dude@michael-virtual-machine /var/common $ ll
total 12
drwxrwxr-x  2 root developers 4096 Nov  9 20:32 .
drwxr-xr-x 12 root root       4096 Nov  9 17:21 ..
-rwsrwxr-x  1 dude dude         62 Nov  9 20:32 myscript.sh
dude@michael-virtual-machine /var/common $ ./myscript.sh 
dude@michael-virtual-machine /var/common $ ll
total 16
drwxrwxr-x  2 root developers 4096 Nov  9 20:33 .
drwxr-xr-x 12 root root       4096 Nov  9 17:21 ..
-rwsrwxr-x  1 dude dude         62 Nov  9 20:32 myscript.sh
-rw-rw-r--  1 dude dude         44 Nov  9 20:33 script.log
dude@michael-virtual-machine /var/common $ cat script.log 
run by dude at Sun Nov  9 20:33:39 EST 2014
dude@michael-virtual-machine /var/common $ su lady
Password: 
lady@michael-virtual-machine /var/common $ ll
total 16
drwxrwxr-x  2 root developers 4096 Nov  9 20:33 .
drwxr-xr-x 12 root root       4096 Nov  9 17:21 ..
-rwsrwxr-x  1 dude dude         62 Nov  9 20:32 myscript.sh
-rw-rw-r--  1 dude dude         44 Nov  9 20:33 script.log
lady@michael-virtual-machine /var/common $ ./myscript.sh 
./myscript.sh: line 2: script.log: Permission denied
```

So when the user named 'lady' tries to run 'myscript.sh' it is failing because she does not have permission to write to the file 'script.log'.  However, the 'dude' user does have permission to write to that file, and the SUID bit is set on the 'myscript' file.

Why is this not working?

---

### Post by papibe on 2014-11-09
Hi Michael_Knapp.

That does not work on scripts.

It is a security measure that most distributions set that way.

Hope it helps. Let us know if you have more questions.
Regards.

---

### Post by Michael_Knapp on 2014-11-09
so it just works for executables that are not scripts?  what about python scripts?  java archives?

---

### Post by jason147 on 2014-11-09
Python Should work? And Not so sure about java archives, If you like I can do some reasearch/tests

---

### Post by papibe on 2014-11-09
I'm no expert, but my guess would be yes.

Let's say you have a shell script called myscript.sh that starts with:
```
#!/bin/bash
...
...
```
If you run it, it won't be actually loaded in memory since it does not actually contain machine code. That line '#!/bin/bash' is sort of like a shortcut that tell the OS to do something similar to:
```
/bin/bash -f myscript.sh
```
Then a new instance of /bin/bash (which does not have any special bit turn on) would be loaded and it would start interpreting the script.

Does that make sense?

Just some thoughts.
Regards.

---

### Post by Michael_Knapp on 2014-11-10
I think I understand now, the SUID bit just works for files that are standalone executables, programs that were compiled into machine code, not interpreted scripts.

Thanks for explaining.

---

### Post by Impavidus on 2014-11-10
Of course the system could start the interpreter with the owner of the script as the user running the script, but this is insecure. This text explains it: [http://www.faqs.org/faqs/unix-faq/faq/part4/section-7.html](http://www.faqs.org/faqs/unix-faq/faq/part4/section-7.html)

In short: there are ways a normal user could get an interactive shell or use his own environment variables (like PATH) in a shell owned by the owner of the script.

---

