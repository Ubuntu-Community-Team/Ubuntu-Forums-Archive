---
title: "Revoke user sudo"
date: 2016-11-16
forum: General Help
---

### Post by FerryGnu on 2016-11-16
Hi, I am new to Ubuntu so probably did this the wrong way around. I have my Master account and then created a User for the kids. I  tried to install Flash in the kids account so they can watch videos (with browser parental controls, of course) but it said the "account does not have sudo privilege," or something close to that  I checked online and found that I could grant sudo from the Master account with "sudo adduser kids sudo" and then logged back into kids and installed Flash. All good.  Now I'd like to revoke the kids account  "sudo" status back to "account does not have sudo privilege."  How do I do that? I found a lot of stuff on removing the account but I don't want to remove it, just that sudo privilege.  Thanks

---

### Post by howefield on 2016-11-16
```
sudo deluser username sudo
```

should do it, change username to the correct account name though, that is the one you want to remove from the sudo group..

---

### Post by FerryGnu on 2016-11-16
Awesome, thanks. I have run the command OK and it said "removed from sudo," will test kids account after lunch, but looks like it did the trick.

---

### Post by SeijiSensei on 2016-11-16
First, I'm not sure I understand what you mean by "installing Flash in the kids' account."  When you install Flash from the repositories, it's available to all users.  That's generally true for most software in Linux.  So you did not need to add sudo privileges to the kids' account.  You could have installed Flash from your own account using sudo.

Sudo permissions are handled by adding the user to the sudo group. The quickest way to remove the kids account is to edit the file /etc/group as root with nano:
```

sudo nano /etc/group

```
In the line that starts with sudo, you should see both your account and the kids account listed.  Just delete them from the group then save the file by hitting Ctrl-X and typing "Y".

---

### Post by FerryGnu on 2016-11-16
> **SeijiSensei said:**
> When you install Flash from the repositories, it's available to all users.

Thanks, but that's why I said, "I am new to Ubuntu so probably did this the wrong way around." I was not aware that it would be available to all accounts as Wine (installed for the Master account) does not seem to work in the kids account so I figured I'd have to install stuff individually for their account.

But when going to the BBC site this morning and it suddenly started playing Flash, I realized that it was shared, so then wanted to revoke the sudo privilege for the kids account.

Thanks for the "sudo nano /etc/group" approach. Still on the pointy end of learning Ubuntu. :)

---

### Post by SeijiSensei on 2016-11-16
Wine is an unusual beast, so I can see why it would be confusing.  Wine builds a replica of Windows in each user's /home/user/.wine folder.  If you run "wine program_name" from the command prompt using the kids' account, it will build a .wine environment in that account's home directory.  Try running "wine notepad" to launch the version of Notepad that is shipped with wine.  It will announce that it's building its environment, then the program will pop up on the screen.

In general, though, programs written for *nix systems are available to all users.  Most every executable file lives in /usr/bin and is available to everyone.  If you run "ls -l /usr/bin" you'll see that they all look like this:
```
-rwxr-xr-x 1 root root        1582 Apr  4  2014 notepad
```
This is the entry for the notepad program that comes with Wine.  Notice that it's stored in /usr/bin despite running in each user's personal Wine environment.  The "rwxr-xr-x" entries indicate that the file's owner, root, has read, write, and execute privileges.  The two "r-x" entries show that members of the root group have only read and execute privileges as do all other users on the system.  If you were to run the command
```
sudo chmod a-x /usr/bin/notepad
```
that would remove the execute privilege for **a**ll users, leaving only root and members of the root group able to run /usr/bin/notepad.

---

### Post by FerryGnu on 2016-11-18
Thanks SeijiSensei,

At this time, I don't need to run wine in the kids account, I had just tried to use it on a test .exe I copied over. When it didn't run that's when I thought I had to install flash for each account. Seemed a little weird, but I am new to Ubuntu.

Pretty funny actually, had I tried to run anything else except a wine program, it would have worked and none of this would have been needed. That's why they call it a learning curve and I am still way down on that curve. :)

Thanks again for taking  the time to give me that detail. I have copied the directions in case I actually need to install an .exe in their account at some time in the future.

---

