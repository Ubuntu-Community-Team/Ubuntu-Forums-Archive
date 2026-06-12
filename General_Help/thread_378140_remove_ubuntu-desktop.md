---
title: "remove ubuntu-desktop?"
date: 2007-03-06
forum: General Help
---

### Post by dryder on 2007-03-06
Hi,

Please can the _correct_ answer be made a sticky somewhere? (No offense to all the many willing helpers by my underlining).

In trying to solve a few problems (e.g. adding synaptic package lpr to see if efax will then auto print received faxes) or just to learn more about some packages, or to uninstall tried and unwanted packages, synaptic packager may come up with "this will remove ubuntu-desktop".

What does this mean exactly?

I have googled and searched these forums and the opinions are contradictory. "It is only a meta package and safe to remove - nothing really happens", "if you remove it you will not be able to upgrade", "if you reinstall ubuntu-desktop it will reinstall all the packages associated with it, the old Firefox, Open Office ...".

I would suggest that that these differing opinions leave newbies and many experienced people confused - and very wary.

Is there a definitive answer and if so, could it be made a sticky or a reference note?

Desperate for knowing the answer,

David

---

### Post by FIONEX on 2007-03-06
I dont think that you can install a version that's older than the one currently installed on your computer.  However, I've never ran into the upgrade problem they speak of.  Must be something minor.

---

### Post by po0f on 2007-03-06
dryder,

ubuntu-desktop represents all the base packages that *should* be installed on a default Ubuntu installation.  If you are using Edgy or any previous release, it is safe to remove.  Whoever said you can't upgrade if you don't have this package installed is mistaken.  You can upgrade just fine.  Also, as you have found, when you reinstall ubuntu-desktop, it brings all its dependencies back with it.

---

### Post by aysiu on 2007-03-06
You *can* upgrade without it, but you'll just get more up-to-date versions of the packages you already have installed. You won't get any new packages or replacement packages.

It's recommended you keep it installed for a smooth upgrade.

---

### Post by dryder on 2007-03-06
Hi,

Thanks for replying. I have not 'dared' yet to try anything that gives me this message.

May I ask, just what is it removing and if it doesn't matter (I'm not arguing - I don't know) why tell me? Presumably it is telling me something that really matters?

If I install something that removes it,* such as* lpr, what happens to lpr when I reinstall ubuntu-desktop?

I'm on Ubuntu 6.10.

Many thanks,
David

---

### Post by aysiu on 2007-03-06
Think of *ubuntu-desktop* as a pointer or label.

This analogy isn't perfect, but think of it as a six-pack of beer. This particular six-pack has a label attached that says "Six cans of beer." If you remove one of those cans of beer, it's no longer six cans of beer. It's five cans of beer. If you want to call it six cans of beer again, you have to add a can back in.

*ubuntu-desktop* is the label that describes "everything that comes with a default Ubuntu installation." So if you remove one of those programs, you no longer have everything that comes with a default Ubuntu installation. You have everything minus... whatever you removed. Reinstall *ubuntu-desktop*, and you have all the default programs again.

It's recommended you keep it installed for upgrades because Ubuntu often adds and/or replaces packages. For example, in Hoary, there was no menu editor installed with Ubuntu. So if you wanted to edit the menus, you had to install a menu editor yourself. With Breezy, there came a menu editor called *alacarte*. With Breezy, there wasn't a point-and-click way to install .deb files. With Dapper, there came an application called *gdebi* that allows you to a double-click way to install .deb files.

If you have *ubuntu-desktop* installed when you upgrade, you will get the new packages. If you don't have it installed, you'll just get newer versions of whatever you already had installed.

---

### Post by po0f on 2007-03-06
aysiu,

Do you mean to say it is only useful to have ubuntu-desktop installed when doing a release upgrade, ie Dapper to Edgy?  There are different kinds of "upgrades", and I think it needs clarifying here.

---

### Post by aysiu on 2007-03-07
> **po0f said:**
> aysiu,

Do you mean to say it is only useful to have ubuntu-desktop installed when doing a release upgrade, ie Dapper to Edgy?  There are different kinds of "upgrades", and I think it needs clarifying here.
Yes, that's exactly what I'm saying (and Dapper to Edgy is a good example).

Of course, if you think it's worth the trouble to uninstall something only to have to reinstall it later before the upgrade... and then uninstall it again after the upgrade... then you can remove *ubuntu-desktop*.

The other option, which honestly makes a lot of sense for the clutter-phobic, is to just remove *ubuntu-desktop* and do a clean reinstall (instead of an upgrade) when a new release comes.

---

### Post by dryder on 2007-03-07
aysiu,

Thanks for the explanation.

I guess I'm left with asking, why would installing lpr (just one package) mean that ubuntu-desktop has to be uninstalled?

Surely leaving it installed would leave the label of what is to be updated the same - and I would not expect lpr to be updated in an upgrade because it isn't on the 'label' nor in the six pack the label is attached to.

It implies (just as one example) that adding lpr affects how many cans of beer are really there even though the label would say otherwise. Are you saying adding these things remove 'cans of beer'?

Many thanks,
David

---

### Post by aysiu on 2007-03-07
I don't know.

My guess is that installing *lpr* also removes something else that is part of *ubuntu-desktop*.

---

### Post by po0f on 2007-03-07
dryder,

Sometimes, packages conflict with one another.  When you install a program that conflicts with an already installed one, the latter is removed.  In your case, the program removed was a dependency of ubuntu-desktop.

---

