---
title: "Ubuntu 7.04 User Permissions Problem"
date: 2007-05-24
forum: General Help
---

### Post by bumcheekcity on 2007-05-24
I want my family to have a PC with Ubuntu 7.04, but I DONT want them to have admin/root access to the PC. So, I created a user called 'family' for them to use, but want to disallow them from being able to have root access, and either allow myself to log on as root, or create another user, probably called 'andreas' with root priviliges. How do I do this.

---

### Post by codesplice on 2007-05-24
Try Settings-->Administration-->Users and Groups.  Click "Add User", and under Profile select "Unprivileged".  That should do it :)

---

### Post by strixy on 2007-05-24
A new user account is created without root access by default. You have to kind of go out of your way a little to give them root access.(see /etc/sudoers file)

You could create a user for each of your family members and then create a group "family". One idea would be to create a folder somewhere eg. /home/family/shared and chgrp that directory to "family". Then set permissions to 774. That will give them all access to the directory. If you then create symlinks in the users home directory to that shared directory you will give them all access to it. (I use that for sharing files with my roommate who also uses my computer). Each user could also set the group (chgrp) to "family" for any other folders or files that they may wish to share.

Better yet, but a little more challenging... before you create the new users, create a symlink in /etc/skel to /home/family/shared (all new accounts are modeled after whatever appears in /etc/skel ). If that symlink is there, it will appear in any new users directory when you create their account. Also, any files you place in /etc/skel will be copied to the new users home directory. You can place a welcome.txt file in there for your new users or a custom desktop image, or custom configuration files, etc... it's a very handy trick.

---

### Post by bumcheekcity on 2007-05-24
Thanks for the advice strixy, but I'm a little new and need it to be slightly simpler than that :D

I just want ONE account for my family, and one account for me, they'll all happily use the same account. I just want, you know when you open (for example) Synamptic Package Manager, and it asks you for your password, for them to be disallowed access to that stuff, but me to be able to access it on my other account.

What's the difference between root permissions, and between the permissions of the user you create when you initially install Ubuntu?

---

