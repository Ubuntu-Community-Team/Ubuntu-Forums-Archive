---
title: "Failed to obtain authentication."
date: 2020-07-25
forum: General Help
---

### Post by asearle on 2020-07-25
Hallo Everyone,

I have been experimenting with Lubuntu 20.04 and it seems pretty good!

But I installed virtual machines and wanted to make the directory accessible to all users so adjusted permissions (both for those directories and the users).

Now I find that ...

Software installers (e.g. Discover and Muon) are blocked (they return the message "Failed to obtain authentication.") and disk-analysers (e.g. gparted) seem to also lack permissions to read in drive information.

I have compared the users-permissions to a another identical PC and everything seems to tally: e.g. users are members of adm and sudo (amongst others).

And, indeed, using "sudo" in the command-line I can install and remove software now problem. So the permissions are available ... but not for those applications.

It is important for me to know what has happened because otherwise I don't know what other impacts this has had / is having.

Can anyone help me here?

Many thanks.

Yours,
Alan 
in Cologne

---

### Post by TheFu on 2020-07-25
> **asearle said:**
>  

But I installed virtual machines and wanted to make the directory accessible to all users so adjusted permissions (both for those directories and the users). 

What exactly did you do?  Should we guess which directories and which permissions you changed for the 500,000 different files?

---

### Post by asearle on 2020-08-01
I created a directory called \VirtualMachines, assigned to a group called "virtualbox", and assigned permissions (for two users) to that directory.

The confusing thing is that both users are "admin" (sudo works in the terminal for, e.g. apt-get) but for certain programmes ("discover", "muon", "gparted") authentication is blocked.

As mentioned, I compared the groups that those users belong to (with another PC) and that seems fine.

All I was hoping was that someone has had similar behaviour and could tell me which permissions/groups to check.

Yours,
Alan

---

### Post by asearle on 2020-08-01
Yes, it seems that the users have permission to carry out all "sudo" opperations in a terminal (e.g. apt-get ) but that there is a permissions (authentication) issue in (some) applications running in the (LXQt) graphical environment.

This is bizarre: How can it be that a user has full (root / sudo) permissions (in the Terminal) but is blocked in the graphical environment?

Yours,
Alan

---

### Post by TheFu on 2020-08-01
> **asearle said:**
>  
This is bizarre: How can it be that a user has full (root / sudo) permissions (in the Terminal) but is blocked in the graphical environment? 

Because Unix doesn't work that way.  Being the the sudo group doesn't magically provide access to anything. Whenever access is required, it must be proactively requested.  But sudo abuse -- using it too much -- is dangerous.  Bad things are likely to happen which will only be fixed by doing a fresh install of the OS.  You've been warned.

To understand Unix (and Linux is 90+% Unix), you'll need to learn the Unix file and directory permissions.  That's the root of all Unix security regardless of platform.  Every popular OS used today follows the same rules (cough - except one desktop). All the other popular OSes use the Unix security model.

Unix doesn't know or care if you use a GUI or not. That has zero to do with permissions.  File access permissions matter.  Directory access permissions matter.
You have 2 choices.
[LIST]
[*]Ignore these Unix-style file/directory permissions model and spend all the time not understanding why and how things work for the next 50 yrs
[*]Work through a tutorial to get a basic understand, then spend 30-45 minutes playing/testing with 3 userids, 3 groups, in some test directories under /tmp/somewhere and work through each possible combination of the 32-bit permissions, groups mixed and matched to see which users have access and which don't as the permissions change. Understanding will come. It will click - probably around 25 minutes into the play time.  From that point on, you'll never struggle with these kinds of problems again.
[/LIST]

Now, let me re-read the original issue.

It is unclear what virtual machines have to do with permissions to me.  Please clarify where you have having the problems - inside each VM or in trying to launch the VMs?  I haven't used virtualbox in a fairly long time.  For a shared environment with VMs, we use KVM + libvirt.  Being a member of the libvirtd group is all that is required to be able to launch, stop, modify the XML settings which control each VM.  I think virtualbox is meant to be used by a single userid.

