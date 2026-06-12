---
title: "help! kubuntu desktop disapeared"
date: 2013-02-23
forum: General Help
---

### Post by monkblah on 2013-02-23
Turned on my 12.10 machine today, it got to the lightdm greeter and asked me to login as usual. However, the kde plasma desktop session (the one I always use) had disappered from the greeter menu. All that is there is 'Xubuntu session' and 'Xfce Session', which work, but I can't start kde.

I did not do anything to cause this to happen. What is going on?

---

### Post by xc3RnbFO8P on 2013-02-23
Can you see it in:
> ls /usr/share/xsessions/

---

### Post by monkblah on 2013-02-23
Figured this out. I should have said 'I did not do anything to cause this to happen THAT I AM AWARE OF.'

Short answer, I realized I accidentally changed the permissions of some files in the root file system. One of them was /usr/bin/startkde .

Sorry for the false alarm. Thanks for the quick reply, Ringi.

---

