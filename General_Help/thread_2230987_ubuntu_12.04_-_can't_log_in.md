---
title: "ubuntu 12.04 - can't log in"
date: 2014-06-22
forum: General Help
---

### Post by ziig_starD on 2014-06-22
I have my computer set up to not require a password on startup. I use an admin user account. Today on startup I get a screen asking me to choose between my account or the guest login, which asks me for my password. When I enter a wrong password it says "invalid password, please try again", when I enter my password it seems to load but jumps straight back to the same login screen, but I'm sure my password was correct since otherwise it would've given me the "invalid password" message. On the guest account I've used programs that asked my password for permission, so once again I'm 100% sure I'm not just trying to get in with the wrong pw.

Yesterday I installed a new windows program using Wine, so I guess that is what caused it, even though I'm sure it's a legitimate program and not some virus or shady thing, since I use it on my Windows computers all the time without any problems.

Apart from rebooting I've tried nothing, and I'm all out of ideas. I really need access to my account, there's some files on there I really can't afford to lose. It's a laptop so I'm reluctant to try and open it up and put the harddrive in another computer and try to get them off... Please tell me what to do and please keep in mind I'm not familiar at all with command lines and terminals.

---

### Post by Impavidus on 2014-06-23
Your automayic login fails, and therefore you are returned to the login screen. Logging in from the login screen fails again, returning you to the login screen again. There's nothing wrong with your password, but the graphical session crashes as soon as it starts. This is usually (but not always) caused by a permission problem with the file .Xauthority.

To solve this we need some terminal work. At the login screen, hit ctrl-alt-F2. Log in with your username and password. Then run these commands:```
ls -ld ~
ls -l ~/.Xauthority ~/.ICEauthority
```(That is ell es space dash ell (dee))
The response should be similar to```
$ ls -ld ~
**drwx**r-xr-x 56 **username username** 12288 jun 23 09:28 /home/username
$ ls -l ~/.Xauthority ~/.ICEauthority
**-rw-------** 1 **username username**   52 jun 23 09:28 /home/username/.Xauthority
**-rw-------** 1 **username username** 1610 jun 23 09:28 /home/username/.ICEauthority
```
The bold text has to match exactly (except that you have to substitute your own user name).

If the owner of .Xauthority is wrong (it doesn't say **username username**), which is the most likely scenario, run this command to fix it:```
chown username:username ~/.Xauthority
```(Again, substitute your user name). Then use the command```
logout
``` to log out and use ctrl-alt-F7 to return to the login screen. You should be able to login.

If something else is wrong, post the output of those commands here.

---

