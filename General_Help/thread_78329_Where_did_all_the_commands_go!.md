---
title: "Where did all the commands go?!"
date: 2005-10-18
forum: General Help
---

### Post by Svip on 2005-10-18
After I installed Breezy, I suddenly don't have commands I use reguarly!

Commands such as mail, make, etc.

Is there an **apt-get install** to install all those?

I tried **base**, but it says I already have that.

Sorry if I haven't searched for this. :\ I am just really confused.

---

### Post by _Pete_ on 2005-10-18
[QUOTE=Svip]After I installed Breezy, I suddenly don't have commands I use reguarly!

Commands such as mail, make, etc.

Is there an **apt-get install** to install all those?

I tried **base**, but it says I already have that.

Sorry if I haven't searched for this. :\ I am just really confused.[/QUOTE]

for make (and compiling):

apt-get install build-essential

for mail:

apt-get install mailx

Also you might want to check this out when considering terminal based mail program:

[http://www.washington.edu/pine/](http://www.washington.edu/pine/)

---

### Post by matthias_k on 2005-10-18
> for make (and compiling):

apt-get install build-essential

No. build-essential is only needed for creating debian packages; it just happens to depend on make, but it would be silly to install it just to have GNU make installed, too. If you only need make, then just install the GNU make package (apt-get install make). Simple as that.

---

