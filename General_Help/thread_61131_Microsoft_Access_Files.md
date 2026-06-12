---
title: "Microsoft Access Files"
date: 2005-08-30
forum: General Help
---

### Post by matt0137 on 2005-08-30
Does anyone know what can open Microsoft Access Files (MDB,MDE)? OpenOffice.org2 dosen't seem to be able to open them. Thank you for any help you may provide!

---

### Post by izmaelis on 2005-08-30
I am not familiar with any information about opening *.mdb (ms-access) files with OpenOffice, but after doing some googling a found out that there are some app called **MDB Tools**. Maybe you should try it.
P.S. Here is what I found in repos:
```

izmaelis@boxzilla:~$ sudo apt-cache search mdbtools
libmdbtools - mdbtools libraries
mdbtools - JET / MS Access database (MDB) tools
mdbtools-dev - mdbtools development files
mdbtools-gmdb - JET / MS Access database (MDB) file viewer

```
I hope it helps you.  :roll:

---

### Post by professor_chaos on 2005-08-30
I am forced to interact with windoze users at work with a public access db. I use M$ access running on cxoffice to maintain compatibility. If it helps.

---

### Post by Haegin on 2005-09-29
**Read EDIT2 for solution**

open office 2 : base is supposed to be able to do it via the ODBC connection but you need unixODBC installed (available on synaptic).

You then need to get hold of and install a ODBC driver for ms access databases (im stuck here).

After that you define a odbc connection using gODBCConfig (also on synaptic) or some other tool I havent discovered yet.

Then you connect to the ODBC connection in OO2 Base

then it should work (i hope)

EDIT: If you update to breezy (now or when it comes out) then install open office 2 from synaptic. Make sure base is selected and right click and mark all the reccommended and suggested programs

that might help - im trying it now - will report back on my success

EDIT2:
Upgrade to breezy and install openoffice2 from the repositories. Make sure when you select the openoffice2-base package you right click on it and select all the recommended and suggested packages.

When it has installed (big download) open base and you should have the option of opening a "Microsoft Access" database.

If you have further problems contact me: [email]hjmills@gmail.com[/email] or jabber- [email]hjmills@jaim.at[/email]

---

