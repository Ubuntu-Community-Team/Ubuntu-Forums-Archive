---
title: "Copying &quot;Windows Files&quot;"
date: 2005-04-17
forum: General Help
---

### Post by stryderjzw on 2005-04-17
Hi everyone,

I just started using Ubuntu from Windows and now I wanna copy files over.

I have Windows on another partition.  When I use Ubuntu, I mounted the windows partition read-only so I can access the files.

I wanna copy some docs to Linux home directory and it's giving me this error:
Error "Bad file handle" while copying "/media/windows...gineer CL.doc".

Does anyone know anything about this?   ](*,) 

Thanks,

Justin

---

### Post by soul_rebel on 2005-04-17
can you try to do it as root using sudo and post any problem?

---

### Post by stryderjzw on 2005-04-17
I get something like this now:

stryderjzw@legolas:~$ sudo cp /media/windows/Documents\ and\ Settings/Justin/My\ Documents/School\ Work/ ~/
cp: omitting directory `/media/windows/Documents and Settings/Justin/My Documents/School Work/'

---

### Post by speedman on 2005-04-17
Try cp -r for copying a directory and it's contents recursively.


Regards,

SM

---

### Post by stryderjzw on 2005-04-17
Thanks.  Ah boy, it's gonna take a while to get used to all the commands...   :?

---

