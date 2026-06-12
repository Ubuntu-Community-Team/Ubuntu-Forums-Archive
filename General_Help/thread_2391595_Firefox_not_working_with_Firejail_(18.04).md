---
title: "Firefox not working with Firejail (18.04)"
date: 2018-05-11
forum: General Help
---

### Post by linuxyogi on 2018-05-11
Hi,

Today when I launched firefox with firejail no pages are loading. 

```
$ firejail firefoxReading profile /etc/firejail/firefox.profile
Reading profile /etc/firejail/disable-common.inc
Reading profile /etc/firejail/disable-devel.inc
Reading profile /etc/firejail/disable-programs.inc
Reading profile /etc/firejail/whitelist-common.inc
Reading profile /etc/firejail/whitelist-var-common.inc
Parent pid 6513, child pid 6514
Blacklist violations are logged to syslog
Child process initialized in 81.60 ms



```

Chromium works fine.  

Firefox 60.0 (64-bit)

Please help me out.

---

### Post by herronkeith on 2018-05-11
I got it working after I tried this:

On the firejail support page: [https://firejail.wordpress.com/support/#amdgpu](https://firejail.wordpress.com/support/#amdgpu)
Under the heading: Firefox crashing on Netflix, AMDGPU PRO, Nvidia closed source drivers

I modified the launcher I had for firefox so that the command or exec line was as follows:

firejail --ignore=seccomp --ignore=protocol firefox %u -no-remote

The original suggestion included the switch --allow-debuggers, but that doesn't work with the version of firejail that I have.

I hope this helps.

---

### Post by linuxyogi on 2018-05-12
> **herronkeith said:**
> I got it working after I tried this:

On the firejail support page: [https://firejail.wordpress.com/support/#amdgpu](https://firejail.wordpress.com/support/#amdgpu)
Under the heading: Firefox crashing on Netflix, AMDGPU PRO, Nvidia closed source drivers

I modified the launcher I had for firefox so that the command or exec line was as follows:

firejail --ignore=seccomp --ignore=protocol firefox %u -no-remote

The original suggestion included the switch --allow-debuggers, but that doesn't work with the version of firejail that I have.

I hope this helps.

When I open FF with

```
firejail --ignore=seccomp --ignore=protocol firefox %u -no-remote
```

This page opens

[ATTACH=CONFIG]279669[/ATTACH]

Then when I type google.com it opens as  usual.

---

### Post by maglin2 on 2018-05-12
Same problem here too - running Ubuntu 16.04 FF60.
Update --ignore=seccomp seems to get it working, but it is throwing a few warnings/errors in the terminal. Since I don't normally run it from the terminal I don't know if this is new.

---

### Post by linuxyogi on 2018-05-12
I am using Chromium temporarily but want to use Firefox as soon this problem gets solved.

---

### Post by wildmanne39 on 2018-05-12
Hi inuxyogi, I removed the post from laracraft that you quoted as spam so I am going to also remove your post that quotes it.

---

### Post by linuxyogi on 2018-05-12
> **wildmanne39 said:**
> Hi inuxyogi, I removed the post from laracraft that you quoted as spam so I am going to also remove your post that quotes it.

Okay. No problem.

---

### Post by maglin2 on 2018-05-12
If you look here [https://forums.linuxmint.com/viewtopic.php?f=47&t=269263&start=20](https://forums.linuxmint.com/viewtopic.php?f=47&t=269263&start=20)
it suggest this will be fixed in 0.9.54.
There is apparently already a fix for this in 0.9.54rc1, but that still has other bugs so probably isn't worth installing yet.
Don't know if the fix will ever find it's way into the versions offered in the Ubuntu repos.

---

### Post by linuxyogi on 2018-05-12
> **maglin2 said:**
>  Don't know if the fix will ever find it's way into the versions offered in the Ubuntu repos.

I hope Ubuntu repos gets update otherwise I will just continue with Chromium.

---

### Post by poorguy on 2018-05-12
I to had the same problem on my ***Ubuntu 18.04***  computer so I'm using ***Chromium*** until ***Firefox*** and ***Firejail*** are working together again a ***browser*** is a ***browser*** as long as it works imo.

---

### Post by maglin2 on 2018-05-13
> **poorguy said:**
> I to had the same problem on my ***Ubuntu 18.04***  computer so I'm using ***Chromium*** until ***Firefox*** and ***Firejail*** are working together again a ***browser*** is a ***browser*** as long as it works imo.

True, but I'm trying to follow Best Practice from here [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)  wherever it's reasonably easy, so ideally I need two browsers.

---

### Post by linuxyogi on 2018-05-13
There is a fix available. One needs to download the latest firejail form [here]("https://sourceforge.net/projects/firejail/files/firejail/").

But I dont install anything outside of the official repos.

---

### Post by maglin2 on 2018-05-13
> **linuxyogi said:**
> There is a fix available. One needs to download the latest firejail form [here]("https://sourceforge.net/projects/firejail/files/firejail/").

But I dont install anything outside of the official repos.

In which case your best approach for the present may be to do what Fred Barclay suggests here [https://forums.linuxmint.com/viewtopic.php?f=47&t=269263&start=20#p1469063](https://forums.linuxmint.com/viewtopic.php?f=47&t=269263&start=20#p1469063)

and create a file in your home folder ~/.config/firejail/firefox.profile containing the text he posted.

---

### Post by linuxyogi on 2018-05-13
> **maglin2 said:**
> In which case your best approach for the present may be to do what Fred Barclay suggests here [https://forums.linuxmint.com/viewtopic.php?f=47&t=269263&start=20#p1469063](https://forums.linuxmint.com/viewtopic.php?f=47&t=269263&start=20#p1469063)  and create a file in your home folder ~/.config/firejail/firefox.profile containing the text he posted.  Done. Its working. Thanks a lot.

---

### Post by maglin2 on 2018-05-13
No problem - I just copied what Fred Barclay said.

He also points out:

'firejail sets up the sandbox by evaluating arguments in the following order:1. Command-line parameters (--ignore=seccomp, for example) take precedence in any case
2. Next, if there's a suitable profile in ~/.config/firejail/, it's evaluated.
3. If not, if there's a suitable profile in /etc/firejail/, it's evaluated'

so if there is a firejail repo update you will need to remove that home folder config file for it to take effect.

---

### Post by linuxyogi on 2018-05-13
> **maglin2 said:**
>  so if there is a firejail repo update you will need to remove that home folder config file for it to take effect.  In order to do that I have to read every update carefully from now on to see if there's a firejail update

---

### Post by maglin2 on 2018-05-13
Yes, or occasionally run firejail --version and see if it has changed.

---

### Post by poorguy on 2018-05-19
Hey All,

The new version of*** firejail*** ***0.9.54_1 ***works for*** firefox 60*** or does for me.

[https://sourceforge.net/projects/firejail/](https://sourceforge.net/projects/firejail/)

---

