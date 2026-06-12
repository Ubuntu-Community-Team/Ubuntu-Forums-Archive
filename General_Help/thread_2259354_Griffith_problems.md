---
title: "Griffith problems"
date: 2015-01-03
forum: General Help
---

### Post by jlh68 on 2015-01-03
Does anyone know how to open Griffith?  I have it on my desktop and ever since I upgraded from 12.04LTS to 14.04LTS it does not open.  I have in Griffith about 350 DVD and VHS movies listed and now I can not access them.  I know that Griffith is not supported anymore (bummer, it was a great application).  

I would like to get the data base of Griffith files out of Griffith and use some other database with them.

---

### Post by qamelian on 2015-01-03
There is a problem with the file validators.py located at /usr/share/griffith/lib/db. You can download the source archive from [here]("http://launchpad.net/griffith/trunk/0.13/+download/griffith-0.13.tar.gz"), and replace the file at /usr/share/griffith/lib/db with the one found in the downloaded archive. That should allow Griffith to run normally.

---

### Post by jlh68 on 2015-01-04
Some help please.  When I try to extract the file to /usr/share/griffith/lib/db, I get a message that I do not have authority to access the db file.
Would you mind providing the procedure to extract new file to the destination folder?

---

### Post by Dennis N on 2015-01-04
You need root permissions to put something in  /usr/share. Extract your file or folder to your Desktop first, and then copy or move it using sudo to the desired location.

---

### Post by jlh68 on 2015-01-05
I am having trouble getting the correct code to make the replacement..

suggestions?

---

