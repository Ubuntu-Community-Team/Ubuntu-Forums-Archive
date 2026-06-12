---
title: "Ubuntu -sdk is not in official repositories of Ubuntu"
date: 2015-12-06
forum: General Help
---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

I open this post to find out the deeper because it is the ubuntu- sdk package in the official repositories of Ubuntu.

A user in a previous post I linked in the public issue that this package was in the Ubuntu repositories and Synaptic.

But when I install I get this result on the terminal :


> ricardo - root @ desktop : /home/ricardo # apt-get install ubuntu-sdk

Reading package lists ... Done

Building dependency tree

Reading state information ... Done

E: It has not been able to locate the package ubuntu- sdk

And sending a screenshot of my computer to find the package in Synaptic:

[IMG]http://i67.tinypic.com/svqse0.png[/IMG]

---

### Post by Bucky Ball on 2015-12-06
Just to help Ricardo_Velasco along here (and thanks for opening a new thread, Ricardo), this thread is inspired by our discussion on another thread where he doesn't have ubuntu-sdk available in the repos/Synaptics, but I, for some reason, do (see screenshot). I don't have any third-party PPAs installed (except UbuntuSatanic which is only installed for the artwork, but that has nothing to do with this I wouldn't think).

I too am curious as to why I have it available from the repos and Ricardo_Velasco doesn't. I'm on 14.04 LTS. Ricardo, you are using 12.04 LTS? Maybe it didn't make it into the repos there. :-k

(Please attach large pics with 'Go Advanced' or 'Adv Reply' and use the paperclip icon. Thanks. :))

---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

I read your comment and most likely is the distribution although I think better versions would not be equal in repositories ?.

Or do I enable updates not yet published ?

---

### Post by kostkon on 2015-12-07
12.04 is not officially supported for Ubuntu Touch development, but an older version of the sdk and qt5 is available for it through the ubuntu-sdk ppa.

---

### Post by Bucky Ball on 2015-12-07
> **kostkon said:**
> 12.04 is not officially supported for Ubuntu Touch development, but an older version of the sdk and qt5 is available for it through the ubuntu-sdk ppa.

I think that explains everything. Cheers. :)

---

