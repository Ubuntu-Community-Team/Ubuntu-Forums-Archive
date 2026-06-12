---
title: "dpkg -l ... package names are chopped"
date: 2021-08-09
forum: General Help
---

### Post by Skaperen on 2021-08-09
i tried to do "dpkg -l|egrep '^ii  '|field 2" (*field* is my own script to slice off selected white-space separated fields) to get a list of package i currently have installed so that i can try to install them in an fresh installed system (i'm finally going from 18.04 to 20.04).  the problem i get is that longer package names are being chopped shorter down to 28 characters.  i know i have package "xubuntu-community-wallpapers-bionic" installed which is 35 characters.  how can i get the full packages list?

---

### Post by scorp123 on 2021-08-09
```
dpkg -l | grep ^ii | awk '{ print $2 }'
```

Not sure why you are reinventing the wheel and fire with that 'field' program of your's. Awk exists already.

---

### Post by Skaperen on 2021-08-11
i know of awk but for simple things, awk is awkward to use.  i prefer simpler commands especially those that don't need shift on the keyboard as { and } do.  now, back to the original question.  do you have an answer for that?  you have the mic.  are you gonna drop it?

it's reasons like this that people prefer to post less code or none at all.  there's always someone that does it different (and maybe it's better) and wants to go off topic and suggest that.  people need to stay on topic, post it as a new thread somewhere else, or be silent.

---

### Post by norobro on 2021-08-11
```
aptitude search '~i' -F '%p'
```That's one less 'shift' than your original command (tilde and percent sign v. 2 pipes and carat).
> **Skaperen said:**
> ... i prefer simpler commands especially those that don't need shift on the keyboard as { and } do.  ...Is there a reason that you can't use an alias?

---

### Post by Skaperen on 2021-08-11
> **norobro said:**
> Is there a reason that you can't use an alias?
spreading that out among the many userids that i use means replacing the file it is in for each user.  it is easier to just add it to **[FONT=courier new]/usr/host/bin[/FONT]** which each userid already has, or will include (when it logs in), in their PATH variable.  there are over 400 scripts there plus over 300 symlinks.

---

### Post by Skaperen on 2021-08-11
> **norobro said:**
> ```
aptitude search '~i' -F '%p'
```

```

lt2a/forums /home/forums 7> aptitude search '~i' -F '%p'
bash: aptitude: command not found
lt2a/forums /home/forums 8> 

```

i guess i need to install it.  now i have a reason to learn what all it can do.

but no time for that right now.  i'm working on issues that are making my road to *focal* *fossa* a bumpy one.  maybe it will come with *aptitude* already installed.

---

### Post by Impavidus on 2021-08-12
> **Skaperen said:**
> i tried to do "dpkg -l|egrep '^ii  '|field 2" (*field* is my own script to slice off selected white-space separated fields) to get a list of package i currently have installed so that i can try to install them in an fresh installed system (i'm finally going from 18.04 to 20.04).  the problem i get is that longer package names are being chopped shorter down to 28 characters.  i know i have package "xubuntu-community-wallpapers-bionic" installed which is 35 characters.  how can i get the full packages list?

There are 3 possibilities:
1: **dpkg -l** chops off the package names. dpkg is known to chop off package names when writing to a  terminal that's too narrow for the full package name, but normally doesn't do so when writing to a pipe. I don't know how this is implemented.
2: **egrep '^ii '** chops off the package names. I don't think egrep ever does this.
3: **field 2** chops off the package names. I don't know your field script, so I can't tell.
You could try running **dpkg -l | egrep '^ii '** to test for option 1 or 3. If the problem is 1, look into how dpkg decides to chop off names in narrow terminals.

Alternatively, use **apt-mark showmanual** to get a list of manually installed packages. You don't need the automatically installed ones, as they will be pulled in automatically, if still needed. And you probably want to get rid of them if no longer needed. But if you wish, **apt-mark showinstall** will give the full list of installed packages.

---

### Post by TheFu on 2021-08-12
+1 for **apt-mark showmanual > ~/apt-mark.manual **
Just dump those to a file and on restore/new machine, then ....

 feed them back into the system to be installed.
```
sudo apt-mark manual $(cat apt-mark.manual)
sudo apt-get -u dselect-upgrade

```
**sudo apt-get -f install** may be needed. I don't recall.

---

### Post by Skaperen on 2021-08-12
```

lt2a/forums /home/forums 35> dpkg -l|egrep '^ii  '|awk '{print length($2)+100,$2;}'|sort|tail
128 xserver-xorg-video-intel-hwe
128 xserver-xorg-video-nouveau-h
128 xserver-xorg-video-qxl-hwe-1
128 xserver-xorg-video-radeon-hw
128 xserver-xorg-video-vesa-hwe-
128 xserver-xorg-video-vmware-hw
128 xubuntu-community-wallpapers
128 xubuntu-community-wallpapers
128 xubuntu-community-wallpapers
128 xubuntu-community-wallpapers
lt2a/forums /home/forums 36> apt-mark showmanual|awk '{print length($1)+100,$1;}'|sort|tail
134 xserver-xorg-video-intel-hwe-18.04
135 xserver-xorg-video-amdgpu-hwe-18.04
135 xserver-xorg-video-radeon-hwe-18.04
135 xserver-xorg-video-vmware-hwe-18.04
135 xubuntu-community-wallpapers-bionic
135 xubuntu-community-wallpapers-trusty
135 xubuntu-community-wallpapers-xenial
136 xserver-xorg-video-nouveau-hwe-18.04
137 xserver-xorg-input-libinput-hwe-18.04
138 xserver-xorg-input-synaptics-hwe-18.04
lt2a/forums /home/forums 37> 

```

---

### Post by Impavidus on 2021-08-12
The package names don't get chopped off when I run that command on Xubuntu 21.04:
```
$ dpkg -l|egrep '^ii  '|awk '{print length($2)+100,$2;}'|sort|tail
134 xubuntu-community-wallpapers-focal
135 libgstreamer-plugins-bad1.0-0:amd64
136 fonts-material-design-icons-iconfont
136 libboost-program-options1.71.0:amd64
136 libboost-program-options1.74.0:amd64
136 libgstreamer-plugins-base1.0-0:amd64
136 libgstreamer-plugins-good1.0-0:amd64
137 linux-modules-extra-5.11.0-22-generic
137 linux-modules-extra-5.11.0-25-generic
137 speech-dispatcher-audio-plugins:amd64

```
Maybe it has something to do with the terminal or shell you run? I use xfce4-terminal and bash. Or something's different on your 18.04 system.

---

### Post by Skaperen on 2021-08-12
i will try it on 20.04 as seen as i can (very soon).  i had one test run succeed but i rebooted back to 18.04 because it was just on my little SSD and i am not going to do a major upgrade with a line of severe storms heading this way (i can hear the thunder, now).

---

### Post by Skaperen on 2021-08-13
> **Impavidus said:**
> The package names don't get chopped off when I run that command on Xubuntu 21.04:
```
$ dpkg -l|egrep '^ii  '|awk '{print length($2)+100,$2;}'|sort|tail
134 xubuntu-community-wallpapers-focal
135 libgstreamer-plugins-bad1.0-0:amd64
136 fonts-material-design-icons-iconfont
136 libboost-program-options1.71.0:amd64
136 libboost-program-options1.74.0:amd64
136 libgstreamer-plugins-base1.0-0:amd64
136 libgstreamer-plugins-good1.0-0:amd64
137 linux-modules-extra-5.11.0-22-generic
137 linux-modules-extra-5.11.0-25-generic
137 speech-dispatcher-audio-plugins:amd64

```
Maybe it has something to do with the terminal or shell you run? I use xfce4-terminal and bash. Or something's different on your 18.04 system.

it appears to be fixed for pipelines in 20.04, too.  but it still uses the terminal width even for pipelines in 18.04.5 (my last upgrade about a week ago). i  tried creating a virtual terminal session through the [FONT=courier new]screen[/FONT] program and set the width to 1023 and it works there.  it is wide enough that way.

---

