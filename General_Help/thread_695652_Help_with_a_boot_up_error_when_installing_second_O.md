---
title: "Help with a boot up error when installing second OS"
date: 2008-02-13
forum: General Help
---

### Post by seventhc on 2008-02-13
Hi,
I am having the weirdest problem, I have a Sony VAIO VGN-NR160E. As soon as I got it I made the backups of vista then formatted it to install Ubuntu. I can install Ubuntu and BackTrack together just fine, but ideally I would prefer to have a dual boot between FreeBSD and Ubuntu.
Problem:
Whenever I go to install FreeBSD I get an error 
[I](RAM Parity Error)
panic: non maskable trap
system will reboot in 15 seconds
uptime 1s[/I]
I have tried different versions, 4.11, 5.3, 6.3, 7.0 FreeBSIE
I also can't install SOLARIS 10
I have 2 sticks of RAM 512 a peice, I took swapped out each one so it was only using one at a time, same error, I looked in BIOS but there isn't a place to turn on/off parity checking.
Has anyone else ever encountered this?
Does anyone have any suggestions?
Thanks in advance. :)

(P.S) To test my backups I also reinstalled Vista, and that installs fine too.

---

### Post by apetresc on 2008-02-13
Have you tried running Ubuntu's memtest86? It should be in your grub menu already.

Just to eliminate the possibility that it is FreeBSD who is right, and everyone else just doesn't care :)

---

### Post by seventhc on 2008-02-13
I hope they care lol
I'll try that now thanks for the suggestion :)

---

### Post by seventhc on 2008-02-13
That test takes a very long time lol
when running normally it passed 7 tests I stopped that and ran option 3 which scanned BIOS (I think) That showed errors, I will run it completely tonight when I go to bed. I wanted to be online. ;)
If there are errors, is there anything I can do to correct them?
I didn't see anything in BIOS that looked like it would effect it.
Not really sure what to do, but I really want to get FreeBSD on here.
If I just run the memory test and leave it, will it test everything, or do I have to tell it what to test?I've never actually used it before.
Thanks :)

---