If you can show the **groups** for each userid you'd like to have control vbox (**id** for each and the current long listing (**ls -al**) for the directory where the VDI files are located, we can certainly setup the groups to allow that with virtualbox. Both the file owner, group, permissions AND the same for the directory are required.
It is a normal "Working Together" permissions problem.   [https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965) explains.

You've confused me about gparted. That's a program, not a userid.

In the Unix world, everything is either 
[LIST]
[*]a process
[*]a file
[/LIST]
Those are the choices. There aren't any others. Only actively running programs, processes, threads, will show up in the process table. Those are the things call "a process".  Everything else is a file.  Some examples:
[LIST]
[*]files
[*]directories
[*]devices (that includes drivers loaded into the kernel)
[*]mouse
[*]keyboard
[*]monitor
[*]speakers (really the audio chip output to the plug)
[*]microphone
[*]webcam
[*]fifos, pipes, named-pipes, 
[*]network card(s)
[*]scanners, printers, fax machines, phones, .... 
[*]disks
[*]partitions
[*]logical volumes
[*] everything that isn't a process is a file. Period.
[/LIST]
All files have an owner, a group, and permissions.  Period.  Those permissions follow the Unix Permissions model I attempted to convince you to learn above.  If you want a user to be able to hear a sound, their userid needs to have "read" permissions on the "file" where the audio output is sent. Make sense?  If they do not, then that userid will never hear anything.

For almost everything normal, typical, the permissions, owner and groups, are setup correctly automatically. It is only when the defaults fail to work that we'd need to tweak permissions.  For example, pulse audio only works for logins directly on the machine. Remote users don't get the special access to pulse-controlled devices, so if you want to use common, 40 yr old remote access methods, then have some music play in the other room, pulse audio won't allow that by default.  But we can fix it so that IS possible, by controlling the permissions and groups.

Hope this is helpful. Probably much more than you cared to know.  Check out that "Working together" link.

---

### Post by asearle on 2020-08-02
Dear TheFu,

Many thanks for the information: That's excellent!

But let me try to reduce my explanation to the minimum ...

The problem appeared after I created directories for Virtualbox but Virtualbox has no problems and is working fine. I simply suspect that my changing the permissions may have caused the problem. The other thing I did was create a second user and assign admin permissions also to that user.

The reason I mentioned "gparted" is that that is simply one of a number of GUI-Programmes which is refusing authentication. Others include Discover, Muon (sofware installation tools) and User/Group-Admin. The problem is not specifically with those tools/applications.

One suspicion that I have is that it may not be a problem with permissions but rather that the GUI (LXQt) is requesting authentication from me but not passing that on to the OS correctly.

As it is I am new to LXQt (the GUI for Lubuntu 20.04): It seems good but I have no experience of it until now.

Any tips would be a gratefully received.

Yours,
Alan

---

### Post by guiverc on 2020-08-02
I can't help with your issue (currently don't have time to do more than a scan-read of it sorry so I may have missed details in this thread).

