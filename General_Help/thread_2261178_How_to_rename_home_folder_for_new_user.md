---
title: "How to rename home folder for new user?"
date: 2015-01-16
forum: General Help
---

### Post by Becky_Lawson on 2015-01-16
Okay, let's get the specs out of the way...
Dell Inspiron 560, 4 GB RAM, Intel Dual-Core E6700 @ 3.2 GHz, running Ubuntu 14.04 64-Bit with all updates up to 01.15.15 installed.

Now the problem...
I got this computer from my roommate. Pretty clean install, less than a month old. No additional programs installed by the roommate. Naturally, the home folder is named 'home/melissa'.

I'd like to rename it to read my name, as my old computer did. (home/becky)

I was able to change the login name and password using the 'User Accounts' dialog in the Settings, but the home folder still reads 'melissa.' After doing some googling, I found that I can change it through the Terminal command

```
usermod -l {[COLOR=#993399]new-login-name[/COLOR]} {[COLOR=#996633]current-old-login-name[/COLOR]}
```

then run

```
usermod -m -d /home/jerry -l jerry tom
### gone ###
ls /home/tom
### as it moved to ###
ls /home/jerry
```

I'm not too comfortable with Terminal commands as of yet, and I REALLY don't want to mess things up.

So, I have two questions...
1. Will this affect the automatic login? Like, will it keep looking for the 'home/melissa' folder and be in a boot loop?

2. If I were to create a new user, would programs I installed and personal files in the subfolders under the 'melissa' account be accessable to the new account?

Any help would be awesome. Thanks in advance!

---

### Post by mooreted on 2015-01-16
You could create a new user account. As long as you have the root password you can copy files from the old profile to your new profile. You can do this from the command line, or you can open Nautilus as root from the command line:

gksudo nautilus

which will allow you to copy and paste files over. You can change the user that automatically logs on in Settings.

I have not tried any of those commands you have listed, so I can't advise you on that. Never use commands unless you understand how they work.

---

### Post by Becky_Lawson on 2015-01-17
> **mooreted said:**
> You could create a new user account. As long as you have the root password you can copy files from the old profile to your new profile. You can do this from the command line, or you can open Nautilus as root from the command line:

gksudo nautilus

which will allow you to copy and paste files over. You can change the user that automatically logs on in Settings.

I have not tried any of those commands you have listed, so I can't advise you on that. Never use commands unless you understand how they work.

Okay, I have NO clue what a root password is, so I'm PRETTY sure I don't have one! LOL

---

### Post by nerdtron on 2015-01-17
How did you create another user?
Just create another username with your desired home folder and username. Then copy the files over to the new home folder.
After that delete the old one.

---

### Post by Becky_Lawson on 2015-01-17
> **nerdtron said:**
> How did you create another user?
Just create another username with your desired home folder and username. Then copy the files over to the new home folder.
After that delete the old one.

I didn't 'create' a new user... I just renamed the current one by going into 'User Accounts' and renaming it from 'Melissa' to 'Becky.'

But the home folder still reads 'home/melissa'.

I'm most concerned with the two programs I installed, whether I will have to re-install them or not.

---

### Post by Holger_Gehrke on 2015-01-17
> **Becky_Lawson said:**
> After doing some googling, I found that I can change it through the Terminal command

```
usermod -l {[COLOR=#993399]new-login-name[/COLOR]} {[COLOR=#996633]current-old-login-name[/COLOR]}
```

then run

```
usermod -m -d /home/jerry -l jerry tom
### gone ###
ls /home/tom
### as it moved to ###
ls /home/jerry
```
Forget about the first command. That just renames the user and you've already done that.
The second command is also not quite right. It both renames the user --  which you've already done in the GUI -- and moves the home directory. It  would probably fail (and do nothing ...)
```

usermod -m -d /home/becky becky

or with more readable long option

usermod --move-home -home /home/becky becky
```
would  work - but you probably need to put 'sudo' in front of this command, I  don't think you're normally allowed to do something like this without  getting administrative privileges, which is what 'sudo' does.

One thing renaming the home directory might affect are settings of some programs that store absolute paths in their settings, so used files, media player libraries and stuff like that will behave in unusual ways until you sort it all out.

> **Becky_Lawson said:**
> 
1. Will this affect the automatic login? Like, will it keep looking for the 'home/melissa' folder and be in a boot loop?

It shouldn't. But just in case create a new user so you can get into the machine in case you break something.

> **Becky_Lawson said:**
> 
2. If I were to create a new user, would programs I installed and personal files in the subfolders under the 'melissa' account be accessable to the new account?


As long as you installed the programs through the package manager -- using Software Center, Synaptic, aptitude or apt-get -- they are not installed in you home directory, so they should not be affected at all.
Whether or not you could access personal files from a new account depends on the permissions of the files. Every file has three sets of three permission: read, write and execute for the files' owner, the group and everyone else. Unless you set thing up differently, files in your directory are readable for everyone but only the owner is allowed to write into them.

---

