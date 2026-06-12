---
title: "Domain Group Sudoer Permissions"
date: 2014-04-06
forum: General Help
---

### Post by evil5826 on 2014-04-06
Mod please relocate this if its in the wrong area.


So I have been doing some testing with domains and stumbled upon a couple bumps in the road.
I have install Likewise and successfully joined a ubunt server and desktop to the Windows Domain.
Adding the group domain admins to the sudoers file %DOMAIN\\domain^admins ALL=(ALL) ALL works fine on my server....but if i put that same thing in the sudoers file on the desktop it doesn't work. 


sudo -i
***** is not in the sudoers file.  This incident will be reported. <-- this person is a domain admin and it should work. Like I said it works fine on the Ubuntu Server but not on Ubuntu Desktop.


This also occurred on Xubuntu as well.


So besides the default associated packages installed when using apt-get install likewise-open-gui....Joined domain just find the way it was besides the nsswitch file. Is there something else needed that the server has installed by default but the Desktop doesn't?


Only thing I chose to install on the server upon install was ssh server and smb server.

Ubuntu Desktop, Server and Xubuntu 13.10


Update:

Just tried it on LTS Desktop and the same situation occured. Seems to be only the Desktop version doing this. Make me think something else needs to be installed that comes default with server.

---

### Post by evil5826 on 2014-04-06
Just tried it on Kubuntu Desktop and it worked fine. Only thing different I did was edited the sudoers first and then added the desktop to domain via command line instead of using gui. I just don't like KDE.

---

### Post by evil5826 on 2014-04-06
Another fresh install of Ubuntu Desktop, edited sudoers and added to domain via command line. All seems to be working now. Even added another group to sudoers on the fly after domain join and its working.

The gui join must be screwing with something.

---

