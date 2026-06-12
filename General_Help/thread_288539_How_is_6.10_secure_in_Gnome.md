---
title: "How is 6.10 secure in Gnome???"
date: 2006-10-30
forum: General Help
---

### Post by phinn on 2006-10-30
Okay so I log into Gnome in a newly installed Ubuntu 6.10.

Now normally you have to enter your password for sudo, synaptic, and any number of other things you would like to do that could compromise your computer.

I goto:
System -> Administration -> Users and Groups

And I can change my password in there to ANYTHING without entering my previous password and BOOM. Someone has control over my box????

What is going on here?  How is this secure Ubuntu? ](*,)

---

### Post by 23meg on 2006-10-30
Could that be because you entered your password for another administrative task less than 15 minutes ago (the standard timeout)? Reboot and try doing the same, and see if it asks for your password.

---

### Post by phinn on 2006-10-30
Well if I try and use Add/Remove programs or Synaptic is asks for my password. If I try and use Users and Groups it doesn't ask me for anything, and lets me change anything I want.

I will try rebooting too.

---

### Post by seatea on 2006-10-30
I'm glad you posted this. I have just noticed the same thing today. Some of the programs in Administration ask for passwords, others do not. Synaptic does, but, as you mentioned, Users and Groups does not nor does Update Manager. I thought something had gone afoul in my installation, so I reinstalled many gnome applications and packages. Didn't make  any difference. I sort of wish I had not done Edgy as there  are other problems, such as no splash screen, that bug me. Have you noticed the  difference in adding  repositories  to Edgy with  Synaptic? The Edgy Guide does not even have the correct instructions  on  how to add sources with the new repository gui in  Synaptic. Also, it appears the backports are not  working. I  don't understand why  they didn't keep  Edgy as beta. Hopefully things will work out over the  next few days -weeks.

---

### Post by phinn on 2006-10-31
This is a definite security problem in Edgy that should be fixed. I've tested this on a Ubuntu 6.06 box (which are a hot commodity right now) and you must enter the password every time.

Any Ubuntu coders listening???

---

### Post by seatea on 2006-11-01
Does this qualify as a bug?

---

