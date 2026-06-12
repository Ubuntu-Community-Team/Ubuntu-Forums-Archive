---
title: "User set ups"
date: 2007-08-23
forum: General Help
---

### Post by in_omaha on 2007-08-23
I plan on installing Ubuntu on my sons computer this weekend. I am tired of all the problems with XP and since my son won't listen he now gets to use linux. My question is this. I know that having a user account will keep him from installing software from the package management systems, but is there a way to keep him from downloading and installing .deb files and such? He is very smart when it come s to XP, so I know it will be just a matter of time before he figures out how to do it. I want it where there is no way for him to install programs without me doing it.

Thanks for the help everyone

---

### Post by HermanAB on 2007-08-23
If he has physical access to the machine, then he can reboot into single user mode and do whatever he wants to do.  So, unless you lock the box up in a cabinet he will eventually figure out how to install crap on the machine whether you like it or not.

However, the normal user privilege separation will keep his machine running OK much longer.

---

### Post by p_quarles on 2007-08-23
I agree with the above poster that there's ultimately nothing to prevent him from doing what he wants if he has physical access to the machine. 

For the short term, however, you can make sure his account does not have any administrative privileges (I believe this is the default for the second account created on Ubuntu). Running dpkg requires root privilege, so he won't be able to install .debs. 

You could also surreptitiously install an SSH server on his machine, and check the logs now and then. That way, at least, when he *does *figure out how crack the system, you'll know.

---

### Post by Electrical_shock on 2008-02-16
If a computer was setup so that a child doesn't not have administrative privledges could an administrator (parent) monitor the content the child is viewing online?

---

