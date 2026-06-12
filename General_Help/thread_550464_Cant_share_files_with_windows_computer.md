---
title: "Cant share files with windows computer"
date: 2007-09-13
forum: General Help
---

### Post by jasonpeinko on 2007-09-13
my fiend cannot get shared folders to work with his linux comp and windows comp, he needs to get files transfered over. I have triend everything, installing samba lots of other stuff to, what wcould be going wrong?

---

### Post by Fungyo on 2007-09-13
this thread may be helpful [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=202605")
or this guide [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

---

### Post by Wiebelhaus on 2007-09-14
sorry this took so long to reply to , I'm a busy dude.

 First install samba

> sudo apt-get install samba

With this you will have samba installed on your system, now you need to edit the configuration file which is located at:

I type > sudo nautilus and then browse to the file i want to edit , other folks prefer different ways. 
> 
/etc/samba/smb.conf

Here I would put a simple minimal configuration to allow share files from your Linux server.

 

> 

[global]

workgroup = MSHOME

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/USERNAME IN LOWERCASE

 

read only = No

guest ok = Yes

 

 

    * workgroup; Lets you specify the windows workgroup
    * netbios name; Lets you specify the name with your Linux PC will be seen by windows PCs
    * security; specifies the level of security, default is user, but if the users on the windows PCs are not the same as the ones on the Linux PC, you better use share instead
    * auth methods; Possible options include guest (anonymous access), sam (lookups in local list of accounts based on netbios name or domain name), winbind (relay authentication requests for remote users through winbindd), ntdomain (pre-winbindd method of authentication for remote domain users; deprecated in favour of winbind method), trustdomain (authenticate trusted users by contacting the remote DC directly from smbd; deprecated in favour of winbind method)
    * domain master; Lets you configure your PC as a domain master or not, in this case we prefer not, as our goal is only to share files
    * wins support; If you want or not to have wins enabled or not

Now comes the shares section, the string you put between the [] will be how windows will sees the share, in this case share1

      path; You put here the path you may want to share

      read only; yes or no, depending if you want to permit other users to write on this directories.

      gest ok; It is a boolean field, and will permit or not guest users to access this resource

______________________________________________

For simple sharing that is all that is needed___

---

