---
title: "[User account] Change default user"
date: 2008-05-25
forum: General Help
---

### Post by kakyoism on 2008-05-25
I installed Hardy with an initial user account,

now I want to change the name of this account...

I tried to create a new user by doing "useradd" and "passwd"
but then when I try to switch user, I saw pop-ups saying
no home directory for that user was found...

Should I create it manually somehow??

And is there any other way to achieve my original goal:
change the name of my user account

I really don't need two accounts on this machine.
Urgent...

Thank you.

---

### Post by ibuclaw on 2008-05-25
First, use "**deluser**" to remove the account you just created.
Then read this post [here]("http://ubuntuforums.org/showpost.php?p=4968029&postcount=2"). You'll find it very useful.

And secondly, if your going to create a user account.
I'd recommend that you use the **adduser** command instead.

Regards
Iain

---

### Post by driebel on 2008-05-26
Tinivole, thanks for you instructions, they're great!  I'm running into problems when I try to change the name of my home directory, however.  I originally created a new user with my desired new name.  Deleting that user to try your method didn't remove the home directory under that user name, so I now can't rename my old home directory to the new name, because that directory already exists.  sudo rm /home/newname still gives me a permission denied.  (I'm currently dave, I want to be driebel):

dave@Ishmael:~$ sudo rm -r /home/driebel
rm: cannot remove `/home/driebel/.gvfs': Permission denied

Can you help?

---

### Post by driebel on 2008-05-26
Well, I guess I deserve this, but I need some SERIOUS help now.  I tried to switch my username from dave to driebel.  I ran into some problems (see above) but thought I had everything switched back.  The user driebel doesn't exist, but the directory /home/driebel does.  I logged out, thinking maybe this directory would vanish on logging back in as dave.  However, ubuntu now wants dave's home directory to be /home/driebel, an empty folder!  I can't log in as my only existing user.  I can't recall the exact text of the error, but it's looking for something like a .dmps file in the /home/driebel folder.  I'm in DEEP trouble, folks.
The user that exists is dave.  The folder /home/dave does exist, and has all necessary files in it.  I just need help with some backdoor way to get ubuntu to know that.  Obviously, I am very new.  PLEASE HELP!

---

### Post by anjilslaire on 2008-05-26
That IS a mess. What you should have done was:
1. Create your new user account. 
2. Give it sudo/admin/etc permissions
3. Copy or move all your data from the 1st account's Home directory to the new account' Home directory. Not renaming/ reassigning directories.
4. Made sure everything was functional before removing/deleting.

You don't need to create new /home/ directories for new accounts manually. When that user logs in th first time, this is created appropriately by the OS.

So, as of now, can you log in at all? What happens after a reboot? If you can, create another user (not a directory) and log in. Once in, get your data and move it around to the correct /home directory...

Worst case, boot with a Live CD, and get your data before reinstalling.

---

### Post by kakyoism on 2008-05-26
maybe create "dave" as admin, and then delete ur previous account?
if the home folder of the old guy was still there, just
```
sudo rm -rdf /home/oldguy
```

I had the exact same problem and I solved it this way.

---

### Post by kakyoism on 2008-05-26
btw: you should use the "user and group" item in system->administration to remove user account first before removing the home folder

---

### Post by driebel on 2008-05-26
dave is an admin account, it's what I've been using exclusively for the ~3 months I've had my computer.  In my infinite wisdom, I decided I'd rather be driebel.  I created a new user "driebel" via "Users and Groups" in Gnome, who of course came into existence with none of my previous settings (.bash, e-mail accounts, etc.).  When I found this thread, this seemed like a better way to accomplish my goal.  I ran through tinivole's walkthrough, but couldn't carry out the last step, (renaming /home/dave) because /home/driebel already existed.  So, having accomplished most of that walkthrough, My ID was driebel, but my home directory didn't match.  I then used the GUI to remove user driebel, planing to start tinivole's guide over.  The GUI left /home/driebel, on the system, however.  Going through the usermod procedure again, I got the same error.  Apparently, the system HAD changed my home directory, despite the error.
Sorry to be so log winded, I'm just trying to be precise as to what happened.  As of now, there is only one user/group on my system, dave, which is an admin account.  the directory /home/dave contains all the settings I've known and loved for months.  /home/driebel is empty except for .gvfs, which I cannot seem to delete.  dave's home directory is /home/driebel, and I cannot log in.  I am going to attempt to start ubuntu in recovery mode from the boot menu (isn't that logging in as plain "root"?) and run 

usermod -d /home/dave dave  

with the intent of making dave's home directory /home/dave.  I will then live with my user name happily ever after, I promise. :)
I'd love advice or better plans, if someone smarter than me has any!  Again, all the files are there, I just need to tell ubuntu that dave's home directory is /home/dave, without logging in as dave.

I'm optimistic right now.  Using recovery mode logs me in as root, which should let me carry out my plan.  I'll wait a few hours for some wiser feedback, though.

---

### Post by driebel on 2008-05-26
Sorted.  Using recovery mode let me use usermod to put the existing /home/dave directory together with the dave user.  Maybe a few weeks from now, when I'm sure there are no other folders in /home, I'll try this again, but not for a long time!  Thanks all!

---

### Post by chang5562 on 2011-03-24
Following were my steps to switch the default user (and remove the old one)
1. use old user to login
2. run *sudo users-admin*: add the 'new' user and edit the privileges (check "administer the system")
3. click 'Advanced' tab, select the Main group: <new>, user ID: <new id>
- OK the change.
4. run *sudo gksu /usr/sbin/gdmsetup*
5. click 'Security' tab, change 'Enable Automatic Login' and 'Enable Timed Login' to <new> user.
6. reboot the OS,  now the login at new user profile (the background will change)
7. user the gconf-editor to edit the <new> profile accordingly.
8. edit the /etc/gdm/gdm.conf find the <old> user to <new> user in 'Timedlogin'
9. reboot again
10. *sudo userdel -r <old_username>*  Note: perform this at last, ensure the new user profile is OK to use.
11.  check the content of /etc/group, no more old user name there.

---

