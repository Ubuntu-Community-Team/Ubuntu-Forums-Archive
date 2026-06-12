---
title: "Issue with package manage and apt-get"
date: 2006-12-22
forum: General Help
---

### Post by fearevilleet on 2006-12-22
Hello everyone,

I messed something up in my package manager and I am not sure what, and I could use some advised. I was trying to install I was trying to install bearly and I tried to add a deb file to the package manager via the gui since I was not having much luck via the terminal. I was unable to get the pacjage manager to connect to the deb file to download so I removed the deb address. Now when I go to to add a new program via the package manager I get the following error:  

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'


When I run sudo apt-get update I get the following error

E: Malformed line 29 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)


When I go to the synaptic package manager via the admin tab I get the following error
E: Malformed line 29 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I was install programs all day and I am not really sure what I did wrong. Any help with this issue would be appreciated 


Below is a copy of my  /etc/apt/sources.list
 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe main

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security

---

### Post by meng on 2006-12-22
remove the last line altogether

---

### Post by fearevilleet on 2006-12-22
I removed 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security

But I am sill having the same issue. 

I tried 

evilleet@box:~$ sudo apt-get update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)

---

### Post by ethan961 on 2006-12-23
Try removing that same line in the /etc/apt/sources.list.d/edgy-universe.list as well. I am having the exact same problem, and that line is also line 2 i the edgy-universe.list file. 
Cheers, 
Ethan

---

### Post by fearevilleet on 2006-12-24
I got it working!!

I removed all the deb sources via that package manager by unchecking all the options. I then went back into the package manager and re enabled everything and it worked. :}}

Thanks for all your help guys, this forum provides excellent support---far better then many of the services I pay for.

---

