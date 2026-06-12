---
title: "Users Settings 'Could Not Authenticate'"
date: 2008-05-28
forum: General Help
---

### Post by chlhardy on 2008-05-28
Howdy,

So I was working on getting virtualbox installed and was having problems overwriting some file.  So I tried giving me more rights and that didn't work.  So then I created an admin account and now I cant unlock users settings to change anything.  I keep getting a 'Could not Authenticate' message when I click unlock.  Also, I dont have access to synaptic or things like that.


Any idea?

Thanks

---

### Post by PmDematagoda on 2008-05-28
Post the output of:-
```
sudo -i
```

---

### Post by mastermike14 on 2008-06-05
> **PmDematagoda said:**
> Post the output of:-
```
sudo -i
```

hi i got the same problem and its says that my user name not found in sudoers file. this incident will be reported, why isnt my name found? i just installed ubuntu and i am logged on as admin? does it have something to do with user groups?

---

### Post by Master Chief on 2008-06-05
Seems like you tried to add the user to the group "vboxusers" and accidentally removed the other groups from the user, including the admin group hence the user is no longer part of sudoers

Open een terminal and type: groups

You probably only see two groups, right? 

reboot you computer in maintenance mode and enter:

vigr <enter>

Now add the user to the admin group, that will fix this error.

restart your computer and fix the other user groups by opening/unlocking the settings panel/window.

---

### Post by heatpumpcontrol on 2009-01-14
OK, I had this problem too fixed it using the following steps. I have two admin accounts.... I do this for two reasons
 
1- it's good to have two admins just in case one goes down and 
2- I have a second user on this machine.

Do the following:
1- log in under the other (admin) account. That account did not have a problem at all accessing the administration links.

2- Unlocked the 'Users and Groups'

3- Go to the faulty account and double clicked it

4- Select 'User Privileges' tab

5- Uncheck the 'Administer the system' box and click 'OK'

6- Redo steps 3 and 4 and recheck the 'Administer the system' box and 'OK'

7- Log out and log back in 

Good luck

If you don't have two admin accounts or don't have another account try this [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=162867"). You may have to create another account. Another option if you're good with terminal is to restrict the faulty account of its 'admin' privilege then reassign it the 'admin' privilege. I'm not that good yet so I depend on a gui still.

;)

---

