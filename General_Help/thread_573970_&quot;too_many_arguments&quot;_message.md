---
title: "&quot;too many arguments&quot; message"
date: 2007-10-12
forum: General Help
---

### Post by jmvidalvia on 2007-10-12
This is the message I am getting:
```
/home/jmd/sh/cartas.sh: line 2: [: too many arguments
```
My script is:
```

#!/bin/bash
if [ -n $(ls /home/as400/cartas) ]
then
   chown nobody:desa /home/as400/cartas/*
   chmod 660 /home/as400/cartas/*  
   mv /home/as400/cartas/* /home/datos/comercial/cartas/
fi

```

The mistery is that I am only getting the message sometimes, not always.
Thank you very much for your help!

---

### Post by cmnorton on 2007-10-12
This is probably coming from the ls, and you are getting it because there is too much data for ls to handle.  Use xargs. You'll need to look either at man xargs or info xargs. 

I would experiment with a modified command file that doesn't move anything, so you can test this without doing something unintended.

Edit:

I googled to get some examples. It looks like you could isolate one file at a time by doing something like this, and I am sure there's a better or more elegant way to do this:

for single_file in `find  /home/as400/cartas -type f -print0 | xargs -0`
do
       chown nobody:desa $single_file
       chmod 660 $single_file  
       mv  $single_file /home/datos/comercial/cartas
done

---

### Post by jmvidalvia on 2007-10-12
Thank you very much!
The problem is not the large amount of files, because the max amount are 10 or 20 files.
These are files comming from an IBM iseries, through ftp.
What I can imagine is that *ls* starts executting at the same time new files are being saved in the folder, and that might cause the error.
I love your solution: if I add a 2 or 3 seconds sleep, for shure all files read by *find* command will already be saved in the folder.
Am I right?
thanks a lot!

---

### Post by cmnorton on 2007-10-12
I'm rusty with asynch stuff. The loop should deal with one file at a time, but I don't know how that will play out with files coming from ftp. You might want to gate this with the completion of the ftp command.

---

