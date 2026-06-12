---
title: "Need Help!! Restricting access to users' home folders"
date: 2006-12-28
forum: General Help
---

### Post by bvisser on 2006-12-28
Hi All, First post :-D 

I've been running ubuntu 6.06 server for a while now in a basic LAMP configuration.

I've just now started granting access to my server for some friends, but I would like it if I could restrict my friends from accessing my home folder, while at the same time I'm running a website in my /home/brandon/public_html/ folder. 

Basically I want a permission denied if someone was to try and cd /home/brandon and they weren't me. I know it seems easy but I don't understand permissions that well.

Can someone tell me how to accomplish this? I'm most concerned about my home folder, but is there a way to generally restrict any user from going into any other users' home folder?

Keep in mind I'm doing this all through the command line, I don't have gnome/kde installed.

THANKS!! I've been spinning my wheels for an hour or so on this ](*,) 

- Brandon

---

### Post by dcstar on 2006-12-28
> **bvisser said:**
> Hi All, First post :-D 

I've been running ubuntu 6.06 server for a while now in a basic LAMP configuration.

I've just now started granting access to my server for some friends, but I would like it if I could restrict my friends from accessing my home folder, while at the same time I'm running a website in my /home/brandon/public_html/ folder. 

Basically I want a permission denied if someone was to try and cd /home/brandon and they weren't me. I know it seems easy but I don't understand permissions that well.

Can someone tell me how to accomplish this? I'm most concerned about my home folder, but is there a way to generally restrict any user from going into any other users' home folder?

Keep in mind I'm doing this all through the command line, I don't have gnome/kde installed.

THANKS!! I've been spinning my wheels for an hour or so on this ](*,) 

- Brandon
```
sudo ls -l /home
``` will show you the permissions, Owner and Group of the various Home directories, they should all only be accessible (by default) by the particular user and the System Administrator.

If you create "ordinary" users, they should only have permission for their own home directories.

---

### Post by bvisser on 2006-12-28
Hi DcStar,

Thanks for your reply.

ok I have my user i created using adduser, of group users. his home directory is 755. 

then there is me, the user ubuntu created on install, my name is brandon and for some reason my group is brandon. My home dir is also 755. 

i can get into his home dir, and for some reason other users can get into my home dir. 

Obviously i can't write to his and vice versa, but I would prefer that if my users tried to get into my home dir  (ie cd brandon) they get a permission denied.

---

### Post by majoridiot on 2006-12-28
this will set the privileges to owner read, write and execute with no permissions for the rest
of the group or other users:

```
chmod 700 <dir>
```

you can use that on whichever home (or other) dirs you like.  you didn't specify how the
other users will be connecting... but both ftp and ssh have methods for chroot-ing 
(restricting) users to their home directories.

---

