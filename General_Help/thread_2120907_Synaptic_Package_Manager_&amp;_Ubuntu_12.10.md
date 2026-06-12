---
title: "Synaptic Package Manager &amp; Ubuntu 12.10"
date: 2013-02-27
forum: General Help
---

### Post by kb7ypf on 2013-02-27
Hi All-

Just installed Ubuntu 12.10 the other day and found the Ubuntu software center to be inadequate so I installed Synaptic Package Manager.  To the point it will now work for some reason.  

Does anyone know how to get it working?  Appreciate you reading and maybe posting a fix and why Ubuntu did not incorporate in this distribution.

BTW, if you know of another Package Manager I would surely look at it.  Thanks.  :p


kb7ypf

---

### Post by oldos2er on 2013-02-27
Does it give an error?

Can you post the output of these commands please? ```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by kb7ypf on 2013-02-27
Ann, I tried that.  I should mention the Synaptic Manager Package was installed by the Ubuntu Software Center.  Synaptic, after installed, will open and I can select things to install, de-install, and remove.  After selection the "Apply" Check Mark is grayed out.  

Any Ideas?

kb7ypf

---

### Post by oldos2er on 2013-02-27
You don't have both the Software Center and Synaptic open at the same time, do you? Normally the system wouldn't let you do that.

If you start Synaptic in a terminal with ```
gksudo synaptic
``` can you apply any changes?

---

### Post by tdockery97 on 2013-02-27
> **kb7ypf said:**
> Ann, I tried that.  I should mention the Synaptic Manager Package was installed by the Ubuntu Software Center.  Synaptic, after installed, will open and I can select things to install, de-install, and remove.  After selection the "Apply" Check Mark is grayed out.  

Any Ideas?

kb7ypf

I had the same problem when I tried out 12.10.  The problem you mention came when I tried to start Synaptic from the launcher.  I fixed it by unlocking from launcher, then running it from the app menu.  After the first time doing that you should be able to drag it back to the launcher and it will work as it should.




Running Ubuntu 12.04.2

---

### Post by kb7ypf on 2013-02-27
tdockery97, thanks, it worked like a charm.  My hat is off to you.


kb7ypf

---

### Post by mc4man on 2013-02-27
See you have resolved but just to note - 
It appears that Software center will add the 'non-administrative' (kde) version of synaptic to the launcher - you'd know because it should tell you when starting - see screen
You want the one shown in 2nd screen (authenticate
Certainly a bug of some sorts

(-  the best way to run from terminal in 12.04 on is this (current user auth method
```

synaptic-pkexec
```
 or
```
pkexec synaptic
```

---