### Post by grahammechanical on 2015-01-17
> [COLOR=#000000]Okay, I have NO clue what a root password is, so I'm PRETTY sure I don't have one! LOL[/COLOR]

Oh, yes you do. When we install Ubuntu we are asked for a username and password. When we run Ubuntu we work as a standard user until we try to do a task that requires administrator privileges. We are asked to authenticate the action. At the moment our password becomes the administrator or root password for that action. Once, the action has completed we revert to being a standard user.

You could not have done this without Melissa's password. And when you used that password you were working as administrator or root.

> [COLOR=#000000]I was able to change the login name and password using the 'User Accounts' dialog in the Settings,[/COLOR]

You are now both a standard user and an administrator user as is necessary. You can now delete Melissa's user account. And then you will have compete control over this machine.

When running commands from the terminal we put the word "sudo" in front of the command for those commands that require root or administrator privileges. We are then required to put in our password before the command will run.

By this method of working Ubuntu allows us to set up standard users whose passwords cannot authenticate actions that only an administrator can should should be doing.

Regards.

---

### Post by Becky_Lawson on 2015-01-17
> **Holger_Gehrke said:**
> As long as you installed the programs through the package manager -- using Software Center, Synaptic, aptitude or apt-get -- they are not installed in you home directory, so they should not be affected at all.
Whether or not you could access personal files from a new account depends on the permissions of the files. Every file has three sets of three permission: read, write and execute for the files' owner, the group and everyone else. Unless you set thing up differently, files in your directory are readable for everyone but only the owner is allowed to write into them.

So, because the 'owner' would technically be "melissa" at this point, I would not be able to write to the files under a new account, correct?

---

### Post by Becky_Lawson on 2015-01-17
> **grahammechanical said:**
> Oh, yes you do. When we install Ubuntu we are asked for a username and password. When we run Ubuntu we work as a standard user until we try to do a task that requires administrator privileges. We are asked to authenticate the action. At the moment our password becomes the administrator or root password for that action. Once, the action has completed we revert to being a standard user.

You could not have done this without Melissa's password. And when you used that password you were working as administrator or root.

** [COLOR=#000000]I was able to change the login name and password using the 'User Accounts' dialog in the Settings,[/COLOR]**

You are now both a standard user and an administrator user as is necessary. You can now delete Melissa's user account. And then you will have compete control over this machine.

When running commands from the terminal we put the word "sudo" in front of the command for those commands that require root or administrator privileges. We are then required to put in our password before the command will run.

By this method of working Ubuntu allows us to set up standard users whose passwords cannot authenticate actions that only an administrator can should should be doing.

Regards.

Okay, I think I'm just confusing everybody... myself incuded. LOL

Let me try to explain this again...
I understand now, by using Melissa's password, I was using the Root password. I get this.

[COLOR=#000000]Last night, when I booted, I was able to change the login name and password using the 'User Accounts' dialog in the Settings. The name showing in all dialogs (The gear icon, the shut down window[/COLOR], the User Accounts tab) all say 'Becky.'

[IMG]http://i.imgur.com/LIPWOfV.png[/IMG]

However, it still has 'melissa' as the name of the computer. For example, when I look at the properties for my files, it reads as follows:
/home/melissa/Pictures/examplefolder/examplefilename.doc

How can I change the /home/melissa folder to read /home/becky (or preferably /home/admin/ or something similar)?

---

### Post by deadflowr on 2015-01-17
melissa is the username, Becky is the user's *new* Full Name.
(the machine name is something completely different. You can see the machine name in a terminal when you open it there should be a line that says melissa@something~$. the something is the machine name, because melissa is at that machine.
User Accounts only changes the user's full name, but not the username.
User Accounts is meant to add and subtract users, and not to manipulate user setting like changing the username or home folder.
It is simply not as flexible as the command line utilities such as usermod.

The only method i can see to change the user via User Accounts is to make a new user, then copy the files of the old user into the new user's home folder, then change/verify the ownership of the copied files, then delete the older user.
Quite a painstaking venture...
(As compared to using usermod)

---

### Post by Bashing-om on 2015-01-17
Becky_Lawson; Hello;

I expect that the "computer name" can be effected by editing a couple of files;
/etc/hosts, and /etc/hostname .
Both these files when edited MUST contain the same 'name' .

See: [http://ubuntuhandbook.org/index.php/2014/04/change-hostname-ubuntu1404/](http://ubuntuhandbook.org/index.php/2014/04/change-hostname-ubuntu1404/)
In small steps if you are the more comfortable:
make a backup of the current files:
```

sudo cp /etc/hosts /etc/hosts-orig
sudo cp /etc/hostname /etc/hostname-orig

```
Next fire up a GUI text editor with the privileges to edit system files:
```

gksudo gedit etc/hosts

```
The 2nd line 2nd field is the 'name' of the host, change it as desired and save the file.
Repeat for the file " /etc/hostname " .
This file contains only the "hostname" change it to EXACTLY the 'name' you used in the 'host' file.

Now reboot the system.

I hope you are pleased as punch
[INDENT][INDENT]with what you have achieved 
[/INDENT][/INDENT]

---

### Post by Becky_Lawson on 2015-01-17
> **deadflowr said:**
> melissa is the username, Becky is the user's *new* Full Name.
(the machine name is something completely different. You can see the machine name in a terminal when you open it there should be a line that says melissa@something~$. the something is the machine name, because melissa is at that machine.
User Accounts only changes the user's full name, but not the username.
User Accounts is meant to add and subtract users, and not to manipulate user setting like changing the username or home folder.
It is simply not as flexible as the command line utilities such as usermod.

The only method i can see to change the user via User Accounts is to make a new user, then copy the files of the old user into the new user's home folder, then change/verify the ownership of the copied files, then delete the older user.
Quite a painstaking venture...
(As compared to using usermod)

Guess it's just as viable to deal with the username being different than the user's full name. :? I mean, it's NOT affecting the performance, just a minor annoyance/pet peeve of mine.

I could make the new user account, set to administrator, delete melissa, then recopy the files from a flash drive the files are still on, correct?

---

### Post by yancek on 2015-01-17
> I could make the new user account, set to administrator, delete melissa,  then recopy the files from a flash drive the files are still on,  correct? 		

I would suggest you add a step between 'set to administrator' and 'delete melissa' and that would be to reboot and test that your new user has admin privileges.  A little paranoia goes a long way.

---

