---
title: "Grub awareness of hibernation in Linux and Windows in Dual-boot"
date: 2014-02-06
forum: General Help
---

### Post by mike134 on 2014-02-06
I have a dual-boot of Windows XP and Lubuntu 12.04, so if I hibernate in either Windows or Linux, then I want grub to thaw the system that is hibernated and for Grub not to give me a choice (or at least give me a warning) to boot the other O/S.  Looking at other forums, this is possible and the theory is quite straightforward:
[LIST=1]
[*]When hibernate in Linux, run script, so that Grub boot Linux when Grub is next called on the next power on
[*]Grub should check hiberfil.sys to see if Windows is hibernated and boot Windows if it is
[/LIST]

There is a forum discussing checking hibernate for Linux at [https://features.opensuse.org/308705](https://features.opensuse.org/308705) where this says Suse has the feature, but Ubuntu does not - how do I implement this feature in Lubuntu
There is a thread at [http://lists.gnu.org/archive/html/grub-devel/2011-12/msg00011.html](http://lists.gnu.org/archive/html/grub-devel/2011-12/msg00011.html) which has grub code to check for Windows hibernation, but I don't know how to implement this - has this code being incorporated into Grub (if so how do I enable it) and it it hasn't, how do I add this function?
There is a forum at [http://www.linuxquestions.org/questions/linux-general-1/how-grub-knows-there-is-a-system-in-suspend-hibernate-state-742782/](http://www.linuxquestions.org/questions/linux-general-1/how-grub-knows-there-is-a-system-in-suspend-hibernate-state-742782/) where both features are working, but doesn't say how this is done.

I have a separate drive for my data, so if I mount this drive in one O/S as I haven't realised the other O/S is hibernated with it mounted, then I will lose data, so I want to prevent this.  Stopping Linux mounting hibernated drive is fairly straightforward as I can mount with a script that checks hiberfil.sys file, rather than automount, but it is not so easy to stop Windows mounting a drive if it Linux is hibernated.

Thanks

Mike

---

