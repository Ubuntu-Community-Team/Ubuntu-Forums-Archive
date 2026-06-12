---
title: "music and me ... :("
date: 2005-10-10
forum: General Help
---

### Post by online14230 on 2005-10-10
H there!
Ive installed Ubuntu and it runs beautifully .. 
Problem is though, I cant seem to play any music. I keep getting "Cannot open location for writing", no matter what I try to play.
Also, I downloaded some "codecs" but I seem to have lost them, and the site I got them from. Anyone have any Ideas where I can get them from, again? Those I did have, I tried installing but I need to be logged in as root (priviledges...). Problem is, I ONLY created 1 account and I only have that passwd. help?
Please consider that this machine cannot be connected to the net. No NIC, no modem (winmodem not recognised :( )
Please dont tell me to reinstall, as THAT takes forever! read the thread about my installation method ...... funny really!!
Brendan aka Online14230

---

### Post by Moha on 2005-10-10
first of all to get root acces just go to your terminal and type: sudo -s
after that you will be prompted for the root password, just give the password of your current account (or if you have a root passwd just give that one). don't forget to type "exit" after your done with the root account ;).
if you are not familiar with the terminal you could also try the program "run as different user" located in your (if you are using kde) kde menu --> System.
just type the command of the program (usually the name of the program) and select root. after that give the passwd of root. as for the music issue it seems you don't have permission... are your music files on a windows partition or on a different partition then your linux one?

i hope i was helpfull (i am also new to linux).

---

