---
title: "KDE Packages"
date: 2004-11-13
forum: General Help
---

### Post by larry on 2004-11-13
I am a newbie and I am considering to give Ubuntu a try this Xmas, when I will have some time to toy around with it.
I do not understand much the choice of the sudo feature instead of the usual root and I read in the Ubuntu site that if for instance you try installing k3b using sudo you can seriously compromise the system. Somewhere else I read this is a general feature of all of the KDE applications, which are unsupported by Ubuntu.
Is it really so? Is it really easy to damage Ubuntu by using sudo rather than root when dealing with KDE packages?
Many thanks
Larry

---

### Post by HungSquirrel on 2004-11-13
[QUOTE=larry]I am a newbie and I am considering to give Ubuntu a try this Xmas, when I will have some time to toy around with it.
I do not understand much the choice of the sudo feature instead of the usual root and I read in the Ubuntu site that if for instance you try installing k3b using sudo you can seriously compromise the system. Somewhere else I read this is a general feature of all of the KDE applications, which are unsupported by Ubuntu.
Is it really so? Is it really easy to damage Ubuntu by using sudo rather than root when dealing with KDE packages?
Many thanks
Larry[/QUOTE]
 I don't know if installing a KDE package will compromise the system, but I do know you don't have to keep using sudo if you don't want to.  If you do *sudo passwd root*, you unlock the root account and set its password, therefore meaning you could use su as normal if you wanted.  (By default, the root account is not allowed to login, so the Ubuntu sudo method is secure.)

That's what I did my first two weeks in Ubuntu land, but this sudo thing has kind of grown on me.  8)

---

### Post by larry on 2004-11-13
Thanks, I was simply worried about the advice they give in this site about installing k3b (which I like quite a lot) and I thought there could be some dangers involved with KDE applications in general.
Larry

---

### Post by ~zoey~ on 2004-11-13
I installed and am running kde with no problem.

In order to be able to do that it is necessary to uncomment universe.  Then I used apt-get install kde and it installed in a little less than an hour [with DSL].

I run synaptic with sudo synaptic in kde because it asks for a root password if I just click on it

I haven't tried to run k3b yet, but I think that it should work.  It might take sudo to be able to run it.

I think that you should give ubuntu  a try.  It is a great distro!

zoey   :smile:

---

