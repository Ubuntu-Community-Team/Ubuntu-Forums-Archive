---
title: "mount: only root can mount //Server"
date: 2012-11-02
forum: General Help
---

### Post by xScooterx on 2012-11-02
Hello everyone, 

I am trying to mount a windows share in /etc/fstab to a folder /home/user/windows 

I am using Ubuntu 12.10 32-bit

I made the folder with:

mkdir ~/windows

The line at the end of my fstab is :

[LEFT]//media-tower/OldMedia /home/media/windows cifs user=user,password=password,uid=1000,gid=100 0 0
[/LEFT]

I can see a icon of a network share on my side bar, clicking it, nothing happens.  When I open my home folder in the explorer i can see it under network, but clicking it gives me the following error:

mount: only root can mount //media-tower/OldMedia on /home/media/windows

What am i missing? It seems to me that for some reason when it tries to mount that share, it is not using the root user,  I got the uid and gid from the results of

 sudo id user_name 

Can someone please help me out?

---

### Post by redmk2 on 2012-11-02
> **xScooterx said:**
> Hello everyone, 

I am trying to mount a windows share in /etc/fstab to a folder /home/user/windows 

I am using Ubuntu 12.10 32-bit

I made the folder with:

mkdir ~/windows

The line at the end of my fstab is :

[LEFT]//media-tower/OldMedia /home/media/windows cifs user=user,password=password,uid=1000,gid=100 0 0
[/LEFT]

I can see a icon of a network share on my side bar, clicking it, nothing happens.  When I open my home folder in the explorer i can see it under network, but clicking it gives me the following error:

mount: only root can mount //media-tower/OldMedia on /home/media/windows

What am i missing? It seems to me that for some reason when it tries to mount that share, it is not using the root user,  I got the uid and gid from the results of

 sudo id user_name 

Can someone please help me out?
The root user is the only that can mount shares or partitions unless you tell the *mount command* otherwise in fstab.

The pertinent section of "man mount" is```
       The non-superuser mounts.
              Normally,  only  the  superuser can mount filesystems.  However,
              when fstab contains the user option on a line, anybody can mount
              the corresponding system.

              Thus, given a line

                     /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

              any  user  can  mount  the iso9660 filesystem found on his CDROM
              using the command

                     mount /dev/cdrom

              or

                     mount /cd

              For more details, see fstab(5).  Only the user  that  mounted  a
              filesystem  can unmount it again.  If any user should be able to
              unmount, then use users instead of user in the fstab line.   The
              owner option is similar to the user option, with the restriction
              that the user must be the owner of the special file. This may be
              useful e.g. for /dev/fd if a login script makes the console user
              owner of this device.  The group option  is  similar,  with  the
              restriction  that  the  user  must be member of the group of
```

The user mentioned is NOT the *user=<someone>* that you use with CIFS mounts.  This means you have to have both *[COLOR="Blue"] user[/COLOR]* and *[COLOR="Red"]user=<someone>[/COLOR]*

---

