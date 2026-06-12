---
title: "Accidentally changed password?"
date: 2013-07-31
forum: General Help
---

### Post by wmmurrah on 2013-07-31
After attempting to install a program called jmetrik, I seem to have changed my root password. I followed the instructions on the following webpage:

[http://www.itemanalysis.com/linux-installation.php](http://www.itemanalysis.com/linux-installation.php)

the program was not installed properly, and now when I use a sudo command my password does not work. When I enter it I get "Sorry, try again." I also can not update software, I get "username is not in sudoer" or something similar. I am not sure what I did. can anyone help?

---

### Post by deadflowr on 2013-07-31
You can try resetting your password
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Although the issue with sudoers seems fishy.
What groups are you a part of
simply type "groups" without quotes in the terminal, and the groups you belong to will be listed.
sudoers are in the sudo group, or admin.
Watch out for adm group as that one has nothing to do with sudo or root, and is a group used for reading log files.

---

### Post by wmmurrah on 2013-07-31
I am in two groups: one is my username and the other is "jmetrik", the program I tried to install.

---

### Post by wmmurrah on 2013-07-31
I tried the password reset, but that did not work. When I attempt to update, I get "Your authentication attempt was unsuccessful. Please try again"

---

### Post by deadflowr on 2013-07-31
You can try adding your user back into the sudo group.
Follow the guide of using the recovery modes root shell and try entering
```
adduser yourusername sudo
```
replace yourusername with your username.

I think your problem stems from the usermod -G command
from the usermod man page
> -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option.


           If the user is currently a member of a group which is not listed,
           the user will be removed from the group. This behaviour can be
           changed via the -a option, which appends the user to the current
           supplementary group list.




Hopefully adding the user back into the sudo group will give you the rights again.

---

### Post by wmmurrah on 2013-07-31
Thanks, but that didn't work either. I have to have root permission to add a user.

---

### Post by VMC on 2013-07-31
Have you tried using the [RecoveryMode]("https://wiki.ubuntu.com/RecoveryMode"), then change your password from there.

---

### Post by deadflowr on 2013-07-31
> **wmmurrah said:**
> Thanks, but that didn't work either. I have to have root permission to add a user.
Did you follow my advice of using the recovery modes, and entering the root shell, like when trying to reset the password.

Follow the reset password guide, and make sure you follow the mount command.
i think recovery mount as read-only, the guide lists the command needed to mount read/write.

---

### Post by VMC on 2013-07-31
> **deadflowr said:**
> Did you follow my advice of using the recovery modes, and entering the root shell, like when trying to reset the password.

Follow the reset password guide, and make sure you follow the mount command.
i think recovery mount as read-only, the guide lists the command needed to mount read/write.

Yes indeed. I missed your posting on the first read.

---

### Post by wmmurrah on 2013-07-31
I did try the reset in recover, but that didn't work. I now don't think I changed the password. Could I have changed who the root user is?

---

### Post by deadflowr on 2013-07-31
> **wmmurrah said:**
> I did try the reset in recover, but that didn't work. I now don't think I changed the password. Could I have changed who the root user is?

No, most likely; it would seem; when you ran the sudo usermod -G command adding jMetrik it wiped your user from the group sudo.
The -G option alone will list only the groups listed in the command, and remove any other not listed.
The proper command should hve been
```
sudo usermod -a -G groupname username
```
the -a appends it and adds the group to the users groups, where as the -G alone sets whatever groups list in the command as the only groups.

Does that make sense?

Having rethought this, I would suggest trying this
1) Boot into the recovery mode
2) open the root shell
3)run
```
mount -o rw,remount /
```
4) then try
```
usermod -a -G adm,cdrom,sudo,dip,plugdev,lpadmin YOURUSERNAMEHERE
```
these are the default groups I have on pretty much all my installs.
6) type exit and go to resume in the recovery mode menu, and start your session.

Don't know if it'll help or not but I'm hopeful.
Also, you might not care for lpadmin, as it is for cups printer configuration, so if you want, ignore it.

---

### Post by wmmurrah on 2013-08-01
Bam! that worked Deadflowr! You are amazing! Live is good again.

