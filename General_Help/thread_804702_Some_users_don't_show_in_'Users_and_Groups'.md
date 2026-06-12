---
title: "Some users don't show in 'Users and Groups'"
date: 2008-05-23
forum: General Help
---

### Post by NDPeter on 2008-05-23
Hi.  I'm trying to lock down some folders such as my music folder that I have in my users home folder.  I'd like to change it so that others can't copy those files.  The issue I've run up against is that I use Ampache to stream my music and so the apache user (www-data) needs edit ability.  

I've played around with the [wiki page]("https://help.ubuntu.com/community/AddUsersHowto?highlight=(Users)") and been able to create a group that has my user and the www-data user.  And I am confident I could go find the page on 'chown' to change the permissions.  I'd like to be able to do this all with the permissions tab of the folder properties in Nautilus.

I'm also curious about the fact that the www-data user doesn't appear when I try to modify Users and Groups graphically (hence learning...however temporarily...how to do this via the command line).  Are these issues related?

It'd be easier for me to be able to use Nautilus as I doubt I'll be back changing permissions all that often and I tend to forget the commands I don't use more than once a week.

And I know that www-data exists as when I check the apache process it's being run by www-data.

To sum up...mainly wondering why all the users don't show up in the Users and Groups window (System-->Administration).  

Thanks.

*Edit: I've almost solved the permissions issue by making edits to /etc/apache2/envvars.  Never did figure out the other bit with the users not showing up...but I'll settle for the assumption that those much smarter than me designed it that way so that things don't get too messy.*

---

### Post by Audiosears on 2008-06-11
I had the same problem as well - the www-data user/groups still works, but it doesn't appear for me either and I'm forced to use the command line to do anything with users / groups.

In my case, one or all of the passwd / group / shadow files got corrupted and when I replaced them and reset permissions, I can't administer any user from the "Users and Groups" GUI anymore, unlock button doesn't work, etc.

---

