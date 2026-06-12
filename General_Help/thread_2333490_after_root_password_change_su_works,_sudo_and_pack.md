---
title: "after root password change: su works, sudo and package update from GUI does not"
date: 2016-08-10
forum: General Help
---

### Post by sir2 on 2016-08-10
Hello,

I have forgotten my root password. So I started my Lubuntu 16.04 in recovery mode, went into root menu and entered
```
mount -o remount,rw /
passwd USER_NAME
```
and typed my new password. I then did exit the shell, so the system should continue reboot. This caused some errors, so I had to switch off my laptop and start it again. Unfortunately my new password did not work. Tried a second time, still did not work. I searched the net and found that I should try (after changing the password)
```
synch
mount -o remount,ro /
```
However, synch gave an error, no such command exists, only the second call to mount was successful.

After doing all this, I can now call su in a terminal. So now the password change worked. However, I still cannot update my packages from the GUI, I get the error Authentication failed. Wrong password? And sudo does not work, either. I checked groups, I am in the group sudo, and I am in /etc/sudoers.

Does anyone have an idea what I can do to get a fully working password again?

Thanks in advance

Ciao
Claus

---

### Post by ajgreeny on 2016-08-10
Did you wait for the prompt to re-enter your new password a second time following the **passwd *username*** command?  I am not certain from your post whether you did that or not.

---

### Post by sir2 on 2016-08-11
> **ajgreeny said:**
> Did you wait for the prompt to re-enter your new password a second time following the **passwd *username*** command?  I am not certain from your post whether you did that or not.

Hi, 
sorry for being unclear. Yes, all the times I did enter the password a second time. And actually the last time it did work. However it only worked for the command su, not for sudo and not for the GUI.

---

### Post by &amp;KyT$0P# on 2016-08-11
What is the full exact **su** command you're entering that works for you?

---

### Post by ajgreeny on 2016-08-11
> **halogen2 said:**
> What is the full exact **su** command you're entering that works for you?
Good point.  We do not use **su** by default in Ubuntu; in fact the only time I have ever used it in my 11 years of Ubuntu use was in the manner of an option for sudo, ie **sudo su**.

To get root permissions for a command we use **sudo <command>** and then use our user password, not a root password as the root account is disabled by default in Ubuntu.

Did you enable the root account by any chance?

---

### Post by sir2 on 2016-08-11
> **halogen2 said:**
> What is the full exact **su** command you're entering that works for you?

Well, I did not add anything to su, just these two letters and then I hit enter. I tried this after the first unsuccessful changes of the password, and there the new password did not work (ie I got an error about wrong password). Now it works. After running su I did run **whoami** and **groups**, both giving me **root** as an answer. I also can do something like **cat /etc/sudoers**. After running **exit** again I'm back to my normal user and I get permission denied from that cat-command.

---

### Post by &amp;KyT$0P# on 2016-08-11
What you have done is not to change your account password but change the root password and enable the root account.  So try again to change the user account password, since you don't know it you'll have to do it from root, so in a Terminal type:
```
su
passwd USER_NAME
```

Then exit out of su and see if you can sudo (from the user account) using the new password.

Only when you are 100% sure your user account password works as expected and you can sudo, only then should you lock the root account again.

---

### Post by sir2 on 2016-08-11
> **halogen2 said:**
> What you have done is not to change your account password but change the root password and enable the root account.  So try again to change the user account password, since you don't know it you'll have to do it from root, so in a Terminal type:
```
su
passwd USER_NAME
```

Then exit out of su and see if you can sudo (from the user account) using the new password.

Hey, thank you very much! So I most likely forgot to add my user name as parameter to passwd? 

> **halogen2 said:**
>  Only when you are 100% sure your user account password works as expected and you can sudo, only then should you lock the root account again.

OK, so I did 
```
sudo passwd -dl root
```
Indeed, just **su** no longer works, while everything else works perfectly. Again, thank you very much!!

---

### Post by &amp;KyT$0P# on 2016-08-11
You're welcome!  :KS

---

### Post by sir2 on 2016-08-22
Hi,

somehow I still have some trouble with my password,  something is still wrong.

The first thing I noticed was, that I no longer have to enter a password if I want to update the system. 

The other thing is, that I get an error (or just warning?) when installing new packages. If I go to the Synaptic package management, I get the following error if I try to install:

```
W: Can't drop privileges for downloading as file '/root/.synaptic/tmp//tmp_sh' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Keine Berechtigung)
```

The new software is ready to use nonetheless, so maybe I can just ignore this warning. But I thought as there is obviously something wrong it might be a good idea to try to fix it.

Any ideas what might be wrong?

---

