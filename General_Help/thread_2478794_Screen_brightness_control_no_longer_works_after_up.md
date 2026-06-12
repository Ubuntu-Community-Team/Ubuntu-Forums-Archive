---
title: "Screen brightness control no longer works after upgrade 20.04 -&gt; 22.04"
date: 2022-09-05
forum: General Help
---

### Post by ne29914 on 2022-09-05
HW: Laptop PC (HP/Compaq 6910p).

I upgraded my PC from Lubuntu 20.04 LTS to 22.04 LTS using this recipe: [https://linuxize.com/post/how-to-upgrade-to-ubuntu-22-04/](https://linuxize.com/post/how-to-upgrade-to-ubuntu-22-04/)
The upgrade was uneventful with no errors or warnings and took around an hour.

Everything works fine. My /home survived with all contents. Super.

**But I can no longer control screen brightness**. 

Brightness was previously set using function keys or using the "LXQt Settings/Brightness menu" and would _stay after reboot_.
Now, the function keys do not work, and I have to set brightness again after every reboot.

The command for brightness settings is:
```
lxqt-config-brightness
```
with parameter -i or -d for increasing/decreasing brightness.

Sorry for a TL&DR type question.

Did anyone experience this problem?
Did you find a solution?
Where are the lxqt-config-brightness settings stored?

Thanks.

---

### Post by ne29914 on 2022-09-06
Result on this one:
After playing around, I concluded that the current version (22.04) of "lxqt-config-brightness" 0.17 is dysfunctional.
I recovered version 0.14.1 from a 20.04  machine and replaced it in the /bin directory: instant success. My hotkeys work again, all is well.

---

