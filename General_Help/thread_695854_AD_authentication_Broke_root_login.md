---
title: "AD authentication Broke root login"
date: 2008-02-13
forum: General Help
---

### Post by arell12 on 2008-02-13
I have been working on getting my Ubuntu isntallation authenticate to AD for authentication so that it can be a file server.  I did get this working but now when I try to log into my server using ssh I enter root and then the password and I get dropped right away.  But I can login in as a AD user with my AD password. I must have disabled the root login somehow, anyone know where I could start looking?

Services that I have installed are samba, winbind, krb5-user, ntp and ssh-server.

---

### Post by pointone on 2008-02-13
Ensure you have root logins enabled: /etc/ssh/sshd_config (although keep in mind that this is insecure; make sure you know what you're doing here!)

You should also look through your PAM stack: /etc/pam.d

There are a number of things that could go wrong here. Post the contents of /etc/pam.d/ssh(d) here if you're unsure. Be sure to post the includes as well (if any).

---

### Post by arell12 on 2008-02-13
I think that I edited a file wrong in the pam.d folder.  This is the common-account file

# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
#account        required        pam_unix.so
account         required        pam_winbind.so
~
I think that i need to unremark this line

#account        required        pam_unix.so

but I dont have rights to do so.

---

### Post by pointone on 2008-02-13
Indeed you do. You'll want it to read:

```
account sufficient pam_unix.so
account required pam_winbind.so
```

This makes it so it will immediately succeed if pam_unix succeeds (local users), but if pam_unix fails, it will try pam_winbind (AD users).

You'll need to reboot into recovery mode to fix this, I believe. Hopefully it hasn't completely stuffed your system.

BE VERY CAREFUL WHEN EDITING YOUR PAM STACK. You can easily lock yourself out of the system! I recommend you read up on PAM before trying anything else.

---

### Post by arell12 on 2008-02-13
How to I get into recovery mode?

---

### Post by arell12 on 2008-02-13
Well I was able to get into recovery mode and chagne that file but I still cannot login the Ubuntu box with local accounts.  I must have chagned something else.  I did join this computer to the windows domain but I should still be able to log into the box with local accounts shouldnt I?

---

### Post by pointone on 2008-02-13
Did you edit any other files in /etc/pam.d? Post them here.

Did you edit /etc/nsswitch.conf? If so, post the file here.

Try checking /var/log/auth.log for details of what's failing when you attempt to log in.

---

### Post by arell12 on 2008-02-13
I went back over what I did to the pam.d files and I posted them below:

Now go to /etc/pam.d and edit the following files:

common-account:

#Commented for winbind to work
#account-required pam_unix.so
account-required pam_winbind.so


common-auth:

auth sufficient pam_winbind.so
auth required pam_unix.so nullok_secure use_first_pass


common-session:

session required pam_unix.so
session required pam_mkhomedir.so umask=0022 skel=/etc/skel/


sudo:

auth sufficient pam_winbind.so
auth required pam_unix.so use_first_pass

Now I cant login to the server usign windows user account via SSH but that is how I wanted it.  I just want winbind to do authentication at that seems to still be working.  this is jsut a fiel server that domain users will have access to.

I commented out the chagnes that I made and rebooted and was able to get back in with root via ssh.  I did make chagnes to the nsswitch.conf file but its working now so it must have been one of those files I edited.  If you know which one let me know.  Thanks for pointing out where to look. I have only been using Ubuntu for 2 days.  I tried looking for some info on PAM but didnt get to far.  I will most definatley look at getting more info on Ubuntu.  Thanks for your help.

---

### Post by pointone on 2008-02-13
I learned about PAM primarily with [this helpful guide]("http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html").

The problem in common-account I pointed out above is still there. Have you tried changing it yet?

Also, I notice you write:

```

#account-required pam_unix.so
        ^
account-required pam_winbind.so
       ^
```

You do not want hypens/dashes there. They should be spaces/tabs.

---

### Post by arell12 on 2008-02-13
yes, sorry, I just copied and pasted what was on the site that I was referencing for this.  I did remove hyphens and removed the remark from common-account and remarked the second line.  this did not fix my problem.  It must have been one of the other files that remarked to get this to work.  

thanks for your help.

---

