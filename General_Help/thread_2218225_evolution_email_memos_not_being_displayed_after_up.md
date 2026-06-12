---
title: "evolution email memos not being displayed after upgrade"
date: 2014-04-19
forum: General Help
---

### Post by stinger30au on 2014-04-19
g'day,
i have in the past few days upgraded from ubuntu 12.04 to lubuntu 14.04. i did a backup of evolution email in 12.04 using the backup feature in the program before i did a full install from cd of 14.04 and deleted all partitons and started from scratch.

i have lubuntu 14.04 running fine now with one exception.


i can start evolution email and send/recieve email etc & all is well till i click the memo button.

when i click in there all my memos are gone.

however, if i look in

/home/dez/.local/share/evolution/memos/system

i can see the directorys with the attachments for the memos that have attachments for them. and i can see the journal.ics file.

if i open the journal.ics file with gedit i can see all my data safe & sound but evolution memo refuses to see anything. i have double checked to make sure i havenot done anything silly like put a tick in a box any where that shouldnt be there and i cant find anything.

i have tried to restore my data to another pc i have running 14.04 and it also does the same thing, i can see everything in evolution except my memo's.

im sure it will be a simple fix, but i cant for the life of me figure this out. anyone got any ideas??

thanks

---

### Post by stinger30au on 2014-04-20
YIPPIE!!! i found a solution.

WOW man this took some serious reading on many different fourms. 

firepup evolution and goto memo's

click on 

new

then click

memo list

then point it back to the journal.ics file that i memtioned in the previous post and presto! theres all your memo's & attachments back again.

now the only issue is i now have 2 memo lists, i have the original "personal" list and my new "restored" list. so now i need to figure out how to delete the "personal" mem list that is empty and have just the one list and then i can do cartwheels for finding a solution!

---

### Post by stinger30au on 2014-04-20
in evolution in the memo section it says on the right side

on this computer

under that it says

personal

the directory called personal you can not delete by the looks of it, you can rename it, but not delete it. my memos are restored to a new memo list called "restored". i can rename this list to what ever i want and even delete it if i wish, but i can not for the life of me merge it in to the diectory called "personal"

anyhow, whatever, i give up, all my memos are now working again it would have been nice to have them all merged together in the one directory called "personal" but looks like it cant be done.

hope htis information helps someone else later down the track

---

### Post by stinger30au on 2014-04-20
another update to this. last night before i went to bed i put a tick in my "restored" memo's and clicked one of the memo's and then clicked edit select all, then copy. then put a tick in the "personal" memos and clicked edit paste & went to bed. this morning all the memos from "restored" are now copied back in to "personal" and i can now delete "restored" and all my memos are back where they should be and eveything is fine again. yippe!

hope this helps some one

---

