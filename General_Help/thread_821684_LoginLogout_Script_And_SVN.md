---
title: "Login/Logout Script And SVN"
date: 2008-06-07
forum: General Help
---

### Post by hut101 on 2008-06-07
Though this subject has been thoroughly beaten to death, I wish to discover a means for roaming desktop capabilities using login/logoff scripts and svn. I work at a student organization on an engineering project that requires considerable flexibility and redundancy.

Our environment consists of a Window 2003 Server as domain controller and running an Active Directory. We also posses several computers which run Ubuntu 8.04 server edition with daily automatic updates. One acts as an SVN server for software development while another runs our web application. Our workstations consist of x86-64 computers that dual boot into either Windows XP SP 2 or Ubuntu 8.04 workstation edition.

For our Ubuntu workstation we need roaming desktop capabilities similar to Windows. This is partly due to “musical chairs” that we play on a daily basis. Also, no single workstation is assigned to a student, and we have a high turn over in terms of users. Therefore my plan was to create an SVN server that will house a trunk that consists of folders for each user at our organization. Upon logging into an Ubuntu workstation the SVN folder named after the user is checked out into the user’s workstation profile folder that is automatically created by the workstation. That folder should therefore contain all their preferences and files. During their session any changes they make are committed to the SVN server and any changes made to the server are updated within the user’s session. Upon logging out of their session, all changes are committed to the SVN server, and their user folder is deleted from the workstation.

By implementing roaming profiles by this method, users would be provided with a revision history for all their files. It would also eliminate folders from workstations of users who are no longer at our organization.

Is there a means to create a script that will be called upon the creation of a user profile folder when they first log onto a computer and have that script checkout their SVN folder? Then when they logout, all their changes are committed to the SVN server, and their user profile deleted.

An issue which would result from this method would be the time it takes to checkout files from the SVN server. Therefore another solution would be the update of a user profile upon logging in and the commit of their changes without the deletion of their user profile when logging out.

Using the ~/.bash_profile file within each user profile folder is out of the question. We can’t add user profiles to each computer as we get new computers or users. I’ve attempted to use the /etc/profile file but with no luck. I’ve read a thread of someone who used the /etc/X11/Xsession.d/ folder to store a script that would automatically run when someone logged in using a GUI session, though I am not sure if that would be the best solution in this case.

Any help would be greatly appreciated for this situation.

---

