---
title: "Can't run some programs after changing some folder permissions"
date: 2015-02-25
forum: General Help
---

### Post by thora2 on 2015-02-25
I am having multiple problems with a new installation of Ubuntu 14.04.  I was using it before, but got a new hard drive.

I managed to give myself permission to access one of the hard drive partitions, and the items under Home.  And rebooted.

Now, I can't get gksu nautilus to run (I can still access the files in Home and my one extra drive).  And I can't get GParted Partition Editor to run (need to format other hard drive partition).  And I can't shut down the computer.  And now my sound is all messed up, and I can't get sound out of my headphones or my speakers.  There are probably more problems that I have not yet discovered.

Help.  Note that I don't share this computer with anyone, so I will want full control, full access, full read/write permissions at all times when I'm logged in.

I don't mind some fixes that require the use of terminal, but I do want to have a permanent solution that runs at all times without ongoing terminal workarounds that I must keep enetering all the time.

Thora

---

### Post by Impavidus on 2015-02-25
If you mess up permissions, things won't work anymore. If you don't know exactly which permissions were changed, it's practically impossible to fix. So reinstall.

We often get requests to help disabling all safety features. Better not to do so, as it usually leads to a broken system sooner or later &#8211; as you noticed. The defaults shouldn't be too intrusive. Once you've finished installing your favorite applications, you hardly ever need to do anything outside your home directory. You only really need the password for installing kernel updates every few weeks.

---

### Post by oldos2er on 2015-02-25
Please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
sudo -i
``` gives you a persistent root terminal.

---

### Post by QIII on 2015-02-25
There are even things in /home you don't want to mess with haphazardly.  Some applications expect particular permissions to be set.  A good example right off the top of my head are some things in ~/.ssh if you use ssh.

If you change permissions or chown directories randomly -- especially if you do it recursively, a reinstall is often your only choice.

---

