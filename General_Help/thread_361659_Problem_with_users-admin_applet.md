---
title: "Problem with users-admin applet"
date: 2007-02-14
forum: General Help
---

### Post by quark_77 on 2007-02-14
Hi all,

Not sure where this post should go, so here it is:

For reasons I don't understand users-admin, the user admin applet that comes with gnome no longer displays the users I have on my system, with the exception of the root. /etc/passwd and /etc/group are obviously full of users and groups I had set up before this problem and they can still log in without problem, both on the tty's and via gdm. Screenshot attached.

My question is, how do I persuade users-admin to display my user list again and if this fails how do I manage users from the command line. I know I can use sudo adduser, but how would I delete users or change their group, user details etc?

Thanks in advance for your help!

Quark_77

---

### Post by John.Michael.Kane on 2007-02-14
This is just a guess.

You tried clicking on manage groups and manually adding the need people?

Also to delete users via the terminal.

This should remove the user and their home directory
sudo userdel -r username



To modify a user

 sudo usermod - option username

Options:

    * -d home directory
    * -s starting program (shell)
    * -p password
    * -g (primary group assigned to the users)
    * -G (Other groups the user belongs to)

Example: To add the group 'others' to the user 
sudo usermod -Gothers usersname


Hope this offers some help.

---

### Post by quark_77 on 2007-02-25
Cheers SP-Plissken,

As may be fairly obvious I am new to Ubuntu hence the disappearing users unsettled me somewhat. I think I must have customised users groups at some point which probably confused the applet. I have restored all the users to their own groups (eg a user fred has primary group fred) and added other groups using -G now.

The applet still doesn't work, but the command line and editing /etc/passwd and /etc/group is much more fun. Two questions though:
[LIST]
[*]How do I remove a user from a group (say, out of the admin group)?
[*]When I create a new user I take it I need to assign the following groups to it via -G: adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse
[/LIST]
If anyone else has any suggestions as to how I can fix the users-admin applet it would be much appreciated!!

Thanks again,

Quark_77

---

