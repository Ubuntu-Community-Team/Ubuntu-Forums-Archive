---
title: "user group membership - strange behavoiur"
date: 2008-01-08
forum: General Help
---

### Post by jghallen on 2008-01-08
I have created a 'users' group that will be able to share files in a common directory. 

The users are added
$>usermod -a -G users firstuser 
(have also tried $>gpasswd -a firstuser users)

Verified in the /etc/group file that I can find the entry
users:x:1001:firstuser

So far so good I thougt!
Now to the problem: the groups command does not show that user 'firstuser' is 
member of the 'users' group. 
$>groups   <-- does not show 'users' group
$>groups firstuser  <-- will show the 'users' group

If I su to firstuser, then the groups command will show the 'users' group correctly.
$>groups <-- will show the 'users' group

What am I missing?

Please help! (Without the right group membership - the users can not write to the directory as specified by the file permissions.

/John

---

### Post by p_quarles on 2008-01-08
The "groups" command without any arguments displays the group memberships of the current user. So, this just means that *your* user is not a member of that group. The system is behaving as it should.

---

### Post by jghallen on 2008-01-08
But I am! Or...

firstuser@computer:~$ id
uid=1000(firstuser) gid=1000(firstuser) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),
46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(firstuser)
firstuser@computer:~$ id firstuser
uid=1000(firstuser) gid=1000(firsuser) groups=1000(firstuser),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),
46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1001(users)
firstuser@computer:~$ 

This is what I find strange
When starting the shell from the desktop I get one set of group memberships that is not the same as when I su to my user.

Where should I read to understand what is happening?

Brgds / John

---

### Post by p_quarles on 2008-01-08
If you have to use su to login as "your" user, then presumably you are initially logged in as someone else.

EDIT: Possibly useful: If you're unsure of who your initial login user is, you can get its memberships by running this:
```
whoami | groups
```

---

### Post by jghallen on 2008-01-08
Thanks for your quick reply! 

The problem was resolved by itself! I think it must have been an error in the desktop session.
I switched user to test. My session crached and was logged out. When logging in again it works as expected.

Unfortunately I did not test the whoami | groups command. To se my effective user id.

Brgds / John

---

### Post by bodhi.zazen on 2008-01-08
When you change your group membership you need to log out and back in for the changes to take effect.

Thus when you crashed and logged back in -> problem solved :twisted:

---

