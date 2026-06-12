---
title: "Changed permissions of /home folder and cannot login anymore"
date: 2013-01-16
forum: General Help
---

### Post by Tjalleman on 2013-01-16
I was messing around with the permissions and changed permissions of /home and /etc folder to 770. After doing that, I got disconnected of the terminal and now I cant login anymore. When I type Username + correct password, I get logged in for just half a second and then thrown out again, back to the login part (login as: ).

How do I restore the permissions back to its default settings?

---

### Post by circa on 2013-01-16
If you can access terminal, type 
 > chmod *700*  /home 

This gives the directory "owner" full access, but not anyone else. If you want to share files, use 755 in place of 700.

If you want to understand more, go here ...

[http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)

---

### Post by Tjalleman on 2013-01-16
Circa, thanks for your answer. What you are suggesting started all my problems. Since i changed the permissions, I cannot login to the terminal anymore. I'm looking for a way to restore the permissions of the folder back to its default settings (fingers crossed that this will solve my login-problem).

---

### Post by Warren Hill on 2013-01-16
[I]First you need to get to a terminal prompt.  If you can't the normal way then follow the instructions here [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
as far as 

ls /home

You are now logged in as root so can change the pernissions back to what they should be

chmod  755 /home
chmod 755 /etc

[/I]

---

### Post by mcduck on 2013-01-16
As long as you didn't use the "-R" option for recursive chmod, booting into recovery mode (available in the Grub enu when you boot the system) or with a live-CD/USB should be enough to allow you to change the permissions back to correct ones.

...however if you did use the "-R" option, fixing the permissions of all the files inside /etc would probably take more work than backing up your persona files and making a fresh install.

---

### Post by Tjalleman on 2013-01-16
Solved! Thanks guys! This is what I did:

1 Booted in recovery mode
2 mount file system as read/write the way the link of Warren Hill does, with one small difference in code: mount -o remount,rw /[directory]
3 changed the permissions back to 775.
4 reboot

Now i can login at the terminal again.

N.B.: Eventually the directory that caused the problem was /bin.

edit: @ mc duck: i didn't use the -r option.

---

