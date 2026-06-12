---
title: "Help with installing downloaded files??"
date: 2006-12-04
forum: General Help
---

### Post by slyjelly on 2006-12-04
Hi there,

im relatively new to ubuntu and am trying to install some game demos just for personal satisfaction of not using windows....:D 

im strictly trying to install them using the graphical methods (not console and commands)

when i click the files, gedit opens but thats as far as i get

e.g how do i install the linux quake 3 demo in ubuntu gui?? its called "linuxq3ademo-1[1].11-6.x86.gz.sh"

other demos include quake 4 and coldwar. im sure there is simple explanation somewhere but i cant find it and my brain is hurting from excessive reading of information i dont need!!

plz help.............thx

---

### Post by 23meg on 2006-12-04
[http://ubuntuforums.org/showthread.php?t=258823](http://ubuntuforums.org/showthread.php?t=258823)

---

### Post by slyjelly on 2006-12-04
i cant beleive you just posted that, did you actually read it? or my question? that link is to a question with no replies!!!

and i said i cant work with terminals and commands, only gui

plz only post answers, not directions to the same question (which received no answers anyway)

---

### Post by 23meg on 2006-12-04
> i cant beleive you just posted that, did you actually read it? or my question? that link is to a question with no replies!!!Yes, I read both. Did you read it? It did get replies; posts 4 and 5 should direct you to what you have to do with the file. 
> and i said i cant work with terminals and commands, only guiSorry, there's no way to run this kind of installer with clicks only. You don't have to know anything about the command line interface to install it. Just follow the instructions. 

What you have to do is navigate to the directory where the file is with the cd command; if it's on your desktop, that would be ```
cd ~/Desktop
```and then type ```
./linuxq3ademo-1[1].11-6.x86.gz.sh -target ~/q3
```
This information was already in the thread I linked to (which you could have found with a forum search without even asking a question), and simply linking to the thread took me three seconds, whereas typing the above took a minute.

---

### Post by slyjelly on 2006-12-04
hey thanks for trying. i apologize for my stupidity but i am literally being driven to insanity by trying to look for answers(nearly 4 hours now)](*,) . after following your instructions of typing in the terminal, i got the same problem as the last post on that page

[http://ubuntuforums.org/showthread.php?t=258823](http://ubuntuforums.org/showthread.php?t=258823)

i tried 3 or 4 different command/terminal approaches given in the forums, none of them worked. im currently downloading something within the terminal by use of this 

wget [ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3ademo-1.11-6.x86.gz.sh](ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3ademo-1.11-6.x86.gz.sh)
./linuxq3ademo-1.11-6.x86.gz.sh -target ~/q3
chmod -R 755 q3/
cp q3/bin/x86/glibc-2.0/q3demo q3/
cp q3/bin/x86/glibc-2.0/libMesaVoodooGL.so.3.2 q3/libMesaVoodooGL.so
ln -s /usr/lib/libGL.so.1 q3/libGL.so
rm -R q3/setup.data
rm -R q3/bin
rm q3/setup.sh
cd q3/
./q3demo

found in the same forum 
will take 30 mins or so (i doubt it will work) i dont exactly know what im doing but its the only thing i haven't tried

by the way, your comment on how these files require terminal activity was crucial to me. this seems fundamental to everything yet i found no one else who mentioned it. (probably due to it being widely known)

im sure the instructions are out there somewhere, there just not ordered simply enough. i have to piece together bits of instructions to come up with the exact, step by step installation, which eventually i lose track of where i am, or find out it doesnt work anyway.

p.s truely many thanks for helping

---

### Post by slyjelly on 2006-12-04
i finally got it sorted although i cant remember precisely how. :) (took me 3 hours)

you where right, all information was in the forum, without you i would be back in xp right now fighting virus's and adware!

thanks dude!!!

---

