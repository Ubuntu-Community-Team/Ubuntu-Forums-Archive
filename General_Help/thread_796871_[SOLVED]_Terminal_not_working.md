---
title: "[SOLVED] Terminal not working"
date: 2008-05-16
forum: General Help
---

### Post by Nampla on 2008-05-16
I tried to do an rsync to a remote machine on my lan and it seemed to hang.  I killed the process and now unable to sign into the remote machine.  I can ssh in as root or any other user, but cant su to me or sign in as me.  I can Nomachine into it and have full GUI but then the terminal app wont work either.  The curser blinks with no words nothing.  I have tried to reboot no luck. What did i do wrong and how can i fix it?

---

### Post by Mr A Mouse on 2008-05-16
How odd. Did you reboot the remote machine?

---

### Post by Nampla on 2008-05-16
Yes 2x and nothing.  when i try to ssh as me into it, it hangs.  I can ssh into it as root and any other user and it is fine, but then i cant su into me cuz it will just hang again.  I have tried replacing my .bashrc file and that didnt help. I am totally stumped here

---

### Post by Mr A Mouse on 2008-05-16
Can you su to a different user? (assuming there's a different user to su to)

---

### Post by bodhi.zazen on 2008-05-16
what rsync command were you using ?

Does your user's /home exist ?

---

### Post by Nampla on 2008-05-16
yes my /home exsists.  I can nomachine into the compter, and everything seems to be running fine.  I just cant seem to use the terminal, or shell.  I can ssh into the machine as root or any other user and everyting is fine.  If I try to su at that point it just hangs. If I try to ssh with my user name it will get past all the way to just before the prompt and hang without any promt.

I was using rsync -av /docs/to/bak/up me@myip:/place/to/go

---

### Post by Nampla on 2008-05-17
I found it was a bad .basrc file.  Replaced it and everything great.

---

