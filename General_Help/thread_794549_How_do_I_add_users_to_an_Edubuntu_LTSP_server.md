---
title: "How do I add users to an Edubuntu LTSP server?"
date: 2008-05-14
forum: General Help
---

### Post by wonk-o-matic on 2008-05-14
I started with Skolelinux, but the LDAP tool for adding users (lwat) wouldn't let me get past the login screen.  I found other references to the problem, but no solution, so I just switched to Edubuntu.  

The nice thing about lwat (if it had worked) was that it let me create a user as either an Admin, Jr. Admin, Teacher, or Student.  That would have been great, and I expected something like that in Edubuntu.  However, I don't see anything like that.  

Maybe I'm not supposed to do this at the Main server, but that doesn't seem reasonable.  Nothing in the docs seemed to cover adding a new user.  

Does anyone know the "right and recommended" procedure for adding a new user?  

Thanks, 
Dan

---

### Post by ahmadzainul on 2008-07-30
I think its just very simple. You go to sytem-adminstrator-adduser and group. Its better after that u go to terminal. update your ltsp-kernel, LTSP image, ltsp-sshkeys.
sudo ltsp-update-kernels
sudo ltsp-update-images
sudo ltsp-update-sshkeys
:guitar:

---

