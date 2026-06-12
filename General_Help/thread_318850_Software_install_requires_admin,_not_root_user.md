---
title: "Software install requires admin, not root user"
date: 2006-12-14
forum: General Help
---

### Post by rfroemming on 2006-12-14
I am installing a software program to a server that says to complete the installation you cannot be logged in as root, but have to be loggedin as a seperate system administration user.  Running the setup.sh install file as a normal user results in the setup program not being able to create directories, copy files, and edit config files like it needs to do.  Runing sudo setup.sh results in an error message saying that the root user cannot run the setup program.  Is there anything else I can do, like give the user I am logging in as different permissions?  From what I can tell, the user is a member of adm and admin.  I also added it to the root group.  Any ideas would be appreciated.  Thanks!

---

### Post by fragos on 2006-12-14
Log into the server as the first user you created for it.  That will be an admin group user.  I checked my admin group and saw that root isn't a member.  Making root a member make also fix things for you.

---

