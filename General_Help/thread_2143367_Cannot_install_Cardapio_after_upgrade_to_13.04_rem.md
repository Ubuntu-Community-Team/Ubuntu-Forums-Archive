---
title: "Cannot install Cardapio after upgrade to 13.04 removed it"
date: 2013-05-08
forum: General Help
---

### Post by typos1 on 2013-05-08
I noticed that Cardapio was removed when upgrading, I ve tried to re-install it but, I get "no release candidate" error, can anyone help ? Thanks

---

### Post by monkeybrain2012 on 2013-05-08
Because it has not made a version for 13.04. Cardapio appears to be  dead.
[https://launchpad.net/cardapio/+announcement/11268](https://launchpad.net/cardapio/+announcement/11268)

You can try to get a deb from the ppa's 12.10 archive and see if it works.
[https://launchpad.net/~cardapio-team/+archive/cardapio-ppa/+packages](https://launchpad.net/~cardapio-team/+archive/cardapio-ppa/+packages)

Edited: or you can checkout the classic menu indicator if you must have a menu
[https://launchpad.net/~diesch/+archive/testing](https://launchpad.net/~diesch/+archive/testing)



BTW, I think third party software installed through ppa is supposed to  be removed during upgrade and you might get into problem upgrading if  you have installed versions of software which are not compatible with  the repo versions, installed proprietary drivers etc. Upgrade tends to  be troublesome  if your system has been modified in some ways and not  pristine enough.

---

### Post by typos1 on 2013-05-08
Thanks, I m aware of classic menu, but I prefer Cardapio. 

I had heard development had stopped, but I still thought I could instal it using ppa s, I re-enabled it after installation, but it still wont install. 

I take it that when I add a ppa it requests updates for the version of Ubuntu I m using then ? 

I m unsure of how to add the 12.10 ppa you suggested.

---

### Post by monkeybrain2012 on 2013-05-08
If you look at the ppa and go to the box "published in" you will see that it is only up to 12.10. Like I said, if you must have it, grab the .deb for 12.10 and try to install that, it may work.  

You just go to [https://launchpad.net/~cardapio-team/+archive/cardapio-ppa/+packages](https://launchpad.net/~cardapio-team/+archive/cardapio-ppa/+packages)

and download the .deb, you don't add any ppa. Click the package you want and it will open  and just download the .deb(.debs)

---

### Post by cinq on 2013-06-05
Is there a command that pops-up the classic menu? so that i can open it when i click on docky anchor?

---

