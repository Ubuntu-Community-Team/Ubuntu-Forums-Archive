---
title: "Accidentaly Deleted my Linux Account"
date: 2013-05-10
forum: General Help
---

### Post by thisislinuxdj on 2013-05-10
:confused: When i was making my Livecd manually because remastersys will not be up anymore soon, did not get what this command did below typed it in and deleted my account! i can still access my stuff through another Distro i have installed, but cannot login to the distro i put this command in! NOW I KNOW WHAT IT DOES LOL! do i need to reinstall that Distro??? i was wondering if i could go into recovery and drop down to a root shell and reinstall my account! Thank You! :P for any help given! 
[COLOR=Blue]for i in `cat /etc/passwd | awk -F":" '{print $1}'` do     uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`     [ "$uid" -gt "998" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null done[/COLOR]

---

### Post by sandyd on 2013-05-10
Try
```

useradd *username* --gid *username* --groups adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare -d */home/username* -M -N -s /bin/bash

```
Replace *username* with your username (also /home/username)

---

### Post by deadflowr on 2013-05-10
^ Would the above command need a sudo?

---

### Post by matt_symes on 2013-05-10
Hi

Slight typo by sandyd.

```
UN="<Your_username>" && sudo useradd --gid $UN --groups adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare -d /home/$UN -M -N -s /bin/bash $UN
```

Change <Your_username> to your user name.

It assumes that your main user group still exists (-N). This is probably a valid assumption.

It assumes you still have your home directory (-M) and that switch was most probably put in there for this comment.

> i can still access my stuff through another Distro i have installed, but cannot login to the distro i put this command in!

However, from man userdel.

> 
-f, --force
           This option forces the removal of the user account, even if the user is still logged in. [B]It also forces userdel to
           remove the user's home directory[/B] and mail spool, even if another user uses the same home directory or if the mail spool
           is not owned by the specified user. If USERGROUPS_ENAB is defined to yes in /etc/login.defs and if a group exists with
           the same name as the deleted user, then this group will be removed, even if it is still the primary group of another
           user.

[COLOR=#000000]```
for i in `cat /etc/passwd | awk -F":" '{print $1}'`  
do     uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`
      [ "$uid" -gt "998" -a  "$uid" -ne "65534"  ] && 
**userdel  --force** ${i} 2>/dev/null done
```[/COLOR][COLOR=Blue]
[/COLOR]
Are you sure you can access your home directory ? I would check you still have a home directory. If not the above command will need tweaking.

userdel --force will delete a user ;).

Kind regards

---

### Post by thisislinuxdj on 2013-05-11
Thank You Guys for Reply's! Will try them when have time! :guitar:

---

