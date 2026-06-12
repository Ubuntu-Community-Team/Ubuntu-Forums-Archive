---
title: "krita install held broken packages problem"
date: 2019-10-01
forum: General Help
---

### Post by jim Kane on 2019-10-01
Xubuntu18-4
Im trying to install krita from synaptic but get &#8220;You have held broken packages&#8221;
I seem to have tried most of fixes from a google search but still cant resolve it im wondering if something is different with 18-4
[IMG]http://imgbox.com/eaEsaj47][IMG]https://thumbs2.imgbox.com/cf/00/eaEsaj47_t.png[/IMG[/IMG]

---

### Post by deadflowr on 2019-10-02
Might be an issue beyond just installing krita.
Look at what apt shows
```
sudo apt update
sudo apt full-upgrade
```
post the results.

---

### Post by jim Kane on 2019-10-02
> **deadflowr said:**
> Might be an issue beyond just installing krita.
Look at what apt shows
```
sudo apt update
sudo apt full-upgrade
```
post the results.

that looks quite normal
```

   :~$ sudo apt update
[sudo] password for mike:
Hit:1 http://gb.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://archive.canonical.com/ubuntu bionic InRelease
Hit:3 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04
 InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up-to-date.
   :~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

this is the error message, thanks for your help 
[IMG]https://i.vgy.me/g1Aup8.png[/IMG]

---

### Post by Bashing-om on 2019-10-02
jim Kane; Hello

Show us next the outputs from:
```

sudo apt -f install
dpkg --configure -a
sudo dpkg -C
sudo ldconfig

```

[INDENT]see where we go from here
[/INDENT]

---

### Post by jim Kane on 2019-10-03
> **Bashing-om said:**
> jim Kane; Hello

Show us next the outputs from:
see where we go from here

Hello
[LEFT][COLOR=#000000][FONT=Arial][SIZE=4]that was all normal and did not work still get error [/SIZE][/FONT][/COLOR] [/LEFT]
 [LEFT][COLOR=#000000][FONT=Arial][SIZE=4]tried to install the PPA for Krita but that is greyed out and does not work[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#000000][FONT=Arial][SIZE=4][URL="http://ppa.launchpad.net/kritalime/ppa/ubuntu"]http://ppa.launchpad.net/kritalime/ppa/ubuntu
[IMG]https://i.vgy.me/zBGYnK.png[/IMG]
[/URL] [/SIZE][/FONT][/COLOR] 
[/LEFT]

---

### Post by deadflowr on 2019-10-03
> that was all normal and did not work still get error
Post what
```
dpkg -l | egrep -v "^ii|^rc" 
```
shows.
The above command will remove any outputs for okay packages (both installed, and removed successfully)
Leaving only anything marked as problematic. Hopefully.

---

### Post by jim Kane on 2019-10-03
Solved

in Synaptic if you right click on Krita it give a list of &#8220;recommended for installation liberty's&#8221; ok that and it installs ok.

However 18-4s latest version doesn't have a Print function which is what I was trying to install it for !
Now installed Gimp which I was trying to avoid as its possibly the most unintuitive thing I have ever come across 
but as always thanks for the Forums Help

---

