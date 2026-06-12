---
title: "cant type lowercase charracters"
date: 2007-08-16
forum: General Help
---

### Post by plop166 on 2007-08-16
Hello,

Im hoping someone out there can help me with this weird problem. Yesterday i was playing with xserver config and i changed the keyboard settings. Now when i boot up I cannot enter some lowercase charracters. By some strange twist of fate all the passwords for the accounts i have on the machine require a lowercase 'p' which i cannot enter. Thus im locked out of my machine and cant fix the problem!

Any ideas on how to get around this? I really dont want to format and reinstall as i finally got everything working.

Please let me know if you can help:)

Thanks in advance .

---

### Post by SPr on 2007-08-16
Do you have the Ubuntu install disc?

Stick the installation disc in the disc drive and reboot then select "Rescue a broken system".

IIRC you'll get to the busybox shell so mount the partition with the broken x server and chroot into it. You should then have access to the partition and a bash shell.

I don't know if you'll be able to run the x server config program from here or whether you'll just have to edit the config files.

Forgive me if I'm way off target with this suggestion but I'm new to Linux :)

---

### Post by plop166 on 2007-08-16
Hey SPr hanks for the reply....
Im not seeing an option to  "Rescue a broken system" when i put in my live cd(feisty Fawn).

Is there something im missing here or am i doomed to be locked out of my machine untill i format and reinstall??

Is there anyway i could login from another computer and change the settings that way? Im grasping at straws here :-)

---

### Post by SPr on 2007-08-18
> **plop166 said:**
> Hey SPr hanks for the reply....
Im not seeing an option to  "Rescue a broken system" when i put in my live cd(feisty Fawn).

Is there something im missing here or am i doomed to be locked out of my machine untill i format and reinstall??

Is there anyway i could login from another computer and change the settings that way? Im grasping at straws here :-)

The choice is present on the alternative CD. My mistake.

With the live CD could you mount the partition and edit the config files or chroot into it and run the configuration program? I'm not sure if running that would work  though.

---

