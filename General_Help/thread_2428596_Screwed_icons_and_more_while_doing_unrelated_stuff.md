---
title: "Screwed icons and more while doing unrelated stuff"
date: 2019-10-06
forum: General Help
---

### Post by bjngchn on 2019-10-06
What I did. I wanted to  move files from another user to  current user. 
So  I did things like sudo su, change directory, cp,  chmod . 
I removed some files and directories, but they  were on the Desktop and I knew what they were.
copied files which were not needed.
So I didn't  touch application files , or anything starting with a dot in file/diretory name.
...............................................................................
So what is wrong now. Application icons turned into zombies and are not functional.
Start menu is almost not functional. Can' t search most things. I can run firefox by 
searching for firefox and typing enter, at start menu. But I can't locate terminal
so there is no command line. 
...............................................
I think this might be related to using wildcards when chmod'ing. I did chmod 700 or chmod 777.
I didn't use random wildcards. I did things like chmod 700 *ar* to target specific directories
on Desktop. 
I can't imagine how such a thing can screw things up.
..............................
Another possibility, the system doesn't know which user I'm .

......
Whatever, I either need to restore some files , or bring them to the right chmod state, I think.
Can I fix this with a simple update? 
If I can just open a terminal window this would count as a progress.
Currently only  thing I can do is to browse directories using dolphin, and run some programs, but terminal is missing. 
..............
Thanks in advance. 




.....

---

### Post by CatKiller on 2019-10-06
> **bjngchn said:**
> I didn't use random wildcards. I did things like chmod 700 *ar* to target specific directories
on Desktop. 
If you did it like that, I'm pretty sure that would expand to things like /usr/share/, for example.

---

### Post by bjngchn on 2019-10-06
Thanks. And I can use terminal now, because by  typing konsole and  hitting  enter button, I get  the terminal window. 
So I can  used command line.
....................
I think when I was using chmod I was under /Desktop, so root directories shouldn't have been affected.
Shortcuts to applications  on Destktop and Panel, and Menu are nonfunctional, and their icons are not visible.
Everything else might be working correctly. 
So where am I supposed to look  at now? 
.............

Is chmod 700 on everything, a good idea, or would it make some applications not work? 
Would it make shortcuts to applications not work?

..........
BTW, All programs load very fast after this accident. 

............
I logged in as other users and they have the same problem. 
Maybe erasing some files starting with dot would fix this problem? Or doing 
another chmod.
Can I bring permissions of root directories shared by all to their  default states
easily?

---

### Post by bjngchn on 2019-10-07
UPDATE

I think it happened like this.

Let's say  I'm user A, and I wanted to move  files from user B's home directory.
I moved files from B's desktop to to A's desktop, but was unable to access them, becase of their ownership , or chmod status.
So  to change their ownership or chmod status,  I  chmoded 700 many things on A's desktop. 
Maybe at that stage  I was logged in as  B, instead of A, and chmod 700 made those files  unaccessible to A. 
But whatever happened it affected other user C as well equally. 

.........

UPDATE: 
 
By doing sudo  700 at A's desktop while logged in as A ,  I was able to recover part of it. Namely part of the  panel links. 
By doing  sudo 777  I corrected stuff on  the Desktop. 
But StartMenu  is still problematic. I think search function is not working correctly. And some icons are missing
although their links  may be functional. 
I search for kmix, I can add it to the panel, but when I run it, nothing happens. 
 So there is no sound control.
Browsers   load very fast. I wonder what was making load them slowly. 


............................
What should be default chmod state of root files?  700 doesn't make sense because then it depends on the user. 
Is 777 the correct one?


For example if I do 

sudo chmod 777 /usr/


will do it any harm?

---

### Post by bjngchn on 2019-10-10
RESOLVED.

Fixed after applying nautilus command here:

[https://ubuntuforums.org/showthread.php?t=2247343](https://ubuntuforums.org/showthread.php?t=2247343)

and then disabling one of monitors.

---

