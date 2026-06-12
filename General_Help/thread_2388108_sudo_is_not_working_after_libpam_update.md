---
title: "sudo is not working after libpam update"
date: 2018-03-28
forum: General Help
---

### Post by sbahadirarslan1 on 2018-03-28
Hi,
I am using Ubuntu 10.04. I know it is too old, but I have to use this version for some reasons.
I want to update libpam version to 1.2.1. So I followed following tutorial from linuxfromscratch for update this lib.  [http://www.linuxfromscratch.org/blfs/view/7.9/postlfs/linux-pam.html](http://www.linuxfromscratch.org/blfs/view/7.9/postlfs/linux-pam.html)
After all, I can take root permission by using su. But when I try to run sudo, I get following error every time :
[B]Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
[/B]
And this is my /etc/pam.d/sudo file :[B]
#%PAM-1.0

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so[/B]

Also here is /var/log/auth.log :
[B]Mar 28 19:45:31 sarslan-laptop sudo: PAM (sudo) illegal module type: @include
Mar 28 19:45:31 sarslan-laptop sudo: PAM pam_parse: expecting return value; [...common-auth]
Mar 28 19:45:31 sarslan-laptop sudo: PAM (sudo) no module name supplied
Mar 28 19:45:31 sarslan-laptop sudo: PAM (sudo) illegal module type: @include
Mar 28 19:45:31 sarslan-laptop sudo: PAM pam_parse: expecting return value; [...common-account]
Mar 28 19:45:31 sarslan-laptop sudo: PAM (sudo) no module name supplied
Mar 28 19:45:31 sarslan-laptop sudo:  sarslan : 3 incorrect password attempts ; TTY=pts/2 ; PWD=/etc/pam.d ; USER=root ; COMMAND=/bin/bash[/B]

Also &#305; add my user to root group. And this is not solved problem.

So I cant figure out what is my problem. Could you help me ?
Thanks and Best Regards

---

### Post by mörgæs on 2018-03-29
> **sbahadirarslan1 said:**
> 
I am using Ubuntu 10.04. I know it is too old, but I have to use this version for some reasons.

It certainly is too old and you are taking a big risk. If you post the reasons there is a chance that people can help you switch to recent software.

---

### Post by sbahadirarslan1 on 2018-03-30
Hello, thanks for your answer. 
I dont know it is totaly safe or not, I updated libpam successfully and it is working for now ( at least basic commands like su,sudo, sshd is working for now.)

For update the libpam, I followed this steps :

1 - First I followed this tutorial for update libpam :
[http://www.linuxfromscratch.org/blfs/view/7.9/postlfs/linux-pam.html](http://www.linuxfromscratch.org/blfs/view/7.9/postlfs/linux-pam.html)

2- When you update the libpam correctly, you should reinstall the shadow library ( this is indicated in the link.)
here is tutorial for updating shadow , [http://www.linuxfromscratch.org/blfs/view/7.9/postlfs/shadow.html](http://www.linuxfromscratch.org/blfs/view/7.9/postlfs/shadow.html)

as shown in these tutorials, /etc/pam.d/sudo is not updated. ( also sshd is not updated, this is important for ssh.)
I update sudo and sshd files in /etc/pamd/ directory correctly. 

If you don't use libpam before, I strongly suggest, read this tutorial [http://www.tuxradar.com/content/how-pam-works](http://www.tuxradar.com/content/how-pam-works)

Try to update this library carefully, because if you dont update this carefuly, maybe your system is not working after this update.
I faced many problems with updated this library.

But at the end, It seems working for now. :)

Thanks and best regards.

---

### Post by mörgæs on 2018-03-31
The problem is not libpam. It's all the hundreds of other packages in the system.

[Ubuntu security notices]("https://usn.ubuntu.com/") is a list of all security related bugs which have been fixed. Let's for simplicity assume that one bug fix is released every day. 

Your 10.04 was abandoned by the developers in May 2013. Now imagine how many security holes were discovered from then until today, almost five years later.

---

