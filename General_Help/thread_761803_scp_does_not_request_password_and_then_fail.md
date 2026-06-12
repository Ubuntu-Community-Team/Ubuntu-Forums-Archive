---
title: "scp does not request password and then fail"
date: 2008-04-21
forum: General Help
---

### Post by atbrew on 2008-04-21
Hi I have just installed the ssh package on my ubuntu machine, however when I got to scp files to that machine from any other machine I am not prompted for a password and the transfer then as one would expect fails. I can scp to other machines fine so it must be a setting that I am missing on my ubuntu box.

Thanks a Mill,
Anthony

---

### Post by bodhi.zazen on 2008-04-21
can you ssh into the server ?

If so, what exactly is the command you are using for scp ? If you changed the ssh port, scp uses -P rather then -p to signify a port.

---

### Post by atbrew on 2008-04-21
](*,)

Sorry, I made the rather stupid mistake of missing the colon at the end of 

scp myfile.zip [email]user@host.com[/email]:

and from the other machines I was using cntl r to look up the history of command I had typed

---

