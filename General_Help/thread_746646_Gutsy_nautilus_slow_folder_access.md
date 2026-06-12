---
title: "Gutsy nautilus slow folder access"
date: 2008-04-05
forum: General Help
---

### Post by thecec on 2008-04-05
Hi all, 

I'm running gutsy on  a brand new laptop.
I experience a very very slow performance of nautilus: tu display, as list view, the content of /usr/bin ( 1835 files) it takes around a minute!!

I read the other threads about nautilus problems, but nothing was good for my problem.

I'm running compiz with the nvidia drivers.
Before telling me about compiz being a possible cause, if I used dolphin, it takes 2 seconds.

I actually love dolphin, but it takes a bit to start up the first time, since it needs to load some kde libraries I think.

Any help would be very appreciated.

If someone can just tell me how to set my system to load the kde libraries while starting up the system, I'd love that: I'm using also amarok, and kate for C and Ruby :)

Thx a lot,
TheCec

LONG LIFE UBUNTU!

---

### Post by jpeddicord on 2008-04-05
Nautilus could be trying to generate thumbnails from the files in /usr/bin. It takes 5 seconds to load on average here, since there are over 2,000 files.

To change this behavior, go to Edit > Preferences in Nautilus, and go to the Preview tab. Change both "Show Text in icons" and "Show Thumbnails" to Never. This will shut off thumbnails for everything else, but will speed up the folder view.

---

### Post by thecec on 2008-04-06
I'm always using the list view, so there are no thumbnails being generated.

I tried turning previews off anyways and nothing changed.

Does someone have any idea on how to have an instance of a kde application being loaded when logging in?

Can I simply put it in the GnomeSession?

Thx

---

### Post by ellgor on 2008-04-06
Hi,

One thing I found that using Nautilus is that the problems gradually get worse, to the point that it becomes unworkable, after a few reloads and the same thing happening I switched to KDE.
Granted its not perfect, but it seems to operate faster and when an application fails its only that app that fails and not the whole system as I found Nautilus was doing most of the time, I note you already have some KDE Libs on the go I suggest give KDE a go, once you find the little differences between the setups I think you will be impressed, hope this is of help.

Regards, Ellgor.

---

### Post by thecec on 2008-04-10
Hi, 

I agree with u that KDE is great, but I cannot find a good network manager working also for the wireless.
I'm running gutsy on a laptop, therefore it's fundamental for me.

Cheers,
thecec

---

