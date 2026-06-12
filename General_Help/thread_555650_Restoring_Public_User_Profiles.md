---
title: "Restoring Public User Profiles"
date: 2007-09-20
forum: General Help
---

### Post by ashkev on 2007-09-20
I am using Edubuntu Server and thin clients in a public library.  I would like to have each public profile restored to it's original state on each reboot.  I have found [this tutorial]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux") .  
I think it would work, but I am not sure how to copy and restore all of the user accounts "except" the administrator account:

In the home directory I have: kevin  patron4  patron5  patron6

The tutorial says to do this :

> #!/bin/bash

rm -f /root/Desktop/clean_all.tar

tar -cpPf /root/Desktop/clean_all.tar /home/all


but as I have said, if i do that it will also restore my kevin directory right?
Is there a way to exclude the kevin directory from the tarball? Or is there a way for me to put all of my public profiles in a directory like all?  How would I do that? 

Also, the tutorial mentions that to get the restore script to run at bootup, the bootmisc.sh should be modified.  Would this work by modifying /etc/rc.local?

Thanks

---

### Post by ddrichardson on 2007-09-21
There's an easier way, although it could be circumvented by the user.

If you create a .login file for each user you neeed to restore and carry out the same script actions then it'll carry them out at each user's login. You could do it in .logout for logout to.

---

### Post by ashkev on 2007-09-21
Could you please tell me in a bit more detail what I need to do?  I see that in the home directory there is a file called .bash_logout.  Do I need to create a file called .bash_login?  Also how do I restore only the public logins, and not the administrator account.  I am sorry that I don't know enough to ask the question correctly, but ultimately I want the public profiles to be restored upon each login, but I want the administrative account left untouched.  If someone could walk me through it I would be much obliged.  I aslo know that other librarians would like to know how to do this.

Thanks,

Kevin

---

### Post by ddrichardson on 2007-09-21
> **ashkev said:**
> Could you please tell me in a bit more detail what I need to do?  I see that in the home directory there is a file called .bash_logout.  Do I need to create a file called .bash_login?  Also how do I restore only the public logins, and not the administrator account.  I am sorry that I don't know enough to ask the question correctly, but ultimately I want the public profiles to be restored upon each login, but I want the administrative account left untouched.  If someone could walk me through it I would be much obliged.  I aslo know that other librarians would like to know how to do this.

Thanks,

Kevin

There is no reason why you can't have just one guest account, that everyone can use. There are several ways to accomplish what you want, depending on how you want to control it. I wouldn't use .bash_login/logout as they would execute every time a terminal is opened. The other problem is that if multiple guests were logged in then the restoration could cause a problem for someone already logged in.

It depends on how much you want to control - if it's specific files then you can change the permissions or groups on them to prevent users messing around with them in the first place.

Rebooting, you could add scripts to /etc/init.d but then they only restore on reboot.

The last option is to use cron. Cron is a schedular and can be set to run at a specific time - such as when no-one was logged on.

As for the script itself, you could create a setup how you want it, then archive it:```
cd /home
tar cvfz restore_guest.tar.gz guest
```Then use it to restore the home folder:```
#!/bin/sh
# Restore script
cd /home
tar xvfz /home/restore_guest.tar.gz

```

---

### Post by ashkev on 2007-09-26
But wouldn't having everyone using the same accounts cause problems?  When I have tried this in the past, a single user can be logged into Firefox only once.  When more than one person is logged in as "guest" and the second one tries to open Firefox, they are given a msg stating that firefox is already running.

---

### Post by ddrichardson on 2007-09-26
Firefox, yeah hadn't considered that. It does require individual profile access.  No matter as the same principle applies, just with multiple accounts.

If you want to do it for multiple users, then just add the script to restore to  /etc/gdm/PostSession/Default.

---

### Post by ashkev on 2007-09-26
> As for the script itself, you could create a setup how you want it, then archive it:
Code:

cd /home
tar cvfz restore_guest.tar.gz guest

Then use it to restore the home folder:
Code:

#!/bin/sh
# Restore script
cd /home
tar xvfz /home/restore_guest.tar.gz

Wouldn't this also back up and restore the admin account as well? All of the accounts.. patron1, patron2, patron3, as well as the admin account Kevin, are located in home....  I am not understanding how this would restore the public profiles, while allowing the admin profile to change....

Thanks for your help!

---

### Post by ddrichardson on 2007-09-26
No, as it's only backing up guest, to do everyone you need to do it from /.

The tar command is compressing /home/guest into /home/restore_guest.tar.gz

For multiple profiles just add a tar command for each folder in the same manner. Or use iteration if you're feeling adventurous.

---

### Post by ashkev on 2007-09-26
Thanks! It works great....I also decided that I should remove the files before I restore them so I put this in /etc/rc.local

```
cd /home
rm -fR /home/patron4
rm -fR /home/patron5
rm -fR /home/patron6
tar xvfz /home/restore_patron4.tar.gz
tar xvfz /home/restore_patron5.tar.gz
tar xvfz /home/restore_patron6.tar.gz
```

It apears to be working like a charm.  Thanks for the help.

---

### Post by ashkev on 2007-09-26
> **ddrichardson said:**
> Firefox, yeah hadn't considered that. It does require individual profile access.  No matter as the same principle applies, just with multiple accounts.

If you want to do it for multiple users, then just add the script to restore to  /etc/gdm/PostSession/Default.

Since I am using Edubuntu LTSP clients...it is using LDM rather than GDM.  I am not sure if there is a comparable place to put a logout script.....

---

### Post by ddrichardson on 2007-09-26
Pass - I know little to nothing about the Edubuntu distro.

---

