---
title: "Cannot Login - Display Issue?"
date: 2007-02-19
forum: General Help
---

### Post by mondae on 2007-02-19
I have been trying to research this for the past few days but I could not find anything.

I was working on a document in OppenOffice.  The program froze up on me and I was not able to do a bloody thing.  I did a cold reboot of the machine.  When I get to the login screen I try signing in, press enter and the screen goes black, flickers a bit and goes back to the login screen. 

I am able to sign in through the recovery terminal.  I have tried several suggestions from articles i have found but nothing worked.

Any ideas?  

Thanks

---

### Post by taurus on 2007-02-19
At the GUI login screen, press <Ctrl><Alt>F2 and see if you can log in with your username and password.  Then, post the output of this command here.

```
df -h
```

---

### Post by mondae on 2007-02-21
Hey thanks for your help.

I was being a retard.....

I had a daily backup put in place oh my /home dir.  I added around 10 GB's of data a few days prior and the backup double the used drive space and maxed out my HDD space.  I removed the backup dir and everything worked fine.

Thanks again

---

