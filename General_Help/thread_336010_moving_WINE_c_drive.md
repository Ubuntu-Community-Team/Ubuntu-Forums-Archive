---
title: "moving WINE c drive"
date: 2007-01-11
forum: General Help
---

### Post by jaffa_nz on 2007-01-11
Kia Ora

I want to move my ~/.wine/drive_c/ to another location due to lack of directory space.

I have done the obvious and searched for "wine directory move" and other configuration combinations and im really buggered if i know how to move it?

can anyone tell me how this can be done please

wicked ya all

New Zealand

---

### Post by Jongi on 2007-01-11
I've also been thinking of moving mine. The reason being I run more than one distro and I don't like the thought of using 500MB+ for the same program across different distros. Anyway my thoughts about this so far are to do this:

1. move the contents ~./wine/drive_c/ to a directory on the new drive. So say the new drive is /dev/hdb and it is mounted at /mnt/drive2. I would create a folder /mnt/drive2/wine. I would then move (using Konqueror) everything, in ~./wine/drive_c/ to /mnt/drive2/wine.

2. From a terminal:
# cd ~/.wine
# rm -rdfv drive_c/
# ln -s /mnt/drive2/wine drive_c/ 

The only thing I would worry about is whether registry links and the like would work. Thinking about it now, maybe if I ran winecfg I could just change drive_c to point to /mnt/drive2/wine from there.

I am not at my computer so can't check. That's how I've conceptualised it so far.

---

### Post by jaffa_nz on 2007-01-11
i tried moving the directory (without the link) and it didn't work.  =(   

So i used the command winprefixcreate --prefix <new_wine_dir> then modified the path for C: (not sure if i had too) to this new location using the command winecfg

When i ran notepad.exe it ran from the new path and the c: worked from their as well.  I then installed an application and noted that these went into C:\Program Files\ directory underneath the  new path... i guess after a reboot i'll know if this change stays??

=)

---

### Post by Jongi on 2007-01-11
I suspect moving the directory runs into registry problems.

I'll try that winprefixcreate.

Thanks.

---

### Post by Jongi on 2007-01-29
I think you need to do the changes in winecfg

---

### Post by pizpot on 2007-02-26
hey, i used to use unux, before windows, so i remembered about unix's soft and hard links. I think just moving the .wine folder to a nice place and putting a link to it will do the trick. I have to find out the command... don't have my old pal to ask hang on...

---

