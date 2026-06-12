---
title: "Synaptic doesn't remove dependencies??"
date: 2005-10-18
forum: General Help
---

### Post by matthias_k on 2005-10-18
Hi,

I just installed BitComet using synaptic which installed tons of python dependencies. I then decided the program sucks and removed it using synaptic, but it only removed the program package, and not the stuff it installed just to resolve dependencies!

Does that mean I have now at least ten packages rotting on my harddisk which I don't need at all because there is no program anymore using them? ^^ That doesn't sound very smart to me. I remember from Debian that aptitude used to remove everything which wasn't needed anymore (unfortunately, using aptitude along with synaptic tends to mess things up even worse and due to Ubuntu's update manager you can't use aptitude exclusively).

Or maybe I am missing a setting in the options pane? ^^
Because this way, it sucks really hard. I'd have tons of useless stuff on my harddisk after using it a year or so.

---

### Post by Pablo_Escobar on 2005-10-18
You can use debfoster or deborphan to check for unneeded packages.
You can get them via apt.

---

### Post by SilentCacophony on 2005-10-18
> I remember from Debian that aptitude used to remove everything which wasn't needed anymore (unfortunately, using aptitude along with synaptic tends to mess things up even worse and due to Ubuntu's update manager you can't use aptitude exclusively).

Speaking of aptitude, I use it exclusively. I just tick off the 'Show Notifications' option from the right-click menu of the update notifier to keep the 'bubble' messages from popping up (I hate those.) It still shows that there are updates when you hover over it. If I see any, I just update using aptitude.

As Pablo_Escobar mentioned, there are utilities you can run to clean up, too.

---

### Post by temcat on 2005-10-18
Just yesterday I was thinking about exactly the same problem. I wanted to try Kubuntu, so I installed kubuntu-desktop. 10 minutes after install I decided that I still don't like KDE and wanted to purge everything I installed with kubuntu-desktop. Now, I was smart and marked kdelibs for removal, which pulled most of the crap with itself. But is a newbie supposed to know that? 

I suggest adding an option to Synaptic to remove a package with the prerequisites that were chosen during its last installation (to do that, Synaptic has of course to log install process).

---

### Post by matthias_k on 2005-10-18
Thanks for your answers guys, I will check out these tools. Probably I will fall back to aptitude in the long run though, I used it exclusively from the command line for over a year in Debian and it never disappointed me. It's a great tool.

I agree however that Synaptic should implement something like debfoster as a backend to clean up behind itself, otherwise you end up with a very messy system sooner or later.

---

