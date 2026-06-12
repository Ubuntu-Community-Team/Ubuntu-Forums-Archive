---
title: "[SOLVED] Security: disabling 'root' account?"
date: 2007-11-02
forum: General Help
---

### Post by perixx on 2007-11-02
I'm a bit confused about the 'root' account in Xubuntu:

> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If for some reason you have enabled your root account and wish to disable it again, open a terminal and issue the following command:

sudo passwd -l root


this suggests, that the root account should be disabled. 

But when I check in the users/groups manager, 'root' is there - including a password that's of the same length like my user-password is. Though it has set no permissions. How can I verify if 'root' is really disabled?

Will the 'sudo passwd -l root' command have any impact on my user account and its 'sudo' abilities?


perixx

---

### Post by KingWilliam on 2007-11-02
I am just a noob but i believe that the root account does exist and has normal root account permissions, but you are just not allowed to sign in with it. The password is the same as your user password because I believe that during the installation ubuntu takes your password for the root password. So if you run a command using sudo, you actually are using the root account but not logging in with it.
So if you change the root password, your user password will stay the same, but if you give a sudo command you'll have to type the new root password

Im not sure about it, but I think its possible.

Greetz...

---

### Post by az on 2007-11-02
By default, the root account is disabled.  There should not be a password set for it.

That doesn't mean that there are no files on the system with root ownership.

---

### Post by perixx on 2007-11-02
Thanks for the hint, KingWilliam...

But why is there a password set for 'root', az?
Are you really sure my root account isn't activated - how could I verify that? By trying to open a root session at login?

Besides, what can I do if I have to manually move root-owned files?


perixx

---

### Post by Ramorous on 2007-11-02
try "ssh root@localhost" and try to login. If that works, then the account isn't disabled.

Another method is switching to ttyX. "Ctrl-Alt-F1" (F1 through F6). To return to GUI "Ctrl-Alt-F7".

While I'm on the Ctrl-Alt wagon, you may also want to know "Ctrl-Alt-Backspace" this will restart the GUI interface.

Cheers

---

### Post by chrislau on 2007-11-02
1) The root account exists. It is the owner of the system
2) The root login is disabled. That doesnot mean there is no password for root. **If there were no password, then, anyone could login, with "login :  root" and then press return when asked for the password.** Some other means are used to disable root acces. For example it'is possible to deny root logon threw telnet, etc. But that means nobody should know that password
3) The root account is accessible with sudo. For example, enter : "sudo su -" with your power user and you have almost the same access as if you logged with the root account.

---

### Post by perixx on 2007-11-02
Thanks, Ramorous...

It said 'connection refused' - does that mean that ssh is also deactivated? 
I don't want remote connections for this PC, nor do I wanna share files. File sharing isn't installed, so I only needed to know how to remove/disable the ssh- and telnet-services.

Btw., can I remove the 'avahi' Automatic Service Discovery-service savely? 
I've deactivated in the Applications > System > Services anyway... it's said to be a 'potential security risk'...

I'd also like to deactivate the use of IPv6 which is considered unsecure - do you know how to deal with that as well?


thanks, 
perixx


P.S.: so this means, that I should apply a different password for root, that will be required for 'sudo' access as well in future, as mentioned before? How to change the root password if login isn't allowed?

---

### Post by KingWilliam on 2007-11-02
if you want to log in as root, go to system> login screen somwhere in that configuration panel you will be able to activate root login. If you do that you can login as root, which proves that there IS a root account and it has a password. But it is not wise to use that account. But if you need to do things for wich you require root priviliges, you can use the "sudo" command. That command ask a password, he password of the root account indeed, wich is set on the moment that you installed your system. Ubuntu automatically takes the password from your first user for that.

Don't take me to serious. Like i said i am still a noob in Linux. But I have the feeling that Im right about this one :)

---

### Post by mrpeenut24 on 2007-11-02
Here it is:

1) Ubuntu default installs with root login disabled.
2) The root password is disabled.  You can tell this by looking at /etc/shadow:
> sudo more /etc/shadowThe ! means disabled.
3) The root password will in NO WAY affect your ability to use sudo.  This is controlled by the file /etc/sudoers.  Ubuntu defaults to allow anyone in the group 'admin' ability to use sudo with *their own password*.
4) Even with root login disabled, you can change to the superuser on your computer by typing > sudo -s
5) The reason all of this works is because sudo is a separate program from the user root.  Sudo simply changes your userid to root's once you put in *your own password*.


If you're worried about security, as it seems you are, don't mess with much in the root login.  It's default-installed to be secure.  Don't enable the root login
as it's disabled to begin with.

---

### Post by perixx on 2007-11-02
Hi mrpeenut24...


Thanks for your reply! I understand that 'sudo' is invoked with the account's specific password, now...

I'm not trying to enable the root account, I just read some guy's problem before who had only bash availible and was locked out from his X-server - he wanted to move some root-owned file - that's why I asked.

Me personally, I want to make sure 'root'-account is **disabled**!

```
sudo passwd -l root
``` -- that is what I wanted to know, if it would affect my current user's 'sudo' ability (if 'sudo' is only a **reference** to the 'root'-account's 'sudo'-program as it seems to be)....

By the way, looking into the /etc/shadow file - do you know what 'nobody' is? Is that similar to Window's 'anonymous/guest' account?


perixx

---

### Post by mrpeenut24 on 2007-11-03
You shouldn't need to do the run the "sudo passwd -l root" command.  Root should be locked out from the get-go.  But it also shouldn't hurt to do it.  If you want to move a root owned file, even if it's readable *only by root*, you only have to issue the command: > sudo mv *file destination*

To the best of my knowledge, and this is admittedly limited, the user 'nobody' is assigned to a process (daemon) that should not be modified.  For instance, say you're running a web server.  If it's set up automatically, it shouldn't be interfered with.  Therefore it may assign itself the userid 'nobody', so that nobody is allowed to change it.  The reason is, since the userid 'nobody' is already taken, it cannot be assigned to any normal user.  Therefore, if you want a process (or perhaps even a file) to be unable to be modified by *anyone*, you might assign it the userid 'nobody'.  I may be off slightly on this, but it's usually a good idea not to assign a file the owner id of 'nobody'.  Instead, assign it root.  The wikipedia page describes it pretty well: [http://en.wikipedia.org/wiki/nobody_(username)]("http://en.wikipedia.org/wiki/nobody_%28username%29")

---

### Post by perixx on 2007-11-03
Ah, yes, interesting!

Thanks for clarifying that... well, so I can put my mind at rest regarding this matter :]

You also happen to know sth. about the Ubuntu-services like 
telnet, ssh, avahi and filesharing?

I don't need them, thus I want to disarm or even remove them, if possible.


perixx

---

### Post by mrpeenut24 on 2007-11-03
You can look for boot-up manager:
> sudo apt-get install bum then run it by either typing 'sudo bum' or by looking in System>Administration>Boot Up Manager.  If you go to Advanced Mode, you can see many (not all) of the services that run at startup.  By unchecking them you can disable them from running at startup.

---

### Post by perixx on 2007-11-04
Thanks, mrpeenut24...

I'll try that "bum" anytime soon! 

Meanwhile, I've stumbled upon something really interesting:

> [http://ubuntuforums.org/showthread.php?t=89491&highlight=atd](http://ubuntuforums.org/showthread.php?t=89491&highlight=atd)

but there's no explanation for most of my mentioned tasks (telnet, avahi and filesharing), unfortunately, and how to configure them savely.


perixx

---

