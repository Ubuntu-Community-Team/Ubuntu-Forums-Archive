---
title: "Users &amp; Groups - Minimising Access to stuff"
date: 2006-08-06
forum: General Help
---

### Post by Ted_Smith on 2006-08-06
Hi. I realise Linux is a true multi-user OS (unlike Windows) so I had assumed the following would be easy, but I'm struggling. 

Basically, I want to prevent my 17 Yo sister-in-law from being able to do anything other than access her own home folder, launch FF and launch aMSN to chat to her mates. I don't want her to be able to access the floppy disk, browse the FS, use the terminal, or anything. 

I've added her as a user, and unticked many of the tickable options in the 'User Priviliges' part of adding a new user. I had imagined that with Ubuntu there'd be a 'restricted users' group that basically meant that any user added to it would have very basic or no priviliges unless the admin added specific permissions. I thought if it wasn't there it would be easy enough to create. But Google returns very little and Ubuntu seems to be how it is. 

Any ideas how I can restrict my troublesome sis in law?

Thanks

Ted

---

### Post by orb9220 on 2006-08-06
Nope by select properties of user and un-checking admisastrative,cdroms,etc
you are creating a restricted user account.

sign on the account and see if you can do the things you are worried about.

---

### Post by Ted_Smith on 2006-08-06
thanks for your help, but I have already done that which is how I know that the problem exists. I logged in, and initially, by default, she could browse MY home folder, the File System, access the floppy drive etc despite me unticking 'Access to floppy drives' in the permission set-up. Granted, she couldn't change anything, but that's not everything that I'm trying to restrict. 

I prevented her access to my home folder by removing access permissions of the 'others' user group. But that is not the point. 

I want, by default, a secure user group wherein they can't dop anything unless I add the instruction for them to do so. For example, "she can access the terminal, she can access the file system, she can access floppy disks", etc. It seems that by default a new user can access everything which is not much better than Windows (allbeit they don't get admin privis!). Unless I am doing something wrong. 

Ted

---

### Post by aysiu on 2006-08-06
Try *kiosktool*--it's in the Universe repositories.

I believe there's a Gnome equivalent for it, too.

---

### Post by Ted_Smith on 2006-08-06
I think the Gnome equiv is 'gconf-editor' accessible via terminal or 'Application --> System Tools --> Configuration Editor'. 

However, it's not apparent how you apply the settings in there to a specific user or groups of users. I think whenever it's run, the settings apply to the user who is running it. But again, if that is the case, I wouldn't have expected to have to create a new user account with sufficient priviliges to run this utility to then log into it myself and configure the settings for that user account, and then log out of it for the settings to take effect for when the genuine user actually logs in! All I want to do, as the system admin, is say "Hey Ubuntu, I want this group of users to be able to run X, Y and Z, but not A, B or C". Is it just me - or am I expecting too much? Surely that is not a major thing to ask of an OS that is based on something as old and tested as Unix? I must be doing something wrong here? 

Considering Linux is hailed as being a true multi user OS and that fact alone is supposed to make it so much better than Windows, this task is proving to be rather more tricky than I had envisaged! Shocked I am that there's no 'locked down' user group that you can add users into to give them just the most very basic and menial permissions. Maybe I should suggest to the development folk? I'd do it myself...if I were a programmer!

---

### Post by sidd-tx on 2006-09-27
I have noticed the same thing as well. It's not a default with all linux distros though. CentOS, Red Hat and Fedora have more restrictions file permissions, where regular users cannot even view the contents of other user's directories...

But I really like Ubuntu/Kubuntu, and it's not a good enough reason for me to leave. I hope that the next release has a little more secure file permissions though... I'm sure Canonical will eventually get around to it...


Sidd...

---

