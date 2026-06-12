---
title: "Tried installing Beryl 0.1.3 through Synaptic"
date: 2006-12-02
forum: General Help
---

### Post by elbowgeek on 2006-12-02
I probably don't deserve help for trying to install the beta version of Beryl, but if y'all can help me decode a couple of error messages related to the install that would be grand.

I've got Synaptic to recognize and list Beryl 0.1.3, but when I go to select Beryl in the list I get the error:

> beryl:
 Depends: emerald but it is not going to be installed or
 	aquamarine but it is not going to be installed or
 	heliodor but it is not going to be installed or
 	compiz-gtk  but it is not installable
 Depends: beryl-manager but it is not going to be installed

I kinda figure it means that it needs beryl-manager to be installed as well, but selecting the beryl-manager yields the following message:

> beryl-manager:
  Depends: libatk1.0-0 (>=1.12.1) but 1.11.4-0ubuntu1 is to be installed
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 is to be installed
  Depends: libcairo2 (>=1.2.4) but 1.0.4-0ubuntu1 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.10.3) but 2.8.20-0ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.14.5) but 1.12.3-0ubuntu3 is to be installed
 Depends: beryl but it is not going to be installed


If anyone can shed light on the errors above and maybe how to resolve them I'd much appreciate it.

Cheers

---

### Post by LLRNR on 2006-12-02
Are you on Dapper or on Edgy ? Also, what kind of video card do you have ? Another thing... for myself, I avoid installing tricky things through Synaptic/Adept...

LLRNR

---

### Post by elbowgeek on 2006-12-02
I'm using Dapper with an older Nvidia GeForce2 MX/MX 400 card.


Yeah, I definitely shouldn't have tried through Symaptec, but 'tis done.  I'll certainly do it manually in future, but I'm only using this system as a test bed for beta software and general experimenting; I'm basically doing everything I can to break it so I get to know it better, kinda like when I was starting out.  I learned DOS inside and out through this sort of experimenting.

Thanks!

---

### Post by LLRNR on 2006-12-02
I love this part... :lol:
> I'm basically doing everything I can to break it so I get to know it better

I installed Beryl 0.1.1 from [here](http://doc.gwos.org/index.php/BerylOnEdgy), but this is an *Edgy* guide, and then upgraded to 0.1.2 through a message I found on the Beryl forums. For me it just worked, with nVidia also.

For Dapper I'd suggest to try something from [here](http://doc.gwos.org/index.php/EyeCandyDapper) as well.

Of course there's no guarantee, I actually broke my X Server once when attempting a Beryl install back when I was using Dapper, but I was using another guide, not the one I pointed to here.

Good luck (and be sure not to wreck everything just yet, there's still much to do !),

LLRNR

---

### Post by elbowgeek on 2006-12-02
Many thanks again - I'll check the sites out now :-)

Cheers

---

