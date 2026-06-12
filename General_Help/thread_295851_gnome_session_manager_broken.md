---
title: "gnome session manager broken?"
date: 2006-11-08
forum: General Help
---

### Post by geokok1981 on 2006-11-08
It is impossible to add any commands/applications to the session manager 
(system-->preferences-->sessions-->Launch programs (the third tab))

I add anything, from firefox to firestarter to terminal but when 
close the window it wont be saved in the list and therefore will not launch 
the next time I boot. It seems that it does not save the list except for the
original list that is there (including power manager, beagled, etc).

Any workarounds?

---

### Post by feign on 2006-11-11
I seem to have the same problem too.  According to [this link]("http://ubuntuforums.org/showthread.php?t=286958&highlight=startup+script") it should be straight forward.

Edit:
This resolved it for me.
[http://www.ubuntuforums.org/showthread.php?t=286508&highlight=session](http://www.ubuntuforums.org/showthread.php?t=286508&highlight=session)

---

### Post by geokok1981 on 2006-11-12
Thanks I have found other posts as well with this.
THe solutions does work but I consider it to be a bug and I 
have added a report at launcpad here:
[https://launchpad.net/distros/ubuntu/+source/upstart/+bug/71200](https://launchpad.net/distros/ubuntu/+source/upstart/+bug/71200)

U might want to conform it so the devs will have a look at it.,

---

### Post by groggyboy on 2006-11-13
I've confirmed the bug on launchpad.

---

