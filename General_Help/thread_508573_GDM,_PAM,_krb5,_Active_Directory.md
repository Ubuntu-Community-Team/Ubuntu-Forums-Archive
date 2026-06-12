---
title: "GDM, PAM, krb5, Active Directory"
date: 2007-07-24
forum: General Help
---

### Post by SnowEagle on 2007-07-24
Hello world! Just swapped to ubuntu for my desktop a few weeks ago and it's great!!!! 

I've successfuly added my machine to our domain using: 
[URL="https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"]

I've stopped short of the PAM configuration as my objective is to acquire a TGT and mount my active directory home folder (I've heard that pam_mount might do this the most elegance?) at GDM login, while retaining the ability to login locally and sudo with my domain account.

I've tried this once with entertaining but undesireable results...

I copied the winbind lines into the 4 files as suggested in the howto, but obviously did it wrong as I was unable to login as a local user and/or root (password was asked twice and the correct password entered twice yielded no joy) and I was unable to sudo or su using my domain account (the account wasnt on the sudoers list). Unfortunately it was a busy friday so cant remember what exactly i did.

I've reinstalled ubuntu now, and re joined the domain etc with no problems but am feeling a bit cautious about messing with the PAM files again so wanted some advice before making the changes! 

How can i edit the files in /etc/pam.d for insta-kinit and AD home folder mounting at a GDM login???

PS I've followed the howto exactly but am aware that there could be a serverside issue as we're not using win2k3 r2, so the AD schema might not be cool enough for what I want, but am not sure if that's needed.

I appreciate any input anyone might have!!!

thanks, 

Andres

---

