---
title: "NIS help"
date: 2008-02-25
forum: General Help
---

### Post by fouadk on 2008-02-25
hi everyone....

Our problem is the following: while configuring NFS on an ubuntu machine, We mount the home directory that is on the server to the home directory of the client. While doing so, we are deleting whatever was on the home directory of the client including the local administrator. So if at any time the connection is off, I will loose all access to the machine. How can I keep a local administrator account running while having the NFS set?

Thank you

---

### Post by rome-NY on 2008-02-25
That is why root login must be enabled because roots home directory does not get replaced. all local user home directories get replaced so they are gone. This is why I want to smack everybody who says there is no need to login as root. If your nis configuration does not work...and ubuntu's nis is broken...then you are screwed.

---

### Post by fouadk on 2008-02-25
Thank you for your help. But now I have a new question, how do I enable the root account.

I looked up, some suggested that I use the following command root passwd. But when I try to log in, it gives me the following
"The system administrator is not allowed to login from this screen"

Thank you in advance, your help is really appreciated.

---

### Post by fouadk on 2008-02-25
Thank you for your help. But now I have a new question, how do I enable the root account.

I looked up, some suggested that I use the following command root passwd. But when I try to log in, it gives me the following
"The system administrator is not allowed to login from this screen"

Thank you in advance, your help is really appreciated.

---

### Post by rome-NY on 2008-02-25
start a konsole and type
passwd root
enter the password you would like for root to use
in the same konsole window you are going to edit /etc/kde3/kdm/kdmrc
you will have to find what editor you can use, vi , nano, gedit, joe. iF you don't know just open adept and install nano or kate or gedit.
Now type sudo kate(whatever editor u have) /etc/kde3/kdm/kdmrc
look for a line that says
 # allow root logins?
 # Default is true
AllowRootLogin=false
now just delete the false and replace with true
save file and reboot

---

