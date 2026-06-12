---
title: "cd burning application only occasionally sees the cdrw"
date: 2007-02-15
forum: General Help
---

### Post by badbreeze on 2007-02-15
i have a strange problem which will probably be easy to fix, please help if you can. i am a noob's noob so bear with me. after working perfectly, my windows cd burning application, running under wine, was working great, but now i have to do this insane series of steps to burn an audio cd. first, i have to put in a cd with audio already on it and only then start the application, otherwise it won't see the burner. the little devices widget on the panel will now allow me to mount the cdrom (cdrw) drive, the windows app says put in a blank cd, i unmount, eject, put in a blank cd, and everything's fine. but it didn't used to do this and it's driving me crazy. i think i may have mounted & unmounted the cdrom drive too many times at the wrong times. anyway. any insight appreciated, i'm tearing my hair out.

---

### Post by louis_nichols on 2007-02-15
I must admit I'm surprised to see it works at all! I mean, a cd burning tool under wine... that is pretty amazing.

Why not use a native Linux app? There are quite a lot there, some very good. And you will get all kind of advantages in performances and much less hassle to make things work the way you want them.

---

### Post by badbreeze on 2007-02-15
well, if you can recommend anything i'd be grateful. nothing under xubuntu seems to want to allow me to burn audio cds with mp3 files...thought maybe it was a licensing issue but there must be an easier work-around than what i'm doing!

---

### Post by louis_nichols on 2007-02-16
Sure! I recommend [K3B]("http://www.k3b.org/"). It is a great app and I have been using it for all burning-related tasks for more than 2 years now.

The only thing is that k3b is not native to Xubuntu's XFCE, but that isn't a problem. Just remembr to also install the package libk3b2-mp3, which is the one that allows you to burn audio cd-s directly from mp3's.

---

### Post by badbreeze on 2007-02-18
works great, thanks!

---

