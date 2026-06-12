---
title: "Desktop does not appear when logging in"
date: 2014-05-29
forum: General Help
---

### Post by kevin94 on 2014-05-29
HI:

Very new user and have installed Ubuntu 14.04 on an ASUS U35JC laptop  (forget the exact configuration but it was running Win7 and has a 64 GB SSD). 

The install ran fine for a week or so.  I only added a few programs (Chromium, Wine, a resource monitor... not much else).   When logging into the main user account, I can unlock the drive, select the main user, enter password and then get as far as the wall paper.  That is, there are no icons, the menu bar on the left does not appear and the only action I can perform is right click on the desk top (to add a new folder etc...).   There is a Guest account and that will boot up normally and I will see the desk top.

I have also been successful at logging into the main user account via the terminal/command line.   I can browse the directories there and see the few files I created but when I return to the graphical interface (shift-alt-f7), I still just see the wallpaper.

Any ideas where to start?   I have done a search but the fixes I found, specifically: 

1) logging in via the command line logs me in as above - I can browse but no pull up the icons etc on the desk top
2) looking at the auth.log for clues but have no idea what I am looking at.  There seem to be some issues with a "module" called "pam_kwallet.so".. The error is

lightdm: PAM unbale to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: Cannot open shared object file: no such file or directory
lightdm:PAM Adding faulty module: pam_kwallet.so
lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)

It does that twice and then one more time with the last line replaced by the following:

lightdm: pam_suceed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kevin"
lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
lightdm: pam_unix(lightdm-greeter:session): session opened for user kevin by (uid=0)


There's more but I am not sure if this is relevant.


Thanks in advance for any help or a direction I can start troubleshooting this.

Cheers,
Kevin

---

### Post by kevin94 on 2014-05-29
Continued to research.  Perhaps related to this:  [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1309535](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1309535) ?  Not sure though....

---

