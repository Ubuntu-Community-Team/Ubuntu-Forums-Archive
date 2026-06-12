---
title: "Problems disabling services"
date: 2007-09-02
forum: General Help
---

### Post by penguinchrissy on 2007-09-02
I'm having problems after disabling some services trying to make my desktop faster. When I login I get this Internal error "failed to initalize HAL !".  Then when I try and get back to services or shared folders after enetering my password I get this error. "**The configuration could not be loaded** You are not allowed to access the system configuration." 
Is there any way to fix this without a complete rehaul?

---

### Post by bam1234567 on 2007-09-02
well you could try to go into recovery mode (pressing esc when it says booting grub please wait or press esc...2...1...) then select the kernel with (recovery) next to it let it boot, and
If your login name is paul then type the following, obviously substitute your own login
**su paul**
then press enter you are now logged in at the prompt as paul.
**startx**
it said x was already running... problem... type
**sudo startx**
enter your password
Now you should get to roots desktop... now you should have access to everything

Hope this helps

---

### Post by penguinchrissy on 2007-09-02
I did what you said but I still get this message when doing anything such as services.
"The configuration could not be loaded You are not allowed to access the system configuration." 
Thanks for trying everything you said did work.

---

