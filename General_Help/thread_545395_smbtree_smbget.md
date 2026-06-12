---
title: "smbtree smbget"
date: 2007-09-07
forum: General Help
---

### Post by ny_NEx on 2007-09-07
Hi guys, i need a little help :-)

I want to use smbtree to see other windows computer in my network and then smbget to download files from them.....

when i use smbtree i only get this 

example 

2CROWDED
        \\OZIRIS         
                \\OZIRIS\C$                     Default share
                \\OZIRIS\ADMIN$                 Remote Admin
                \\OZIRIS\E              
                \\OZIRIS\D              
                \\OZIRIS\print$                 Printer Drivers
                \\OZIRIS\D$                     Default share
                \\OZIRIS\IPC$                   Remote IPC
                \\OZIRIS\E$                     Default share


So my question is this, can i get list of folders and files on let say D$ ?
Second when i use smbget for file download like this 

smbget -r  "link to file i want" i get you dont have permissions ? But when i use GUI everything is ok

So any ideas :-D ?

THX!!

---

