---
title: "password separation"
date: 2007-12-30
forum: General Help
---

### Post by docorange on 2007-12-30
hello everybody
I'm a new ubuntu user. I have had previous experiences with linux, and, after my first ubuntu installation, I noticed something very weird: there is only one password for the common user as well as for the root user. How can I divide them, and eventually how can I log in as root, since there is no grub menu entry for that?
Thank you very much
docorange

---

### Post by taurus on 2007-12-30
Actually, it's not true.  There is no password for root since it's locked as default.  You use your own password when you run sudo/gksudo with root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by docorange on 2007-12-30
I just read the doc you posted, but I still don't understand how can I get an ordinary root user. I need to have a root user on my system, so that normal users don't have any administrative rights
Thanks
docorange

---

### Post by taurus on 2007-12-30
The first user that you created during the installing process can run sudo.  Everybody else that you create after that cannot use sudo _unless_ you add them to groups admi & admin.  So, if you don't want the first user to run sudo, then remove him from group admin.  

It is not a good idea to create password for root and log in as root because if you don't know what you are doing, you can crash the machine beyond repair.  So, use sudo if you need to write or modify something to your system.  It's safer that way (still be careful with it though).

---

### Post by docorange on 2007-12-30
I know that, and I can understand it, but what, if I wanted to have a root user so that I can act as if I were using any other linux distribution?
thanks
docorange

---

### Post by taurus on 2007-12-30
```
sudo passwd root
```

---

### Post by docorange on 2007-12-31
I used the command you suggested sudo passwd root, and everything went okay... at first. When I try to use root privileges from the console, everything is fine, but when I try to do so using a gui, there comes the disaster. For instance, I have no problems in installing packages with a console, through apt, but when I use synaptic, I'm asked for the root password, I insert it, and I get the "wrong password" message. So I try to insert my user password, and strangely enough, it seems to thinks, that my user still has root privileges. The very same thing happens with a lot of programs, such as dolphin's function "browse as root".
How can I get through this?
Thanks
docorange

---

### Post by docorange on 2007-12-31
help!!!

---

### Post by taurus on 2007-12-31
Are you running synaptic from your regular account?  Even if you have created a password for root, your account still has a root privilege for sudo/gksudo so not sure what you mean you are surprised by that.

If you really want to log in as root, run

```
su -
[root password]
```
Keep in mind, you now have complete control of your machine so better be careful since I am not taking any responsible for your own action.  You crash it; you fix it.

On the other hand, if you want to browse your machine as root privilege, try

```
gksudo nautilus
[use your own password]
```

---

### Post by docorange on 2007-12-31
all I want from my system is a user without ANY root privileges, and a root user that can take over every single privilege left by the user. When I run synaptic from my regular account, I expect my system to ask for and accept only the new-created root password.
How can I deprive the user from the root privileges it has?
Thanks
docorange

---

### Post by mcduck on 2007-12-31
Just remove your current user from the admin group, or create a new user (new users don't get admin rights (the right to use 'sudo') by default.

To remove admin rights just go to System/Administration/Users and Groups, select your user and then on the USer Privileges-tab disable "Administer the system". Of course this should be the last time you ever see this dialog, as your normal user hasn't got rights to use it any more, and one should never log into desktop as root so from this on you should handle things like this from CLI only..

IMHO you are just making things harder for yourself without actually gaining anything. :)

---

### Post by cybervegan on 2007-12-31
Just use System>Administration>User manager to add another user.

If you leave the user privileges at default, this user will not have rights to sudo.

When I install an ubuntu system I usually create the first user as 'sysad' and create normal users ('restricted users' in ms-speak) for everyone who will use the machine.

Enabling root is probably not what you want to do. If you want to keep the original user name, create a new user and give it administrator rights, and then downgrade the original user.

BTW, in order to get a root shell here's a little spell for you:

sudo su -

When executed by an administrator user, this will give you a root shell, as if you had logged in as root. Remember this is really dangerous if you are prone to typing mistakes or don't understand the commands you are typing!

With ubuntu, when you type sudo, the password you are prompted for is your own, not root's. Even if you enable root, it will still be *your* password you use with sudo or any of its variants.

hth,
-cybervegan

---

### Post by docorange on 2008-01-02
Thank you cyber, taurus, and mcduck! you see, I'm not doing this because I think it is actually useful, but because of my own stubbornness.
Thanks again
docorange

---

