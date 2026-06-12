---
title: "ubuntu and W2K active directory NM"
date: 2004-12-16
forum: General Help
---

### Post by dobricchi on 2004-12-16
hello,

i am thinking to gradually introduce linux boxes into my windows environment, to leave it at all in a next future.

ubuntu is one of the best distros we are trying.

i'm experiencing a bit of problems trying to use active directory collaboration, more than mounting a share (using samba for windows share mounting is working well); i'm trying to use Win2K AD to authenticate users on ubuntu box.

i read tons of faqs and howtos regarding:
- how to authenticate debian and other distros on a windows domain
- how to make linux a domain member in Win2xAD

i tried some configurations, and the better results are obtained by using the document [nt domain authentication in ubuntu HOWTO](http://www.ubuntuforums.org/showthread.php?t=5409&highlight=winbind) 

the result is that i'm able to join my domain, i'm able to browse domain with wbinfo commands.

but when i try to log in ubuntu after a reboot with a AD user it tells me that every account that i try is locked and i cannot login.

i think that user browsing is working fine cause i don't see problems in /var/log/samba/log.winbindd, and i see errors when i try tu use a user that doesn't exist in my AD.

i read in that howto that it wasn't tested in a native mode AD like i have, even if i read some howtos for other distros (fedora and redhat) that told to use same modules (samba and winbind) and modify same files.

i also read in other distros notes that for a better collaboration with AD it is better to use kerberos 5 modules (even if these notes were referred to a win2003 AD in native mode that is slightly different than w2k)

so,


is there anyone who successfully tryed to authenticate an ubuntu box with a windows 2000 active directory environment? thanks in adv.

---

### Post by Marc Higgins on 2005-06-26
we've been trying to do the same thing, except authenticate to a SME box is 6.0.1 with the unofficial update script applied (that just make esmith so very much better)

We know it can be done because mandrake seems to do a domain login with SME or W2K Server or NT4 Server out of the box as long as you join the domain during the initial build, but well it's just not our desktop of choice we love Ubuntu - Hoary Hedgehog 5.04

We too have been following & playing with this;

[http://ubuntuforums.org/archive/index.php/t-5409.html](http://ubuntuforums.org/archive/index.php/t-5409.html)

but unfortunately haven't got it working yet. It seems to join the domain & everything tests OK, but when we reboot, just like your windows2000 domain we can't log in as any user, as in we're locked out.

If you do intend to play with this, as always i would recomend BACK UP YOUR FILES FIRST.

This is a script to do just exactly that; copy & paste this with your favorite text editor & save it as winbindbak.sh

#winbind_back_up script
cp -v /etc/login.defs /etc/login.defs.bak
cp -v /etc/nsswitch.conf /etc/nsswitch.conf.bak
cp -v /etc/samba/smb.conf /etc/samba/smb.conf.bak
cp -v /etc/pam.d/common-account /etc/pam.d/common-account.bak
cp -v /etc/pam.d/common-auth /etc/pam.d/common-auth.bak
cp -v /etc/pam.d/common-password /etc/pam.d/common-password.bak
cp -v /etc/pam.d/common-session /etc/pam.d/common-session.bak
cp -v /etc/pam.d/sudo /etc/pam.d/sudo.bak

then at a comand prompt run;

sudo sh /path_to_where_you_saved_it/winbindbak.sh

That way if you end up locked out like i did, you can come back up in rescue mode & put them all back;

& heres a script to do just that again copy & paste this to your favorite text editor & save as winbindrest.sh

#winbind_restore_backed_up_files & save the broken ones for investigation script
cp -v /etc/login.defs /etc/login.defs.bak2
cp -v /etc/nsswitch.conf /etc/nsswitch.conf.bak2
cp -v /etc/samba/smb.conf /etc/samba/smb.conf.bak2
cp -v /etc/pam.d/common-account /etc/pam.d/common-account.bak2
cp -v /etc/pam.d/common-auth /etc/pam.d/common-auth.bak2
cp -v /etc/pam.d/common-password /etc/pam.d/common-password.bak2
cp -v /etc/pam.d/common-session /etc/pam.d/common-session.bak2
cp -v /etc/pam.d/sudo /etc/pam.d/sudo.bak2
cp -v /etc/login.defs.bak /etc/login.defs
cp -v /etc/nsswitch.conf.bak /etc/nsswitch.conf
cp -v /etc/samba/smb.conf.bak /etc/samba/smb.conf
cp -v /etc/pam.d/common-account.bak /etc/pam.d/common-account
cp -v /etc/pam.d/common-auth.bak /etc/pam.d/common-auth
cp -v /etc/pam.d/common-password.bak /etc/pam.d/common-password
cp -v /etc/pam.d/common-session.bak /etc/pam.d/common-session
cp -v /etc/pam.d/sudo.bak /etc/pam.d/sudo

then at a command prompt run;

sudo sh /path_to_where_you_saved_it/winbindrest.sh

& you should be back up & running in seconds

Anyway until i get it sorted i'm hard wiring the mounts into the /etc/fstab, less than ideal, & not secure. The most frustrating thing is knowing it can be don't but not having the skills to do it

---

### Post by Triton on 2005-06-28
Have you had any luck?  I've been trying and trying myself and get everything to work except for the the login part.   ](*,)

---

### Post by Marc Higgins on 2005-09-05
no sorry this is as far as we have gotten as well, have started a new thread in networking;

[http://www.ubuntuforums.org/showthread.php?t=62793](http://www.ubuntuforums.org/showthread.php?t=62793)

So hopefully someone will help find the missing pieces in the jigsaw for us

---

