---
title: "Rhythmbox Changing Tags"
date: 2013-02-05
forum: General Help
---

### Post by I Need Help123 on 2013-02-05
Hi,
I am using Ubuntu 12.04, and I am having a problem within Rythmbox Music Player.
Rhythmbox randomly keeps changing the tags on albums so that each song in the album is the same name as the first song in the album. I really like Rhythmbox and would like to know what is causing this problem so i can fix it as it is quite frustrating having to keep manually changing the tags back. 

Any help is appreciated.

Thanks.

---

### Post by I Need Help123 on 2013-02-06
Edit: It would appear that it only changes the names on the album if I have previously changed any of the tags within rhythmbox, so for example if I change the song name/artist all of the songs in the album would then be named as the one i changed.

---

### Post by Adam_GUI on 2013-02-06
I can't help with the problem.

I can chip in and say that I've had the same problem.  
So, it does effect multiple users.

My solution was to switch to using banshee or Guayadeque.

EDIT:
Found [Bug #996150]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/996150") stating that the issue was resolved using Rhythmbox version 2.97-1ubuntu1~precise1 from the Gnome3 PPA.  [https://launchpad.net/~gnome3-team/+archive/gnome3]("https://launchpad.net/~gnome3-team/+archive/gnome3").

---

### Post by I Need Help123 on 2013-02-06
Thanks Adam for that useful info.

I am using rhythmbox 2.96, how would I upgrade to the latest for Ubuntu 12.04?

---

### Post by Adam_GUI on 2013-02-06
Using Synaptic, Go to Settings > Repositories > Other Software > Add>

In the Apt Line field, paste: "ppa:gnome3-team/gnome3" and refresh the repositories.

Mark rhythmbox as your only upgrade and apply.  After that, you can go back to software sources and disable the repository if you don't want to install anything else from Gnome3's PPA.  (There will be checkboxes next to the PPA team.  Unchecking those boxes will disable the PPA.  Refreshes sources and you'll be fine.)

---

### Post by I Need Help123 on 2013-02-06
Thanks Adam for all your help, I have successfully upgraded my rhythmbox to the latest version. I will post back later to see if it has fixed the issue, if it has I will mark this thread as solved.

Thanks again.

---