---

### Post by arno48 on 2013-08-01
```

Hello, 
I have a similar problem
  	 	 	 	   I changed my password unintentionally, and now I am not able to perform actions
 requiring  authentication as, for instance, installation of updates.
 In detail,  I modified as follows:  
 System Settings/User Accounts/ Unlock/Password: None/ Automatic login: ON
 as you can see in the attached.
 The problem is that the System goes on asking  me for a password, not accecpting the old one any longer.    
 Thanks for you help.
 


  
```

---

### Post by deadflowr on 2013-08-01
> **arno48 said:**
> ```

Hello, 
I have a similar problem
                        I changed my password unintentionally, and now I am not able to perform actions
 requiring  authentication as, for instance, installation of updates.
 In detail,  I modified as follows:  
 System Settings/User Accounts/ Unlock/Password: None/ Automatic login: ON
 as you can see in the attached.
 The problem is that the System goes on asking  me for a password, not accecpting the old one any longer.    
 Thanks for you help.
 


  
```

You need to follow the [Reset Password link]("http://www.psychocats.net/ubuntu/resetpassword") I provided earlier.

None means that the password has been disabled, and so any passwords you try will be for naught.

Following the guide will reset it so you have a password.
In general. you can run your system for the majority of the time without a password, but it is convenient to have.
And not having one set can cause problems one wouldn't think could happen.
Better safe than sorry, as the saying goes.

---

### Post by arno48 on 2013-08-01
```
I am not able to enter RECOVERY MODE, even though I hold SHIFT KEY during booting,
could you please tell me another way to enter RECOVERY MODE
Thanks
```

---

### Post by deadflowr on 2013-08-01
> **arno48 said:**
> ```
I am not able to enter RECOVERY MODE, even though I hold SHIFT KEY during booting,
could you please tell me another way to enter RECOVERY MODE
Thanks
```

Usually with the shift key, you have to presss it when the BIOS screen ends and hold it until the GRUB loading comes up.

However, if getting into it seems too tricky, then You can try the [LiveCD trick]("https://help.ubuntu.com/community/LiveCdRecovery").

Assuming you still have a liveCD somewhere.

---

### Post by arno48 on 2013-08-02
Thank you very much for your kind assistance.
GNU GRUB version 2.00-13 ubuntu3  came up offering several options as:
Ubuntu, with Linux 3.8.0 -26
Ubuntu, with Linux 3.8.0 -26 (recovery mode)
Ubuntu, with Linux 3.8.0 -25
Ubuntu, with Linux 3.8.0 -25 (recovery mode)
Ubuntu, with Linux 3.8.0 -24
and so on.
I selected the "Ubuntu, with Linux 3.8.0 -26 (recovery mode)"
It runned automatically, without asking me for a new password, but at the end the password in Login Options was still "None"

---

### Post by deadflowr on 2013-08-02
> **arno48 said:**
> Thank you very much for your kind assistance.
GNU GRUB version 2.00-13 ubuntu3  came up offering several options as:
Ubuntu, with Linux 3.8.0 -26
Ubuntu, with Linux 3.8.0 -26 (recovery mode)
Ubuntu, with Linux 3.8.0 -25
Ubuntu, with Linux 3.8.0 -25 (recovery mode)
Ubuntu, with Linux 3.8.0 -24
and so on.
I selected the "Ubuntu, with Linux 3.8.0 -26 (recovery mode)"
It runned automatically, without asking me for a new password, but at the end the password in Login Options was still "None"

Did you follow the guide in the reset password link.
After you get into the recovery mode you need to click on the root(root shell) option and then change the mount as it is set as read-only.
Once you remount, changes you make will write to the disk.
It is also important to run the ls /home command to make sure the user is in the home directory.
When you then run the passwd command, it'll ask for a retype of the new password, for confirmation.
When done type exit and then resume.
But it's vital that the mount command be run correctly, because nothing will be saved if that command is wrong.

---

### Post by arno48 on 2013-08-02
As from the attached screenshot the login password has been succesfuly changed.
Thanks a lot for your exquisite assistance

---

