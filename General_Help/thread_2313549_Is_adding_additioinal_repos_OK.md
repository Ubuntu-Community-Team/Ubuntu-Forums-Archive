---
title: "Is adding additioinal repos OK?"
date: 2016-02-13
forum: General Help
---

### Post by PopsTheSailor on 2016-02-13
Two things before I ask my question: 
1. This probably could go into several different forums so hopefully this is an acceptable forum for the question
2. I hope this isn't one of those long heated debates but since I'm asking for opinions, I fear it might be so I'll apologize up front for starting a threat where someone's feelings get hurt. 

OK, now my question...
Is it OK to add a repository to Ubuntu that will then enable me to add an application? I'm purposely not naming the particular repo that made me ask because I don't want to get off on a tangent about whether the "How to Fly to Mars" repository is a good one or bad one. I'm wondering, in general, things like: 1) would I be at a greater risk of system corruption? 2) Am I more prone to viruses (I know Linux is safe but these are just questions that come to mind) 3) will additional repos cause my laptop to run slower? Just looking for general thoughts on this.

---

### Post by Olav on 2016-02-13
> **PopsTheSailor said:**
> Is it OK to add a repository to Ubuntu that will then enable me to add an application?
If the application cannot be installed from the Ubuntu repositories AND the maintainer of the other repository does a proper job: sure, why not. This is why the mechanism exists in the first place.

But it depends, you see. If your external repository (or PPA) contains only the one application that you need you are probably going to be OK. But if it contains a lot of badly tested "bleeding edge" updates to standard operating system components, that could potentially be a problem. I trust you can see the logic in that.

If you really need to know whether a specific software source is trustworthy or not, I think mentioning its name can't be avoided.

Anyway, you are right to be careful.

---

### Post by vasa1 on 2016-02-13
Since it is so general, I'd have thought the Chat section would be more appropriate.

---

### Post by Olav on 2016-02-13
> **vasa1 said:**
> Since it is so general, I'd have thought the Chat section would be more appropriate.
This is the "General Help" forum. Seems a perfect fit.

---

### Post by bapoumba on 2016-02-13
You need to be careful, in particular when upgrading to a later release. Best is to disable the added repositories (ppa, other) to do a release upgrade.

---

### Post by sudodus on 2016-02-13
> **Olav said:**
> If the application cannot be installed from the Ubuntu repositories AND the maintainer of the other repository does a proper job: sure, why not. This is why the mechanism exists in the first place.

But it depends, you see. If your external repository (or PPA) contains only the one application that you need you are probably going to be OK. But if it contains a lot of badly tested "bleeding edge" updates to standard operating system components, that could potentially be a problem. I trust you can see the logic in that.

If you really need to know whether a specific software source is trustworthy or not, I think mentioning its name can't be avoided.

Anyway, you are right to be careful.

+1

In the case of a repo with many other program packages, that might cause confusion, you can add the repo, sudo apt-get update, and install the program package you want. After that you can remove the repo and sudo apt-get update again.

This should be rather safe, but if you have bad luck, 'your' program package will pull in some library that is not compatible with some other program, that belongs to your distro and version of linux.

---

### Post by oldos2er on 2016-02-13
I've never heard of malware being a problem from any of the launchpad.net PPAs, although it's possible (but unlikely). None of them are vetted in any way by Canonical. Name the PPA; you or anyone can then check if it's been updated recently or not, no shame involved.

Adding PPAs does increase your risk of having problems with package management, and the more PPAs you add, the more risk because of mismatches between software versions. There is an app called ppa-purge that you might want to install first; it will enable you to both remove a PPA and any software you might've installed from it.

---

### Post by PopsTheSailor on 2016-02-13
Thanks everyone for your input. In general I think I have a good feeling about what direction to take. The repository that just happened to prompt me to post my question finally (I've wondered for a long time) is to install pipelight. Pipelight lets unity player work on Linux (or something like that) so I can run a game I found that looks fun (Coffee Quest).

---

### Post by grahammechanical on 2016-02-13
Some PPAs are useful for installing an application but produce errors when updating the system. You may find Software Updater offering a Partial Upgrade. Accepting that offer, can of itself, cause problems. Just click continue and the normal update will go through.

One of the reasons for getting the Partial Upgrade offer is "Unofficial software packages not provide by Ubuntu." That, I believe includes, PPAs. So, after using the PPA to install the software, disable it in Software & Updates.

Regards.

---

### Post by Olav on 2016-02-13
> **PopsTheSailor said:**
> The repository that just happened to prompt me to post my question finally (I've wondered for a long time) is to install pipelight.
My experience with Pipelight (following the instructions* on their website) has been without troubles. Mind, I only use it to have a Silverlight compatible plugin in Firefox, to be able to see some streaming TV. I do not use Unity or games.


*[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

---

### Post by monkeybrain20122 on 2016-02-13
pipelight is fine and the developer/maintainer of the PPA is constantly answering questions on launchpad.

---

### Post by oldos2er on 2016-02-14
I've used the pipelight-stable PPA in the past; I think it's fairly well-maintained.

---

### Post by PopsTheSailor on 2016-02-14
Thanks again everyone. I'll mark this as solved.

---

