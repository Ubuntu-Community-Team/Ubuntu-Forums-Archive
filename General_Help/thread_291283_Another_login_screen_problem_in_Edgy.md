---
title: "Another login screen problem in Edgy"
date: 2006-11-02
forum: General Help
---

### Post by hed on 2006-11-02
I updated to Edgy a week ago, and all works fine (video drivers, firefox plugins, sound...) but I have a problem with the login screen.
When the login screen appears when I start the computer it seems to be ok, with my default theme... I enter the login and the session starts, but then the login screen appears again, but with an awfull theme, "Circles" (círculos in spanish). If I login in this screen the system works fine... If when the login screen starts the first time, if I go to a tty and make a gdm restart, the login screens works ok at the first login...
I tried to reinstall gdm and deleting /etc/gdm but this didn't work...
I don't know what to do with this problem, I searched the forum but I don't find any answer...
Please help!!

---

### Post by hed on 2006-11-02
Nobody has an answer?
I know is no good to do this but I need help!! Please!

---

### Post by BobBlum on 2006-11-02
The reason you have not received an answer is probably that people are overwhelmed with the problems they are having with this upgrade and are unable to come up with solutions.  I sympathize with your problem, as I myself am having login screen problems.  I wish I could find a solution.

---

### Post by hed on 2006-11-04
Well, I think I have a solution for this problem. I don't know if it is the best solution but it works.
I deleted again gdm and all that sounds like it... I deleted /etc/init.d/gdm too. I didn't know how to make a new one, so I copy one from a Dapper backup. Then I rebuild all the links that should be in /etc/rc*.d making "sudo update-rc.d gdm defaults" and then all worked fine.
In the moment, I thought that the problem was in the init.d/gdm script, so I changed all the links in rc*.d to the numbers (K01gdm, etc) that I had in Dapper. Then the problem was there again, so I put again the defaults.
P.S: If anybody could post the numbers (rc0.d/K*gdm, etc) to see if there is a better solution I will greet it. (Anybody with a Edgy working fine :rolleyes: )
P.S.S: I also deleted som files calles gdm**** in /etc/pam.d. I don't know what is/was the utility of this files :confused: but if somebody knows howto recreate them...

---

