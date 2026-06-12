---
title: "problems with scp"
date: 2008-04-01
forum: General Help
---

### Post by balkrishna on 2008-04-01
i use ubuntu gutsy gibbon.....the main problem i am facing is with copying folders or files via scp that have whitespaces in them for eg:
if i have a file: x yx 
i type in 
scp user@server:/filepath/x\ yx/ ~/destination
it gives error file x not found
file yx not found.....
Please help me on the same.

---

### Post by Slushdoot on 2008-04-01
What happens when you use
scp user@server:"/filepath/x yx/" ~destination

---

### Post by eldragon on 2008-04-01
nope, that will not work either.

ive tried: 
scp user@server:"folder with spaces/file"
scp user@server:folder\ with\ spaces/file
scp user@server:folder\040with\040spaces/file

none work.

this has been going on for a while, i havent found a solution other than renaming folders with underscores.

or use psftp (apt-get install putty-tools)

psftp works like ftp.exe in windows, but through ssh....

psftp does accept spaces with "folder name"

---

### Post by balkrishna on 2008-04-04
is this a bug with scp or am i using scp wrongly????

---

### Post by eldragon on 2008-04-05
> **balkrishna said:**
> is this a bug with scp or am i using scp wrongly????

i think its neither, but i might be wrong. 
anyway, a fix should be really easy to produce for a programmer, i am not one (or even a skilled one).....

i wouldnt know where to file a report. i guess people just deal with it and use psftp instead.

might be that linux/unix users are not used to dealing with spaces. so noone has been able to find this issue.

---

### Post by ubtutu on 2008-05-29
I got round a similar problem using this format:

scp user@server:/root/"folder\ with\ space"/file

---

