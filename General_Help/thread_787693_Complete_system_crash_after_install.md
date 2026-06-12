---
title: "Complete system crash after install"
date: 2008-05-09
forum: General Help
---

### Post by .rdg on 2008-05-09
Hi,

I just installed Hardy Heron a couple of days ago on my Thinkpad R61i. Everything worked fine for a week or so. Yesterday I stumbled upon bonobo-server-activation error (code 3), so after some tries to correct the problem (workarounds from this forum) I just gave up and reinstalled.

Just before reinstalling I made a backup of my /etc settings and made a list of packages (dpkg-query -l). There were just few from the partner repo (opera, flashplugin-nonfree, acroread, java) and 3 packages which were not in official repos (tuxcmd, pidgin-tlen and ubuntu-tweak). They were all working fine before the 1st system crash.

After the full reinstall (have a separate /home, but moved my old account settings elsewhere) I did some changes here and there to make my system as close to what it was before (with updates of course). After that I did a reboot, after which I'm not even allowed to login in gdm or console (resource termporarily not available).

Gutsy Gibbon was working ok on this laptop, but I don't intend to come back to it (not wanting to work with crappy ndiswrapper wifi, which now is changed to iwl oss - too many crashes during last 6 months as for my taste).

So I'm waiting for any suggestions as to how to get over the silly errors. I suspect there *might* be a problem with me overwriting /etc files (but the rights were preserved as they were), but it's just my experience from RHEL's SELinux stuff I got furious over once :)

Thanks in advance for any info.

---

### Post by .rdg on 2008-05-09
I was not verbose enough about the gmd login I think. I enter the user/pass, which are fine but then it just stucks at "brown screen" :D with no I/O going on.

As for console login (ctrl-alt-f1) - just the info of the resource not being available.

---

### Post by .rdg on 2008-05-09
I decided to give it one more try before going back to some other distro before it is solved (have to work on something). This time I will omit copying etc settings directly. Instead - normal vi modyfication.

---

### Post by .rdg on 2008-05-09
Same problem narrowed down a little bit. After a complete system install and package update - it all goes fine. After some tweaking and installing additional software - system is not available after a clean reboot.

Don't have a clue as to what is exactly the problem here - the stuff I did was so generic it shouldn't be causing so much problems.

Sugestions anyone?

---

### Post by wdaniels on 2008-05-09
I can't say I really have any idea what the problem might be, but in the absence of any better feedback I would suggest the following:

[LIST=1]
[*]See whether you can log in to a failsafe session (in which case the problem might lie with the gnome settings)
[*]See if killing bonobo-activation-server from terminal allows you to log in.
[*]Look for errors in the system log and post what you find.
[/LIST]

---

### Post by .rdg on 2008-05-09
Ok the problem's solved (at least I know what caused such strange side-effects) -> PAM. I assume it was me who did the mess in /etc/security/ with limits and access and activate them not only in ssh but login facilities of PAM.

Anyways - my apologies to Ubuntu Team. It seemed the problem was in the OS, but as usual it was the admin who screwed up :D

---

