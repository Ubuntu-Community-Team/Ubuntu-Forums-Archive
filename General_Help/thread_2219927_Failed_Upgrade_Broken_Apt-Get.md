---
title: "Failed Upgrade: Broken Apt-Get"
date: 2014-04-26
forum: General Help
---

### Post by Uruz on 2014-04-26
Saluton,

So, I tried to upgrade to 14.10 and the upgrade failed.
This is frustrating because it leaves me in a semi-upgraded state until I get a chance to try again.
After trying to install something to fix a mounting error, I noticed something extremely disconcerting.

In a terminal, any "sudo apt-get" command returns "Segmentation fault (core dumped)"

I'm not exactly new to Ubuntu, but I have no clue how to approach this problem. Any suggestions?

Thanks for your help

**EDIT**
Seems to happen from ANY sudo command

---

### Post by monkeybrain20122 on 2014-04-26
Why would you want to waste a few hours to "do it again" even if you can? Backup your data and do a fresh install. There is no point wasting time trouble shooting a blotched upgrade. 

Next time always do fresh install. "Upgrade" is fragile, takes a long time and you need to restore the system to a prinstine state for it to succeed. For all that fresh install is a lot faster and more trouble free.

---

### Post by deadflowr on 2014-04-26
14.10?

Anyway, if you have synaptic, try opening that and look at custom filters at the left pane, then click on broken.
does it list any broken packages?
If so, select all and apply, see if that fixes it.

Otherwise a fresh clean redo might be in order.

What method of upgrade did you use,anyway?

---

### Post by Uruz on 2014-04-26
Reinstalling the broken packages does nothing (and does not remove them from the list). They're all Samba related, anyway.

I upgraded through the update-manager.

Also, of course I could do a reinstall. I'm here looking for a less-destructive solution.

The Samba files seem to have unmatched dependencies... I've tried to remove them through aptdcon, but it fails out because it tries to check their dependencies.

---

### Post by jbcamps on 2014-04-28
I have encountered the same samba-related issue while upgrading. For the moment, I was able to restore my ability to sudo by uninstalling samba-libs in Synaptic (though now, apt-get suggests me to autoremove apturl and various other packages, such as linux-image and linux-headers, which I did not dare to try to do yet).
I have filed a bug report : [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1313739?comments=all](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1313739?comments=all)
There is a related question on AskUbuntu, [http://askubuntu.com/questions/449325/failed-upgrade-of-l-xubuntu-13-10-to-14-04](http://askubuntu.com/questions/449325/failed-upgrade-of-l-xubuntu-13-10-to-14-04)

---

