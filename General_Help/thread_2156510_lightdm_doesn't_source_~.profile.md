---
title: "lightdm doesn't source ~/.profile"
date: 2013-06-22
forum: General Help
---

### Post by alanhorizon on 2013-06-22
I'm a little curious why lightdm doesn't source profile. This was a bug two years ago [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/794315](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/794315) and a comment in 2013 says to reopen the bug, so I'm asking here to see if this was a decision.

If so, which bash files do get sourced by the display manager such that we don't have to repeatedly run stuff in bashrc? I know that you can just put everything in bashrc if you want it run in the gnome terminal, but if it's some large configuration script, it makes sense to run only once, which used to be done by putting it in .bash_profile, or .profile.

Cheers,

---

