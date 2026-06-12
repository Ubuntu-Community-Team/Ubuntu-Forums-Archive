---
title: "[SOLVED] Forgotten administrator password."
date: 2008-02-18
forum: General Help
---

### Post by Tiemen on 2008-02-18
I have had a brain implosion (not unusual at 65 yo) and in-advertently removed the tick from the "administer system" option in Users and Groups. I cannot remember my administrator or root password as I never had to use it. Can anyone help?
Thanks in advance

---

### Post by geo909 on 2008-02-18
Wait..
Isn't that the one you choose when you set your account?
I mean, isn't that the same with the password the first user has when ubuntu are installed?

...


Hmm.. Why do I feel like I have said something stupid right now?!

---

### Post by Tiemen on 2008-02-18
I tried my normal password but that is not accepted.  In the System/Administration menu the Manage Users and Groups has disappeared, so no joy there.

---

### Post by ryanhaigh on 2008-02-18
reboot your computer and from the grub menu choose recorvery mode. once the machine is booted you will have a command line root user prompt where you use the command below to add your username back into the admin group. once you are done with that simply reboot the comptuer again (not in recovery mode) and you should be able to administer the system again.

adduser username admin

where username is your own username/login

---

### Post by aysiu on 2008-02-18
> **ryanhaigh said:**
> reboot your computer and from the grub menu choose recorvery mode. once the machine is booted you will have a command line root user prompt where you use the command below to add your username back into the admin group. once you are done with that simply reboot the comptuer again (not in recovery mode) and you should be able to administer the system again.

adduser username admin

where username is your own username/login
More details [here](http://www.psychocats.net/ubuntu/sudo), if you just removed yourself from the administrator group.

If, however, as your later statement indicates, you forgot your password, you can reset it using [these instructions](http://www.psychocats.net/ubuntu/resetpassword).

---

### Post by Tiemen on 2008-02-18
Thanks Aysiu and Ryanhaigh for your prompt assistance. I have done as you suggested and rebooted in safe or recovery mode and then get the following:
     Give root password for maintenance
     (or type Control-D) to continue.

Well, I do not know the root password and when I Control-d the computer boots normally but still with only limited priviliges. 
Can you help further??
Tim

---

### Post by bodhi.zazen on 2008-02-18
OUCH !!!

Easiest thing to do is use chroot

Boot the Ubuntu live (desktop) cd

Mount your ubuntu partition at /media/ubuntu

Then chroot :

```
sudo chroot /media/ubuntu /bin/bash
```

Then set a new root password:

```
sudo passwd
```

Reboot to recovery mode and use your new password to log in.

==========

Alternate is to directly edit /media/ubuntu/etc/group 

```
gksu gedit /media/ubuntu/etc/group
```

Add your user back to the admin group, reboot

---

### Post by aysiu on 2008-02-18
bodhi.zazen's steps will work.

In the future, consider not setting a root password, as that defeats the purpose of recovery mode, which is made for situations like this.

---

### Post by Tiemen on 2008-02-19
Boddhi.zazen, your direct edit solution worked like a charm!!!!!!!!! Pfffff, I had visions of having to re-install etc, etc. THANK YOU and all other posters who replied to the result of the brain implosion.
Thank you,
Tim

---

