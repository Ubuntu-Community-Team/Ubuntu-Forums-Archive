---
title: "Conky: How to use execgraph?"
date: 2008-05-20
forum: General Help
---

### Post by jschall on 2008-05-20
I am running Conky 1.5.1 on eee Xubuntu. I would like to display a scrolling graph of wireless signal strength as extracted from iwconfig. With inspiration from several posts in these forums, I have almost succeeded.

I created a tiny script file called conkywifi:
#!/bin/sh
 /sbin/iwconfig ath0|grep level|cut -b45-47

and made it executable:
jeff@jeff-eee:~$ ./conkywifi
55 

This shows the received signal level on ath0 to be -55 dBm. Great.

I put this directly into a graph like this:

${execgraph ~/conkywifi}

And the graph is displayed without error - EXCEPT that an increasing signal results in a decreasing graph - for example, if the signal increases to -45 dBm, the graph goes down from 55 to 45.

So, is there a way to manipulate the value returned from the conkywifi script - for example, have it return (100 - conkywfi) instead? That way, the graph would display an increase in signal from 45 to 55 in the above example.

- Jeff

---

### Post by jjgomera on 2008-05-20
for example: 

#!/bin/sh
db=`dcop amarok player bitrate`
expr $db \* -1

---

### Post by jschall on 2008-05-20
Thanks for the reply, jjgomera! I'm not sure what you are suggesting.

I tried changing the conkywifi script to:

#!/bin/sh
x='/sbin/iwconfig ath0|grep level|cut -b45-47'
expr (100-x)

but I obviously don't know how to write scripts, because that gives the following result:
jeff@jeff-eee:~$ ./conkywifi
./conkywifi: 3: Syntax error: word unexpected (expecting ")")

How do I re-write the conkywifi script to print 100-x?

- Jeff

---

### Post by jjgomera on 2008-05-20
> **jjgomera said:**
> for example: 

#!/bin/sh
db=`dcop amarok player bitrate`
expr $db \* -1
puff :oops: , naturally i wanted to say: 

#!/bin/sh
db=`/sbin/iwconfig ath0|grep level|cut -b45-47`
expr $db \* -1

or if you want 100-db:

#!/bin/sh
db=`/sbin/iwconfig ath0|grep level|cut -b45-47`
expr 100 - $db

but maybe the - are conflictive if expr don't recognised as the correct sign, i haven't wireless to see it.

Furthermore, with `/sbin/iwconfig ath0|grep level|cut -b46-47` , you may obtain the positive number, isn't it?

I think all this is not necesary, have you played with conky wireless variables?
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by jschall on 2008-05-20
[QUOTE=jjgomera;5004711]

Furthermore, with `/sbin/iwconfig ath0|grep level|cut -b46-47` , you may obtain the positive number, isn't it?

Yes, but the dBm is a negative number. I can "catch" the "-" sign if I cut from character 45.


I think all this is not necesary, have you played with conky wireless variables?

Yes, but the signal level is not among them.

/QUOTE]

Thanks for the scripting ideas!

- Jeff

---

### Post by jschall on 2008-05-20
jjgomera, your suggested script doesn't do the subtraction :-(

jeff@jeff-eee:~$ cat conkywifi2
#!/bin/sh
db=`/sbin/iwconfig ath0|grep level|cut -b45-47`
expr 100-$db
jeff@jeff-eee:~$ ./conkywifi2
100-56
jeff@jeff-eee:~$ 

How do I get the expr comand to do the subtraction?

(I have read the man page for expr, but I can't understand it!)

- Jeff

---

### Post by jjgomera on 2008-05-20
with spaces!:

expr 100 - $db

---

### Post by jschall on 2008-05-20
jjgomera wrote:

"with spaces!"

That did it! Thank you for your patience, sir!

- Jeff

---

