---
title: "Multiple Users one desktop item?"
date: 2008-06-21
forum: General Help
---

### Post by Cyberpawz on 2008-06-21
I am using the Ubuntu Desktop OS and have found myself needing help. I have five users on my computer, with me being the admin. 

I need to have show up hard links, or links to folders to show up on all user's desktops when they log into their account. This is so they have access to all the same files. 

How can I get this done?

---

### Post by pytheas22 on 2008-06-21
This should be pretty easy to do.  If I understand correctly, you have one directory somewhere on the system (where is it?) containing a bunch of files, and you want to create an icon on every user's desktop that when clicked will open the shared directory.

For this to work, first make sure that all users have read (and, if you want the users to be able to edit and delete files, write) permissions to that folder.  You can set permissions by logging in as the user who owns the folder, right-clicking on it and selecting Properties.  Then under the permissions tab you can change access policies.  Make sure to check to box to apply the policies to subfolders as well.

Then for each user on the computer, right-click on the desktop and select Create Launcher.  In the Name field enter whatever you like, and in the command field enter "nautilus [location of shared folder]"  So if the shared folder is at /home/shared, the command would be:
```

nautilus /home/shared
```

There are other ways to do this, but I think that this is the simplest.  Please let us know how it goes.

---

