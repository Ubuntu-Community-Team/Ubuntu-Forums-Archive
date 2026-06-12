---
title: "Can't Download Any File from Mozilla Firefox (Ubuntu 22.04.1)"
date: 2022-12-04
forum: General Help
---

### Post by eliasmys1 on 2022-12-04
Hi!

I have encountered this really annoying problem on my Firefox app. I give details below.
I installed Mozilla Firefox on my freshly installed Ubuntu 22.04.1 LTS. I tried installing it from Snap Store. However, when I tried saving an image from the web (or, truthfully, any other file chosen by the "Save As..." selection), nothing happened, again and again. I tried many things, including following relevant guides from the internet, but nothing changed. The Firefox version is the 107.0.1 (64-bit), a Mozilla Firefox Snap for Ubuntu canonical-002- 1.0.
I, also, have to report some other things, as well. When tried installing the browser from the internet (I downloaded a compressed file, containing the executable), the same function seemed to work. I, now, use the executable to access Firefox. However, firstly, because other difficulties (not problems, but difficulties) arise and, secondly, because I'd really like ti use, mostly, snaps, I report this bug here requesting for help, as well.

Any helpful answer will be appreciated!

Thank you!

---

### Post by mIk3_08 on 2022-12-05
How come you have installed another firefox from snap where snap firefox is already come along package installed when you decided to install Ubuntu 22.04 lts in your machine. 
Can run the command below in your terminal and paste the results here in thread wrap with code, to run terminal in your desktop just press ctrl + alt + t or just find it in your Ubuntu Installed apps. Regards and cheers. 
```
snap list
```

---

### Post by guiverc on 2022-12-05
Snap packages run *confined* by default, meaning they have restricted access to your file-system (*restrictions on where they can access*).  

Your issue maybe related to where you're trying to save files, is it in the $HOME or your user directory?  It's a local file, and you're not using a *shortcut* or *link* in your local home directory that points to a network loation etc (*as snap logic will detect this and prevent you from making changes*). 

Snap packages by default have access to your /home/$USER directory, with little access (*seeing only the squashfs they are packaged with*) though you can use `snap connect` (*for some apps; as I recall this isn't required for firefox which has it enabled by default*) you can access removable-media directories /mnt & /media.

I'll provide
[https://askubuntu.com/questions/1184357/why-cant-chromium-suddenly-access-any-partition-except-for-home](https://askubuntu.com/questions/1184357/why-cant-chromium-suddenly-access-any-partition-except-for-home) as reference, I wrote an answer on that page.

This may not be your issue, but you didn't say where you're trying to save files, and what you described reminds me of the limits of *confined* in that they run in a more secured environment (ie. *additional security to protect you, though it can get in the way until you know how to use it*).

---

### Post by eliasmys1 on 2022-12-05
First of all, I now have the Firefox snap deleted from my system. But this is the output of

```

snap list

```:

```

Name                       Version           Rev    Tracking         Publisher      Notes
bare                       1.0               5      latest/stable    canonical&#10003;     base
core20                     20221027          1695   latest/stable    canonical&#10003;     base
core22                     20220902          310    latest/stable    canonical&#10003;     base
cups                       2.4.2-4           836    latest/stable    openprinting&#10003;  -
curl                       7.86.0            1256   latest/stable    woutervb       -
discord                    0.0.21            145    latest/stable    snapcrafters   -
gnome-3-38-2004            0+git.6f39565     119    latest/stable/&#8230;  canonical&#10003;     -
gnome-42-2204              0+git.c271a86     44     latest/stable    canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/&#8230;  canonical&#10003;     -
snap-store                 41.3-66-gfe1e325  638    latest/stable/&#8230;  canonical&#10003;     -
snapd                      2.57.6            17883  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.1               43     latest/stable/&#8230;  canonical&#10003;     -

```.

I hope this helps!

---

### Post by eliasmys1 on 2022-12-05
These are the permissions:

(Seen in the attached image below.).

As I know, the files are saved automatically in the Downloads folder, which is in the Home directory.

After that, I didn't understand much, I'm sorry. If you could help more, I would appreciate it!

Thank you!

---

### Post by mIk3_08 on 2022-12-06
> **eliasmys1 said:**
> 
I installed Mozilla Firefox on my freshly installed Ubuntu 22.04.1 LTS. I tried installing it from Snap Store. 
> **eliasmys1 said:**
> First of all, I now have the Firefox snap deleted from my system. But this is the output of

```

snap list

```:

```

Name                       Version           Rev    Tracking         Publisher      Notes
bare                       1.0               5      latest/stable    canonical&#10003;     base
core20                     20221027          1695   latest/stable    canonical&#10003;     base
core22                     20220902          310    latest/stable    canonical&#10003;     base
cups                       2.4.2-4           836    latest/stable    openprinting&#10003;  -
curl                       7.86.0            1256   latest/stable    woutervb       -
discord                    0.0.21            145    latest/stable    snapcrafters   -
gnome-3-38-2004            0+git.6f39565     119    latest/stable/…  canonical&#10003;     -
gnome-42-2204              0+git.c271a86     44     latest/stable    canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/…  canonical&#10003;     -
snap-store                 41.3-66-gfe1e325  638    latest/stable/…  canonical&#10003;     -
snapd                      2.57.6            17883  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.1               43     latest/stable/…  canonical&#10003;     -

```.

I hope this helps!

I haven't seen any Firefox here based on what you have said that you have tried to install Firefox from snap. Regards and cheers

---

### Post by mIk3_08 on 2022-12-06
> **eliasmys1 said:**
> 
I installed Mozilla Firefox on my freshly installed Ubuntu 22.04.1 LTS. I tried installing it from Snap Store. 
> **eliasmys1 said:**
> First of all, I now have the Firefox snap deleted from my system. But this is the output of

```

snap list

```:

```

Name                       Version           Rev    Tracking         Publisher      Notes
bare                       1.0               5      latest/stable    canonical&#10003;     base
core20                     20221027          1695   latest/stable    canonical&#10003;     base
core22                     20220902          310    latest/stable    canonical&#10003;     base
cups                       2.4.2-4           836    latest/stable    openprinting&#10003;  -
curl                       7.86.0            1256   latest/stable    woutervb       -
discord                    0.0.21            145    latest/stable    snapcrafters   -
gnome-3-38-2004            0+git.6f39565     119    latest/stable/&#8230;  canonical&#10003;     -
gnome-42-2204              0+git.c271a86     44     latest/stable    canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/&#8230;  canonical&#10003;     -
snap-store                 41.3-66-gfe1e325  638    latest/stable/&#8230;  canonical&#10003;     -
snapd                      2.57.6            17883  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.1               43     latest/stable/&#8230;  canonical&#10003;     -

```.

I hope this helps!

I haven't seen any Firefox here in your snap results list based on what you have said that you have tried to install Firefox from snap. I don't think that you have properly installed that Firefox browser. Regards and cheers

---

### Post by eliasmys1 on 2022-12-16
Hi!
I'm sorry, for the late reply, I have given my PC for upgrade.
Fortunately, I don't need your help anymore. I managed to resolve the issue via a workaround.
I installed Firefox via apt.
Thank you!

---

