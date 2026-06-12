---
title: "GUI gksudo and gksu passwords not authenticating"
date: 2006-07-14
forum: General Help
---

### Post by cville_cpl on 2006-07-14
I am setting up an Ubuntu 6.06 system for Ldap authentication against my ldap server. Now I find that none of the "admin" accounts, local or ldap, are able to open GUI admin windows from the GUI, Gnome. I can still use the sudo, gksu, and gksudo from term to open the windows. I have Narrowed this down to the four "common-*" files in /etc/pam.d/ If I put back the old files I do not have a problem authenticating from the GUI but can not authenticate with the Ldap server at all. I was wondering if anybody knew these files to know what would need to be changed to allow both to happen?

---

### Post by jmr on 2006-08-28
I seem to have the same problem.

I configured a machine for network authentication/authorization with pam_krb5 and nss_ldap.  sudo from the terminal works fine, but gksudo fails if it needs to ask for a password.  It fails invariably from the menus, after a while, without any warning or explanation, which is rather unpolite.

It looks like a bug.

Have you found a solution or work-around?  Doing without network authentication is not an option, of course.

João

---

### Post by cville_cpl on 2006-08-28
No. I just started doing everything from Term. If there are any Ideas on the subject, I would be willing to try them out.

---

### Post by garba on 2006-08-29
isn't gksu just supposed to be a frontend to su? i've just bothered with installing gksu on my kde-based debian system and it looks like it doesn't work here either... funny thing is, su works flawlessly when authenticating against ldap accounts... another fine product by gnome i guess :mrgreen:

---

### Post by jmr on 2006-09-01
garba,

Does kdesu work fine in your setup?

---

### Post by luckyjunknowitz on 2006-09-06
All,
Interestingly enough, I'm having the same problem with this, but when using winbind and kerberos to authenticate to a network (Windows AD 200x). (similar to what cville_cpl might have set up...)

This is a laptop which is not always on that network, so I need to be somewhat carefull about what gets put where in the PAM services files: common-*, samba, gdm, etc...

In other words, when on the network, I want to login and authenticate to a user which exists on the AD server, but when off the network I need to have the `pam_unix.so` module authenticate me against a local user. The user names are not the same and have different home directories.

I used a little utility (more like a collection of scripts with a GUI front-end) called SADMS to try to set up things automatically.  It "adjusts" the pam module stacks in the /etc/pam.d folder and this works....for the most part

Fortunately I made backups of all the files it was going to touch, since it doesn't seem to do so on it's own (future feature request I suppose) and I can revert to the original files.

I've found that in the common-auth file located in the /etc/pam.d folder there is the line:
    auth required pam_mount.so
which causes all sorts of strange behavior for gksu - based actions.

Generally pam_mount.so referes to some stuff that's set up in a config file located in /etc/security called pam_mount.conf

It looks like SADMS put all sorts of fungus in there that has the wrong paths for some stuff in either /usr/bin and /usr/sbin which I have to through and figure out.

It's obviously not a module required for local logins, so I have to figure out a way to make it work ONLY for when pam_winbind.so and pam_krb5.so do their thing against an AD server.

For now it's commented out an everything works dandy, but I lose the mount points it is supposed to set up, etc...

I'll post more as I discover it.

Also, while I may appear to have slammed SADMS in this post, I have to say that this little "utility" has been very helpfull in setting stuff up.  It's just that my particular situation is not "Standard" and therefore requires some manual editing of lots of config files.

In other words, don't depend soley on a "wizard" tool to config stuff for you, but instead spend some time learning what all the files do and why.  It helps to have a VM of the system you wish to config to keep the oopsie moments to a minimum pain level.

Cheers,

Luckyjunknowitz

---

### Post by garba on 2006-09-06
> **jmr said:**
> garba,

Does kdesu work fine in your setup?

yep, it works ok

---

### Post by jmr on 2006-09-06
For the record: I'm using pam_mount in my setup too.

Still, I feel inclined to blame gksudo, since sudo works just fine...

---

### Post by ScislaC on 2006-09-12
Add one more to the list of people affected by the gksu problem... also a SADMS user as well. (So yeah, pam related it seems)

---

### Post by abovett on 2007-05-10
I've got the same problem - once I start using winbind, gksudo stops working. Revert my PAM files etc. to their original state and it works again.

Anyone made any progress on this yet?

BTW, there's also some stuff abouut this in this thread:

[http://ubuntuforums.org/showthread.php?t=5409]("http://ubuntuforums.org/showthread.php?t=5409")

Andy B

---

### Post by Sara on 2007-11-27
I've the gksu problem as well with. 
On searching around it appears to be a common problem when ever network authentication is used.
The workaround I have at present is to 
replace the gksu in all the menu items with sudo 
then change 
Type to "Application in terminal"
Not the most elegant solution but functional.

Regards Sara

---

