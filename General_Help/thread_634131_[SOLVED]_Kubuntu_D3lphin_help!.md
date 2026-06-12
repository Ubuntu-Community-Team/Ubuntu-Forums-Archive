---
title: "[SOLVED] Kubuntu D3lphin help!"
date: 2007-12-07
forum: General Help
---

### Post by khurrum1990 on 2007-12-07
Hi, can some one please take a look at this bug report and tell how to apply the patch mentioned here. You will find out what problem I have with D3lphin here. I am running an up to date Kubuntu 7.10 with KDE 3.5.8 with D3lphin 0.9.2.

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/d3lphin/+bug/162279](https://bugs.launchpad.net/ubuntu/+source/d3lphin/+bug/162279)

Thanks!

---

### Post by barney_1 on 2007-12-07
Save the attached file to your home directory as "patch_d3lphin.diff"

```

cd /usr/share/apps/d3lphin/servicemenus
sudo patch -p1 < ~/patch_d3lphin.diff

```

---

### Post by khurrum1990 on 2007-12-07
> **barney_1 said:**
> Save the attached file to your home directory as "patch_d3lphin.diff"

```

cd /usr/share/apps/d3lphin/servicemenus
sudo patch -p1 < ~/patch_d3lphin.diff

```
I will try that thanks!

---

### Post by khurrum1990 on 2007-12-07
Sorry I got an error message like this:
khurrum@khurrum-desktop:~$ cd /usr/share/apps/d3lphin/servicemenus
khurrum@khurrum-desktop:/usr/share/apps/d3lphin/servicemenus$ sudo patch -pl < ~/patch_d3lphin.diff
patch: **** strip count l is not a number
khurrum@khurrum-desktop:/usr/share/apps/d3lphin/servicemenus$

Anything I am doing wrong?
Thanks!

---

### Post by khurrum1990 on 2007-12-07
> **khurrum1990 said:**
> Sorry I got an error message like this:
khurrum@khurrum-desktop:~$ cd /usr/share/apps/d3lphin/servicemenus
khurrum@khurrum-desktop:/usr/share/apps/d3lphin/servicemenus$ sudo patch -pl < ~/patch_d3lphin.diff
patch: **** strip count l is not a number
khurrum@khurrum-desktop:/usr/share/apps/d3lphin/servicemenus$

Anything I am doing wrong?
Thanks!
Thanks I go it!

---

### Post by barney_1 on 2007-12-07
Glad you figured out to use a numeral 1 instead of a letter "L".  Just a tip, if you ever have problems with running commands you usually can get some guidance by using the "man" command:
```
man patch
```

Did the patch fix up your problem?

---

