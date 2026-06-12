---
title: "Boot issue"
date: 2014-03-09
forum: General Help
---

### Post by Andi_GreyScale on 2014-03-09
I decided to switch my driver from the generic one to the recommended one.  After updating, I restated but now I either get stuck on the black screen after choosing which version of Ubuntu I want or on the purple screen. 

No idea what to do. Typed this up from my phone.

---

### Post by r.stiltskin on 2014-03-09
> **Andi_GreyScale said:**
> I decided to switch my driver from the generic one to the recommended one.

Hi Andi,

That's a little vague.  Need more details.  Which "generic one", which "recommended one" (recommended by whom?), and which version of Ubuntu?  It would also be helpful to know exactly which graphics card (mfr and model) you have.

And also try to describe as precisely as possible exactly what you did.

---

### Post by Mark Phelps on 2014-03-09
I'm guessing you were using the generic video drivers (radeon?) and use Additional Drivers to install Restricted Drivers (fglrx or fglrx-updates)?

Having to guess leaves us in a bad situation of not being able to provide detailed help.

Since you can't boot into your system, you will need to do the following:
1) Boot from Ubuntu install media (CD/DVD/USB stick)
2) Once at a desktop, open a terminal and enter "lspci" (without the quotes).  Look for the line containing "VGA" -- and post that info back here.

Also, need to know which version of Ubuntu you are running.

---

