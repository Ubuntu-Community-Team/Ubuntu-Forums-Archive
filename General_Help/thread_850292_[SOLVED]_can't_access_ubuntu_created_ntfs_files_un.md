---
title: "[SOLVED] can't access ubuntu created ntfs files under windows"
date: 2008-07-05
forum: General Help
---

### Post by wrax on 2008-07-05
hi,
i'm using ubuntu hardy and windows xp. hardy became my main os during the last months but i'm still using the "old" ntfs data partion which holds mp3, pictures, etc.

here is my problem: some of the files i have created with hardy on this ntfs partition can't be accessed under windows xp. (for instance, backuped emails).
they are shown with file size 0 and no (just an empty gap) creation-  or last-change date in properties. same applies for directories. but there is no problem with those files under hardy; and i can't say why some files are affected by this problem and some aren't.
when i try to open it, windows says something like "file can't be found"

anybody got the same problem or can help me? i have searched through the forum but couldn't find anything useful. 

thanks in advance.

---

### Post by niyonk on 2008-07-05
hi, 
let me see...
-you are creating files in that partition using hardy and you cannot access them using xp (just to make sure i got your Q)
anyway, i do not have such problems...i am triple booting with vista

-both vista and xp can acces those files....
try mp3s from hardy to ntfs partition and see if you get the same error.

Like i said so far no such problems :(

---

### Post by prshah on 2008-07-05
> **wrax said:**
> 
here is my problem: some of the files i have created with hardy on this ntfs partition can't be accessed under windows xp. (for instance, backuped emails).
they are shown with file size 0 and no (just an empty gap) creation-

Looks like cross-linked clusters; try running "chkdsk /f" on the affected drives, eg:```
chkdsk /f x:
```.

Note: if you have crosslinked files, chkdsk does it's best to recover the files, but usually save it in chunks of .CHK files. This may cause you to lose data, so you give this command at your own risk. If those files are accessible in ubuntu, i'd suggest that you back them up before issuing this command.

---

### Post by wrax on 2008-07-07
niyonk you got the question right. what exactly was you answer :) i can't say why some files are affected and some work perfectly fine. 

prshah, i have tried chkdsk (without that automatic repair option) but it couldn't find any errors. 
i have already made a backup (on another ntfs disk...), but since i would like to keep on using hardy i am still open for other suggestions :confused:

---

### Post by niyonk on 2008-07-08
Wrax,

:tongue: My answer was what filetypes are affected??
If mp3s copy just fine, then it should be some kind of corruption in some speficic filetypes.
But Linux doesn't care about filetypes and extensions, so I am confused :confused:

Anyone else willing to help out?? :)

---

### Post by wrax on 2008-07-20
ok, problem solved:

ubuntu does not care about the textual restrictions of ntfs filenames. so when i saved thunderbird emails it named the files same as the subject line, which sometimes contained a ":".

so i removed those invalid filename-characters under ubuntu and now i'm able to access the affected files under windows.

thanks anyway for your advices.

---

