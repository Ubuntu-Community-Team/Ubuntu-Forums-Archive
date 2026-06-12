---
title: "ubuntu 12.10 kiosk customisation"
date: 2012-10-20
forum: General Help
---

### Post by Quentin84 on 2012-10-20
Hello I an new to linux and was wondering if a person on this forum could point me in the right direction in creating a workstation which:

has a restricted account which:

logs in automatically
only opens firefox to browse the web
the user is restricted to only browse the web.

So in it is like a machine that are in run in internet cafe's for example.

i have googled kiosk ubuntu tweaks but i can not get any where with the instructions just need to be pointed in the right direction.

Cheers Quentin.

---

### Post by dino99 on 2012-10-20
hi Quentin,

your question is all about how to create restricted user account by you, the admin. See this little howto:

[http://www.howtogeek.com/54036/how-to-create-a-family-friendly-ubuntu-setup/](http://www.howtogeek.com/54036/how-to-create-a-family-friendly-ubuntu-setup/)

On ubuntu, there is a meta-package named ubuntu-desktop. His job is to set a default apps list for installation. As you want to limit the possible installation of apps, you need to unistall that ubuntu-desktop first, then uninstall the other apps; for example, gwibber, ubuntuone, ...

[http://askubuntu.com/questions/28238/how-do-i-restrict-users](http://askubuntu.com/questions/28238/how-do-i-restrict-users)
[http://askubuntu.com/questions/8149/how-can-i-restrict-program-access-to-other-users](http://askubuntu.com/questions/8149/how-can-i-restrict-program-access-to-other-users)

---

### Post by zombifier25 on 2012-10-20
Also, configure Firefox to always use private browsing is a good idea. Go to Edit > Preferences. Select the Privacy panel. Set "Firefox will:" to "Use custom settings for history". Then check "Always use private browsing mode".

---

