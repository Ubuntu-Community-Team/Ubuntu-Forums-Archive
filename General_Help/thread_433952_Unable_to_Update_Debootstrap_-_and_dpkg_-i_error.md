---
title: "Unable to Update Debootstrap - and dpkg -i error"
date: 2007-05-05
forum: General Help
---

### Post by mojohn on 2007-05-05
The update notification icon appeared in my system tray, telling me that there's 1 update available.

When I press the notice icon, Debootstrap program 0.3.3.3ubuntu3~dapper1 is the available program. When I press the Install Updates button, it acts like it's going to install except it doesn't download anything and nothing gets installed. The icon never goes away.

I'm running Dapper.

Also, I don't know if this is a related problem or not. I downloaded OpenOffice.org 2.2 and used alien to change the RPMs to debs. When I went to the folder where the debs are located, opened a terminal and typed sudo dpkg -i *deb, I got the following error message:  dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `

I don't remember the last program I installed using dpkg, but I did an install maybe a week ago and things worked fine.

If you could help me answer these questions, I'd much appreciate it.

mojohn

---

### Post by Theimon on 2007-05-06
What Ubuntu version are you using? In Feisty, OOo 2.2 is default so you don't need to download anything, especially not RPMs. If you want to install something that's not in the repos, get the source and compile it. Better than playing with alien and RPMs.

For the update problem, did you try the following already?
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by mojohn on 2007-05-06
Thanks for the reply. I am using Dapper.

I will attempt to download OOo source and compile. 

That said, do you have any clue why dpkg -i doesn't work right, or why Debootstrap won't update?

Thanks,

mojohn

---

### Post by Theimon on 2007-05-06
First off, is the 2.2 version of OOo so much better that you really need it? Dapper has it's own OOo already installed.
Debootstrap update: did you try those 2 commands I gave you? Try that first, and post the error (should an error appear).
The dpkg error could well be a result of the alien conversion. Do you get the error with other .deb files as well?

---

### Post by mojohn on 2007-05-06
I followed your instructions re: aptitude and, after the upgrade command was issued, I got the following message:

john@john:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  debootstrap
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/52.1kB of archives. After unpacking 32.8kB will be used.
Do you want to continue? [Y/n/?] y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `
john@john:~$

I'll find a native deb program to install and see if I get the same parse error when I run dpkg -i and post a follow-up message.

Thanks, mojohn

---

### Post by mojohn on 2007-05-06
I went to the Debian packages site and downloaded Sylpheed. I did dpkg -i on it and got the same error message reported above.

Thanks, mojohn

---

### Post by Theimon on 2007-05-06
Alright, the "available" file is corrupted. Luckily there's a backup file. Enter the following commands in a terminal, so we can try to fix it.
First get inthe right folder: ```
cd /var/lib/dpkg
```
Make a backup of the current file: ```
sudo mv available available.bak
```
Rename the backup file to the working one: ```
sudo mv available-old available
```
Get the dpkg in a good state ```
sudo dpkg --configure -a
```
And then update and upgrade: ```
sudo aptitude update
sudo aptitude upgrade
```
It should leave no errors and the upgrade should be installed.

---

### Post by mojohn on 2007-05-06
Thieman, you rock! This fixed the problem. Thanks so much!

mojohn

---

### Post by Theimon on 2007-05-06
> **mojohn said:**
> Thieman, you rock! This fixed the problem. Thanks so much!

mojohn

Great to hear it worked out 8)

---

