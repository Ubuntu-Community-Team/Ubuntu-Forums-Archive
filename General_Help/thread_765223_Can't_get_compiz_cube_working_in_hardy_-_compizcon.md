---
title: "Can't get compiz cube working in hardy - compizconfig-settings-manager not in repos"
date: 2008-04-24
forum: General Help
---

### Post by jonboy99 on 2008-04-24
As per the title, have just installed the new release of hardy heron, and I wanted to enable the cube (wobbly windows etc working already).

However there is no advanced desktop effects option in the menu, so I went to the repos for the usual fix - install CCSM.  However it isn't there, no mention of it at all.
Also tried apt-getting compizconfig-settings-manager but no package found.

Has it being left out of the final version??  Can't believe that, so where should I be looking?

Thanks
Jon

---

### Post by twist2b on 2008-04-24
first check your repo allowance level.
goto: System>Administration>synaptic package manager

enter your pass
then click on settings>repositories
check EVERYTHING under EVERY MENU except dont select download from cd if you dont want to, server is better to me.

then once everything is checked, goto update manager and click check. It should install now on its own..... and you should get ccsm.

if your still having troubles just let me know. Theres an error I got when using beta. I dont know if its still in the release, but theres a fix.

---

### Post by jimbo99 on 2008-04-24
For those HP/Compaq/various other laptop users, compiz may not work on your unit under 8.04 even though it worked under 7.10.  Canonical knows this and is has been reported hundreds of time, yet though what I feel is neglect, let it go.  So, if you are interested in compiz on your notebook don't plan on upgrading.

Keep in mind that not only compiz is failing.  Standard features such as sound adn wifi still don't work or are worse off than they were.

My opinion is that they have abandoned many p4 class notebooks, even those that were cash cow products for the likes of compaq / HP.

---

### Post by jonboy99 on 2008-04-24
Well, finally realised there was no main universe repo in my sources.list
Wasn't even an entry for it in synaptic, or the sources.list file - everything was checked in synaptic.  Had to type in the line myself.  Bizarre.

---

