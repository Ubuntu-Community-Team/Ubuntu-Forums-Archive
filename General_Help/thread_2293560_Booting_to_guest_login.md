---
title: "Booting to guest login"
date: 2015-09-05
forum: General Help
---

### Post by jgw on 2015-09-05
I see one more posting similiar to this, with no answer.  I am running with 15.04  My firefox kept on dropping out on me so I wanted to update to the newest nvidia driver (355) which seemed to fix the firefox problem on another machine.  I searched and found directions to install that driver.  When installing it also said it much delete the 340 drivers.  I went ahead and ran the install.  I then went to software and updates to see what happened and found no differences.  I then rebooted and the problem started.  When I boot the guest account comes up and asks me to login.  Since I have never used a guest account I entered my normal login password, which did nothing.  I also tried nothing which got me nothing.  Basically I have no idea how to get past the guest account thing.  I thought I had disabled it but, I guess, I was wrong. 

I think I need to get to the booting menu screen but I forget how to get there (actually have no clue).  Any thoughts on this would be appreciated, thank you.................

---

### Post by jgw on 2015-09-06
Ok, I kinda fixed my problem.  First I kept hitting escape during boot and get to recovery mode.  Then you get some more options. I should also add that I ended up trying every option.  I finally got to one (forget the option) which gave me a gray screen and then an actual desktop screen and not a guest account.  I then went to /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf and added a line "allow-guest=false"  This took care of my guest problem.  Then I rebooted.  Now I had a desktop but had lost my unity.  I then installed the gnome desktop and am currently messing with installing cinnamon.

In other words I fixed my problem, created other, etc.  Sometimes, I guess, flailing mightily actually works!  I apologize for the few specifics as I tend to forget stuff that is less than 5 minutes old (artifact of old age)

I will mark this as solved.

---

