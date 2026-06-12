---
title: "rsync sets owner to 500 - user #500"
date: 2013-06-10
forum: General Help
---

### Post by xtrailrunner on 2013-06-10
I want to backup my laptop to a NAS drive using rsync. On both devices I have the same user and group. I'm using rsync with options: rltzuv. If I check the permissions on the NAS device I find the correct group setting but user is set to "500 - user #500". If I look into /etc/passwd user 500 is guest.
What can I do that ownership is set to the same user as on the laptop ?

---

### Post by HiImTye on 2013-06-10
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try the option
> -p, --perms preserve permissions
[http://linux.die.net/man/1/rsync](http://linux.die.net/man/1/rsync)

---

### Post by xtrailrunner on 2013-06-11
Thanks, but -a equals -rlptgoD, so -p is already included.

---

### Post by HiImTye on 2013-06-11
> **xtrailrunner said:**
> Thanks, but -a equals -rlptgoD, so -p is already included.

ah, you listed [quote=xtrailrunner]rltzuv[/quote]sorry for not being a mind reader

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by papibe on 2013-06-11
Hi xtrailrunner.

Could you post the actual command you are using?

Are you using rsync over ssh, or there's a rsync daemon on the NAS?

Is there a username on the NAS that matches laptop's ?

Have you tried mapping uids instead of usernames (option --numeric-ids)?

Regards.

---

### Post by xtrailrunner on 2013-06-11
Here is the command:
rsync -rltzuv --delete --stats --exclude='/dev' --exclude='/lost+found' --exclude='/media' --exclude='/mnt' --exclude='/proc' --exclude='/run' --exclude='/sys' --exclude='/tmp' --exclude='/var/crash' --exclude='/home/jmenge/.cache' --exclude='/home/jmenge/.local/share/Trash' --exclude='/home/jmenge/Downloads' --exclude='/home/jmenge/VBShared' --exclude='/home/jmenge/VirtualBox' --exclude='/home/jmenge/.recoll/xapiandb' '/' '/media/mybook/Public/Lenovo_T430/Ubuntu1304/Backup_110613'
The command worked until a new firmware was installed on the NAS. Both files from root and from my user were backed up correctly.

The NAS is mounted using NFS. Do I need the rsync daemon on the NAS ?

---

### Post by papibe on 2013-06-11
Thanks.

I don't see neither the option [COLOR="#FF0000"]**-a**[/COLOR] nor [COLOR="#FF0000"]**-p**[/COLOR] as you suggested you were using. Have you tried adding any of those options?

Also, in order to properly back up files owned by root to a NFS mount, you need to set the export option 'no_root_squash' (on the NAS).

Regards.

---

### Post by xtrailrunner on 2013-06-13
Thanks. The firmware import replaced my /etc/exports file. Therefore I had to modifiy the settings again and it works now. Sorry for the confusion concerning the options. I used two different versions of the command over the time and got confused when writing the posts.

---

