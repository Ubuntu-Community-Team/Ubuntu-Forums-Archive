---
title: "help!!! virus killing my lappy and dont know whatto do!"
date: 2007-07-20
forum: General Help
---

### Post by dan171717 on 2007-07-20
i was playying around with kde and pressed the anivirus (aegis) and decided to do a scan. it scanned my windoze xp partion andfound about 40 files including the kernel infected with 

w32/magistr.a@MM

i read somewere that this can destroy a hard disk and flash a bios


what should i do

1. should i leave it alone and not not boot into windows
2.should i kill my windoze partion
3.completey format the  hdd install ubuntu back on

i cant qurrentine the files as it wont let me

i can rename them but what about the kernel

---

### Post by bodhi.zazen on 2007-07-20
[http://www.symantec.com/security_response/writeup.jsp?docid=2001-031313-1110-99&tabid=3](http://www.symantec.com/security_response/writeup.jsp?docid=2001-031313-1110-99&tabid=3)

---

### Post by Seisen on 2007-07-20
If you have an antivirus installed on your Windows Partition boot into safe-mode and then run the antivirus software and it should get rid of it.

---

### Post by pointone on 2007-07-20
You can download and run a specific cleaner for the virus (boot into safe mode) but if the system is too far gone, you might consider just formatting the Windows partition.

---

### Post by dan171717 on 2007-07-20
windows boots ok normally but

avg (windoze) wont detect it.

but aegis (linux) does

---

### Post by Seisen on 2007-07-20
Check out Bodhi Zazen's link he posted, there was tool that you can download that will remove the virus.

---

### Post by dan171717 on 2007-07-20
ok i will try it

---

### Post by dan171717 on 2007-07-20
i ran it but it crashed half-way

---

### Post by p_quarles on 2007-07-20
I had a virus once, about seven years ago, that was designed to prevent certain security software from operating correctly. There are many tools like the one you just tried -- I'd suggest finding a bunch of them (majorgeeks.com is a good place to find them) and seeing if any of them work. Chances are, the virus is preventing the Symantec program from working correctly, but it probably won't have the same effect on more obscure virus killers.

If that doesn't work, I'd reinstall.

---

### Post by dan171717 on 2007-07-20
> **p_quarles said:**
> I had a virus once, about seven years ago, that was designed to prevent certain security software from operating correctly. There are many tools like the one you just tried -- I'd suggest finding a bunch of them (majorgeeks.com is a good place to find them) and seeing if any of them work. Chances are, the virus is preventing the Symantec program from working correctly, but it probably won't have the same effect on more obscure virus killers.

If that doesn't work, I'd reinstall.

i cant find one on major geeks for this virus

---

### Post by timzak on 2007-07-20
Have you considered the possibility that the Linux scan is a false positive?  If AVG is not catching it (AVG is a pretty decent AV) then there probably isn't anything to catch.  My brief experience with AV software in Linux indicated that since there are fewer viruses in Linux, they're not as up to speed with AV programs in Linux, and things like false positives occur fairly frequently, especially when scanning Windows drives from Linux.  Let Linux AV scan Linux drives and Windows AV scan Windows drives.

Just to be sure, try a couple of other free virus scanners in Windows before doing anything else.  Try Avira Anti-Vir ([www.free-av.com](www.free-av.com)), and there's a free version of AOL's AV that uses the Kaspersky engine and is supposedly one of the top virus scanners out there.  Here's a link to a FAQ on this program on another messageboard:
[http://forums.anandtech.com/messageview.aspx?catid=76&threadid=1982241&enterthread=y](http://forums.anandtech.com/messageview.aspx?catid=76&threadid=1982241&enterthread=y)

---

### Post by bodhi.zazen on 2007-07-20
> **timzak said:**
> Have you considered the possibility that the Linux scan is a false positive?  If AVG is not catching it (AVG is a pretty decent AV) then there probably isn't anything to catch.  My brief experience with AV software in Linux indicated that since there are fewer viruses in Linux, they're not as up to speed with AV programs in Linux, and things like false positives occur fairly frequently, especially when scanning Windows drives from Linux.  Let Linux AV scan Linux drives and Windows AV scan Windows drives.

Just to be sure, try a couple of other free virus scanners in Windows before doing anything else.  Try Avira Anti-Vir ([www.free-av.com](www.free-av.com)), and there's a free version of AOL's AV that uses the Kaspersky engine and is supposedly one of the top virus scanners out there.  Here's a link to a FAQ on this program on another messageboard:
[http://forums.anandtech.com/messageview.aspx?catid=76&threadid=1982241&enterthread=y](http://forums.anandtech.com/messageview.aspx?catid=76&threadid=1982241&enterthread=y)

+1 on that !

The number 1 reason I do not run Linux antivirus is I do not run windows (why scan a linux file system for windows viruses which do not run on Lninux ???).

The number 2 reason is false positives >>> true positives and thus I never felt the results of linux scanners was reliable.

---

### Post by dan171717 on 2007-07-20
i will hope it is a false for now because i am tyred and want to go to bed

i will have another look at it tomowrow

---

### Post by strabes on 2007-07-21
By the way, what don't you like about google?

---

### Post by dan171717 on 2007-07-21
because google buy and sue everything. at first they were a search engine then they were a satellite imaging then a picture editor.

---

### Post by davedumas0 on 2007-10-18
it might be a false positive check this 1 [http://ubuntuforums.org/showthread.php?p=3560872&posted=1#post3560872](http://ubuntuforums.org/showthread.php?p=3560872&posted=1#post3560872)

---

