---
title: "[SOLVED] Password Not Accepted in Terminal"
date: 2008-01-30
forum: General Help
---

### Post by galeg on 2008-01-30
Evening / Morning / Afternoon

This may seem like a dumb question, but as a new user I am attempting to run a sudo command in Terminal.

sudo apt-get update && sudo apt-get install swiftfox

On pressing Enter, cmd is accepted and the following line is displayed -

[sudo] password for ¨username¨ :

¨username¨ is correct as name I logon to Ununtu 

cursor flashes after : however at this point terminal will not allow any entry..

Obviously I am doing something wrong, but from memory the sudo password worked when I attempted to Wine DVDShrink.

I also have another issue with some non alpha / numeric character eg. ´ requiring the key to be pressed twice before the character is displayed.

Thanks

---

### Post by p_quarles on 2008-01-30
It allows password entry, but doesn't show anything on screen. Just type your password and press enter. It will work. ;)

---

### Post by Joeb454 on 2008-01-30
This is the 2nd thread I've read on this today ;) p_quarles is right. It's a security feature of Linux/Unix machines

---

### Post by galeg on 2008-01-30
Thanks all.

Stuffed if I know what I was doing wrong (tried numerous times) but command line just looped waiting for what I thought was password.

Anyway it eventually worked as suggested, but to no avail as Swiftfox appears to have been removed from the repository as documented in another thread,so I will need to do some further research before trying again.

What I am trying to do is locate a quicker version than Firefox, which on my box is quite slow.

Thanks again

---

### Post by p_quarles on 2008-01-30
Sorry, I missed the Swiftfox part. No, that's not available in the repositories. You can get that here:
[http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by galeg on 2008-01-30
Thanks All for your help

Swiftfox up and operational.

I had a few problems with installing with apt-get so did a manual install.

Swiftfox is much quicker on my Pentium 4 than Firefox was.

---

