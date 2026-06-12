---
title: "Cannot remove files from trash [Resolved]"
date: 2007-02-24
forum: General Help
---

### Post by olavjunior on 2007-02-24
Somehow, the catalog windows has been copied to the trash! I don't have a clue on how...

So there it is, taking up all that space... I tryed to delete, and I get the message that I'm not the owner, so therefor... you know. They stay. 

Any help?

---

### Post by taurus on 2007-02-24
Try something like

Applications -> Accessories -> Terminal
```
cd ~/.Trash
sudo rm *
```

---

### Post by aysiu on 2007-02-24
While taurus' advice will work, the words *sudo rm* shouldn't really be typed into the terminal--for safety's sake.

It's much safer to do Alt-F2 ```
gksudo thunar
``` and then go to /home/olavjunior/.local/share/Trash/ and delete what's there.

Alternatively, if you prefer the terminal, you can just make sure you're the owner of everything in your home directory: ```
sudo chown -R olavjunior:olavjunior /home/olavjunior
``` and then empty your trash.

**P.S.** Your profile says you're a Xubuntu user--that's why I assumed your trash was /home/olavjunior/.local/share/Trash/ instead of /home/olavjunior/.Trash

---

### Post by olavjunior on 2007-02-25
First, thanx alot! Great answers. 
But sadly, none of the above advises worked for me:( 

I get the error: "you don't have rights to change the origin" (or something like that, I'm norwegian)

And my trash is at home/olavjunior/.trash so I guess I'm not an xubuntu user :D I'm kinda  confused about all the ubuntu-versions.. I  guess I have plain ubuntu! Gonna change my profile. (What's the differense between ubuntu and xubuntu?)

---

### Post by olavjunior on 2007-02-28
NOONE knows the soulution to my problem? :(

---

### Post by ~LoKe on 2007-02-28
Alt+F2
```
gksudo nautilus ~/.Trash
```
You'll be in the file browser as root, so if you can't delete it, then something's wrong.

If that doesn't work, in the terminal type:
```
ls -la|grep ~/.Trash
```
And tell us what it says.

---

### Post by olavjunior on 2007-03-03
> **~LoKe said:**
> Alt+F2
```
gksudo nautilus ~/.Trash
```
You'll be in the file browser as root, so if you can't delete it, then something's wrong.

If that doesn't work, in the terminal type:
```
ls -la|grep ~/.Trash
```
And tell us what it says.

Hey! This worked! Very useful, thank you very much :)

---

### Post by meer1977 on 2008-04-07
Hi ! first to all sorry when i interput but i got the same problem and i do what (---aysiu----) say gksudo thunar....its work thankx...

---

