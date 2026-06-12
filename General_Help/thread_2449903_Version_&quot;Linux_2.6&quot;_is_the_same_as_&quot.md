---
title: "Version &quot;Linux 2.6&quot; is the same as &quot;Linux Ubuntu 2.6.x&quot; and they maintain support"
date: 2020-09-03
forum: General Help
---

### Post by carlos09w on 2020-09-03
Nice to greet you and at the same time I would appreciate your collaboration with respect to a question that I present since I do not know if the version of Linux 2.6 is the same as Linux Ubuntu 2.6.x, I would also like to know if both versions are still valid regarding the support provided by the Linux community or if, on the contrary, they are versions that can be considered obsolete.


Any help on this topic is welcome.


Thank you

---

### Post by guiverc on 2020-09-03
Ubuntu is a distribution of GNU/Linux

The linux kernel is the core of the operating system, and is used by GNU/Linux distributions (usually just shortened to Linux distros), Android phones and far more.

The Linux kernel 2.6 is now EOL (*end-of-life*) in the Ubuntu world, the last supported release to use it was Ubuntu 10.04 LTS which reached its EOL long ago.

Yes some-other older distributions (eg. RHEL, CentOS) still use it, but those releases are very close to their EOL too.  Most of the Linux community won't support kernel 2.6 due to it's age.

There is no Linux Ubuntu 2.6.x

An answer can be found at [https://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version](https://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version) which has a nice table showing Ubuntu releases, and the respective kernels each used (the last to use a 2.6 kernel was 11.04, the last supported release using it was 10.04 LTS)

---

### Post by TheFu on 2020-09-03
The current kernel for the current LTS release - Ubuntu 20.04 is v5.4.0-42-generic. It has been at least a decade since I saw a 2.6 Linux kernel used anywhere - and really before that.  Legacy doesn't fully describe that.

Don't confuse the kernel version with any distribution versioning. Those are never connected for any distro I remember - though in the early 1990s it may have worked that way a few times.

"Linux community" is like saying "the world".  Some things are supported by excellent teams of people and other things formerly supported get dropped all the time as people's lives change and priorities have to change.

Wikipedia has lots of different articles about different linux parts and distributions.  Usually, just add "history" to any web search. "kernel history" for example.  The first result for me was: [https://en.wikipedia.org/wiki/Linux_kernel_version_history](https://en.wikipedia.org/wiki/Linux_kernel_version_history)

Linux history [https://en.wikipedia.org/wiki/History_of_Linux](https://en.wikipedia.org/wiki/History_of_Linux)
Ubuntu history: [https://en.wikipedia.org/wiki/Ubuntu_version_history](https://en.wikipedia.org/wiki/Ubuntu_version_history)
You get the idea. The English articles will usually have fuller content, but some other languages get good coverage too.

---

### Post by carlos09w on 2020-09-04
Guiverc, thank you for your answer and help.

---

### Post by carlos09w on 2020-09-04
TheFu, [COLOR=#000000]thank you for your answer and [/COLOR]I understand your idea to search information in the future.

---

### Post by TheFu on 2020-09-04
> **carlos09w said:**
> TheFu, [COLOR=#000000]thank you for your answer and [/COLOR]I understand your idea to search information in the future.

Questions are always welcome, but most answers are already available at the other end of a web search.  Getting clarification about something you read elsewhere, assuming it is a reputable source, is fine. Many things related to Linux don't change THAT much over decades, but some things do when we get into specific commands.  Bit ideas are about the same now as 20 yrs ago, but how to configure networking has been changing every few years since 2012. Before then, it was very stable, the same.

Here's a really great diagram that shows the relationships between different Linux distros over time.  
[https://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg](https://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg)
These "families" usually have configuration and package management handled in very similar ways. Jump between different families, and those things change.

I think there are 5 "original" major distros that are still around today.  Every other distro is a child of those five, unless it is niche.  OpenELEC is a niche distro, created for a special purpose. So is Android.  You can make your own, if you like.

Do some research first, in the question, show that you've done some, and ask away. ;)

---

