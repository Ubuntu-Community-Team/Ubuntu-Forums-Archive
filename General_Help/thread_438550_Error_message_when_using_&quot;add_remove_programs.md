---
title: "Error message when using &quot;add remove programs&quot; in feisty"
date: 2007-05-09
forum: General Help
---

### Post by zhkent on 2007-05-09
In a discussion on how to get quickbooks to work on feisty the following post was made:

if you have the resources on your computer than I would install virtualbox and use that to install a copy windows xp. you can then run it in a window on linux. xp thinks it is running standalone and runs better than if you run it on its own pc. I would suggest you have at least a gig of memory because xp will want at least 256 but runs better with 512. This solution for me was far better than wine or crossover or any of the other emulators.... try it.... it is free...

Wine had not worked for me.  While downloading with the add remove program feature virtualbox kind of hung up.  After exiting I get this message when i try to install or uninstall programs now.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can someone help me resolve this?  I get this message on all install or uninstall tries now.

Kent

---

### Post by obviouslyshane on 2007-05-09
I am having a similar problem...

i get this error, when i attempt to sudo apt-get update:

> Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing gaim (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


I get the following error when i try to add/remove a program:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Also, the update manger gives me this...

> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing gaim (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

I'm lost... and i cant find any thing on the net about how to fix it.

---

### Post by avai on 2007-05-22
I'm having a near identical problems, except it is occurring from downloading compiz 0.4. I was able to successfully get wine up and running though prior to my problems with compiz.

When I click on Add/Remove, I receive the following:
> 
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


I don't have those error messages on hand anymore, but it was near identical the one below and directed me to '/var/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages'
I entered 'source.list' and 'source.list.save' and removed the "deb http:// ..." entries for compiz. I searched the file for anything with compiz and removed it. I currently get the following message, which is more concise:

> 
E: Dynamic MMap ran out of room
E: Error occurred while processing language-pack-gnome-sq (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


The contents of my sources.list is as follows:

> 
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted


---

### Post by avai on 2007-05-22
Well, a new problem.

When I left the root user account and booted into the admin account, I now do not have the header bar (with Applications, Places, Systems, etc) and footer bar (with the window bars for in use programs). This likely resulted from my deleting something I shouldn't have deleted.

---

### Post by avai on 2007-05-22
Well, I fixed the original problem. Removing the "deb http://..." from the sources.list worked, but most of the edits I made to the '/vars/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages' file were not so good.

Even though I repair that problem, the header and footer bars are still not available. What I currently need to repair my computer is a certain portion of text from '/vars/lib/apt/lists/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages'. 

Open it and search using the key word compiz. Copy and paste the blocks of information found with it and post them. There should be 2 to 6 blocks of information altogether in the document.

---

### Post by avai on 2007-05-23
Never mind guys, I fixed the rest. Thanks for the help. :D

---

