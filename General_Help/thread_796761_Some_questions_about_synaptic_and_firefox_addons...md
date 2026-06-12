---
title: "Some questions about synaptic and firefox addons..."
date: 2008-05-16
forum: General Help
---

### Post by El_Belgicano on 2008-05-16
Getting some weird things with Synaptics, I compiled some programs (sonata 1.5.1, conky 1.5.1, transmission 1.20) but synaptics keep them tracked as sonata 1.4.2, conky 1.4.9, transmission 1.11. Is it due to the fact I compiled them myself or is there anything wrong? :confused:

Also I can't install firefox addons or even remove the ones installed, should I reinstall FF? (I migrated the account from my win partition)

Thanks in advance :)

---

### Post by Bakon Jarser on 2008-05-16
> **El_Belgicano said:**
> Getting some weird things with Synaptics, I compiled some programs (sonata 1.5.1, conky 1.5.1, transmission 1.20) but synaptics keep them tracked as sonata 1.4.2, conky 1.4.9, transmission 1.11. Is it due to the fact I compiled them myself or is there anything wrong? :confused:

Also I can't install firefox addons or even remove the ones installed, should I reinstall FF? (I migrated the account from my win partition)

Thanks in advance :)

First the firefox problem.  I've heard other people have had this problem and I think they fixed it by deleting their .mozilla file in their home folder.  Make sure you have view hidden files turned on and make sure you back up your bookmarks before trying this.

Since you compiled those programs yourself you didn't get them from synaptic.  The synaptic package information only changes when one of the programs is updated from one of the package managers.  Ubuntu doesn't update to the latest versions because they want stability.  For the most part they only provide security updates.

---

### Post by El_Belgicano on 2008-05-17
Then do I have two different versions installed and may I remove one of them or do I need to keep te "old" synaptic version?

---

### Post by Xiong Chiamiov on 2008-05-17
You don't need 2 versions of the same program installed.

When you're compiling from source, you can also use the command "checkinstall" instead of "make", and that will create a .deb and install it into apt, so that you can remove it through Synaptic.

---

### Post by El_Belgicano on 2008-05-17
And how do I remove a self-compiled program from my installation to go back to the version in the repos?

---

### Post by Xiong Chiamiov on 2008-05-17
Just the same as installing, but instead of typing "make install", you enter "make uninstall".  If you still have the source folder, you shouldn't have to run configure and make again, just navigate to there and
```

sudo make uninstall

```
I keep a folder in my home directory for all the apps I compile from source now so I can easily uninstall them if I need to.

---

### Post by El_Belgicano on 2008-05-17
> **Xiong Chiamiov said:**
> ...I keep a folder in my home directory for all the apps I compile from source ...

I'll keep that in mind, :)

and what about apps I installed with "sudo python setup.py install", do I just replace "install" with "remove" or "uninstall"?

---

### Post by El_Belgicano on 2008-05-17
BTW, the FF addons are working now (see post #2 above) ...

---

### Post by Xiong Chiamiov on 2008-05-17
> **El_Belgicano said:**
> I'll keep that in mind, :)

and what about apps I installed with "sudo python setup.py install", do I just replace "install" with "remove" or "uninstall"?
Hmm, with those it seems that they wrote a python script to install things.  You'll have to check with the devs or the documentation (or dive into the script and see what they did and try to reverse it).

---

### Post by El_Belgicano on 2008-05-23
> **Xiong Chiamiov said:**
> Hmm, with those it seems that they wrote a python script to install things.  You'll have to check with the devs or the documentation (or dive into the script and see what they did and try to reverse it).

looking for some documentation, I don't know a lot about python so it'll be hard to understand (but i'll try :)) ...

---

### Post by El_Belgicano on 2008-06-02
Another compiling question: To compile some options you need the **name**-dev packages, can I remove them after compile and keep the **name** package, or do I still need both?

---

