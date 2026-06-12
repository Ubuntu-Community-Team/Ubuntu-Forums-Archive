---
title: "Edubuntu user group confusion"
date: 2007-12-03
forum: General Help
---

### Post by peterroots on 2007-12-03
School using Edubuntu
all users currently in /home/username
problem!
two different users at two different schools (unconnected systems) tried to delete some old users (staff and students)
Result
total mess!! some users were deleted as planned others lost their loggins but still had their files in their folders but their user name did not exist anymore.

I have been looking at one of these systems and the users and group numbers seem out of sync
some are fine eg usera is 1120 groupa is 1120 but others are like userb 1121 groupb 1125
Today I created myself as a new user - i got a user number 1151 and found myself in group 1153 (both called proots as intended/expected)
I also had a home folder /home/proots but interestingly it was owned by me but the group it was attached to was that of a student whose group number as 1151
I assume it is this mixing up of groups/users that caused the problems when a user was deleted.
I was thinking of solving the problem by trying to ignore it in the following way
move all students into /home/students/username and setting the group ownership of students to students such that each student had rwx to their folder but group and others were denied access.
If I did this, could I then delete all the groups that match student names?
(I would do the same sort of thing for staff)
then I would edit adduser.conf to make new users get added to /home/group/username by default and specify which group new users belonged to (staff, student etc)
I would then set an acl's on /home/students to let teachers see students work without letting students see other students or staff.

The big question!  Am I going to make things worse? It's not my computer system. I don't want to break it more than it is (my wife will never speak to me again if I do, and I don't suppose several other people will again either!)

---

### Post by peterroots on 2007-12-28
:( so no ideas from anyone :(

O well, I took the bull by the horns yesterday and had a go - it was still working when I left but I have yet to try deleting any users so don't know it the system is fixed.
There is something badly screwed up in the graphical edubuntu user administration - it caused the user group mismatch in the first place - disables unrelated users when you delete another user (probably because the group number of one matches the user number of the other)
it won't delete groups - says it has done it but acually does nothing.

for anyone interested this is what i did
I created folders  teachers, students and office in the /home folder
I moved all the home folder of students to /home/students teacher to /home/teacher and office staff (you guessed it) to /home/office

I created 3 new groups - teachers, students, office

I used chown to change ownership of the moved home folders
sudo chown -R  :teachers /home/teachers/
and did the same for students and office
I set the permissions to read write execute for owner and no access to group or others to the individual folders but not to the top level folder (ie all folders in /home/students but not students it self or no one could log in)

I edited /etc/passwd to reflect the new positions of users home folders and changed their group id to that of either teachers students or office as appropriate

I edited /etc/group to delete all the original users groups as I could not get rid of them with delgroup or the user/group management GUI.

I edited /etc/adduser.conf changing the following
i set GROUPHOMES=yes
I uncommented EXTRA_GROUPS = "......."  and added fuse to the list (and deleted dialout as I did not think is was worth having)
I uncommented ADD_EXTRA_GROUPS=1
then, after saving the file, I could create new users with the command 
sudo adduser --ingroup groupname username
this nicely put new users groups in the right subfolder of home, based on their group membership and avoids creating a group of the same name as the user.

I hope this now solves the problem of deletion of users!

To make file security work nicely I used the idea from another posting on these forums about how to get acl's to work (sorry can't remember url)
but basically
sudo setfacl -Rdm g:groupname:rwx /pathname
will set the default or change the default permissions to, in this case, let members of groupname have read write execute permissions on any new files or folders created (does this recursively for all folders)
sudo setfacl -Rm g:groupname:rwx /pathname does the same to all existing files and folders

g:groupname can be replaced with u:username and rwx can be just r or rw or, i assume rx or wx if that is your fancy

multiple users or groups can be added but running the command again and if you really bog up
sudo setfacl -Rb /path will recursively delete all the acl's you have set up so you can start again (or forget them altogether) - this has no effect on the normal user/group permissions it just extends them greatly

---