I'm not aware of any issues with Lubuntu/LXQt being different except for a recorded bug that your description doesn't fit anyway ([https://bugs.launchpad.net/ubuntu/+source/lxqt-admin/+bug/1875774](https://bugs.launchpad.net/ubuntu/+source/lxqt-admin/+bug/1875774) which requires permissions to be removed using GUI tools), but if you use normal *nix commands anyway; the bug won't be encountered (the issue only impacts the `lxqt-admin`).  I don't believe this is your issue but i'm adding it only for completeness.

Your issue maybe running GUI program if started at terminal with `sudo` given comment #4, as for example if you change settings in a GUI program initiated with `sudo`, you may indirectly deny yourself permissions to use/run that tool normally (as it'll required elevated privileges to read the config files written with elevated privileges).  This is not a LXQt issue, but general POSIX permissions issue created by user behavior.

---

### Post by asearle on 2020-08-05
> **guiverc said:**
>  Your issue maybe running GUI program if started at terminal with `sudo` given comment #4, as for example if you change settings in a GUI program initiated with `sudo`, you may indirectly deny yourself permissions to use/run that tool normally (as it'll required elevated privileges to read the config files written with elevated privileges).  This is not a LXQt issue, but general POSIX permissions issue created by user behavior.

My suspicion is that this is what has happened: I did assign (and now de-assign) users to a number of extra groups.

Anyway, I have compared groups on the problem-system with those on an identical fresh install and have adjusted accordingly.  But the GUI-programmes mentioned are still refusing authentication.

I am tempted now to completely re-install (that would be the easiest) but would much rather know what I did wrong/messed up.

The groups allocated to the users are (currently): adm; cdrom; dip; lpadmin; plugdev; sambashare; sudo ... and to a group (automatically created) with the same name as the user.

Maybe something is missing (or wrongly allocated) here?

Yes, I would really like to know what I did!

Many thanks.

Yours,
Alan

---

### Post by asearle on 2020-08-06
Diagnosed ...

This is VERY strange: I managed to fix the problem by removing the second user that I had created.  Then the original user was able to access the GUI tools which require authentication (e.g. Disk partitioning tools, Users, etc.).  I was very pleased!

But then I recreated the second user (also with admin-rights) carefully copying the group-allocation from an identical working system.

And the problem has returned!  For both users.  Arrgghh.

Has anyone got an idea why this is happening?  And how I can prevent it?  Or is the system only allowed one admin-user?  Surely not.

Yours,
Alan

---

### Post by SeijiSensei on 2020-08-06
Granting users sudo privileges is managed by putting them in the "sudo" group like this:
```

sudo useradd -G sudo mytrustedfriend
sudo passwd mytrustedfriend

```
User mytrustedfriend should now have sudo privileges.  To check run this command:
```
grep ^sudo /etc/group
```

See the file /etc/sudoers for details.

---

### Post by asearle on 2020-08-06
Hallo,

Exactly that is the strange thing:  Both users are in the sudo group and both users (even when the GUI authentication is blocked) can carry out sudo commands from the command line.  But GUI-authentication is refused.

This is very strange.

I wish I knew why it does this but my temptation is to simply do without the second user.

Yours,
Alan

---

### Post by SeijiSensei on 2020-08-07
I'd never run a GUI environment with sudo privileges. Too easy to make big mistakes. The only reason to need sudo is to run administrative commands in the terminal.

> But then I recreated the second user (also with admin-rights) carefully copying the group-allocation from an identical working system.

What exactly did you do here? What does creating the second user with admin rights mean? The usual process is to set up an ordinary user account then add it to group sudo. Is that what you did?

Let's see the results of 
```

grep mytrustedfriend /etc/passwd
grep mytrustedfriend /etc/group

```
replacing "mytrustedfriend" with the name of the second account. You should get results like this
```

$ sudo useradd -G sudo testuser

grep testuser /etc/passwd
testuser:x:1006:1006::/home/testuser:/bin/sh

$ grep testuser /etc/group
sudo:x:27:seiji,testuser
testuser:x:1006:

```

"testuser" has UID and GID 1006 and belongs both to its own testuser group and the sudo group.

---

### Post by asearle on 2020-08-08
Both users are allocated to these groups ...

adm; cdrom; dip; lpadmin; plugdev; sambashare; sudo ... and a group with the same name as that user.

I would really like to know what is happening here: Have I allocated one or two wrong groups?  (but I copied this allocation from a fresh install of Lubuntu 20.04)

Many thanks for any ideas/tips.

Yours,
Alan

---

### Post by TheFu on 2020-08-08
asearle, a specific command was requested by SeijiSensei.  Please run those commands AND post the results.  We've seen what you claimed to have done.  Perhaps it didn't actually happen?  Those commands will tell the truth, unlike many GUI programs.

Or did you not want help?

---

### Post by asearle on 2020-08-09
Sorry, yes, here is the output from those commands (below).

The main/original user is "alan". The second (new) user is "teresa".

Many thanks for any tips.

Yours,
Alan

```
alan@alanterra1451:~$ grep alan /etc/passwd
alan:x:1000:1001:Alan:/home/alan:/bin/bash
alan@alanterra1451:~$ grep alan /etc/group
adm:x:4:syslog,alan,teresa
cdrom:x:24:alan,teresa
sudo:x:27:alan,teresa
dip:x:30:alan,teresa
plugdev:x:46:alan,teresa
lpadmin:x:119:alan,teresa
sambashare:x:1000:alan,teresa
alan:x:1001:alan
alan@alanterra1451:~$ grep teresa /etc/passwd
teresa:x:1001:1002:teresa:/home/teresa:/bin/sh
alan@alanterra1451:~$ grep teresa /etc/group
adm:x:4:syslog,alan,teresa
cdrom:x:24:alan,teresa
sudo:x:27:alan,teresa
dip:x:30:alan,teresa
plugdev:x:46:alan,teresa
lpadmin:x:119:alan,teresa
sambashare:x:1000:alan,teresa
teresa:x:1002:

```

---

### Post by TheFu on 2020-08-09
So, it appears you replaced the default group for the alan username which would have been alan (gid:1000) and renamed it sambashare.  That would break all the group settings for every file on the system owned by alan:alan --> alan:sambashare. Nice. Not really.

On my single samba-using machine, sambashare is a daemon grpup - gid 118.
These are the reasons why using a GUI to manage users and groups is a bad idea. Just because the GUI does it, don't expect it to magically look in every file system and fix the files appropriately.  So, I'd guess that username-alan's home directory has all sorts of screwed up permissions due to this.  That may not be the situation, but it is likely.

**The answer**
It may be a mess or not. Hard to tell.  The correct answer is to 
[LIST=1]
[*]look through all the files owned by alan that need to be also in the group "alan" and make that happen.  
[*]Do the same for teresa (owner and group).  
[*]Then look for all the files with a group of "sambashare" and verify those all should have that group.  Hopefully, there aren't any.  
[*]If there are not (cross your fingers), then delete the sambashare group, reinstall samba, see that it adds a daemon group, sambashare, and 
[*]then start working to get samba working the way you want.
[/LIST]

* daemon userids and groupids have numbers less than 1000.  

There are a few shortcuts which might make this easier, but that completely depends on how well 'alan' and 'teresa' were at keeping personal files in their HOME directories or not. If they've been sharing files/directories from directories in their HOME on the network, it isn't nearly as easy.  Anyways, assuming all files are owned by the correct userid in their HOME directories, you can run two commands with sudo, then 1 more command as each userid to fix most things.
```
sudo chown -R   alan   ~alan
sudo chown -R   teresa   ~teresa

```Then for each userid, run this **chgrp -R alan ~/**  and for 'teresa' use **chgrp -R teresa  ~/**.
Now you are just left hunting down any wild files in other directories outside HOME for files owned by those userids. Oh, and I think all the GUI authentication stuff should work now too.

You can use the id command to view that data for any userid.  **id -g** or **id -G** may be helpful to.
```
$ id -g
1000
$ id -G
1000 4 7 27 29 33 46 102 109 115 139
```
1000 is my "effective gid".  My username is a member of 11 other groups, only 1 is a non-daemon group.

What have we learned?
**Modifying users, groups, is fine, but it doesn't do anything on storage, filesystems. That stuff has to be addressed manually.** Almost always, it is best to add new userids/groupids, do all the file management stuff to make use of those new, ensure the old userids/groupids aren't being used anywhere, then delete them.  If you just want to change the name of a user or group, you can manually edit the password DB and group DB files, assuming no external DBs, like LDAP or MS-Active Directory or x.500 directory services, are being used. If you didn't setup LDAP or the others, then you aren't using those.

I'd use **find** with some options to locate by owner and group, look at the specific files to be certain only the files need to be chgrp'd are in the list.  Find is one of those tools that can really ruin you day. I've nearly wiped complete operating system installs with **find** by accident.  Using find is a skill worth having, but the manpage is difficult to understand for people who have never used it before.  Look for examples on the internet.  I'd post the commands, but honestly, I'd have to look them up just like you would. I'm 100% positive that **find** can do the searches by owner and group.

Or you can reinstall if there isn't that much data and try to avoid making the similar mistakes next time.

Clear as mud?

---

### Post by asearle on 2020-08-11
TheFu,

Many thanks! Well spotted!

You guys are fantastic: I will get to work untangling that and give you feedback whether I was successful.

Most important for me was to know what had happened: And you spotted it.

Bravo!

Yours,
Alan

---

### Post by TheFu on 2020-08-11
That's just 1 possible answer. Lots and lots of other things may have happened too, especially when trying to fix it.

---

