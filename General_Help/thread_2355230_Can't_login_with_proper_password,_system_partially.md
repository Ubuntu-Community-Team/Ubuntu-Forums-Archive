---
title: "Can't login with proper password, system partially crashes"
date: 2017-03-10
forum: General Help
---

### Post by zklaozog on 2017-03-10
I had a password.  
I needed to change that password.  
I went as root, wrote "passwd myname". And wrote my password.  
I received something about "Segmentation Error".  
I decided to ignore it (on the other hand it was probably very stupid).  
It kicked me out "Password not altered".  
And I attempted to reenter password (again "passwd myname" etc.). Which worked.  
I "quit" root access in terminal, then I "sudo su" and I verified that I've written this password correctly.  
And yes, the password got updated, then I went on with my life.  
And then I had to move. I turned off my laptop.  
At home, I opened my laptop. Input the password, and Linux crashed (partially).  


I use Plasma KDE. I get regular account screen.   I go to my account, fill in my latest password. AND, it crashes. The time doesn't go onward (I checked with phone, literally 5 minutes delay not a single change), can't select anything, only mouse is moving (but doesn't react on hover, clicks or anything, and its a cross (which means "wait" or "loading")).


I have some important stuff on this Linux, and I've encrypted my drive through options during installation. So I can't really draganddrop.  


I can't login, I don't know what happened. My password consists of capital letters, minor letters, "/" and numbers. It would be cought by regex `[a-zA-Z0-9/]` It's length is about 15 characters.  


Help. How did this happen? How can I fix it?  


There seem to be solutions but they seem to far from mine.  
 - I didn't update Nvidia drivers. And even then I have integrated chip. If one would fail, wouldn't the other pick it up?  
 - I didn't install packages at that time. And the time I did, already did couple full restarts, so why wouldn't it crash back then, but now?


I always use latest version of Ubuntu (it tells me to update, so I update) and switching versions in grub doesn't change anything.


It seems to be everyone's issue (I get tons of suggestions with people of same problem, but their solutions are different and do not apply to me, as far as I know).

---

