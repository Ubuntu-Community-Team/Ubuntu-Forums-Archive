---
title: "I need Everest poker. It's possible using wine?"
date: 2006-11-27
forum: General Help
---

### Post by mautvleal on 2006-11-27
Hi!

I'm trying to use everest poker on edgy through wine. However, it fails: " this computer doesnt have minimum requirement to run our software"

Thanks!

---

### Post by V-ernie-R on 2006-12-08
same problem here.....

---

### Post by Chinello Cybernético on 2007-03-06
same here..

I tried to contact developers, but they don't reply me.

---

### Post by asdir on 2007-09-03
As seen on [www.winehq.org](www.winehq.org) --> Everest Poker:

>  The game does not run using plain wine. However i got it running up to the login window doing:

1. Install ies4linux.

2. Install Everest PokerClient in normal way(will crash in the end)

3. Now run by:  

cd ~/.wine/drive_c/Program\ Files/Everest\ Poker/

WINEPREFIX=~/.ies4linux/ie6/ wine Everest\ Poker.exe  


Did not work for me though. :(

The program (not wine or ie4linux, I checked that) says that the minimum hardware requirement is not met. Any idea anyone?

---

### Post by karlklammer on 2008-03-01
you need to change the windows version of wine with winecfg for example

---

