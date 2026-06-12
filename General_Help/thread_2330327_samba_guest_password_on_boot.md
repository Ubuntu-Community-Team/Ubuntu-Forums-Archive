---
title: "samba guest password on boot"
date: 2016-07-10
forum: General Help
---

### Post by jgw on 2016-07-10
I am getting a samba guest password on boot.  I have removed all guest accounts before this ever started.  I never had a samba guest account (as far as I know) but, now I do!  Also don't know what the password is.  I have been unable to find any instructions as to how to remove a samba guest account on boot (with: sudo apt-get remove samba). Removing the samba package, however, may not take care of this samba guest account thing so I thought I would as for thoughts on this one.  

My other problem is that I cannot boot so I am running in recovery mode.  I thought I would try and make a run at removing the lock file (/var/lib/dpkg/lock) but its read only.  I then got a bunch of other stuff but, basically, my problem seems to be that something got interrupted and now my root privileges are not working.  This is odd as my terminal prompt ends with a '#' rather than "$" which, in theory, means that I AM root.   I tried to set a password for root (su) with "passwd -u root" but that failed with "cannot lock /etc/shadow/ try again later".  I just re-booted, to recovery mode and tried again - same failure.

Thank you...............

---

### Post by gordintoronto on 2016-07-10
I'm sorry, but I can't figure out what you are trying to say:

"I am getting a samba guest password on boot."

Could you take a picture?

---

### Post by jgw on 2016-07-11
Sorry - to take a picture of the desktop is not possible given the failure to boot.  Here is one I took with my camera.  It may not be real clear but I tried <G>  What I need to do is to get rid of it so I can actually log in.  I have no idea what my password is and I am unable to deal with any read only stuff when I am in recovery mode.  

If I can't fix this I will remove the drive and run it on another machine to rescue whatever and then reinstall.  I also wonder, if I do that, if I should stick with 14.04 or move on to 16.04.

---

### Post by gordintoronto on 2016-07-11
Can you click on "greg" and enter your password?

---

### Post by jgw on 2016-07-14
Thank you for the replies.  I can enter my password - I just don't know what it is.  I gave up.  I will mark this solved as there seems to be no answers and so I just installed a copy of 14.04.4 I then took the old drive and put it on another machine (external) and took a look.  Half my drive was missing so I was fighting a lost cause.  I think what happened is that I choose to clean up my drive and it REALLY decided to clean up my drive!  (will not do that again).  In spite of the fact that I was in recovery mode and used both sudo and su I could never change any files.  It turns out, given the situation with the drive, that even if I had been able to change anything it wouldn't have made any difference.  In other words I apparently worked really hard screwing this one up! <G>

Thanks again for the replies

---

