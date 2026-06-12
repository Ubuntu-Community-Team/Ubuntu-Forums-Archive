---
title: "Only guest account available"
date: 2016-03-06
forum: General Help
---

### Post by d676PPF on 2016-03-06
I just installed Ubuntu 15.04 from a mini ISO on a CD as my windows 10 system was messed up and this is all I had in order to use my computer, so I installed using the entire HDD (finally liberated from Windows!!) and it's finally all set up despite some issues with errors during installation. I'm on ubuntu desktop however I only have an option for a Guest account. Therefore I can't log in to an account through which I can save my information. I've tried CTRL+ALT+F1 and logged in with the credentials I used during setup (triple checking they are correct as I wrote them down as I typed each character) and nothing is recognized. How would I be able to set up a user account when the only account I can access is a guest account? Many thanks. :confused:

---

### Post by goofprog on 2016-03-06
I am not sure if you can because Linux moved far from the super user mode.  You would have to force boot to super user mode and create an account from there.  I am far from being a Linux guru so I am only talking from hands on experience.  So maybe...
How to boot to super user mode from ubuntu 15.04 may point you to the right direction.

---

### Post by d676PPF on 2016-03-06
> **goofprog said:**
> I am not sure if you can because Linux moved far from the super user mode.  You would have to force boot to super user mode and create an account from there.  I am far from being a Linux guru so I am only talking from hands on experience.  So maybe...
How to boot to super user mode from ubuntu 15.04 may point you to the right direction.

fixed. Booted into recovery mode, dropped to root shell:

adduser username -m -s /bin /bash
passwd username
adduser username sudo

and all fixed! Thanks for the advice.

---

### Post by goofprog on 2016-03-06
Yup, as a guess I think recovery mode IS super user mode.

---

