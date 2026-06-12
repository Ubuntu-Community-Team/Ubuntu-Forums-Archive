---
title: "ubuntu crashed bad and i desperately need the files inside, PLEASE HELP"
date: 2013-03-06
forum: General Help
---

### Post by mikesmithxvx on 2013-03-06
i apologize, i am not trying to bypass searching for the answer to my question but i am not the most computer savvy person out there.  any help, even just linking to some posts that deal with this problem would be appreciated. basically what happened is that my laptop got shut while a video was playing.  later, when restarted for the first time since being closed, all i get is a purple screen if i try to start ubuntu normally. i tried loading in safe mode and tooling around with the command prompt, but i know nothing about the commands.  any help would be greatly appreciated.

---

### Post by GameX2 on 2013-03-06
Put the Ubuntu CD inside your computer, and choose "Try Ubuntu".  You'll boot from a Live Session, and most probably be able to get your files back!

---

### Post by mikesmithxvx on 2013-03-07
awesome, thank you.  i am going to try that literally as soon as i finish this reply.

---

### Post by mikesmithxvx on 2013-03-07
ok, i have loaded the trial ubuntu but it is showing none of my files.  i know my way around computers but i am in no way a programmer, but with that said here it what i am thinking is going on.

a video was playing when my laptop got closed, however it also got the battery and power pulled from it(dont ask why, it was a fight with someone over something ridiculous).  i was reading the wubi guide at this link:   

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

if i am understanding this guide correctly, i am guessing i totally corrupted ubuntu's ability to operate.  now the guide also says that i can copy the root.disk, reinstall ubuntu, and retrieve my files.

am i on the right track?  i sure hope so, because i am in MAJOR trouble if i cannot get to these files.  this is not like "i lost important college papers" trouble, more like "i just lost my job" trouble.

---

### Post by Cheesemill on 2013-03-07
Have you tried mounting the root.disk file from a Live CD?
[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)
If your root.disk file is intact then this should let you recover your files.

If your root.disk file is corrupted, then your only option is to restore your files from your most recent backup.

---

### Post by bcbc on 2013-03-08
See [http://askubuntu.com/q/228709/14916](http://askubuntu.com/q/228709/14916)

I'd first run the chkdsk shown there. Then you might still want to fsck the root.disk from the live CD.

---

