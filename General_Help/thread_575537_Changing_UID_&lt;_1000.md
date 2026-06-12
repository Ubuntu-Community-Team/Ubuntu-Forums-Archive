---
title: "Changing UID &lt; 1000"
date: 2007-10-14
forum: General Help
---

### Post by r-mo on 2007-10-14
Hi,

I'm trying to configure uid's to be the same between mac os and ubuntu. I've changed the uid and gid to be the same and it works fine but, I can't see the users in users-admin for them to change passwords. I guess this is because the uid is less than 1000 as I had to change a setting in gdmsetup to show uid's over 500 rather than 1000.

So, my question is, can I change the minimum value for uid's to 500 rather than 1000 for users-admin to work? Or, am I being simple and really should be doing this some other way?

Hope someone can help

Stephen

---

### Post by geirha on 2007-10-14
I think users-admin uses adduser/addgroup when it creates users/groups, so configuring adduser might work. Edit /etc/adduser.conf and change LAST_SYSTEM_UID and FIRST_UID.

---

### Post by r-mo on 2007-10-14
I was hopeful then but changed it and the users still don't show up.

I've changed a couple of other things as well.

In /etc/gnome-system-tools/users/profiles I changed the uid-min values this has made users-admin create new users with uid's in the 500's but they still don't show up in the gui :(

I also changed /apps/gnome-system-tools/users/showall to true in gconf but, this didn't seem to do anything at all :(

---

### Post by geirha on 2007-10-14
/etc/gnome-system-tools/users/profiles certainly sounds like the right file to change. The fact that it had no effect sounds like a bug to me. You should probably file a bug report [https://bugs.launchpad.net/](https://bugs.launchpad.net/) .

---

### Post by r-mo on 2007-10-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/99265](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/99265) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks for your help, there's already a couple of bug reports for this.  Might look at changing the uid to over 1000 in mac os instead.  Scary though as it doesn't seem to use /etc/passwd etc :s google here I come

Bug report

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/99265](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/99265)

---

### Post by r-mo on 2007-10-14
Yay! I got it working.  Changed /etc/login.defs so UID_MIN 1000 became UID_MIN 500

found that in [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/70850](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/70850)

Just in case anyone else is having this problem here's what you need to do

edit /etc/login.defs change UID_MIN 1000  to UID_MIN 500

edit /etc/gnome-system-tools/users/profiles  changing each uid-min=1000 to uid-min=500

edit /etc/adduser.conf LAST_SYSTEM_UID=999  to 499  and FIRST_UID=1000 to 500

---

