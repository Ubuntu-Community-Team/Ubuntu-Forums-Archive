---
title: "%d variable doesn't work anymore?"
date: 2013-05-03
forum: General Help
---

### Post by FeraTech on 2013-05-03
I'm trying to do have a simple backup run daily and setup a copy script to copy into a folder by day.

I use to use %d which would populate with the day of the month. However, now all it does is create a folder called "%d".

I've tried to find a solution and don't see anything on why it doesn't work. Anybody help?

---

### Post by matt_symes on 2013-05-03
Hi

Post your script and all other relevant information.

You have provided way to little information to help you.

Post details of you setup and environment as well please.

Kind regards

---

### Post by FeraTech on 2013-05-03
This is the script, it works but creates a directory called "%d" 

cp -R /home/Public /BACKUP/%d

Ubuntu 12.04 LTS x64 server

---

### Post by matt_symes on 2013-05-03
Hi

> **FeraTech said:**
> This is the script, it works but creates a directory called "%d" 

cp -R /home/Public /BACKUP/%d

Ubuntu 12.04 LTS x64 server

It would create a directory called %d if that is what you are asking it to do.

```
matthew-S206:/home/matthew % mkdir -p BACKUP/%d
matthew-S206:/home/matthew % ls -ld BACKUP/%d  
drwxrwxr-x 2 matthew matthew 4096 May  4 02:02 BACKUP/%d/
matthew-S206:/home/matthew % 

```

I don't see how that would have ever created a directory with the date in it.

Are sure sure you're not trying to do something like this...

```
mkdir -p /BACKUP/$(date +"%d") && cp -R /home/Public /BACKUP/$(date %d);
```

You may even want to store the day in a variable and use that in both places.

EDIT:

Silly question: what shell are you using ?

Kind regards

---

### Post by Doug S on 2013-05-04
Above, I thiink Matt meant to write```
mkdir -p /BACKUP/$(date +"%d") && cp -R /home/Public /BACKUP/$(date [COLOR=#ff0000]+[/COLOR]%d);
```Example:```
doug@doug-64:~/test$ ls -l
total 28
drwxrwxr-x 2 doug doug 4096 May  3 21:37 backup
drwxr-xr-x 3 doug doug 4096 Jul  2  2011 o1
doug@doug-64:~/test$ ls -l backup
total 0
doug@doug-64:~/test$ [COLOR=#ff0000]cp -r o1 backup/$(date +%d)[/COLOR]
doug@doug-64:~/test$ ls -l backup
total 4
drwxr-xr-x 3 doug doug 4096 May  3 21:46 03
doug@doug-64:~/test$ ls -l backup/03
total 12
-rw-r--r-- 1 doug doug    6 May  3 21:46 bla.txt
drwxr-xr-x 3 doug doug 4096 May  3 21:46 t2
-rwxr--r-- 1 doug doug  501 May  3 21:46 test
doug@doug-64:~/test$ ls -l o1
total 12
-rw-r--r-- 1 doug doug    6 Jul  2  2011 bla.txt
drwxr-xr-x 3 doug doug 4096 Jul  1  2011 t2
-rwxr--r-- 1 doug doug  501 Jul  2  2011 test
```

---

### Post by matt_symes on 2013-05-04
Hi

Thanks DougS. 

3am typo that one :D.

Kind regards

---

