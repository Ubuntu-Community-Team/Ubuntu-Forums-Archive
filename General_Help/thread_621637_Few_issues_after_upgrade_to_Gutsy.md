---
title: "Few issues after upgrade to Gutsy"
date: 2007-11-23
forum: General Help
---

### Post by x1a4 on 2007-11-23
Hi,

I've a bunch of issues after upgrading Xubuntu from Feisty to Gutsy.

1) Consoles are gone, yet according to ps the gettys are running.
When I boot with the previous kernel the consoles show up but X is
blank, and when I run startx I get a message the server is already running 
on display :0.

2) Firefox crashes periodically with exit code 139.  The only time I was 
able to reproduce the crash is when visiting ubuntuforums.org.  It doesn't 
matter which profile is used or which user is running Firefox.

3) My main user account, the one I used to upgrade, works more or less 
fine, but whenever I switch X displays, regardless of what desktop it's 
running, the screen is blank and I have to open an application to see 
what's on the screen.  Sometimes refreshing the desktop or switching 
workspaces will do the trick but not always.  This does not happen on the 
main account.

4) I cannot set Nvidia settings except on the main account. On any 
other I get a message I'm not using the Nvidia X driver and should run 
nvidia-xconfig. I've run it to no avail. According to the Restricted 
Drivers Manager nvidia is running, and in xorg.conf the driver is set to 
'nvidia'.

How do I fix these problems?  Thank you.

PS I upgraded using the Update Manager.

---

### Post by x1a4 on 2007-12-14
Anyone?

---

### Post by PLAY3ER on 2007-12-14
sorry i can't answer your questions but, i can say that updating to a new release can make more problems then you had ( if any ) , you could try a fresh install by downloading the ISO and making a CD

---

### Post by x1a4 on 2007-12-30
Never mind.  After recent kernel upgrade things got a whole lot worse and I just reverted back to Feisty.

---

