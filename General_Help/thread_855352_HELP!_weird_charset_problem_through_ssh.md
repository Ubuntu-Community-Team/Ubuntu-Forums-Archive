---
title: "HELP! weird charset problem through ssh?"
date: 2008-07-10
forum: General Help
---

### Post by kermis on 2008-07-10
hello all,

i'm new here, and almost as new with ubuntu. :) i ran into this weird problem today, when fixing my OpenBSD up for ssh.

everythings cool now, ssh connection work (yes i actually got it work! hah) got to install screen + irssi to run irssi all the time. works perfectly no prob. but.. when i connect to the OpenBSD server the problem starts.. i loose my charset settings..

i live in finland so i need scandinavian keyboard layout all the time.. this might sound like a OpenBSD problem, but wait.. 

1) on my OpenBSD server, scandinavians work (set to sv)
2) when connected through putty @ winxp, scandinavians work
3) when connected through ssh @ ubuntu terminal, scandinavians letters come question marks + blocks!

so it seems, that when i connect to my shell via ssh from Ubuntu, Terminal looses my scandinavian layout after i get connected to the host... in irssi everyone else BUT ME, can see my scandinavians when i enter them. i also cannot see anyone elses scandinavian letters. when i connect to my OpenBSD server using putty.. from WinXP, everything works. also logged in on the server as a superuser or my account, works.. so i got to the point, that it could be a Ubuntu problem after all?

what about scandinavian settings on different os's?
- in Ubuntu, works and set to finnish
- in WinXP, works and set to finnish
- in OpenBSD, works and set to swedish

in any other combination the charset works, but the ssh connection via terminal in Ubuntu.. i've tried several terminals on ubuntu, but no solution.. the problem exists as long as i stick in to ubuntu..

any help, please?! :confused:

---

### Post by kermis on 2008-07-11
I've figured out, that the problem is between OpenBSD using ISO and Ubuntu UTF-8.. Is there any chance i could change Terminal charset to ISO, to make it working with OpenBSD..?

Anyone..? :confused:

---

