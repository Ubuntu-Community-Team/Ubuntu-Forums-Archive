---
title: "Login screen flashes briefly, then goes black"
date: 2017-02-06
forum: General Help
---

### Post by kgibson2 on 2017-02-06
I'm running kubuntu-desktop on top of ubuntu 16.10 and using sddm to log in.  My video card in my laptop is an nvidia 1080, using nvidia 3.78 drivers.

When I boot my laptop it goes to the login screen very briefly (1/4 sec?), then goes black.  If I enter my password immediately and hit enter, it will log me in.  If I wait at all, it eventually stops functioning.  I can hit tab to occasionally show a brief flash of the login screen, but it immediately goes black again.

My personal guess would be that it seems like some power saving issue, although I have had no success in fixing the poblem.

The issue happens identically with all versions of nvidia-drivers I've tried (I've tried at least 4 from nvidia-current to nvidia-3.78).

The issue happens regardless of using the unity login or the kde login screen.

Anyone have any suggestions as to what the problem is and how I might go about fixing it?

Cheers!

---

### Post by cis190 on 2017-02-11
Had this problem just now this worked for me,

When at login screen,

ctrl + alt + f3

then,

```
sudo chown 'YourUserName':'YourUserName' .Xauthority
```

then,

 ctrl + alt + f7

and try to login again.

---

### Post by kgibson2 on 2017-02-14
Thanks for looking and taking the time to respond!  Unfortunately, the permissions were already set for .Xauthority and it had no effect.

---

