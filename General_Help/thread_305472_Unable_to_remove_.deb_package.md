---
title: "Unable to remove .deb package"
date: 2006-11-23
forum: General Help
---

### Post by kamillozo on 2006-11-23
I can't find any solution for removing kav4ws package installed via apt-get. Problem is that all files and folders created during installation of this package were manually deleted from disk (ouch!).

I've tried different tricks to remove it including:
#dpkg --configure -a
#apt-get - f install

I've also used -f -m options with apt-get remove but it doesn't help.
At the end I get following messages:
Configuring kav4ws (5.5.19) ...
Can't open perl script "/opt/kaspersky/kav4ws/lib/bin/setup/postinstall.pl": No such file or directory
update-rc.d: /etc/init.d/kav4ws: file does not exist
dpkg: b&#322;&#261;d przetwarzania kav4ws (--configure):
 podproces post-installation script zwróci&#322; kod b&#322;&#281;du 1
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 kav4ws
E: Sub-process /usr/bin/dpkg returned an error code (1)

It ends like that everytime I try to install or remove any package.
Got any ideas how to remove kav4ws?

---

### Post by CatKiller on 2006-11-23
Have you tried reinstalling it and then removing it in the sensible way?

---

### Post by kamillozo on 2006-11-23
You mean:
sudo apt-get --reinstall install kav4ws

Got the same errors when I run this command.

---

### Post by CatKiller on 2006-11-23
I was thinking more

sudo aptitude install kav4ws
sudo aptitude purge kav4ws

but your way might be better anyway. I can't think of anything else. Sorry.

---

### Post by CatKiller on 2006-11-23
Ah. Actually, you said you used a .deb file. You could also try dpkg -i *nameofdebfile*.deb if you still have it. Then try removing it again.

---

### Post by kamillozo on 2006-11-23
> **CatKiller said:**
> I was thinking more

sudo aptitude install kav4ws
sudo aptitude purge kav4ws

but your way might be better anyway. I can't think of anything else. Sorry.

Still nothing - printing the same errors.

I will try to install .deb package as you say and see if it helps.

---

### Post by kamillozo on 2006-11-23
Done! :D 

First I must say that I've made a mistake saying that kav4ws was installed via apt-get (not saying that removing package files manually was idiotic mistake).

After many combinations I've managed to get to state in which system printed:
"Unknown error:
'exceptions.SystemError' (E:The package kav4ws needs to be reinstalled, but I can't find an archive for it.)"

As far as I don't know any method of telling apt-get how to use and install a local .deb package I had to find another solution. And I've found it.

Knowing that all files, folder and registries created by kav4ws were deleted I made what follows:

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
sudo mcedit /var/lib/dpkg/status
I've erased all section related to package kav4ws
saved changes
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update

Now everything is allright. Thanks for help CatKiller!

---

### Post by evilc on 2006-11-23
Have you tried in Synaptic select custom filters...package with debconf, and see if its in there, if it is you should be able to uninstall from there by r/click package & complete uninstall.


edit:  Just saw your update post.

---

