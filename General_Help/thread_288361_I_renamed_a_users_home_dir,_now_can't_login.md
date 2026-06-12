---
title: "I renamed a users home dir, now can't login"
date: 2006-10-29
forum: General Help
---

### Post by gregconquest on 2006-10-29
[B][I]See post #5 below, updates 2 and 3 for the current situation.
Greg[/I][/B]

I am using VMware to run ubuntu, kubuntu, . . ., and I have run into a problem. The VMware kits come preconfigured with users and passwords. Ubuntu's is "ubuntu" as both the name and password, for example. In trying to personalize these virtual machines, I went into "Users" and changed the names **and the home directories**. I neglected to actually move anything into these new directories, or even create the directories. I thought ubuntu would do that for me, since the option to change it was there.

So, now, how can I view the directories available to choose where to login? And what should I have done? Create a new user, log out log in, and then delete the old user?

Thank you.
Greg Conquest

error message:

> Your home directory is listed as:
'/home/munged'
but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory?

---

### Post by bsussman on 2006-10-29
> **gregconquest said:**
> I thought ubuntu would do that for me, since the option to change it was there.

If it did that, how would you tell it to use a pre-existing dir?
> 
So, now, how can I view the directories available to choose where to login?

User home directories belong in /home unless you know exactly why you do not want them there and are willing to go against many decades of convention that helps us talk about things and know what we are talking about.  Sort of like not using the word blue to refer to the color of eggs when white and yellow (actually my chickens lay orange yolks) will do.

Many things like this location although you can put a user's home anywhere you like.
> 
 And what should I have done? Create new user, log out log in, delete old user?

That is generally how I would have done it - you can edit the /etc/passwd file to achieve the same effect but your proposed steps do it with a minimum of fuss :mrgreen:

---

### Post by polt on 2006-10-29
Did you try logging in as /root and fixing the things you changed?

---

### Post by gregconquest on 2006-10-29
> **bsussman said:**
> If it did that, how would you tell it to use a pre-existing dir?

User home directories belong in /home unless you know exactly why you do not want them there and are willing to go against many decades of convention that helps us talk about things and know what we are talking about.  Sort of like not using the word blue to refer to the color of eggs when white and yellow (actually my chickens lay orange yolks) will do.

Many things like this location although you can put a user's home anywhere you like.

That is generally how I would have done it - you can edit the /etc/passwd file to achieve the same effect but your proposed steps do it with a minimum of fuss :mrgreen:

I'm not tryng to change anyone's conception of the color of the sky or discuss what the meaning of "is" is.

I didn't move anything out of /home, I:
1) changed the users name from "ubuntu"to "greg"
2) changed the home directory of the user from "ubuntu" to "greg"
* the problem is that "greg"'s info is actually still in the "ubuntu" directory, I'm guessing.

Greg

---

### Post by gregconquest on 2006-10-29
> **polt said:**
> Did you try logging in as /root and fixing the things you changed?


Logging as root? In looking around the forums, I see discussion about logging in as root from within a terminal, but not from the boot screen. I'm thinking I need to start from a non-GUI screen, rename the directory designated for the users, and then reboot . . . Other approaches?

Since these are all new installs from within VMware, I can also just start afresh from the 6.06 versions, get the user names and passwords down right, and then re-do the upgrade to 6.10. I did some other customizations . . . an hour or two worth [-( A quck edit would be preferrable, though. 

Greg

UPDATE 1: I installed another xubuntu into my VMware Player, booted, then tried making a new user and deleting the old one. I also edited the root user to have another password. Still, there are problems](*,) 

I created the user "greg", gave him the full checklist of powers, rebooted and deleted the pre-existing user, "vmware". Yet now, when trying to enter "Users and Groups", get into I am greeted with:

Error
Failed to run users-admin
Wrong password
Close
   if I use my newly set password.

If I use the pre-existing "vmware" password, I am let in. Loh and behold, vmware is the only listed user. How did the user, vmware, come creeping back after being deleted by the user greg :-k 

Could it have something to do with xubuntu not asking me for my username or pass at evey boot, even after I tried to change the default user?

UPDATE 2: Now, when xubuntu starts, it tries to login directly, hangs, <CTRL><ALT><DEL>(<INSERT> in VMware), releases me to re-login, "vmware" is listed as the user logging in, yet I deleted the user and group. There is no password to this non-existent account. I end up relogging in as "greg"

Somewhere xubuntu has a setting to autologin using "vmware" as user. Where could this setting be? If I fix this, is there anything else I should do in terms of getting this machine away from the pre-setup ID's? Manually change all hidden users' passwords? Are they even set? I actually had residual DNS servers and the like listed in the network settings in one or more of these ubuntu family VMware virtual appliances.

And of course, how can I rectify this situation in my ubuntu and kubuntu machines? Reinstalling them will be quite a bit more labor-intensive than with my near-virgin xubuntu install.

UPDATE 3: At this page: [http://tinyurl.com/ydylwc](http://tinyurl.com/ydylwc) , I was told the login was configured in Applications->System->Login Window->Security Tab. I removed the automatic login there. Now I seem to be able to login everytime with no problems, but there is still an underlying problem.

I have removed "vmware" as a user and the group "vmware", and in creating the user "greg", I gave him all the powers in the checklist. However, if I go into System -- Users and Groups and attempt to edit the users further, I get this message:

> 
Error
Failed to run users-admin
The underlying mechanism (sudo) does not allow you to run this program. Contact the system administrator.
Close


Trying to use "vmware" as a password fails as well, but as the wrong password.

Thanks for any more pointers . . .
Greg

---

