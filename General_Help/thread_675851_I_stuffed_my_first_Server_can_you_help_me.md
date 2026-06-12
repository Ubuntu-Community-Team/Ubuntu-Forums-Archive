---
title: "I stuffed my first Server can you help me?"
date: 2008-01-23
forum: General Help
---

### Post by rawsco on 2008-01-23
Hi Peeps,

Ive been a bit of a moron and ran the following command (by accident)

*sudo mv -v * /vm*

Regretably I was in / and not the intended dir. The command did not complete i interupted it using CTRL + C

Now I cannot run the command to copy the files back to fix my now near death server (Ubuntu Server 6.06)

Its on life support just now, I have an ssh session to it which works fine bar the fact that my environments are all gone so i need to run everything by absolute path eg /vm/bin/ls however it will not let me sudo so as i can run the reverse mv to put all the files back. I cannot connect new sessions or log into the console.  If i lose the ssh session its flatline time...  Error as follows when i try to sudo to move the files back....

*sudo: uid 1000 does not exist in the passwd file*

I expect this is because I moved it the passwd file.  My question is as follows; Can I remap sudo to the passwd file in /vm/etc/ so as i can sudo then run the mv command to repair the problem.

Also any suggestion on how to recover the server would be good...

They warned me about this!!!

Ross

---

### Post by kpkeerthi on 2008-01-23
> Boot with the Live CD
> Mount the / partition to /ubuntu
> Then move the files over from /ubuntu/vm/ to /ubuntu

---

### Post by rosegarden78 on 2008-01-23
Try Gutsy Gibbon fresh install and/or re-install these packages using Synaptic::

Apache2
PHP5
MySql

This get a LAMP going for me every time!

---

### Post by rawsco on 2008-01-23
Okdokey, that seemed to do the trick kpkeerthi, managed to get the server to boot and allow me to log in however there are still some problems with the networking IE it wont pick up an ip address.

Im sure i can figure that out on my own... thanks mate.

rosegarden78, I think you missed the point totally, its not a LAMP server nor is it running Gutsy nor would i want to update to gutsy at the moment.

Anyways thanks again kpkeerthi.

R

---

