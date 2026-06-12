---
title: "samba /opt/samba/profiles"
date: 2007-03-21
forum: General Help
---

### Post by b4nsh33 on 2007-03-21
Hi, i want to disable the use of profiles in samba3, wtf, my /opt/samba/profiles is 3.2 Gb and i still dont add all my users, samba copies the my docs and desktop and other folders for each user, why on earth would someone transfer so much data to the pdc server, my users are used to place a lot of information in their desktop and in my doc (the ms office's recommended place), in my old ms w2k server it didnt take so much space,  is this a samba or windows fault?

i have googled around and i  found that you have to place in smb.conf

logon home =
logon path =

i already have those, but i also have this one :
[profiles]
   path = /opt/samba/profiles
   writeable = yes
   browseable = no
   #create mode = 0644
   #directory mode = 0755
   # this prevents users from browsing other peoples' profiles
   create mode = 0600
   directory mode = 0700


but it didnt work, and if i cut off the [profile] item, the user gets a error when shes loging in and any setting in the desktop, start menu or msoutlook dont survive a logoff/login

thanks
---
Miguel

---

### Post by lptr on 2007-03-31
This is the client centric way to change things:

+ Open Windows control panel / System 

+ In Systemsettings tab advanced there is a button 'user profiles'

+ In this dialog you can choose user and changing type of stored profiles - local or server based.

Maybe anybody could help out how to  manipulate this setting to be default? Would be interesting for me, too.

rob*

---

