---
title: "gvfs/nautilus ftp connect to a server in hardy"
date: 2008-06-06
forum: General Help
---

### Post by matcram on 2008-06-06
Hi all,

i am a bit confused since my installed Hardy on my macbook. I used gutsy during my day to day job as a webdevelopper. I used to store the ftp locations and edit my websites via gedit via the "connect to a remote server" button in the menu.

It was pretty nice until i installed hardy. Now i can't connect anymore on any ftp location. SSH works fine thought.

I searched the forums for a possible cure to my problem but i don't really know if it's a known bug shared by others or if i have to digg on my side ?

So the question is : Are you able to connect to remote ftp locations like how you did under gutsy ? Or is it a known problem and gvfs still isn't ready for ftp ? Should i go back to gutsy to get this feature back ?


Thank you in advance to anyone that will take the time to answer my questions.

Matthieu.

---

### Post by matcram on 2008-06-06
What confuse me is that i don't seem to find a lot of threads about it. It's like a few people used this feature...

By the way it was very convenient with gutsy. Just add your remote locations and they were mounted like "local drives" they were accessible by gedit for example. VVVVVVVVVVeeeeeery usefull for me.

---

### Post by mahfiaz on 2008-06-07
I think its better to go back. gvfs was changed lately and seems far from being finished.

Edit: one more thing - if you can happily cope with bluefish, you don't have to. When drag n' dropping files from nautilus to bluefish, opening and saving of files works well.

---

### Post by ftmichael on 2008-06-26
See [http://ubuntuforums.org/showthread.php?t=554555](http://ubuntuforums.org/showthread.php?t=554555) . The advice in that thread fixed the problem for me, but interestingly it didn't help on my boyfriend's computer at all, even though we have the same setup. Still trying to figure out what the issue is on his system.

Michael

---

### Post by Ashly on 2008-11-16
I'm totally going to gravedig this thread because the same thing happened to me. One fateful upgrade, FTP support just tanked.

[LIST]
[*]Using the “connect to” dialog
[*][ftp://example.org/](ftp://example.org/) (where authentication is required)
[*][ftp://ashly@example.org/](ftp://ashly@example.org/)
[*][ftp://ashly:password@example.org/](ftp://ashly:password@example.org/)
[/LIST]

All of the above die with the following error:
[INDENT]
**Could not display "ftp://example.org/".**
Error: Invalid reply
Please select another viewer and try again.[/INDENT]


I can't find the bug report for this — is there one? The above suggestion didn't work, and I'm climbing the walls looking for a fix because I really don't want to go looking for a new OS.

I too am a web developer and this is one of a certain little cluster of bugs that's making my Ubuntu install a living hell.

---

