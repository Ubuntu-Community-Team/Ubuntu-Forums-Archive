---
title: "[SOLVED] Synaptic Segfault"
date: 2008-06-27
forum: General Help
---

### Post by dslachut on 2008-06-27
All Apt related programs on my machine crash to desktop immediately upon opening (add/remove, update manager, Synaptic,...). It began when I tried to install updates a few days ago.  Terminal only says something about ignoring the clearlooks progressbar.  System Log shows:
```
Jun 27 00:42:17 dslachut-desktop kernel: [  939.132625] synaptic[7084]: segfault at 7f7a989b2b88 rip 7f742165d380 rsp 7fff29b0ce20 error 4
Jun 27 00:43:19 dslachut-desktop kernel: [  970.007781] synaptic[7110]: segfault at 7f4272c41b88 rip 7f3bfb8ec380 rsp 7fff03d9bc60 error 4
Jun 27 00:52:15 dslachut-desktop kernel: [ 1182.778778] synaptic[7141]: segfault at 7fba87f02b88 rip 7fb410bad380 rsp 7fff1905bf20 error 4
Jun 27 00:52:26 dslachut-desktop kernel: [ 1188.634707] synaptic[7143]: segfault at 7f2b55d02b88 rip 7f24de9ad380 rsp 7fffe6e5ad20 error 4
Jun 27 01:13:52 dslachut-desktop kernel: [ 1750.161689] gnome-app-insta[7176]: segfault at 7f1364729b88 rip 7f0ce657d380 rsp 7ffffc253860 error 4
```

How do I fix synaptic?

Also problem appeared around same time as symptoms like:
[http://ubuntuforums.org/showthread.php?t=765510](http://ubuntuforums.org/showthread.php?t=765510)
and
[http://ubuntuforums.org/showthread.php?t=839305](http://ubuntuforums.org/showthread.php?t=839305)

---

### Post by p_quarles on 2008-06-27
The two standard things to try when APT is acting up:
```
sudo apt-get -f install
```
and
```
sudo dpkg --configure -a
```
May not help, but this is certainly among the first things to do, in my opinion.

---

### Post by dslachut on 2008-06-27
first command gives
```
Reading package lists... Done
Segmentation faulty tree... 50%

```in terminal and
```
Jun 27 01:31:09 dslachut-desktop kernel: [ 2220.280841] apt-get[7218]: segfault at 7f7313c50b88 rip 7f6c94a37380 rsp 7fff9cee4580 error 4
```in system log

...The second command seems to have worked, what did it do?

---

### Post by p_quarles on 2008-06-27
> **dslachut said:**
> first command gives
```
Reading package lists... Done
Segmentation faulty tree... 50%

```in terminal and
```
Jun 27 01:31:09 dslachut-desktop kernel: [ 2220.280841] apt-get[7218]: segfault at 7f7313c50b88 rip 7f6c94a37380 rsp 7fff9cee4580 error 4
```in system log

...The second command seems to have worked, what did it do?
Both of those commands attempt to fix broken packages, just in slightly different ways.

So the second one didn't give you any errors? Try running the first command again and see if it works now.

---

### Post by Tomatz on 2008-06-27
Just googled the error and apparently deleting the apt cache may fix the issue.

Open a terminal and type:

```
sudo rm /var/cache/apt/*.bin
```

;)

---

### Post by dslachut on 2008-06-27
> **p_quarles said:**
> Both of those commands attempt to fix broken packages, just in slightly different ways.

So the second one didn't give you any errors? Try running the first command again and see if it works now.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
worked too

---

